============================
Data Management Plans (DMPs)
============================

Introduction
============
From the UBC library `website <https://researchdata.library.ubc.ca/plan/>`_:

    A Data Management Plan (DMP) is a document you create that sets out how you will organize, store and share your research data at each stage in your project.  A DMP is a living document that can be modified to accommodate changes in the course of your research.

DMPs are increasingly becoming a part of grant applications. 
Granting agencies such as the Canadian Institutes of Health Research (CIHR), the Natural Sciences and Engineering Research Council of Canada (NSERC), the Social Sciences and Humanities Research Council of Canada (SSHRC) and the Canadian Foundation for Innovation (CFI) require that the research they fund is conducted using best practices in data management for the following reasons:

* To ensure that data management practices align with ethical and legal requirements. This includes animal and patient ethics, university policy, granting agency and government requirements.
* To ensure that research data is accessible, reusable, and stored properly. This includes data standardisation, backup, documentation, and metadata.
* To foster open science practices to enhance research productivity and quality.

Developing a DMP
================
The white paper is intended to aid PIs in developing DMPs. In addition to this, the following resources are available: 

UBC Library
-----------
The UBC library provides resources for Research Data Management through its `website <https://researchdata.library.ubc.ca/>`__. Additionally, research data librarians can be contacted at research.data@ubc.ca

DMP Assistant (Portage) 
-----------------------
`Portage <https://portagenetwork.ca/>`__ was launched by the Canadian Association of Research Libraries and works with 
libraries to enhance shared stewardship of data. This includes availing expertise such as research librarians and services and 
technologies such as the `Federated Research Data Repository <https://ubcbraincircuits.readthedocs.io/en/latest/data_sharing/frdr.html>`_ 
and the Portage `DMP Assistant <https://assistant.portagenetwork.ca>`_, a step-by-step tool for preparing a data management plan. 
Under *Data Management Planning* of section 3, the :ref:`Tri-Agency Statement of Principles on Digital Data Management <tri-agency-principles>` states that DMPs 
should be developed using standardized tools, where available. It is therefore highly recommended that researchers use the 
Portage DMP Assistant for Canadian funders [#]_. 

Additional Resources
====================

Metadata 
--------
Metadata is data that describes data. Ideally, all datasets should be accompanied by, at minimum, metadata that fully describes the 
dataset such that lab members, external collaborators and preferably, any user, can reproduce or extend the study. 

Resources on research data metadata and metadata standards:

* UBC Library - `Document and Describe <http://researchdata.library.ubc.ca/plan/document-describe-your-data>`_
* University of Western Australia -  `Research Data Management Toolkit: Documentation <https://guides.library.uwa.edu.au/RDMtoolkit/documentation>`_
* Cornell University - `Research Data Management Service Group: Metadata and describing data <http://data.research.cornell.edu/content/writing-metadata>`_
* `FairSharing <http://fairsharing.org>`_  is a curated, informative, and educational resource on data and metadata standards, inter-related to databases and data policies.

File Naming Conventions
-----------------------
File naming conventions should be interoperable between different computer systems (length, special characters, and case sensitivity), 
eliminate ambiguity, support versioning, be concise, and be conscious of directory structure and hierarchy.

Resources on file naming conventions:

* UBC Library - `Organize <http://researchdata.library.ubc.ca/plan/organize-your-data>`_
* The University of Edinburgh - `Naming Conventions <http://ed.ac.uk/records-management/guidance/records/practical-guidance/naming-conventions>`_
* Stanford Libraries - `Best Practices for File Naming <http://library.stanford.edu/research/data-management-services/data-best-practices/best-practices-file-naming>`_

Best Practices from Exemplar Labs
---------------------------------

* The **3-2-1 Backup Rule**: At the very least, research data should have 3 copies, with 2 copies on different media and 1 copy off-site. This includes having 2 UBC copies.
* As part of your DMP, set up infrastructure, services, and training to ensure that at worst, **only one day of work can be lost in the event of an emergency**.
* **All data is accompanied by a metadata file**. Secondary data is accompanied by a wiki article describing how the data was processed and analysed.
* **Automated metadata entry** for experimental data. 

	- Example 1: `Murphy Lab dataset on Zenodo <http://doi.org/10.5281/zenodo.3268838>`_ 
	- Example 2: `Alyx <http://github.com/cortex-lab/alyx>`_ 
	
* **Backup snapshots** of all workstations and the central data storage servers. 

.. [#]  For US funders, such as the NIH and NSF, use the analogous `DMP Tool <https://dmptool.org/>`_.