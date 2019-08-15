===============
Version Control
===============

Overview
========
	
Version control is a system that record changes made to one or more files. 
In this section I will discuss distributed version control systems e.g. Git+GitHub

We are pleased to announce that we have set up a GitHub team account for the cluster [github.com/ubcbraincircuits], under which members can set up their repositories.

.. note::
   Go to the Onboarding section below for instructions on becoming a member

   **Resources**
   
   * `Learn Git and GitHub <https://try.github.io/>`_

Not Using Version Control?
==========================

Why Use Version Control?
------------------------
* Revert your files to a previous version
* Compare changes
* Provides a record of what changed and Why
* Lets you experiment 
* Recover files if you make a wrong turn or delete them
* Distruibuted clones of a repository act as full backups
* Collaborate in an organised manner
* Clear attribution of contributions

What Can I use Version Control for?
-----------------------------------
* Code
* Papers
* Theses
* Journals
* Critical data files

Version Control Systems (VCS)
-----------------------------
Git
^^^
Git was created to manage the development of the Linux kernel. It is the most popular
distributed version control system. You can read more about it `here <https://git-scm.com/>`_.
Git is complex and requires training to use safely and appropriately. This complexity gives Git 
greater flexibility and more functionality for power users.

Mercurial
^^^^^^^^^
Mercurial is simpler and easier to use than Git. It makes it more difficult for users to cause inintentional damage.
You can read more about it `here <https://www.mercurial-scm.org/>`_.

.. Tip::
   Git and Mercurial are available on Windows, MacOS and Linux. There are also several graphical user interface 
   options for both options for those who do not prefer to use the command line interface.

Hosting
^^^^^^^
The following platforms can be used to host your repositories remotely:

.. list-table:: 
   :widths: 5 5 5 5
   :header-rows: 1

   * - 
     - GitHub
     - GitLab
     - Bitbucket
   * - VCS Support
     - Git Only
     - Git Only
     - Git and Mercurial
    
None of these platforms store data exclusively on Canadian servers, so sensitive data should 
not be pushed to the remote. 
If this is absolutely necessary, there is the option of setting up your own server as a remote. 
This is possible through:

1. Enterprise offerings from these platforms that may not benefit from academic pricing
2. Setting using an open-source offfering at the expense of losing the rich interfaces of the hosting platforms. One such example is `gogs.io`_.

Using Version Control?
======================

Moving existing repositories to central cluster repository
----------------------------------------------------------
It is highly recommended that all existing respositores be transferred to the main cluster GitHub repository.
Please refer to the ``Setup Instructions`` section below for instructions.

The main aims of doing this are:

* Reducing fragmentation by maintaining a centralised code repository under the administration of PIs for easier management
* Access to research repositories after personell leave labs
* Making GitHub Pro and GitHub Team available to all cluster members, providing access to more powerful tools

Spread the Word!
----------------
Encourage colleagues who have not adopted VCS to do so. Incorporate VCS training during the onboarding process 
when brining new people into the lab.


Benefits of GitHub Education
============================
With the GitHub Education subscription granted to the cluster, members enjoy the benefits like:

Wikis and Websites
------------------
Free wikis for private and public repositories. Use them to: write down documentation, write lab notes, create a 
whiteboard, create meeting agendas. 
Find out more `here <https://help.github.com/en/articles/documenting-your-project-with-wikis>`_

You can also create websites using `GitHub Pages <https://pages.github.com/>`_

Team Collaboration Tools
--------------------
PIs and Researchers can create teams and control who can edit certain repositories.
There are also spaces for team discussions


Onboarding
==========

1) Get a GitHub account
-----------------------
If you do not already have a GitHub account, you can sign up for one `here <https://github.com/join>`_. 
Skip this step if you have an existing account.

2) Become a Member of the Brain Circuits Repository
---------------------------------------------------
Contact `Jeffrey LeDue <mailto:jledue@mail.ubc.ca>`_ and provide your GitHub account name or email to be added as a member. You will receive an invitation via the email account you used to register for GitHub.

3) Move Existing Repositories to the Central Repository
-------------------------------------------------------
If you have exisitng respositories that you desire to move to ``github.com/ubcbraincircuits``, 
the transfer procedure can be found `here <https://help.github.com/en/articles/transferring-a-repository>`_. 
When prompted, set the ``New Owner's Github username or organisation name`` field to ``UBCBrainCircuits``.

..note::

  The main aims of doing this are:

  * Reducing fragmentation by maintaining a centralised code repository under the administration of PIs for efficient management. This also enhances discoverability and the ability to collaborate across labs.
  * Enabling labs to access repositories after members move on
  * Giving cluster members free access to GitHub Team and its benefits

4) Create or Join a Group
-------------------------
If your lab has not yet creted a group, you should create one by going to ``github.com/ubcbraincircuits`` clicking on the ``Teams``, then 
on ``New Group``. Temas can be made private or visible to all member of the cluster. 

If your lab has a group, ask an existing member to add you to it. 

Visible groups can be nested, and are useful for coordination. All members are able to create other groups as they wish.
