.. _data_framework:

The data framework
==================================

The data framework is the basic building block of a data analysis workflow. Data that may be gathered from different sources can be stored in a local database, to provide a fixed source of data, which does not change, *e.g.* if the external data source is altered. Thus, the analysis is repeatable and the results retain reproducible.

Creating a new database
__________________________________

To initialize a database, first import the class and initialize it by:

.. code-block:: python

    from simdatframe import MaterialsDatabase
    database = MaterialsDatabase(filename = 'materials_database.db')

You now created a handle to a database, that will be populated when data is added. 
The default value for the data source (accessed through an :class:`API <simdatframe.apis.api_core>`) is the `NOMAD Encyclopedia <https://nomad-lab.eu/prod/rae/encyclopedia/#/search>`_.

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

    2021-08-09 19:23:09,325 - materials_database_log - INFO - Writing material with mid zgtIgKraH-dRLaVoymLy6Smka9UB:VLAMlHghn_Jw4rpW9E1-a99Qnb5V
    2021-08-09 19:23:09,349 - materials_database_log - INFO - Writing material with mid W7OJrUcN0u2MnlZYPS_96xvDVsN0:tZm0lAa62jOaQzClW9Rr59BscuCD
    2021-08-09 19:23:09,372 - materials_database_log - INFO - Writing material with mid rRlX4tbBdjCJfQao8KQbnzZSflKt:B_LdPJCFFO22Cx_DnWl4rDDNaPDK
    2021-08-09 19:23:09,397 - materials_database_log - INFO - Writing material with mid USYKyJAarPTHpp20Fpq_EMFqc8jd:xgiVvRBHcksVqjmwAuoW31c1HGti
    2021-08-09 19:23:09,424 - materials_database_log - INFO - Writing material with mid vggeFkbJ8Qz36KHe6KA9XkDH49Ae:nqe6o-XEF7-3158xTc2y8see48eU
    2021-08-09 19:23:09,458 - materials_database_log - INFO - Writing material with mid r5jsnDz1ny8cAEZjDT3gxjPT3PmN:OY54HPksvaA8cmvB8r0NJbcNJsan
    2021-08-09 19:23:09,493 - materials_database_log - INFO - Writing material with mid 77mm5w5zS0BZgzWBZ1y7P8ICWmt2:uiiDcDRIm6ZdE__7zrtmInhD9BIJ
    2021-08-09 19:23:09,518 - materials_database_log - INFO - Writing material with mid mxRCD-wtKG4Za5Tv8LEj8iwpxrIp:tPjWX4cYiLIo8xWRPWRs25tJWE6M
    2021-08-09 19:23:09,543 - materials_database_log - INFO - Writing material with mid 6TqhC_bIgwwzoa0bh1ofupUq2qbw:SXi1cv-om8A4uKdUIooHmlLnpJ0q
    2021-08-09 19:23:09,567 - materials_database_log - INFO - Writing material with mid JF8fyvkzXDpwx4bpqWlti7QEUZHs:M_4jMsGtPcMGTqMxCfFVF0xw1ODq
    2021-08-09 19:23:09,592 - materials_database_log - INFO - Writing material with mid lWd5Ly5rn08lg3uIZ843NdLi1nMr:fNYyPFEpHxrVoxICAx-vkTCluM18

This output is not always the same, because the data in the NOMAD Encyclopedia may be extended in the future. 
Thus, new materials may be added or the definition of the material representative may change.

When checking your local directory you'll recognize a new folder with the name ``data``. This folder contain the database file and the log files. 

Let's inspect some arguments of the ``MaterialsDatabase()`` to see how we can customize this behavior.:

    * *filename*:

        As the name states, this is the name of the database file. When creating a ``MaterialsDatabase()`` with a non-existing file, the file will be created.
        If the file exists, the data will be loaded instead.

    * *db_path*:

        This file path - which can be an absolute or relative path name - is a string that points to the folder where the database file and the log files are stored.
        It's default value is ``'data'``. If any non-existing path is given, the directory tree will automatically be generated (using the `Python standard library <https://docs.python.org/3/library/os.html#os.makedirs>`_).

    * *silent_logging*:

        This parameter controlls if the logging information will be printed to the console during usage. To suppress the console output, set this parameter to `True`.


Adding material fingerprints
__________________________________

In the next step, we will add *material fingerprints* to determine the similarity of the materials we just downloaded.

We will be adding *DOS fingerprints*, which encode the electronic density-of-states of the materials.

To add the fingerprints directly to the database, simply use:

.. code-block:: python

    database.add_fingerprint('DOS')

You will see the following output:

.. code-block:: bash

    2021-08-10 14:05:34,509 - materials_database_log - INFO - Starting fingerprint generation for fp_type: DOS
    2021-08-10 14:05:34,776 - materials_database_log - INFO - Writing DOS fingerprints to database.
    2021-08-10 14:05:35,122 - materials_database_log - INFO - Finished for fp_type: DOS

The output represents the modular structure of the code:

First, a list of fingerprints is generated and stored in memory.
Afterwards, the fingerprints are written to the database.
The last log info tells us that writing the fingerprints is finished.

You can learn more about fingerprints in the :doc:`fingerprint module description </modules/fingerprint>`.

The remaining parameters and methods can be found below.

.. automodule:: simdatframe.data_framework
    :members: