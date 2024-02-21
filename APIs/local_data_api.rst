.. _local_data_api:

An API for loading local files
===================================

This API can be used to ingest data from a local directory. To do so, the API scans a directory, finding files that match a specific naming pattern.

The basic configuration requires the following file structure:

* root_directory
    * <properties.file>
    * directory[0]
        * <input.file>
    * directory[1]
        * <input.file>
    * ...

Where ``


.. automodule:: madas.apis.local_data_API
    :members: