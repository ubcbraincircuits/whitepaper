.. UBC Dynamic Brain Circits Cluster Whitepaper documentation master file, created by
   sphinx-quickstart on Tue Jun 18 10:48:04 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

============================================================
Welcome to the UBC Dynamic Brain Circits Cluster Whitepaper!
============================================================

Overview
========

The Dynamic Brain Circuits and Connections in Health and Disease research cluster is composed of researchers across departments and faculties united by their collective 
pursuit of advancing the study of brain connections and their dynamic changes during development, learning, and disease. This white paper aims to provide information, 
recommendations, and best practices in data management to aid labs in the Brain Circuits cluster, and the greater DMCBH community, to develop and maintain Data Management Plans 
(DMPs). This includes considerations to data storage, data sharing, research data workflows, and data stewardship throughout the research life cycle. 

We are addressing a global shift towards Open Science and the pressing need within the cluster for secure data storage throughout the research process, from collection to 
long-term preservation. There is an understandable reluctance to invest time, money, and effort into data sharing and there are also potential risks involved, including misuse 
and misinterpretation of data, and inappropriate or absence of proper assignment of scientific credit [#]_. We therefore encourage cluster labs to recognize that the potential and 
demonstrated benefits of being scientifically open can greatly outweigh its drawbacks. Data sharing and transparency increases reliability and reproducibility of research 
findings and promotes collaboration. Many journals, repositories, and funding agencies now require or encourage open data, and several grant agencies now require researchers to 
outline their data management and sharing plans [#]_. Sharing data can also boost citation count [#]_, [#]_ and a proven record of open science can positively impact careers of both new and 
established neuroscientists. 

We present a number of possible solutions to data management, the selection of which was guided by UBC standards and legal and ethics policies. Since some of the services 
outlined in the paper are in development, we created this website to update the information presented in the document. This website contains example use cases, demonstrations, 
and documentation to aid in training and to speed up adoption. The primary purpose of the white paper and is to reduce the barriers that deter or hinder the implementation 
of DMPs and data sharing within the cluster. 

In pursuit of this goal, we have also provisioned resources for the use of the cluster, including:

* `Dataverse <https://dataverse.scholarsportal.info/dataverse/UBC_BrainCircuits>`__
* `Federated Research Data Repository collection <https://www.frdr.ca/repo/handle/ubcbraincircuits>`__
* `JupyterHub <https://jupyter.alder.arc.ubc.ca/>`__
* `GitHub Team Repository <https://github.com/ubcbraincircuits>`__

Contents
========

.. toctree::
   :maxdepth: 1
   :caption: Data Management and Data Sharing
   
   ethics_legal/federal
   ethics_legal/tri-agency
   ethics_legal/index
   dmp/index
   data_storage/index
   data_sharing/index

.. toctree::
   :maxdepth: 1
   :caption: Workflow Tools 
   
   workflows/index

.. toctree::
   :maxdepth: 1
   :caption: HPC, Tutorials and Examples

   alder_compute_canada/index
   backups/index
   encryption/index
   jupyterhub/index

.. toctree::
   :maxdepth: 1
   :caption: Appendices

   upcoming/index
   term_definitions
   abbreviations

   
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
	
.. [#] Gardner D, Toga AW, Ascoli GA, et al. Towards effective and rewarding data sharing. Neuroinformatics. 2003;1(3):289-295. doi:10.1385/NI:1:3:289
.. [#] Spires-Jones TL, Poirazi P, Grubb MS. Opening up: Open access publishing, data sharing, and how they can influence your neuroscience career. Eur J Neurosci. 2016;43(11):1413-1419. doi:10.1111/ejn.13234
.. [#] Piwowar HA, Day RS, Fridsma DB. Sharing Detailed Research Data Is Associated with Increased Citation Rate. Ioannidis J, ed. PLoS One. 2007;2(3):e308. doi:10.1371/journal.pone.0000308
.. [#] Piwowar HA, Vision TJ. Data reuse and the open data citation advantage. PeerJ. 2013;1:e175. doi:10.7717/peerj.175