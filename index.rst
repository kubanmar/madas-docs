.. simdatframe documentation master file, created by
   sphinx-quickstart on Thu Jul 22 16:34:52 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

The Similarity Data Framework
=======================================

This package attempts to provide a convenient, easy-to-use solution for the analysis of similarity relations between data entries.

It's main focus is on materials data, computed or measured in materials science.

A typical use case would be the analysis of a set of calculations in computational materials science (CMS). It is assumed that these calculations are carried out *a priori* and the results are available either from an external database (*e.g.* the `NOMAD Laboratory <https://nomad-lab.eu/>`_), or can be loaded from a local directory using a custom parser. Each of those calculations is a *data point*.

In a separate next step, the data is used to calculate *fingerprints* of the database entries. In this context, we call *fingerprints* the combination of a *descriptor*, *i.e.* a specified, numeric representation of the data, and a *similarity measure*, *i.e.* a function that, given two descriptors, numerically evaluates the similarity between the data points.

The fingerprints can be used to calculate a *similarity matrix*, which stores all pairwise similarities between data points. While not ultimately necessary, this operation simplifies the analysis of the data, as repeated calculation of similaties can be avoided. The similarty matrices provide several convenient functions to save, load and manipulate the matrix elements.

The package is completed by methods to facilitate the similarity matrices for supervised and unsupervied machine learning (ML) applications.

.. toctree::
   :maxdepth: 1
   :caption: Contents

   about
   install
   modules <modules>
   contact


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
