Tarballing Files
================
Tarballing is the process of bundling multiple files into one file. It is Compute Canada's recommendation that a collection of multiple small files be tarballed into large files.
It is also the recommended way to store files in Nearline since smaller files are not written to tape. Systems like Cedar, which have a conservative number of files allowed in Nearline (5K) also warrant tarballing to keep the file count low.

A tarball can also be compressed using the gunzip command. This has its limitations, such as not being able to add files to an existing gunzipped tarball. It is also unlikely to reduce the size of certain file formats like videos and images. 

Working with Tarballs (CLI)
---------------------------

.. note::

   You can also use a GUI of your choice. The CLI is often the only choice for working over ``SSH``.

Tarballing/Compressing Files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To make a tarball

.. code-block::
   
   # tarball
   $ tar -cvf <.tar file> /path/to/folder/to/tarball/
   # e.g. $ tar -cvf example.tar videos/
   
   # gunzipped tarball
   $ tar -cvzf <.tar.gz file> /path/to/folder/to/gunzip/
   # e.g. $ tar -cvzf example.tar.gz videos/

Adding files to existing archive (only ``.tar`` files)

.. code-block::
   
   $ tar -rvf <.tar file> /path/to/folder/or/file/to/add/

Extracting files
~~~~~~~~~~~~~~~~
To extract a tarball

.. code-block::
   
   $ tar -xvf <.tar file> -C </directory/to/extract/to/>
   
   # or to extract in current directory
   $ tar -xvf <.tar file> 

To extract a gunzipped tarball

.. code-block::
   
   $ tar -xvzf <.tar.gz file> -C </directory/to/extract/to/>
   # e.g. $ tar -xvzf 

   # or to extract in current directory
   $ tar -xvzf <.tar.gz file> 

Extract particular file/folder from tarball/gunzipped tarball

.. code-block::

   $ tar --extract <.tar/.tar.gz file> <path/to/file>
   # e.g. $ tar --extract example.tar example.txt

Extract multiple files

.. code-block::
   
   # tarball
   $ tar -xvf <.tar file> "<path/to/file1>" "<path/to/file2>" 
   
   # gunzipped tarball
   $ tar -xvzf <.tar.gz file> "<path/to/file1>" "<path/to/file2>" 

Extract files by wildcard

.. code-block::

   # tarball
   $ tar -xvf <.tar file> --wildcards "*.mp4"
   
   # gunzipped tarball
   $ tar -xvzf <.tar.gz file> --wildcards "*.mp4"

Viewing Contents of Archive
~~~~~~~~~~~~~~~~~~~~~~~~~~~
To view contents of a tarball/gunzipped tarball

.. code-block::

   $ tar -tvf <.tar/.tar.gz file>