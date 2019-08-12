==============
Compute Canada
==============
Getting a Compute Canada Account
================================
You can apply for a Compute canada account `following this documentation <https://www.computecanada.ca/research-portal/account-management/apply-for-an-account/>`_. 

.. note:: 
* If you are a PI, please create an account as other lab members must be sponsored under your account.
* If you are a lab member, contact your PI for their Compute Canada Role Identifier (CCRI) so that you can complete your application. Your PI must then confirm your role for your account to be created.

Transferring Files to and From Compute Canada
=============================================
This article is meant to complement the following `documentation from Compute Canada <https://docs.computecanada.ca/wiki/Transferring_data>`_, which details the use of tools like ``scp``, ``sftp``, ``rsync``, ``wget``, ``curl`` and ``checksum``.
The section below has been written since Compute Canada's documentation on Globus is outdated.

.. tip::
   The same tools can be used to work with other remote servers

Using Globus GUI
----------------
.. tip::
   This can be extended to file transfers between personal endpoints and between Compute Canada servers

1. `Log in <https://globus.computecanada.ca/file-manager>`_

.. image:: ../Images/GlobusCC/1.PNG

2. Click on ``Endpoints``
3. Click on ``Add an Endpoint`` then ``Globus Connect Personal``
4. Enter a name for your endpoint, e.g. ``My_workstation`` in this case. Check the ``This will be a high assurance endpoint`` box if dealing with highly sensitve data

.. image:: ../Images/GlobusCC/4.PNG

5. Generate the Setup Key and copy it to your clipboard.
6. Using the links at the bottom of the page, install the Globus Connect Personal Client on your machine and follow the on screen instructions
7. Run the client and paste your Setup Key, then click ``OK``

.. image:: ../Images/GlobusCC/4.PNG

8. Add location(s) of data you want globus to be able to access by clicking on `+`. 

.. image:: ../Images/GlobusCC/8.PNG

.. tip:: 
    * Ticking `Shareable` will allow outbound transfers
    * Ticking `Writable` will allow inbound transfers

9. Click ``Save`` when done
10. Go back to your browser and click on the ``File Manager`` Tab
11. Search for the Compute Canada server you want ot upoad the files to. In this example, we are using Graham.

.. image:: ../Images/GlobusCC/11.PNG

12. Log in with you compute canada credentials and click on ``Authenticate``
13. Your Home directory should now be displayed. Navigate to the folder you want to keep the data in. In this example I will use the ``globus_transfers`` directory in my home directory.
14. Click on ``Transfer or Sync to...`` on the right side menu

.. image:: ../Images/GlobusCC/14.PNG

15. Click on ``Transfer or sync to...`` box. Click on ``Your Collections`` then on your desired endpoint's name.
16. Navigate the directory structure on either endpoint and select the folder(s) or file(s) you want to transfer/sync to the other endpoint. Clicking on Transfer and Sync Options below, you can select a multitude of options for managing the content on the destination endpoint. Click on ``Start`` when done.

.. image:: ../Images/GlobusCC/16.PNG

17. You should see a message like: ``Transfer request submitted successfully. Task id: <TASK_ID>`` where <TASK_ID> is a system generated hash for your task.

.. image:: ../Images/GlobusCC/17.PNG

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


Using Globus CLI 
----------------
Globus offers a command line interface, which is useful for its convenience and for automating transfers and backups. Its documentation is available `here <https://docs.globus.org/cli/>`_.
