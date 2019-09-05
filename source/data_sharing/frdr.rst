=========================================
Federated Research Data Repository (FRDR)
=========================================
`Portage <https://portagenetwork.ca/>`_, `Compute Canada (CC) <https://www.computecanada.ca/>`_ 
and the `Canadian Association of Research Libraries (CARL) <http://www.carl-abrc.ca/about-carl/>`_ 
have collaborated to produce the `Federated Research Data Repository <https://www.frdr.ca/repo/>`_.

.. attention::
	We are pleased to announce that we have set up a `FRDR collection for the cluster <https://www.frdr.ca/repo/handle/ubcbraincircuits>`_, 
	on which all cluster-associated datasets will appear.
	
	To deposit a dataset into the cluster's FRDR collection, refer to the :ref:`deposit` section. 
	
Storage and Backup
------------------
Location
~~~~~~~~
From FRDR's `About <https://www.frdr.ca/docs/en/about/#security-and-privacy>`_ page: 

    Data submitted to FRDR is housed on Compute Canada managed infrastructure at the University of Victoria, 
    BC or at the University of Waterloo, ON. Research data submitted to FRDR does not leave Canada.
    The metadata related to datasets is housed in a database the University of Victoria. 
    Most of that metadata is shared with Globus, running on Amazon Web Services services in the USA, 
    to be indexed and made available for discovering datasets. Certain metadata fields, 
    for example, submitter contact information, are not shared with Globus.

Larger uploads are made using Globus. While Globus is hosted in the USA on AWS, 
only the public metadata is stored there; the datasets themselves are transferred 
securely between the endpoints so the data does not leave Canada.

Size limits
~~~~~~~~~~~

.. attention::
	There is a theoretical dataset limit of **4TB** due to the limitation of the Archivematica
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
Curators perform tasks such as:

	- Checking metadata record for completeness
	- Linking DOIs for related publications 
	- Validation of data, for instance, flagging tabular null data with no explanation, corrupt files
	- Checking documentation
	- Checking for copyright and ethical violations

They typically take up to 48 hours to complete this process, after which it takes 15 minutes to 
complete DOI registration, and a further 2 hours for the dataset to appear for download 
in the FRDR portal.

Data Sharing and Collaboration
------------------------------
FRDR includes search functionality for its own datasets and datasets 
that it harvests from other sources such as the Scholars Portal Dataverse. 
Users can search for/deposit datasets using the online web interface or by using an API. 
Note that while depositing data requires authorization, anybody can search for datasets.
FRDR is also format agnostic, and allows users to manage the dataset file hierarchy. 
It also support embargos. They also issue DOIs for all deposited datasets.
Other features include data integrity checks using checksums, curation and upload authentication.
Through the use of Globus, FRDR also enables secure transfer of large datasets with the ability 
to make asynchronous and resumable transfers that are automatically managed.

Deposit and Download
--------------------

Globus Connect Personal
~~~~~~~~~~~~~~~~~~~~~~~

To download or deposit a dataset, Globus Connect Personal must first be installed then your computer must be set up as an Endpoint. 

	1. Log into FRDR using one of these accounts: Orcid, Compute Canada, Globus ID, Google. Detailed log-in instructions can be found `here <https://www.frdr.ca/docs/en/before_depositing/#2-getting-globus-connect-software>`__. 
	2. Click on :guilabel:`Endpoints` from the toolbar on the left-hand side of the page, then click on :guilabel:`Create new endpoint` at the top right corner.
	3. Select "Globus Connect Personal".
	4. Follow the three steps on the page.

The endpoint you created will show up in the "Endpoints" page. You are now able to download datasets from FRDR and if you are already an approved depositor, you can also submit 
datasets.  

.. _deposit:
 
Deposit
~~~~~~~

Any lab in the cluster can deposit datasets into the "UBC Brain Circuits" special storage group in FRDR.
PIs can become depositors by sending an email to `Jeffrey LeDue <mailto:jledue\@mail.ubc.ca>`_ with the email 
address or account that they used to log into FRDR. It can be one of the following (copied from FRDR, `Getting Authorization To Submit <https://www.frdr.ca/docs/en/before_depositing/#3-getting-authorization-to-submit>`_):

	- username@computecanada.ca
	- 0000-0002-1342-3550@ORCID.org
	- username@globusid.org
	- username@gmail.com
	
You will receive an email from noreply@globusonline.org with the subject "You are invited to join FRDR Depositors - Déposants DFDR".
Once you accept the invitation, "FRDR UBC Brain Circuits Depositors" should appear when you click on :guilabel:`Groups`
in the toolbar. You are now eligible to deposit datasets into the cluster's storage group. 

FRDR provides information and instructions on

	- Before Depositing
	- Depositing (includes `Using Globus to Upload Dataset <https://www.frdr.ca/docs/en/depositing_data/#using-globus-to-upload-dataset>`_)
	- After Depositing
	
.. attention::
	To submit a dataset, log into FRDR and click on "Deposit Dataset" in the toolbar at the top of the page. 
	Click on "Submit a New Dataset" in the "New Submission" box. This will take you to a page titled *Submit: Select Storage Group*.
	
	Make sure you select "UBC Brain Circuits" under *Special Storage Groups*!
	
Download
~~~~~~~~

To download a dataset from FRDR, 

	1. Navigate to the page of the desired dataset. Click on :guilabel:`Download Dataset`, which is located near the bottom. This will take you to the *File Manager* page but if you're not already logged into FRDR, it will first prompt you to log in.
	2. You should see two columns: the left one contains the dataset under a Collection that is similar to "FRDR-Prod-2". Select that files you want to download or click :guilabel:`select all` in the blue toolbar if you want to download the entire dataset.
	3. Click :guilabel:`Transfer or Sync to` located in the middle of the two columns.
	4. Click on :guilabel:`-select a collection-`. This is where the dataset will be downloaded.
	5. Choose the Endpoint corresponding to the computer you wish the download to occur in. If you don't already have an Endpoint set up on the computer you are using, click on :guilabel:`Install Globus Connect Personal` and follow the instructions.
	6. Once you've selected the endpoint, the *File Manager* page reappears. Make sure you check out the "Transfer & Sync Options". To start the download, click on the blue :guilabel:`Start` button underneath the left column with an arrow pointing towards the column corresponding to the Endpoint you've chosen. 
	7. A green banner should appear with the message: "Transfer request submitted successfully" followed by the task ID. You can track the transfer's progress in the Activity page. 
	
You will receive an email from noreply@globusonline.org with the subject: "SUCCEEDED" followed by the task id once the transfer is complete. 
	
=========================
Sharing on Compute Canada
=========================

On Compute Canada clusters, Home spaces are unique to individual users while 
the Project space is shared by a research group. Both are backed up and are not purged.
Quotas are exclusive to each cluster and do not extend to the other clusters.

.. csv-table:: 
   :header: "Cluster", "Home Space", "Project Space"
   :widths: 10, 15, 15

   "Cedar", 50 GB and 0.5 M files per user, 1 TB and 5 M files per group
   "Graham", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per group
   "Béluga", 50 GB and 0.5 M files per user, 1 TB and 0.5 M files per group

*Storage Quotas*

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
