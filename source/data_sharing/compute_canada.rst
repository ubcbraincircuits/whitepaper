Compute Canada
==============
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
---------------------------------------
This section contains quick references. For detailed documentation and 
instructions, refer to these `docs <https://docs.computecanada.ca/wiki/Sharing_data>`_.

.. Note:: 
   * You must know the Compute Canada username of the person you want to share with.
   * You must also own the files/directories that you intend on sharing. Use `chown <https://linux.die.net/man/1/chown>`_ to change file owners and groups.
   * Learn more about UNIX file permsissons `here <https://en.wikipedia.org/wiki/File_system_permissions>`_.

Internal Sharing
~~~~~~~~~~~~~~~~
To share files within your own research group, refer to these 
`docs <https://docs.computecanada.ca/wiki/Sharing_data#Filesystem_permissions>`_.

External Sharing
~~~~~~~~~~~~~~~~
To share files with other Compute Canada users, refer to to these 
`docs <https://docs.computecanada.ca/wiki/Sharing_data#Access_control_lists_.28ACLs.29>`_

Quick Reference
^^^^^^^^^^^^^^^
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
~~~~~~~~~~~~~~~~
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
   [<user>@<server>]$ setfacl -d -m g:<group_name>:rwx /home/<user>/projects/<def/rrg-PI>/<shared_data>  
 
Members can be added to the a group through `CCDB <https://ccdb.computecanada.ca/services/>`_.