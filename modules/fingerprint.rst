.. _fingerprint:

The Fingerprint base class
==================================

The fingerprint object provides a base class for the generation of material fingerprints.

It can use :class:`Material <madas.material.Material>` objects as input.

Usage
---------------------------------

All built-in fingerprints can be generated from the base class:

.. code-block:: python

      from madas import Fingerprint

      dos_fingerprint = Fingerprint("DOS", **<dos_fingerprint_kwargs>).from_material(<material>, **dos_fingerprint_calculate_kwargs)

This is equivalent to calling:

.. code-block:: python

      dos_fingerprint = Fingerprint("DOS", **<dos_fingerprint_kwargs>).calculate(<material>.data["dos_energies"], <material>.data["dos_values"], **dos_fingerprint_calculate_kwargs)

The fingerprints can be customized by passing (expected) keyword arguments to the initialization and to the ``calculate`` method.

The similarity to other materials can be calculated for single or many fingerprints:

.. code-block:: python

   single_similarity = dos_fingerprint.get_similarity(<other_dos_fingerprint>)

   many_similarities = dos_fingerprint.get_similarities(<list_of_other_fingerprints>) 

Custom fingerprint generation
--------------------------------

New types of fingerprints can be defined as child classes of ``Fingerprint``. 
Say, you want to generate a fingerprint that compares the highest atomic number of the elements of a material.
The corresponding code would look like this:

.. code-block:: python

   from ase import Atoms

   from madas import Material, Fingerprint

   def MAN_similarity(fingerprint1, fingerprint2):
      """
      Calculate similarity between two MANFingerprint objects.
      """
      # extract data from fingerprint objects
      man1 = fingerprint1.data["maximum_atomic_number"]
      man2 = fingerprint2.data["maximum_atomic_number"]
      # calculate absolute distance
      atomic_number_differences = abs(man1 - man2)
      # convert distance to similarity
      similarity = 1/(1 + atomic_number_differences)
      # return value 
      return similarity

   class MANFingerprint(Fingerprint):
      """
      (M)aximum (A)tomic (N)umber fingerprint.

      Example fingerprint that compares the highest atomic number of the elements of a material.
      """

      # This declaration can be skipped.
      # However, it is advised to explicitly write the `__init__` function.
      def __init__(self, 
                  name = "MAN", 
                  similarity_function=MAN_similarity, 
                  pass_on_exceptions=True) -> None:
         # set the fingerprint type name
         self.set_fp_type("MAN")
         # set a name of the specific fingerprint
         self.set_name(name)
         # set if the fingerprint shall raise an exeption if anything fails
         self.set_pass_on_exceptions(pass_on_exceptions)
         # set the similarity function used to calculate similarity values
         self.set_similarity_function(similarity_function)
         
      def calculate(self, atoms: Atoms):
         # get the maximal atomic number from ASE Atoms object
         atomic_numbers = atoms.get_atomic_numbers()
         max_atomic_number = max(atomic_numbers)
         # REQUIRED: set the fingerprint data
         self.set_data("maximum_atomic_number", max_atomic_number)
         # REQUIRED: return self
         return self

      def from_material(self, material: Material):
         # REQUIRED: set the material identifier for this fingerprint
         self.set_mid(material)
         # use obtain properties from the material object 
         atoms = material.atoms
         # calculate the fingerprint
         self.calculate(atoms)
         # REQUIRED: return self
         return self
         
Note that two methods are required: a `calculate` method to compute the fingerprint directly from data,
and a `from_material` method that collects the required data from a :class:`Material <madas.material.Material>` 
object and calls the `calculate` method internally.

Documentation
------------------------------

The documentation of all methods and parameters can be found below:

.. autoclass:: madas.fingerprint.Fingerprint
   :members:

Built-in fingerprints
------------------------------


.. toctree::
   :maxdepth: 2

   DOS Fingerprint <../material_fingerprints/dos_fingerprint>
   DUMMY Fingerprint <../material_fingerprints/dummy_fingerprint>
   PROP Fingerprint <../material_fingerprints/prop_fingerprint>
