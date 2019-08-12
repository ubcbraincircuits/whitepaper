==============
Workflow Tools
==============

.. toctree::	
	:caption: Table of Contents
	:maxdepth: 3
	
	workflows

Assisted Metadata Entry
=======================
Researchers need to be proviced with an easy to use lab notebook
for metadata entry and experiment registration with enforced entry requirements.
Preferrably, this should operate with relational database backend.
This would ensure that at least a minimum amount of metadata and documentation 
are available for each experiment, that the data are well catalogued, 
searchable and shareable.

This could also lead into automated data pipelines for automatic 
processing of raw data and data preservation/storage, which would 
be a valuable tool for experiments with routine workflows and should 
reduce the time it takes to organise and curate experimental data manually.

Alyx
----
The International Brain Lab at UCL has created a `tool <https://alyx.readthedocs.io/en/latest/>`_ 
built using python on a Django web framework with a 
PostregeSQL database system, which when deployed provides users 
with a web interface that they can use to log the metadata 
for their experiments. 
Features include templated input forms, user account control, 
search, date range filtering and data administration.
The version of Alyx currently on `Github <https://github.com/cortex-lab/alyx>`_ 
is adapted for mouse brain imaging experiments, but a system like this 
could be implemented with different templates for different experiment groups 
provided based on this framework.
A major benefit of this kind of architecture is the ability to deploy 
it on a web server to allow centrallised remote access.

Data Pipelines
==============
A data pipeline is an automated system that can be used to retrieve data from multiple sources 
and manage dependencies in data processing that would otherwise take time and effort to do 
manually. 

Consider the example below:

.. image:: ../Images/pipeline.jpg

Even a simple workflow like this would be tedious to do manually, and can easily be automated for 
routine procedures, such as data cleaning routines on freshly ingested experiment data.

Several free pipeline frameworks are available:

* Python: `Luigi <https://luigi.readthedocs.io/en/stable/>`_, `Airflow <https://airflow.apache.org/>`_, `Pinball <https://github.com/pinterest/pinball/blob/master/USER_GUIDE.rst>`_ and `DataJoint <https://docs.datajoint.io/python/index.html>`_
* MATLAB: `DataJoint <https://docs.datajoint.io/matlab/index.html>`_