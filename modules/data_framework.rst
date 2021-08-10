.. _data_framework:

The data framework
==================================

The data framework is the basic building block of a data analysis workflow. Data that may be gathered from different sources can be stored in a local database, to provide a fixed source of data, which does not change, *e.g.* if the external data source is altered. Thus, the analysis is repeatable and the results retain reproducible.

To initialize a database, first import the class and initialize it by:

.. code-block:: python

    from simdatframe import MaterialsDatabase
    database = MaterialsDatabase(filename = 'materials_database.db')

You now created a handle to a database, that will be populated when data is added. The default value for the data source (accessed through an :class:`API <simdatframe.apis.api_core>`) is the `NOMAD Encyclopedia <https://nomad-lab.eu/prod/rae/encyclopedia/#/search>`_.

To populate our newly created database, we can query the NOMAD Encyclopedia for calculations using the NOMAD API:

.. code-block:: python

    query = {"search_by":
                {"elements" : ["Cu","Pt"],
                 "exclusive" : True,
                 "restricted" : True,
                 "page" : 1,
                 "per_page" : 10},
            "has_dos" : True }

    database.fill_database(query)

This results in the following output:

.. code-block:: bash

    2021-08-09 19:23:00,387 - materials_database_log - INFO - Filling database with calculations matching the following query: [{"search_by": {"elements": ["Cu", "Pt"], "exclusive": true, "restricted": true, "page": 1, "per_page": 10}, "has_dos": true}]
    2021-08-09 19:23:00,931 - test_database_api - INFO - Got materials list.
    Fetching materials 100.000 %

    2021-08-09 19:23:09,325 - materials_database_log - DEBUG - Writing material with mid zgtIgKraH-dRLaVoymLy6Smka9UB:VLAMlHghn_Jw4rpW9E1-a99Qnb5V
    2021-08-09 19:23:09,349 - materials_database_log - DEBUG - Writing material with mid W7OJrUcN0u2MnlZYPS_96xvDVsN0:tZm0lAa62jOaQzClW9Rr59BscuCD
    2021-08-09 19:23:09,372 - materials_database_log - DEBUG - Writing material with mid rRlX4tbBdjCJfQao8KQbnzZSflKt:B_LdPJCFFO22Cx_DnWl4rDDNaPDK
    2021-08-09 19:23:09,397 - materials_database_log - DEBUG - Writing material with mid USYKyJAarPTHpp20Fpq_EMFqc8jd:xgiVvRBHcksVqjmwAuoW31c1HGti
    2021-08-09 19:23:09,424 - materials_database_log - DEBUG - Writing material with mid vggeFkbJ8Qz36KHe6KA9XkDH49Ae:nqe6o-XEF7-3158xTc2y8see48eU
    2021-08-09 19:23:09,458 - materials_database_log - DEBUG - Writing material with mid r5jsnDz1ny8cAEZjDT3gxjPT3PmN:OY54HPksvaA8cmvB8r0NJbcNJsan
    2021-08-09 19:23:09,493 - materials_database_log - DEBUG - Writing material with mid 77mm5w5zS0BZgzWBZ1y7P8ICWmt2:uiiDcDRIm6ZdE__7zrtmInhD9BIJ
    2021-08-09 19:23:09,518 - materials_database_log - DEBUG - Writing material with mid mxRCD-wtKG4Za5Tv8LEj8iwpxrIp:tPjWX4cYiLIo8xWRPWRs25tJWE6M
    2021-08-09 19:23:09,543 - materials_database_log - DEBUG - Writing material with mid 6TqhC_bIgwwzoa0bh1ofupUq2qbw:SXi1cv-om8A4uKdUIooHmlLnpJ0q
    2021-08-09 19:23:09,567 - materials_database_log - DEBUG - Writing material with mid JF8fyvkzXDpwx4bpqWlti7QEUZHs:M_4jMsGtPcMGTqMxCfFVF0xw1ODq
    2021-08-09 19:23:09,592 - materials_database_log - DEBUG - Writing material with mid lWd5Ly5rn08lg3uIZ843NdLi1nMr:fNYyPFEpHxrVoxICAx-vkTCluM18

This output is not always the same, because at the time this 

.. automodule:: simdatframe.data_framework
    :members: