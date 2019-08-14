===============================================
Transferring and Backing Up on Remote Computers
===============================================

This section covers the use of tools like ``scp``, ``Rsync``, ``sftp`` and Globus to make transfers and backups. While the examples place an emphasis on Compute Canada, they can be generalised to apply to any remote computer.

.. Note::
   The storage on Alder is only to be used as Scratch space and is not backed up. Files should not be stored on Alder for longer than 60 days.

``rsync-time-backup``
=====================
``rsync-time-backup`` is a utility available `here <https://github.com/laurent22/rsync-time-backup>`_ that builds on top of ``Rsync``. 

It allows backups over SSH, backup resumes, uses hardlinks to avoid duplication and provides functionality to create full backups. In short, it can be used to create full snapshots, the frequency of which can be configured e.g. keep each hour of the last 24 hours, each day of the previous month and each month in the previous year.

You may find it useful to combine several techinques in the examples below and in the docmentation of this script.

Example: Backing up to Compute Canada Project Space
---------------------------------------------------
The project space is a great place for:

* Frequent backups
* Internal and external sharing

You may want to tarball collections of small files (multiple files < 100 MB) to keep the file count down and to keep the diretory uncluttered.

.. Note::
   This works if you set up the SSH key on the Compute Canada server

In this example, we are backing up a drive mounted to our system. In this instance, it is a NAS drive, althogh it could be a hard drive or any other external media.

.. code-block:: bash
   
   $ rsync_tmbackup.sh /media/user/data cedar:/home/user/projects/def-pi/data/

You can replace ``cedar`` with ``graham`` or ``beluga`` as required

Example: Backing up to Remote Computer
--------------------------------------
Suppose you have an ``ssh`` machine ``computer.domain.com`` 

.. code-block:: bash
   
   $ rsync_tmbackup.sh /media/user/data user@computer.domain.com:/data/

Example: Backing up using an exclusion list
-------------------------------------------
Suppose you do not want to backup certain directories, files or file types. You must create an exclusion list ``exclude-file.txt``, for instance::

    secrets.txt
    folder1/*
    folder2
    folder3/scratch/
    *.mat*

This will exclude the file ``secrets.txt``, copy the folder ``folder1`` but not its contents, will not copy the folder ``folder2`` or its contents, will not copy the subdirectory ``folder3/scratch/`` or its contents, and will exclude all files with the ``.mat`` extension.

Local machine to external drive

.. code-block:: bash 
   
   $ rsync_tmbackup.sh /home/user /media/user/data/ excluded_patterns.txt

Compute Canada

.. code-block:: bash
   
   $ rsync_tmbackup.sh /media/user/data cedar:/home/user/projects/def-pi/data/ excluded_patterns.txt

Example: Change the Expiration Strategy
---------------------------------------
From the README::

    The default strategy is ``1:1 30:7 365:30``, which means:

    * After 1 day, keep one backup every 1 day (1:1).
    * After 30 days, keep one backup every 7 days (30:7).
    * After 365 days, keep one backup every 30 days (365:30).

To change the strategy to:
After 30 Days, keep one backup every 14 days,

.. code-block:: bash
   $ rsync_tmbackup.sh  --strategy="1:1 30:14 365:30"  /media/user/data cedar:/home/user/projects/def-pi/data/

``STFP``
=========
From the `Compute Canada Documentation <https://docs.computecanada.ca/wiki/Transferring_data>`_::
  
    SFTP (Secure File Transfer Protocol) uses the SSH protocol to transfer files between machines which encrypts data being transferred.

Dropping into the SFTP Prompt
-----------------------------

.. code-block:: bash

   $ sftp user@remote_hostnamee_or_ip_address

For instance, 

.. code-block:: bash

   $ sftp john@alder.arc.ubc.ca

If you set up your ``SSH`` key on the remote computer, you won't even need a password.

.. code-block:: bash

   $ sftp cedar

If it worked, you should be in the prompt e.g.

.. code-block:: bash

   $ sftp cedar
   Connected to cedar.
   sftp>

Exiting the SFTP Prompt
-----------------------

.. code-block:: bash

   sftp> exit

   or

   sftp> bye

Help
----

.. code-block:: bash

   sftp> help 

   or 

   sftp> ? 

Navigating the Remote and Local Machines
----------------------------------------
Current working directory
~~~~~~~~~~~~~~~~~~~~~~~~~
Remote Machine

.. code-block:: bash

   sftp> pwd 

Local Machine

.. code-block:: bash

   sftp> lpwd 

List directory contents
~~~~~~~~~~~~~~~~~~~~~~~
Remote Machine

.. code-block:: bash

   sftp> ls 

Local Machine

.. code-block:: bash

   sftp> lls

Change working directory
~~~~~~~~~~~~~~~~~~~~~~~~
Remote Machine

.. code-block:: bash

   sftp> cd <remote dir> 

Local Machine

.. code-block:: bash

   sftp> lcd <local dir>

Make new directories
~~~~~~~~~~~~~~~~~~~~
Remote Machine

.. code-block:: bash

   sftp> mkdir <remote dir> 

Local Machine

.. code-block:: bash

   sftp> lmkdir <local dir>

Transferring File to Remote
---------------------------

.. code-block:: bash

   sftp> put <local file or directory> <new name on remote [OPTIONAL]>

e.g. 

.. code-block:: bash

   sftp> put data.hdf5
   Uploading data.hdf5 to /project/6006382/user/data.hdf5 
   data.hdf5                                    100%   11GB  100.3MB/s   01:50

.. code-block:: bash

   sftp> put data.hdf5 data_20181012.hdf5
   Uploading data.hdf5 to /project/6006382/user/data_20181012.hdf5
   data.hdf5                                    100%   11GB  100.3MB/s   01:50

Transferring File from Remote
-----------------------------

.. code-block:: bash

   sftp> get <remote file or directory> <new name on local [OPTIONAL]>

e.g. 

.. code-block:: bash

   sftp> get data.hdf5
   Fetching /project/6006382/user/data.hdf5 to data.hdf5
   /project/6006382/user/data.hdf5              100%   11GB  100.1MB/s   01:50

.. code-block:: bash

   sftp> get data.hdf5 data_20181012.hdf5 
   Fetching /project/6006382/user/data.hdf5 to data_20181012.hdf5 
   /project/6006382/user/data.hdf5              100%   11GB  100.1MB/s   01:50


``SCP``
=======
From the `Compute Canada Documentation <https://docs.computecanada.ca/wiki/Transferring_data>`_::

    SCP stands for "Secure Copy". Like SFTP it uses the SSH protocol to encrypt data being transferred. It does not support synchronization like Globus or rsync. Some examples of SCP use are shown here.

    SCP supports an option, -r, to recursively transfer a set of directories and files. We recommend against using scp -r to transfer data into /project because the setgid bit is turned off in the created directories, which may lead to Disk quota exceeded or similar errors if files are later created there.

Basic Usage
--------------

.. code-block:: bash

   $ scp <location/file to copy from> <location/file to copy to>

Transferring Files
-----------------

Suppose a folder in your current local working directory is as follows::

    package/
    ├── package
    │   ├── conf.py
    │   ├── __init__.py
    │   ├── models.py
    ├── LICENSE
    ├── README.md
    ├── setup.py
    └── tests
        ├── test_interface
        |   ├── tests.py
        ├── test_models
        ├── run_tests.py

Running this will only copy ``LICENSE``, ``README.md`` and ``setup.py``, and nothing in the other folders or subdirectories

.. code-block:: bash

   $ scp package cedar:/home/user

Running this will copy everything 

.. code-block:: bash

   $ scp -r package cedar:/home/user

.. note::
   
   The above examples will only work if you set up an ssh key on the remote computer

If using the full address of the remote computer, the equivalent examples are:

.. code-block:: bash

   $ scp package username@cedar.computecanada.ca:/home/user

.. code-block:: bash

   $ scp -r package username@cedar.computecanada.ca:/home/user

Transferring between two remote Computers

.. code-block:: bash

   $ scp graham:/home/user cedar:/home/user

.. code-block:: bash

   $ scp username@graham.computecanada.ca:/home/user username@cedar.computecanada.ca:/home/user

Globus
======
Option 1: Globus GUI 
--------------------
.. tip::
   This can be extended to file transfers between personal endpoints and between Compute Canada servers

1. `Log in <https://globus.computecanada.ca/file-manager>`_

.. image:: GlobusCC/1.png

2. Click on ``Endpoints``
3. Click on ``Add an Endpoint`` then ``Globus Connect Personal``
4. Enter a name for your endpoint, e.g. ``My_workstation`` in this case. Check the ``This will be a high assurance endpoint`` box if dealing with highly sensitve data

.. image:: GlobusCC/4.png

5. Generate the Setup Key and copy it to your clipboard.
6. Using the links at the bottom of the page, install the Globus Connect Personal Client on your machine and follow the on screen instructions
7. Run the client and paste your Setup Key, then click ``OK``

.. image:: GlobusCC/4.png

8. Add location(s) of data you want globus to be able to access by clicking on `+`. 

.. image:: GlobusCC/8.png

.. tip:: 
    * Ticking `Shareable` will allow outbound transfers
    * Ticking `Writable` will allow inbound transfers

9. Click ``Save`` when done
10. Go back to your browser and click on the ``File Manager`` Tab
11. Search for the Compute Canada server you want ot upoad the files to. In this example, we are using Graham.

.. image:: GlobusCC/11.png

12. Log in with you compute canada credentials and click on ``Authenticate``
13. Your Home directory should now be displayed. Navigate to the folder you want to keep the data in. In this example I will use the ``globus_transfers`` directory in my home directory.
14. Click on ``Transfer or Sync to...`` on the right side menu

.. image:: GlobusCC/14.png

15. Click on ``Transfer or sync to...`` box. Click on ``Your Collections`` then on your desired endpoint's name.
16. Navigate the directory structure on either endpoint and select the folder(s) or file(s) you want to transfer/sync to the other endpoint. Clicking on Transfer and Sync Options below, you can select a multitude of options for managing the content on the destination endpoint. Click on ``Start`` when done.

.. image:: GlobusCC/16.png

17. You should see a message like: ``Transfer request submitted successfully. Task id: <TASK_ID>`` where <TASK_ID> is a system generated hash for your task.

.. image:: GlobusCC/17.png

18. The client on our endpoint will handle your transfer and send
you an email when it is done. You can view the status of the transfer in the `Activity` tab
19. Looking at the filesystem on Graham upon completion, we can see
that the file is indeed there:

.. code-block:: bash

   [<user>@gra-login2 globus_transfers]$ ls -lha
   total 555M
   drwxr-x--- 2 <user> <user>    3 Jul 18 14:54 .
   drwx------ 6 <user> <user>   13 Jul 18 14:38 ..
   -rw-r--r-- 1 <user> <user> 550M Jul 18 15:02 2015_11_18_5_filtered0.1to10.mat


Option 2: Globus CLI 
--------------------
Globus offers a command line interface, which is useful for its convenience and for automating transfers and backups. Its documentation is available `here <https://docs.globus.org/cli/>`_.

Option 3: Archeion
------------------
Archeion can be downloaded `here <https://github.com/ubcbraincircuits/archeion>`_.
Requirement: Globus personal must be set up on personal endpoints.
It can be used to script transfers using python and provides functionality that handles 
authentication and transfer management.
