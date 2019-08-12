================
Working on Alder
================

.. toctree::	
	:caption: Table of Contents
	:maxdepth: 3
	
	alder

Alder is the DMCBH's High Performance Computing cluster hosted in the University Data Center.
Contact for access. 

.. todo::
   Contact for alder access

.. note::
   A '$' indicates that the line is to be run in the terminal.
   You should only enter the text following the '$' into the terminal.

Logging in to Alder via SSH
===========================
Linux and MacOS
---------------
Test availability of ssh by entering the following command:

.. code-block:: bash

   $ ssh -V

You should see something like 

.. code-block:: bash
 
   OpenSSH_7.9p1, OpenSSL 1.1.1a  20 Nov 2018

Log into Alder

.. code-block:: bash

   $ ssh <username>@alder.arc.ubc.ca

With ``<username>`` replaced with your alder username. 
Input your password and press enter. You should now be logged in.

Windows
-------

A. Using Git Bash
~~~~~~~~~~~~~~~~~
Download and install `Git Bash <https://git-scm.com/download/win>`_. Once you have it set up, you can use the same process as in the previous section.

B. Using PuTTY
~~~~~~~~~~~~~~
Download and install the latest version of PuTTY from `here <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`_

Open up PuTTY.
Under the ‘Session’ section, set the Host Name to ‘alder.arc.ubc.ca’

.. image:: ../Images/putty/1connect.PNG

Click on Open. This should open up a terminal.
Input your login credentials. 
If the login is successful, you should see something like this:

.. image:: ../Images/putty/3login.PNG



Setting up a python environment on Alder with conda
===================================================
Request resources
-----------------
One CPU and 4GB of RAM should be sufficient

.. code-block:: bash
  
   $ salloc --cpus-per-task=1 --mem-per-cpu=4000m


You should see something like this:

.. code-block:: bash
 
   salloc: Granted job allocation 14567


Setting up a python environment using Anaconda
----------------------------------------------
The Anaconda distribution gives you access to many commonly used libraries and is the fastest way
to set up a ready to use python environment. It is also the recommended way of installing
jupyter.

Begin by going to the `Anaconda website <https://www.anaconda.com/distribution/>`_ and copying the 
link to the lastest Linux '64-Bit (x86) Installer.

Download it onto alder using
``wget "<link to installer file>"`` e.g.

.. code-block:: bash

   $ wget "https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh"

Install Anaconda using
``bash <name of the file you just downloaded>``, then following the installer's instructions.
It is highly recommended to use the default settings provided by the installer. 

.. code-block:: bash

   $ bash Anaconda3-2019.03-Linux-x86_64.sh

Installing conda only
---------------------
The links to the Miniconda installer can be found `here <https://docs.conda.io/en/latest/miniconda.html>`_,
and can be installed using the same procedure as in the previous section.

Miniconda only includes python and the conda package manager.

Setting up a custom python environment
--------------------------------------
1. Using conda
~~~~~~~~~~~~~~
Conda combines pip and venv and offers a better user experience.
This excellent `tutorial <https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/>`_
from UoA e-research gives concise instructions on setting up virtual environments using conda.

2. Using venv
~~~~~~~~~~~~~
venv comes into play if you prefer not to work with conda.

Replace 'myvenv' with whatever path you want to keep you virtual environment in.

.. code-block:: bash
   
   # create the venv
   $ python3 -m venv myvenv
   # activate the venv
   $ source myvenv/bin/activate
   # you should now see the name of our venv in the terminal prefix
   (myvenv) [user@alder-login02 ~]$ 
   
Upgrade pip

.. code-block:: bash

   $ pip install --upgrade pip

You can view the packages you have install into your virtual environment using ``pip --list``.
You should see something like:

.. code-block:: bash

   Package    Version
   ---------- -------
   pip        19.1.1 
   setuptools 28.8.0 

Now we can install some packages

.. code-block:: bash

   # install a package
   $ pip install numpy
   # install many packages at once
   $ pip install scipy matplotlib
   # install a particular version of a package
   $ pip install h5py==2.9.0

You can deactivate the virtual environment with

.. code-block:: bash

   $ deactivate

Whenever you want to use the environment again, activate it using 
``source <path to venv activate>``, e.g.

.. code-block:: bash
   
   $ source myvenv/bin/activate

If you want to save your environment configuration, use ``pip freeze``

.. code-block:: bash

   $ pip freeze > requirements.txt

You can also use a requirements file to build or modify your virtual environment

.. code-block:: bash

   $ pip install -r requirements.txt

Run Jupyter on Alder Remotely
=============================
To run the jupyter server on Alder but open the web interface on your local machine:

Linux and MacOS
---------------
SSH into Alder and activate your jupyter python environment.
Start your jupyter server with the following command

.. code-block:: bash

   $ jupyter notebook --no-browser --port=<port on alder>

If you prefer to use jupyter lab, use 


.. code-block:: bash

   $ jupyter lab --no-browser --port=<port on alder>

Replace ``<port on alder>`` with a source port on Alder. It is recommended to use a port number greater 
than 8000 so it does not conflict with the ports used for other services.

Copy the token code that appears after ``token=`` 

On your local machine, open another terminal and tunnel into that port.
Replace ``username`` with your alder username.

.. code-block:: bash

   $ ssh -N -f -L localhost:<port on alder>:localhost<port on your computer> <username>@alder.arc.ubc.ca

Open up a browser and go to ``localhost:<port on your computer>``. 
On the jupyter page that appears, paste your token code into the box and click on ‘Log in’. 
You should now see the usual jupyter notebook/lab interface.


Windows
-------
A. Using Git Bash
~~~~~~~~~~~~~~~~~
Same process as in the previous section.

B. Using PuTTY
~~~~~~~~~~~~~~
Open up PuTTY.
Under the ‘Session’ section, set the Host Name to ‘alder.arc.ubc.ca’

.. image:: ../Images/putty/1connect.PNG

Next, expand the SSH tab and click on Tunnel. 
Enter the Source port at which you want to launch the jupyter server on Alder, and the 
Destination port which you would like to use to access the notebook on your machine in the 
format localhost:<port>. Click on 'Add', then 'Open'.

.. image:: ../Images/putty/1putty-tunnel.PNG

Input your login credentials. If the login is successful, you should see something like this:

.. image:: ../Images/putty/3login.PNG

Next, request the resources you would like to use for your notebook session, for instance, th following 
would give you 4 CPU cores and 8000 MB of RAM.

.. code-block:: bash
  
   $ salloc --cpus-per-task=4 --mem-per-cpu=2000m

Where mem-per-cpu is the amount of RAM per cpu in megabytes.

Activate your jupyter python environment e.g.

.. code-block:: bash

   $ source myenv/bin/activate

Where myenv is the environment

Launch the jupyter notebook server on the source port specified earlier e.g. 
if the port was 8887

.. code-block:: bash

   $ jupyter notebook --no-browser --port=8887

If you prefer to work in jupyter lab instead, use this instead

.. code-block:: bash

   $ jupyter lab --no-browser --port=8887

.. image:: ../Images/putty/4notebook-server.PNG

Copy the token by selecting the text and right clicking
On your local machine, open a browser and go to the localhost port specified in the 
Destination earlier, e.g. ‘localhost:8887’. You should see a page that looks like this. 
Paste the token you had copied in the previous step into the box and click on ‘Log in’. 
You should then see a typical notebook/lab interface open up.


.. image:: ../Images/putty/5logintonotebook.PNG
