.. _about:

About the project
===================================

It is assumed that results are available either from an external database (*e.g.* the `NOMAD Laboratory <https://nomad-lab.eu/>`_), or can be loaded from a local directory using a custom parser.

Through an API, the data can be loaded to a local database, where the data is stored, can be extended and manipulated.

In a separate next step, the data is used to calculate *fingerprints* of the database entries. In this context, we call *fingerprints* the combination of a *descriptor*, *i.e.* a specified, numeric representation of the data, and a *similarity measure*, *i.e.* a function that, given two descriptors, numerically evaluates the similarity between the data points.

The fingerprints can be used to calculate a *similarity matrix*, which stores all pairwise similarities between data points. While not ultimately necessary, this operation simplifies the analysis of the data, as repeated calculation of similaties can be avoided. The similarty matrices provide several convenient functions to save, load and manipulate the matrix elements.

The package is completed by methods to facilitate the similarity matrices for supervised and unsupervied machine learning (ML) applications.