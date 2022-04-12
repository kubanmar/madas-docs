.. _backend:

Database connection wrappers
===================================

The data that was added to a MaterialsDatabase needs to be stored on disc or in memory, depending on the application. To allow for maximal flexibility, `simdatframe` provides a abstract class that can be used as a framework for different database implementations. Thus, if, e.g., a different database is required that stores only spectra, it can be quickly implemented using the `Backend` class and integrated with all other components of `simdatframe`. 

Each child of a `Backend` class should implement all methods listed below.

.. automodule:: simdatframe.backend.backend_core
    :members:

.. toctree::
   :maxdepth: 2
   :caption: Built-in backends

   ASE AtomsDatabase <../backends/ase_backend>
