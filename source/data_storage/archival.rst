========================
Data Archival and Backup
========================

.. toctree::	
	:caption: Table of Contents
	:maxdepth: 2
	
	archival

In this section I compare the costs of different storage solutions.
The storage providers had to be chosen to meet the bare minimum criterion that the data should be stored in Canada. Of the major cloud providers, the following had data centers that met this condition:

* Amazon S3 Glacier (Canada Central)
* Google Cloud (Montreal)
* Microsoft Azure (Canada Central and Canada East)

Amazon S3 Glacier
=================
From their `website <https://aws.amazon.com/glacier/pricing/>`_, these are the costs of various services and transactions:


Tape
====
Tape backup is a Write Once Read Many (WORM) storage media for data archival and disaster
recovery. 
Linear Tape Open (LTO) standard tapes now rival 'enterprise'
proprietary tape formats, making them a good backup solution
for the following reasons:
http://landing.quantum.com/rs/561-AAR-658/images/LTO_enterprise_tape_drive.pdf

1. High capacity media: 
LTO-7 tapes have a native capacity of 6TB for media costing 80 USD
LTO-8 tapes have a native cpacity of up to 12 TB for media costing 130 USD* 
This offers a low storage to cost ratio that rivals hard drives and cloud archival

2. Scalability: 
Modern tape autoloaders and libraries can accomotate multiple tape cartidges, 
allowing for cheap and easy scalability

However, there are some major considerations to be made.

1. High cost of Equipment
To automate tape loading and to allow remote operation, expensive tape autoloaders
or tape libraries mmust be purchased. In addition, they must be equiped with one or more
tape drives to read data from the tapes. 
Physically, they must be rack mounted, cooled and powered. In addition, they need
personell for maintenance.

2. Tape storage does not allow for random access. The drive must go through the tape
to find the files, which makes retrieval slower than from hard drives.
Transfer speeds are also generally slower than hard drives. However, with LTO-7 at 300 MB/sec,
this is not as much of a concern. (LTO-8 at 360 MB/sec)

3. Files written to tape cannot be modified without creating another copy
since tapes are WORM. 

Overall, tape backup is useful for low cost data archival and disaster recovery,
but will probably not integrate well with a day to day workflow.

Teamshare
=========
Teamshare is a service provided by UBC, giving faculty and staff a shared storage space. 
It can only be accessed throug the campus network on-site or via VPN.
`Learn more <https://it.ubc.ca/services/email-voice-internet/myvpn>`_ about the UBC myVPN service.
It costs CAD 0.15 per gigabyte per gigabyte per year and can only be charged to a single speedchart i.e. 
no split billing is permitted. A minimum of 20GB must be purchased.

Teamshare is backed up: 

	1) Every 2 hours between 6:00 am and 6:00 pm. These are kept for 5 days.
	2) Daily at midnight. These are kept for 30 days.

.. todo::
   https://it.ubc.ca/services/web-servers-storage/team-share-storage-service/faqs

More details about the service can be found on this 
`page <https://it.ubc.ca/services/web-servers-storage/teamshare-storage-service>`_.

Overall, Teamshare is the best backup solution for labs with data unlikely to grow beyond 15 TB.

Compute Canada
==============
Compute Canada is considered to be on-site storage as per `UBC’s Information Security Standard #03: Transmission and Sharing og UBC Electronic Information section 11. <https://cio.ubc.ca/sites/cio.ubc.ca/files/documents/standards/Std%2003%20Transmission%20and%20Sharing%20of%20UBC%20Electronic%20Information.pdf>`_

Overview 
--------
Description of Storage Types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Home: Small fixed quota that cannot be changed. Does not offer high performance read and write speeds. Unique to each user.
* Project: Larger quota than Home. Best location to share files from.
* Scratch: Large quota, ~20TB. For high performance read and write operations. This space is not backed up and is purged at 60 day intervals. Files should only be in stored in scratch when running jobs.
* Nearline: A filesystem virtualised onto tape. Files copied to nearline are transferred to tape. Access speeds are slow as files have to be coped onto disk from tape.

Read more about storage and file management `here <https://docs.computecanada.ca/wiki/Storage_and_file_management>`_

Quotas
~~~~~~
.. tip:: 
   Quotas can be increased through `Resource Allocation Comperitions <https://www.computecanada.ca/research-portal/accessing-resources/resource-allocation-competitions/>`_.

   PIs are highly encouraged to apply for RAC to enjoy benefits like:

   * Larger storage Quotas (Except Home)
   * More compute time
   * Cloud allocations

The following information pertains to default allocations, as at July 25, 2019. Users can 
check their quota usage by logging in to a Compute Canada cluster and running this command:

.. code-block:: bash
   $ diskusage_report

.. csv-table:: Default Storage Quotas
   :header: "Cluster", "Home Space", "Project Space", "Nearline"
   :widths: 10, 15, 15, 15

   "Cedar", 50 GB and 0.5 M files per user, 1 TB and 5 M files per project, 2 TB and 5 K files per project
   "Graham", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per project, 1 TB and 0.5 M files per project
   "Béluga", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per project, 1 TB and 0.5 M files per project

Read about backups `here <https://docs.computecanada.ca/wiki/Data_backup_and_restoration>`_.

