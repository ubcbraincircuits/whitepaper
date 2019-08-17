=====================
Cloud Object Archival
=====================
The bare minimum criterion for off-site storage is that the data should be stored in Canada. Providers of cloud based object archival have their pricing models on a per transaction basis. This can make it challenging to determine the costs of their services, and therefore labs considering using this solution should consult with experts, such as UBC ARC. As of 7th August 2019, the following cloud providers have data centers in Canada:

.. list-table:: 
   :widths: 25 25
   :header-rows: 1

   * - Cloud Provider
     - Data Center(s)
   * - Amazon S3 Glacier
     - Canada Central
   * - Google Cloud Platform
     - Montréal 
   * - Microsoft Azure
     - Canada Central, Montréal 
   * - IBM Cloud
     - Toronto, Montréal 

Amazon S3 Glacier
=================
Pricing information is available `here <http://aws.amazon.com/glacier/pricing>`_. Usage is billed monthly. Transactions billed include: storage, retrieval requests, upload requests [LISTVAULTS, GETJOBOUTUT, DELETE and all other requests are free], data retrieval and outbound internet data transfers. All data transfers into Glacier are free. 
Glacier has the highest retrieval costs compared to other storage options. It is therefore probably not ideal for an emergency recovery situation where massive amounts of data must be retrieved.

Google Cloud Platform
=====================
Pricing information is available `here <http://cloud.google.com/storage/pricing>`_. Usage is billed monthly. Transactions billed include: storage, data retrieval, data operations and requests and outbound internet data transfers. All data transfers into GCP are free.
Storage class definitions:

* Regional storage - store data more cheaply, at the expense of data being stored at one location instead of having geographic redundancy.
* Nearline Storage - 30 day minimum storage, ideal for data accessed at most once a month
* Coldline Storage - 90 day minimum storage, ideal for data being accessed at most once a year 

The minimum storage durations for Regional and Coldline storage are 30 and 90 days respectively. If data is removed early, you will be charged the storage cost for the fraction of the time remaining regardless, for instance, if 1,000 GB is deleted from coldline after 60 days, you will be charged 1,000 GB * USD 0.007 /GB.Month * 1 Month =  USD

Microsoft Azure
===============
Pricing information is available `here <http://azure.microsoft.com/en-ca/pricing/details/storage/blobs/>`_. Usage is billed monthly. Billed transactions include storage, data retrieval, data operations and requests and outbound internet data transfers. All transfers into Azure are free.
Definitions of storage classes (`reference <http://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-storage-tiers>`_):

* Hot - Optimized for storing data that is accessed frequently.
* Cool - Optimized for storing data that is infrequently accessed. Data must be stored for at least 30 days.
* Archive - Optimized for storing data that is rarely accessed. Data must be stored for at least 180 days with flexible latency requirements (on the order of hours).

Definitions of redundancy options (`reference <http://azure.microsoft.com/en-ca/pricing/details/storage/>`_):

* Locally redundant storage (LRS) - keep multiple copies in one data center.
* Zone redundant Storage (ZRS) - keep multiple copies across multiple datacenters or across regions.
* Geographically redundant storage (GRS) - keep multiple copies of data in one region while asynchronously replicating in another region
* Read-access geographically redundant storage (RA GRS) - allow read access from the second region used for GRS

IBM Cloud
=========

Pricing information is available `here <ibm.com/cloud/object-storage/pricing/#s3api>`_. Usage is billed monthly. Billed transactions include storage, retrieval, ata operations and requests, and outbound internet transfers.  All transfers into IBM cloud are free.
Definitions of storage classes:

* Standard - Optimised for storing data that is accessed frequently (many times in a month)
* Vault - Optimised for storing data that is infrequently accessed. Data must be stored for at least 30 days
* Cold Vault - Optimised for storing data that is rarely accessed. Data must be stored for at least 90 days
* Flex - Dynamic movement between storage classes on a per month basis 

Definitions of redundancy options:

* Single Data Center - keep multiple copies on different devices in one data center
* Regional - keep multiple copies of your data in different data centers in one region
* Cross Region - Keep copies across three regions
