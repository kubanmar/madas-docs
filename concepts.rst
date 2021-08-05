.. _concepts:

The basic concepts
===================================

The main idea of the package is to provide an interface that allows to analyse data sets on a local machine, by the generation of *fingerprints* (often also called *descriptors*). These fingerprints are completed with any quantitative similarity measure, which allows to determine similarity relations between the data points.
This is achieved through a modular structure of the package. 
The basic components, i.e. the database, fingerprints, similarity matrices, and machine learning (ML) algorithms, can be used both stand-alone and or in combination. Thus, all aspects of the analysis are under complete control of the user, and subsequent steps can be adressed individually.
To achieve a decent amount of extendability, the code is structured through *adapters* and *abstract classes*. These provide starting points to change the program behaviour and adapt to the needs of a user.