Scholars Portal Dataverse
=========================
Scholars Portal Dataverse is a publicly accessible secure Canadian data repository 
provided by Scholars Portal on behalf of the `Ontario Council of University 
Libraries (OCUL) <https://ocul.on.ca/>`_ and other participating institutions. Dataverse can be used by 
affiliated researchers to deposit, share, and archive research data.

.. todo::

   citation: https://learn.scholarsportal.info/all-guides/dataverse/

We are pleased to announced that we have set up 
a `dataverse for the cluster <https://dataverse.scholarsportal.info/dataverse/UBC_BrainCircuits>`_, 
under which we can set up dataverses for individual labs that are administered by PIs. 

Contact `Jeffrey LeDue <mailto:jledue\@mail.ubc.ca>`_ to set up a dataverse for your lab.


Storage and Backup
------------------

Location
~~~~~~~~
The Scholars Portal Dataverse is hosted in Canada at the UofT Libraries. 
Although institutional Datavarses can be set up, the data is still stored at this 
data center.

Size Limits
~~~~~~~~~~~
The limit for an individual file upload is 2.5 GB
There are also other considerations to be made when making uploads:

1. When .zip or .tar archives are uploaded, they can be:
 - Unpacked, with loss of hierarchy and file organisation. They recommend having fewer than 500 files in each archive due to processing and user experience concerns.
 - Packed, maintaining hierarchy and file organisation. To achieve, this, the archive must be zipped or tarballed.

2. Tabular data files (Excel, SPSS, R Data, CSV) should be less than 500MB in size as the processing that takes place at upload time will make the process slow. 

For larger datasets, dataverse support can be contacted at  dataverse@scholarsportal.info. 
However, the recommended next step is to use, FRDR.

User Permissions
----------------
Users can be granted the following tiered access and permissions:

1. Admin: A person who has all permissions for dataverses, datasets, and files.
2. Contributor: For datasets, a person who can edit License + Terms, and then submit them for review.
3. Curator: For datasets, a person who can edit License + Terms, edit Permissions, and publish datasets.
4. Dataset Creator: A person who can add datasets within a dataverse.
5. Dataverse + Dataset Creator: A person who can add subdataverses and datasets within a dataverse.
6. Dataverse Creator: A person who can add subdataverses within a dataverse.
7. File Downloader: A person who can download a published file.
8. Member: A person who can view both unpublished dataverses and datasets.


Making Changes to Datasets
--------------------------
Users with curation persmissions can edit dataset metadata and contents.
Dataverse has built in versioning to ensure data is preserved. 
It is recommended that curators are clearly identified in your labs’ DMP, as well 
as the guidelines and procedures they should abide by.

Dataset Templates
-----------------
Dataverse provides the following templates by default:
1. CC Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
2. CC Attribution-Non-Commercial 4.0 International (CC BY-NC 4.0)
3. CC Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) 
4. CC Attribution 4.0 International (CC BY 4.0)

It is possible to create custom templates. While it is not possible to create custom fields, 
there are large selections of metadata fileds available in the template creator, and the ability 
to create keywords for other particulars.

Labs are encouraged to create standardised templates for their datasets to ensure all required 
metadata are captured.