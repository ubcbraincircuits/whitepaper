======================
Data Storage Platforms
======================

To facilitate the construction of data management plans, we make a distinction between data in an ongoing research investigation and final data that has been processed and/or analyzed. Thus, we divide data storage services into two sections: Live Storage and Data Archival.

For both sections, we provide overviews and brief evaluations of various storage platforms and technologies.

Live Storage
============
Live storage is appropriate for data that is actively changing and accessed frequently. This typically requires a high performance file system with low wait times and high read-and-write speeds to support demanding research workflows. They are normally characterised by mid to high storage costs.

.. toctree::
   :maxdepth: 1
   
   teamshare
   compute_canada
   network_attached_storage
   cloud_object_storage

Data Archival
=============
Research data that does not change or is not accessed often (< 1 times a month) should be archived for preservation to reduce storage costs and effectively manage live storage resources. Archival and long-term availability of research data is also a requirement of most research grants.

There are solutions available that are designed for archival, with common characteristics including low storage costs, high retrieval times, and high retrieval costs.

.. toctree::
   :maxdepth: 1

   teamshare_archive
   compute_canada_nearline
   cloud_object_archival
   data_sharing_platforms

.. image:: archival_overview.png

*Summary of data archival solutions*