==========
JupyterHub
==========

Introduction
============
JupyterHub is a multi-user notebook server, allowing multiple users to access a pool of resources for interactive analysis. 

Python 3.7.4 (`list of packages <https://github.com/ubcbraincircuits/whitepaper/blob/master/source/jupyterhub/python_packages.txt>`_) and R 3.6.1 (`list of packages <https://github.com/ubcbraincircuits/whitepaper/blob/master/source/jupyterhub/r_packages.txt>`_) kernels are currently installed, with multiple packages already available.

Benefits and features:

* Shared filesystem for quick collaboration
* Work anywhere from any device
* Access more powerful compute resources than a single workstation
* All standard Jupyter Notebook features, including a Text editor, file manager and Command Line Interface 

.. note:: 
   To use the JupyterHub, you must
   
   1. be affiliated with DMCBH 
   
   To install packages, contact `Jeffrey LeDue <mailto:jledue\@mail.ubc.ca>`_ with your requirements.

Resource Allocation
-------------------
Currently, when users log in to a notebook session, they can choose from the following resources:  

 * 4 CPUs and 16 GB RAM  
 * 8 CPUs and 32 GB RAM
 * 16 CPUs and 64 GB RAM
 * 32 CPUs and 128 GB RAM  
 * 16 CPUs and 256 GB RAM
 * 32 CPUs and 512 GB RAM
  

Future Directions for Resource Allocation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Uniform resource allocation for each user, much like the current configuration, for demonstrations and workshops. User accounts will be generated on an as needed basis.
2) Users will be given a list of configurations to choose from so as to be allocated the resources they need.
3) A schedule for resource allocation requests, whereby researchers can request dedicated resources and compute time to ensure they have sessions and resource availability when needed. This would mean that certain nodes will not be accessible through the dynamic scheduler in 2) and will only be available to a user/group of users on a manually administered queue.

.. tip::
   PIs are encouraged to advocate for additional resources for cluster upgrades. This includes GPUs, storage backup, and other computational resources.
