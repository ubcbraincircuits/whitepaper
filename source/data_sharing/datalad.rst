Git-Annex
=========
`Git-Annex <https://git-annex.branchable.com/>`_ uses git to create an annex, which presents 
files to the user in a single directory structure, even though the individual files are distributed across 
multiple locations. It can also be confiogured to create a number of copies of a file distributed across 
different annexes. This enables users to remove a local copy while ensuring redundancies are available on 
other storage locations. It is also able to synchronise files across redundancies. 
File versions can be uniquely tracked and referenced using git changeset hashes.

It also comes with a `webapp interface <http://git-annex.branchable.com/assistant/>`_.

.. Note::
   Git-Annex is a powerful tool but requires knowledge of git, UNIX command line and careful scripting to use 
   effectively.

Use Case Demo: Syncing files with Git-Annex using Linux CLI
-----------------------------------------------------------
The following demo was tested on Ubuntu 18.04 LTS

.. note::
   
   sudo priviledges are required to install git-annex

Install the `Git-Annex <http://neuro.debian.net/install_pkg.html?p=git-annex-standalone/>`_ from NeuroDebian.

Create a repository in a location of your preference

.. code-block:: bash
   
   $ mkdir annex
   $ cd annex
   $ git init
   Initialized empty Git repository in /home/user/annex/.git/
   $ git annex init
   init ok

Add file to the repository

.. code-block:: bash

   $ cd /home/user/annex/
   $ cp ~/Pictures/121406.jpg ./
   $ git annex add .
   add 121406.jpg ok
   (recording state in git...)
   $ git commit -a -m added
   [master (root-commit) 1259e1c] added
   1 file changed, 1 insertion(+)
   create mode 120000 121406.jpg

Add a remote, in this case, an external hard drive called 'My Passport'

.. code-block:: bash

   $ cd /media/user/USB\ DISK/
   $ git clone /home/user/annex/
   Cloning into 'annex'...
   done.
   $ cd annex
   # get the desktop and the hard drive to get to know each other
   $ git annex init
   $ git remote add desktop /home/user/annex
   $ cd /home/user/annex
   $ git remote add harddrive1 /media/user/My\ Passport/annex

Now let's add a bunch of files to the Desktop's Annex

.. code-block:: bash
   $ cd /home/user/annex/
   $ cp ~/Pictures/121419.jpg ~/Pictures/121421.jpg ./
   $ git annex add .
   add 121419.jpg ok
   add 121421.jpg ok
   (recording state in git...)
   $ git commit -a -m added
   [master 8a68299] added
   2 files changed, 2 insertions(+)
   create mode 120000 121419.jpg
   create mode 120000 121421.jpg

And now let's add a bunch of other files to the Hard Drive's Annex

.. code-block:: bash
   $ cd /media/user/My\ Passport/annex
   $ cp ~/Pictures/121415.jpg ~/Pictures/121420.jpg ./
   $ git annex add .
   add 121419.jpg ok
   add 121421.jpg ok
   (recording state in git...)
   $ git commit -a -m added
   [master 8a68299] added
   2 files changed, 2 insertions(+)
   create mode 120000 121419.jpg
   create mode 120000 121421.jpg

Looking at the contents of the Desktop annex, we see the following:

.. code-block:: bash

  $ ls
  121406.jpg  121419.jpg  121421.jpg

Looking at the contents of the Hard drive annex, we see the following:

.. code-block:: bash

  $ ls
  121406.jpg  121415.jpg  121420.jpg

Now we need to sync the files and make sure our annexes have the same contents
  
.. code-block:: bash  
  $ cd /media/user/My\ Passport/annex
  $ git annex sync desktop
  $ git annex get .
  $ cd /home/user/annex/
  $ git annex sync harddrive1
  $ git annex get .

Now, looking at the contents of the Desktop annex, we see the following:

.. code-block:: bash

  /home/user/annex$ ls
  121406.jpg  121415.jpg  121419.jpg  121420.jpg  121421.jpg

And also when looking at the contents of the Hard drive annex, we see the following:

.. code-block:: bash

  /media/user/My Passport/annex$ ls
  121406.jpg  121415.jpg  121419.jpg  121420.jpg  121421.jpg

This can be automated as a cron job that syncs your files with your backups in regular intervals

Refer to the `documentation <http://git-annex.branchable.com/walkthrough/#index21h2>`_
to learn more about setting up ssh remotes, removing and transferring files and troubleshooting.

DataLad
=======
DataLad is a solution that provides decentralised access to data from open data annexes.
It provides a command line interface to interact with the technologies it is built on,
such as git and Git-Annex to provide functionality such as dataset searches, dataset nesting,
dataset collections and git annex file management. This makes it a good candidate for 
further extensibility using a web interface.

DataLad also comes with support for metadata, with a search command that enables metadata 
queries via a flexible query language.

Use Case Demo: DataLad on Ubuntu
--------------------------------
.. note::
   
   sudo priviledges are required

Install the `Git-Annex <http://neuro.debian.net/install_pkg.html?p=git-annex-standalone/>`_ from NeuroDebian.
Install DataLad

.. code-block:: bash

   $ sudo apt-get install datalad


.. rubric:: Footnotes

.. [1] https://about.zenodo.org/infrastructure
.. [#] http://eos.web.cern.ch/