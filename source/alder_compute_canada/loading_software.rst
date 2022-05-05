Loading Software
================

Working with Modules
--------------------

On Compute Canada Systems, a list of all available modules can be obtained by running:

.. code-block:: bash
   
   $ module spider

To see detailed information about a module, run:

.. code-block:: bash
   
   $ module whatis <module name>

To load a module, for instance a module called ``python``, run:

.. code-block:: bash 

   $ module load python

To see a list of modules you have loaded, run:

.. code-block:: bash
   
   $ module list

See also: `List of software available on Compute Canada <https://docs.computecanada.ca/wiki/Available_software>`_

Bash Configuration
------------------
If you are working in Bash, you can configure your account to automatically load the modules you need each time you log in. 

1) Loading modules
~~~~~~~~~~~~~~~~~~
Add to your ``$HOME/.bashrc`` file (on the remote computer) bash commands you want to execute when you log in.
For loading some modules, for instance, there is the following example::

    module load python
    module load machinelearning
    module load hdf5

2) Ensure ``.bashrc`` is run when you log in
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Create a file called ``$HOME/.bash_profile`` (on the remote computer) the following::

    if [ -f ~/.bashrc ]; then
        . ~/.bashrc;
    fi
