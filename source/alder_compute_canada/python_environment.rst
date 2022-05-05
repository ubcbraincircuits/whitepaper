Setting up a Python Environment
===============================

.. tip::

   You can also use these instructions to set up python environments on your personal computer

Setting up a python environment using Anaconda
----------------------------------------------
The Anaconda distribution gives you access to many commonly used libraries and is the fastest way
to set up a ready to use python environment. It is also the recommended way of installing
jupyter.

Begin by going to the `Anaconda website <https://www.anaconda.com/distribution/>`_ and copying the 
link to the lastest Linux '64-Bit (x86) Installer.

Download it using
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
   (myvenv) [user@<cluster> ~]$ 
   
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
