============================
Data Management Plans (DMPs)
============================

Introduction
============
From the UBC library `website <https://researchdata.library.ubc.ca/plan/>`_:

    A Data Management Plan (DMP) is a document you create that sets out how you will organize, store and share your research data at each stage in your project.  A DMP is a living document that can be modified to accommodate changes in the course of your research.

DMPs are increasingly becoming a part of grant applications. 
Granting agencies such as the Canadian Institutes of Health Research (CIHR), the Natural Sciences and Engineering Research Council of Canada (NSERC), the Social Sciences and Humanities Research Council of Canada (SSHRC) and the Canadian Foundation for Innovation (CFI) require that the research they fund is conducted using best practices in data management for the following reasons:

* Ensuring that data management practices align with ethical and legal requirements. This includes animal and patient ethics, university policy, granting agency and government requirements.
* Ensuring that research data is accessible, reusable and stored properly. This includes data standardisation, backup, documentation and metadata.
* Fostering open science practices to enhance research productivity and quality

Important documents that should be read by all researchers include:
* The Tri-Agency Research Data Management Policy science.gc.ca/eic/site/063.nsf/eng/h_547652FB.html 
* Canada’s Commitment to Open Science canada.ca/en/treasury-board-secretariat/services/access-information-privacy/canada-commitment-open-science.html

Developing a DMP
================
This whitepaper is intended to aid PIs in developing DMPs. In addition to this, the following resources are available: 

UBC Library
-----------
The UBC library provides resources for Research Data Management, including this website and research data librarians who can be contacted at  research.data@ubc.ca

Portage 
-------
Portage was launched by the Canadian Association of Research Libraries and works with libraries to enhance shared stewardship of data. This includes availing expertise such as research librarians and services and technologies such as the `Federated Research Data Repository <https://ubcbraincircuits.readthedocs.io/en/latest/data_sharing/frdr.html>`_ and their `DMP Assistant <assistant.portagenetwork.ca>`_, a step-by-step tool for preparing data management tools. Researchers are highly recommended to develop their DMPS using this tool.

Additional Resources
====================
Metadata 
--------
Metadata is data that describes data. Ideally, all datasets should be accompanied by at least the bare minimum of metadata that fully describes them to target audiences including lab members and external collaborators.

Resources on research data metadata and metadata standards:

* UBC Library - `Document and Describe <researchdata.library.ubc.ca/plan/document-describe-your-data>`_
* University of Western Australia -  `Research Data Management Toolkit: Metadata Standards <guides.library.uwa.edu.au/c.php?g=325196&p=2178564>`_
* Cornell University - `Research Data Management Service Group: Writing Metadata <data.research.cornell.edu/content/writing-metadata>`_

File Naming Conventions
-----------------------
File naming conventions should carefully consider how they are interpreted by different computer systems, eliminate ambiguity, be concise, support versioning and be conscious of directory structure and hierarchy.

Resources on file naming conventions:

* UBC Library - `Organize <researchdata.library.ubc.ca/plan/organize-your-data`_
* The University of Edinburgh - `Naming Conventions <ed.ac.uk/records-management/guidance/records/practical-guidance/naming-conventions>`_
* Stanford Libraries - `Best Practices for File Naming <library.stanford.edu/research/data-management-services/data-best-practices/best-practices-file-naming>`_

Best Practices from Exemplar Labs
---------------------------------

* The 3-2-1 Backup rule: At the very least, research data should have 3 copies, with 2 copies on different media and 1 copy off-site. This includes having 2 UBC copies.
* As part of your DMP, set up infrastructure, services, and training to ensure that at worst, only one day of work can be lost.
* All data is accompanied by a metadata file. Secondary data is accompanied by a wiki article describing how the data was processed and analysed.
* Automated metadata entry for experimental data. `Example 1 <doi.org/10.5281/zenodo.3268838>>`_, `Example 2 <github.com/cortex-lab/alyx>`_ 
* Backup snapshots of all workstations and the central data storage servers. 