.. _material:

A generic material object
===================================

The `Material` class is used as a communication protocol between the different components of `simdatframe`. If follows a simple schema:

    Every material can be identified by a unique identifier, the `mid`. This identifier is usually set by the `API`, and can be reversed to obtain the original data from the external database.

    Most materials have atomic structures associated with them. Because this property is not always known, it can be optional.

    All data that is obtained from external databases is stored in the materials `data` attribute.

    All data that is computed using `simdatframe` is stored in the materials `properties` attribute.

.. automodule:: simdatframe.material
    :members: