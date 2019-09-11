==========
JupyterHub
==========

Introduction
============
JupyterHub is a multi-user notebook server, allowing multiple users to access a pool of resources for interactive analysis. 

We have collaborated with the Pacific Institute for Mathematical Sciences to deploy an instance of a JupyterHub on Alder, the DMCBH compute cluster, which can be accessed `here <https://jupyter.alder.arc.ubc.ca/>`_.

Python 3.7.4 (`list of packages <https://github.com/ubcbraincircuits/whitepaper/blob/master/source/jupyterhub/python_packages.txt>`_) and R 3.6.1 (`list of packages <https://github.com/ubcbraincircuits/whitepaper/blob/master/source/jupyterhub/r_packages.txt>`_) kernels are currently installed, with multiple packages already available.

Benefits and features:

* Shared filesystem for quick collaboration
* Work anywhere from any device
* Access more powerful compute resources than a single workstation
* All standard Jupyter Notebook features, including a Text editor, file manager and Command Line Interface 

.. note:: 
   To use the JupyterHub, you must 1) be affiliated with the cluster and 2) have an account on Alder. To obtain an account on Alder, you must be sponsored by your PI and you must send an account request to arc.support@ubc.ca 
   
   To install packages, contact `Jeffrey LeDue <mailto:jledue\@mail.ubc.ca>`_ with your requirements.

Resource Allocation
-------------------
Currently, when users log in to a notebook session, they are allocated the following resources: 4 CPUs and 16 GB RAM. 

Future Directions for Resource Allocation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Uniform resource allocation for each user, much like the current configuration, for demonstrations and workshops. User accounts will be generated on an as needed basis.
2) Users will be given a list of configurations to choose from so as to be allocated the resources they need.
3) A schedule for resource allocation requests, whereby researchers can request dedicated resources and compute time to ensure they have sessions and resource availability when needed. This would mean that certain nodes will not be accessible through the dynamic scheduler in 2) and will only be available to a user/group of users on a manually administered queue.

.. tip::
   PIs are encouraged to advocate for additional resources for cluster upgrades. This includes GPUs, storage backup, and other computational resources.
