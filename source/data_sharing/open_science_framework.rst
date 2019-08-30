Open Science Framework
======================
`Open Science Framework (OSF) <https://osf.io/>`_ is a free and open source cloud-based data management 
system developed by the `Center for Open Science (COS) <https://cos.io/>`_.

The following introduction is based on the `OSF Guides <https://help.osf.io/hc/en-us>`_.

Storage and Backup
------------------
OSF uses Google Cloud for active and archival storage and Amazon Glacier as a backup location. 

.. note::
	OSF is maintained and developed by the Center for Open Science, which has established a $250,000
	preservation fund in the event that COS closes down. This fund can preserve and maintain read access
	to hosted data for more than 50 years. 
	
	OSF is free due to the support of `COS sponsors <https://cos.io/about/our-sponsors/>`_.

Location
--------
The U.S. is OSF’s default storage location. A variety of storage locations are available,
including Canada (Montreal). The global (default) storage location can be changed and will 
be applied to new projects and components. Each project and component can also have its own storage location.

Size limits
-----------

.. attention::
	There is no limit on storage per project and no cap on the amount of OSF Storage per user. Direct upload of individual 
	files to OSF Storage has a **5GB** limit. 

Third-party add-ons like Dropbox can be used to integrate different services already in use and connect them to OSF
to allow access to existing data/materials. There is no limit for the amount of storage used
across add-ons. 

Add-ons
-------
Citation add-ons
~~~~~~~~~~~~~~~~
There are two reference managers supported by OSF:

	1. `Mendeley <https://help.osf.io/hc/en-us/articles/360019929893-Connect-Mendeley-to-a-Project>`_
	
	2. `Zotero <https://help.osf.io/hc/en-us/articles/360019929913-Connect-Zotero-to-a-Project>`_

Storage add-ons
~~~~~~~~~~~~~~~
If data needed for a project already exists in one of the services below, 
it can be connected to OSF rather than transferring it. 
This feature is also useful if a file exceeds the 5GB limit for upload. 

This page provides a `list of available storage add-ons in OSF 
<https://help.osf.io/hc/en-us/sections/360003623833-Storage-add-ons>`_, which includes platforms like 
Amazon S3, ownCloud, Dataverse, GitHub, Bitbucket and GitLab.

.. warning::
	OSF does not store or back up content within an add-on. Ensure that each individual
	add-on being used complies with :ref:`UBC's Information Security Standard #03: Transmission
	and Sharing og UBC Electronic Information <ubc_transmission>`.
	
Collaboration
-------------

Within a lab
~~~~~~~~~~~~

**Contributors**

OSF projects and components are private by default. 
Members of the lab can be added as “Contributors” to projects. There are two types of contributors:

	1. Bibliographic (displayed in contributor list and in project citations)
	2. Non-bibliographic

Each component within a project can have its own set of contributors.

**User Permissions**

A contributor can be given three levels of permissions: 

	1. Administrator
	2. Read + Write
	3. Read only

Each contributor can be granted different levels of permissions across components. 

**Checkouts**

OSF has a checkout feature that prevents multiple contributors from editing the same file at once.     

Across labs
~~~~~~~~~~~

**Access requests**

Researchers can request access to both private and public projects, 
which means they can be added as a contributor and given a level of permission. 

**View-only (Projects)**

For peer review, presentations, or data sharing, a view-only link can be created
for a project. The contributor list can be anonymized for blind peer review and
only selected components will be visible via the link. 

**Quick Files**

A single file can be shared independently from a project using the Quick File feature, 
which allows files to be publicly searchable and accessible on the profile page.

Public Access
~~~~~~~~~~~~~

**DOIs**

DOIs can be created for projects but OSF does not currently support DOI versioning.

**Citations**

OSF generates citations (APA, MLA, Chicago, or custom) automatically for every
project and component.

**Licensing**

A license can be added to a project either by choosing from a list provided by
OSF or uploading your own. Components will have the same license as the
top-level project by default but they can also be licensed individually.

Version Control
---------------
OSF has built-in version control and provides access to previous versions of
files, including those stored on add-ons.

Registration
~~~~~~~~~~~~

A registration is a time-stamped copy of an OSF project that cannot be edited or
deleted. This feature is useful for archiving and to capture and preserve significant
moments in the research process (i.e. before submission for peer review, etc.).

A registration can be withdrawn, which means the project contents will be removed but its 
basic metadata will be maintained. 
All registrations will be made public, which can be done immediately or embargoed for up to 4 years. 
