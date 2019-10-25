.. _compute_canada:

===================
Compute Canada (CC)
===================
`Compute Canada <https://www.computecanada.ca/>`__ is a provider of Advanced Research Computing infrastructure, including systems, storage, and software. Their regional partner is `Westgrid <http://westgrid.ca>`_ which provides additional support.

Compute Canada provides heterogeneous, general purpose clusters and clouds that allow researchers to access resources such as CPU and GPU time, `software <http://docs.computecanada.ca/wiki/Available_software>`_, as well as different storage systems. A list of the available national systems can be found `here <https://docs.computecanada.ca/wiki/National_systems>`__.

Cost
====
Compute Canada and Westgrid resources can be used at no financial cost to researchers.

Signing up
==========
You can apply for a Compute Canada account following the `documentation <http://computecanada.ca/research-portal/account-management/apply-for-an-account>`_.

* If you are a PI, please create an account as other lab members must be sponsored under your account.
* If you are a lab member, contact your PI for their Compute Canada Role Identifier (CCRI) so that you can complete your application. Your PI must then confirm your role for your account to be created.

Storage Types
=============

.. glossary::

	Home
		Small fixed quota that cannot be changed. Does not offer high performance read and write speeds. Unique to each user. It is not clear whether this space is backed up. Best location to store smaller files like source code, scripts and configs.

	Project
		Larger quota than Home. Resource shared by PI and all users registered under the PI. Details on backups can be found `here <https://docs.computecanada.ca/wiki/Data_backup_and_restoration>`__. Best location to share files from and for live storage. 

	Scratch
		Large quota for each user, ~20TB. For high performance read and write operations. This space is not backed up and is purged at 60 day intervals. Files should only be in stored in Scratch when running jobs.

	Nearline
		A file system virtualized onto tape. Files copied to nearline are transferred to tape. Access speeds are slow as files have to be copied onto disk from tape. Resource shared by PI and all users registered under the PI. Data is not backed up. Best location for data archival.

Security and Status
===================
Compute Canada is considered to be off-site UBC storage as per :ref:`UBC’s Information Security Standard #03: Transmission and Sharing of UBC Electronic Information <ubc_transmission>`.

Resource Allocations
====================
The following information pertains to the national heterogeneous clusters as of 8th August 2019.

Default Resource Allocations 
----------------------------

* CPU/GPU time is for opportunistic use (no priority is given on the queue). If you require priority, apply to the Resource Allocation Competitions (RAC)
* No Cloud Allocation
* `Default storage allocations <http://docs.computecanada.ca/wiki/Storage_and_file_management/en>`_ [#]_:

.. image:: compute_canada_filesystems.png

Rapid Access Service (RAS)
--------------------------
From the CC `website <http://computecanada.ca/research-portal/accessing-resources/rapid-access-service>`_:

    Rapid Access Service (RAS) allows Principal Investigators (PIs) to request a modest amount of storage and cloud resources without having to apply to the Resource Allocation Competitions (RAC). 

* CPU/GPU time is for opportunistic use (no priority is given on the queue). If you require priority, apply to the Resource Allocation Competitions (RAC)
* Cloud allocations available

PIs are encouraged to apply for storage through RAS. Details can be found on their website, linked above.

Resource Allocation Competitions (RAC)
--------------------------------------
`RACs <https://www.computecanada.ca/research-portal/accessing-resources/resource-allocation-competitions>`_ are held annually in the fall and are awarded the following April. They enable researchers to request resources beyond what they can apply for through RAS. 

* CPU/GPU time by priority
* larger storage allocations
* larger cloud allocations

Recommended Usage Scenario for Live Storage
-------------------------------------------
The project file system can be used as a backup, made at regular intervals such as daily or bi-hourly. This can be automated as a cron job using shell scripting tools like Globus, rsync, scp, or sftp. 

Documentation on these tools:

* `Transferring data <https://docs.computecanada.ca/wiki/Transferring_data>`_ from the Compute Canada documentation
* `Data Transfer and Backup on Remote Computers <https://ubcbraincircuits.readthedocs.io/en/latest/backups/transferring_data.html>`_ from the white paper website 

`Archeion <https://github.com/ubcbraincircuits/archeion>`_ or the `Globus API/SDK <https://docs.globus.org/api/>`_ can be used to script Globus transfers.

.. [#] Obtained usign the `diskusage_report <https://docs.computecanada.ca/wiki/Storage_and_file_management/en>`_ command-line utility of the Compute Canada clusters.  