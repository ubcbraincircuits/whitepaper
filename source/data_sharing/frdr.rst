=========================================
Federated Research Data Repository (FRDR)
=========================================
`Portage <https://portagenetwork.ca/>`_, `Compute Canada (CC) <https://www.computecanada.ca/>`_ 
and the `Canadian Association of Research Libraries (CARL) <http://www.carl-abrc.ca/about-carl/>`_ 
have collaborated to produce the `Federated Research Data Repository <https://www.frdr.ca/repo/>`_.


Storage and Backup
------------------
Location
~~~~~~~~
From frdr.ca/docs/en/about:

    Data submitted to FRDR is housed on Compute Canada managed infrastructure at the University of Victoria, 
    BC or at the University of Waterloo, ON. Research data submitted to FRDR does not leave Canada.
    The metadata related to datasets is housed in a database the University of Victoria. 
    Most of that metadata is shared with Globus, running on Amazon Web Services services in the USA, 
    to be indexed and made available for discovering datasets. Certain metadata fields, 
    for example, submitter contact information, are not shared with Globus.

Larger uploads are made using Globus. While globus is hosted in the USA on AWS, 
only the public metadata is stored there; the datasets themselves are transferred 
securely between the endpoints so the data does not leave Canada.

Size limits
~~~~~~~~~~~
There is a theoretical dataset limit of 4TB due to the limitation of the Archivematica
data preservation system. There has not been further comment on whether they will 
impose their own upload size limit.

However, they do have limited resources so they may impose restrictions during curation 
if datasets of unreasonable magnitude are uploaded.

Changes
-------
Only authorised curators can make changes to submitted data. 
A request must be made via email in case any changes need to be made.

Curation 
--------
Curators will perform tasks like:
* Checking metadata record for completeness
* Linking DOIs for related publications 
* Validation of data, for instance, flagging tabular null data with no explanation, corrupt files
* Checking documentation
* Checking for copyright and ethical violations

They typically take up to 48 hours to complete this process, after which it takes 15 minutes to 
complete DOI registration, and a further 2 hours for the dataset to appear for download 
in the FRDR portal.

Data Sharing and Collaboration
------------------------------
FRDR includes search functionality for its own datasets and datasets 
that it harvests from other sources such as the Scholars Portal Dataverse. 
Users can search for/deposit datasets using the online web interface or by using an API. 
Note that while depositing data requires authorisation, anybody can search for datasets.
FRDR is also format agnostic, and allows users to manage the dataset file hierarchy. 
It also support embargos. They also issue DOIs for all deposited datasets.
Other features include data integrity checks using checksums, curation and upload authentication.
Through the use of Globus, FRDR also enables secure transfer of large datasets with the ability 
to make asynchronous and resumable transfers that are automatically managed.

=========================
Sharing on Compute Canada
=========================

On Compute Canada clusters, Home spaces are unique to individual users while 
the Project space is shared by a research group. Both are backed up and are not purged.
Quotas are exclusive to each cluster and do not extend to the other clusters.

.. csv-table:: Storage Quotas
   :header: "Cluster", "Home Space", "Project Space"
   :widths: 10, 15, 15

   "Cedar", 50 GB and 0.5 M files per user, 1 TB and 5 M files per group
   "Graham", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per group
   "Béluga", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per group


This means they can be used to share files to Compute Canada users. If a Globus subsription 
is purchased, files can be shared with non Compute Canada users as well. 
`Learn more here <https://docs.globus.org/how-to/share-files/>`_.


Sharing files with Compute Canada Users
=======================================
This section contains quick references. For detailed documentation and 
instructions, refer to these `docs <https://docs.computecanada.ca/wiki/Sharing_data>`_.

.. Note:: 
   * You must know the Compute Canada username of the person you want to share with.
   * You must also own the files/directories that you intend on sharing. Use `chown <https://linux.die.net/man/1/chown>`_ to change file owners and groups.
   * Learn more about UNIX file permsissons `here <https://en.wikipedia.org/wiki/File_system_permissions>`_.

Internal Sharing
----------------
To share files within your own research group, refer to these 
`docs <https://docs.computecanada.ca/wiki/Sharing_data#Filesystem_permissions>`_.

External Sharing
----------------
To share files with other Compute Canada users, refer to to these 
`docs <https://docs.computecanada.ca/wiki/Sharing_data#Access_control_lists_.28ACLs.29>`_

Quick Reference
~~~~~~~~~~~~~~~
Sharing a Single file
.....................
If you are logged in as ``<user>`` on compute cluster ``<server>`` and want to share a 
generic file, e.g. ``<data.zip>`` with another user ``<other_user>``, 

.. code-block:: bash
   
   [<user>@<server>]$ setfacl -m u:<other_user>:rx <data.zip>
   
   # substitute the variables, but don't include the <>'s
   #                            `u` to identify other users to share with
   #                                           'rx' - give the user the rights to:
   #                                           `r` - read 
   #                                            'x' - execute


Sharing a folder
................
For most use cases, it is more practical to share one or more folders and give 
different groups access to them using Access Control Lists (ACL).

.. note:: 
   * You must have a group created in `CCDB <https://ccdb.computecanada.ca/services/>`_
   * You must own the directory you want to share
   * All parent directories of the directory you want to share must have public execute properties
   
   If you do not meet these requirements, consult the 
   `docs <https://docs.computecanada.ca/wiki/Sharing_data#Access_control_lists_.28ACLs.29>`_.

If you are logged in as ``<user>`` on compute cluster ``<server>`` and want to share a folder 
``<shared_data>`` in some project or home space to a group ``<group_name>``

.. code-block:: bash
   
   # make any file inside the folder inherit the same ACL rules (for new files)
   [<user>@<server>]$ setfacl -d -m g:<group_name>:rwx /home/<user>/projects/<def/rrg-PI>/<shared_data>

   # make any file inside the folder inherit the same ACL rules (for existing files)
   [<user>@<server>]$ setfacl -R -m g:<group_name>:rwx /home/<user>/projects/<def/rrg-PI>/<shared_data>  
 
Members can be added to the a group through `CCDB <https://ccdb.computecanada.ca/services/>`_.
