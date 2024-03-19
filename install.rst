.. _install:

Installation guide
===================================

This page shows different ways to install the package.

Installation from PyPI
++++++++++++++++++++++++++++++++++

The newest stable releases are available via `pip`:

```bash
pip install madas
```

Installation from source
++++++++++++++++++++++++++++++++++

Currently, the code can be installed only through the git project. You can clone the project using:

.. code-block:: bash

    git clone git@github.com:kubanmar/madas.git

After cloning, you can enter the project folder and install the package using ``pip``:

.. code-block:: bash

    cd madas
    pip install .
    cd ..

Running tests
++++++++++++++++++++++++++++++++++

After installation, it is advised to test the code. This can be done in the same directory of the code, using ``pytest``, which will be installed as a dependency via pip.

.. code-block:: bash

    pytest -v tests

The flag ``-v`` improves the test verbosity, so the output is more detailed. More details on ``pytest`` can be found `here <https://docs.pytest.org/en/latest/contents.html>`_ .
