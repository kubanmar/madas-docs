.. _nomad_archive_api:

An API for NOMAD Archive entries
===================================

The `NOMAD project <https://nomad-lab.eu>`_ provides a rich database of both theoretical and experimental FAIR materials-science data. 
To access this data, the NOMAD Graphical User Interface (GUI), or the web Application Programming Interface (API) can be used.
To do so, a query has to be defined, that can be sent to the NOMAD servers. If data matches this query, the corresponding data will be returned.

`MADAS` provides a wrapper for the NOMAD API, that allows users to query NOMAD and recieve the results as :doc:`Material </modules/material>` objects. 
Then, the data can be processed and filtered to be stored in a :doc:`database </modules/data_framework>`. 

A complete tutorial with examples is in :doc:`the tutorials section </tutorials/0_API_usage>`. 

.. automodule:: madas.apis.NOMAD_web_API
    :members: