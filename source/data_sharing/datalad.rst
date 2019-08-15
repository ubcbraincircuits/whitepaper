DataLad
=======
DataLad is a solution that provides decentralised access to data from open data annexes.
It provides a command line interface to interact with the technologies it is built on,
such as git and Git-Annex to provide functionality such as dataset searches, dataset nesting,
dataset collections and git annex file management. This makes it a good candidate for 
further extensibility using a web interface.

DataLad also comes with support for metadata, with a search command that enables metadata 
queries via a flexible query language.

Installation: Linux
-------------------
.. note::
   
   sudo priviledges are required

Install the `Git-Annex <http://neuro.debian.net/install_pkg.html?p=git-annex-standalone/>`_ from NeuroDebian.
Install DataLad

.. code-block:: bash

   $ sudo apt-get install datalad