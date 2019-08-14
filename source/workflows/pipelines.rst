=========
Pipelines
=========

Data Pipelines
==============
A data pipeline is an automated system that can be used to retrieve data from multiple sources and manage dependencies in data processing that would otherwise take time and effort to do manually. Various forms of automation can be integrated into a pipeline to create powerful and robust systems.

Pipelines are useful for researchers who need to:

* Produce or use large volumes of data from different sources
* Require real time output
* Perform analytics with a complex logical flow

Pipelines, when implemented correctly, have benefits like:

* Enhanced productivity due to automation
* Greater reproducibility
* Quality assurance through automated testing and checks

Frameworks have been developed to build data pipelines, and have been tried and tested by multiple organisations and research institutions, such as:

* Python - Luigi, Airflow, Pinball, DataJoint
* R - Drake
* MATLAB - DataJoint

DataJoint
---------
Best use: ideal for MATLAB/Python-proficient users 

DataJoint [datajoint.io] is a free and open toolbox for building scientific data platform using Python, MATLAB, or both. It was developed by neuroscientists in Andreas Tolias’ lab at the Baylor College of Medicine. DataJoint provides data integrity and accessibility with intuitive language for defining, querying, and visualizing data pipelines. Through DataJoint’s relational data model, users can automate data entry, processing, and analysis by simply storing data in tables. Relationships between tables enforces data integrity while efficient querying is achieved by performing operations on tables. 

A GUI such as Heidi SQL can be used to enter and view data but data pipelines must be defined in a Python or MATLAB environment. DataJoint is therefore ideal for labs with members that are already familiar with these languages, otherwise its use will require extensive training. DataJoint has both documentation and tutorials, which are easy to follow and conveniently uses neuroscience examples. 

DataJoint enables multi-user access and the ability to grant privileges hence collaboration among researchers is simplified, particularly through features that prevent duplicated, missing, and otherwise erroneous data. 
Note that this platform entails resource considerations. DataJoint relies on a database server which can be self- or cloud-hosted. Depending on the scale of its use and the number of users, significant IT support  may be needed to establish a database server and hardware may also be required to accommodate DataJoint. The complexity of the setup and configuration depend entirely on the needs of the lab.

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