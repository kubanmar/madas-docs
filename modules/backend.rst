.. _backend:

Database connection wrappers
===================================

The data that was added to a MaterialsDatabase needs to be stored on disc or in memory, depending on the application. To allow for maximal flexibility, `MADAS` provides a abstract class that can be used as a framework for different database implementations. Thus, if, e.g., a different database is required that stores only spectra, it can be quickly implemented using the `Backend` class and integrated with all other components of `MADAS`. 

Each child of a `Backend` class should implement all methods listed below to ensure compatibility with the other components of `MADAS`.

.. automodule:: madas.backend.backend_core
    :members:

.. toctree::
   :maxdepth: 2
   :caption: Built-in backends

   ASE AtomsDatabase <../backends/ase_backend>
   DictBackend <../backends/dict_backend>

