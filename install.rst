.. _install:

Installation guide
===================================

Currently, the code can be istalled only through the git project. You can clone the project using:

.. code-block:: bash

    git clone git@git.physik.hu-berlin.de:kuban/similarity-data-framework.git [<target directory>]

After cloning, you can enter the project folder and install the package using ``pip``:

.. code-block:: bash

    cd similarity\_data\_framework
    pip install -e .

The installation may take some more minutes. 

Testing
===================================

After installation, it is advised to test the code. This can be done in the same directory of the code, using ``pytest``, which will be istalled as a dependency via pip.

.. code-block:: bash

    pytest -v tests

The flag ``-v`` improves the test verbosity, so the output is more detailed. More details on pytest can be found `here <https://docs.pytest.org/en/latest/contents.html>`_ .
