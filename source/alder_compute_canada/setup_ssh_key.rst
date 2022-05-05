Set Up an SSH Key 
=================
SSH keys allow you to conveniently authenticate to remote computers by allowing you to connect to them 
without entering your passsword each time.

This procedure is meant to be done on your local machine.

.. Note::

   This procedure should work for Windows, MacOS and Linux users.
   If you are on Windows and the command below does not work in PowerShell, 
   you must `install Git Bash <https://git-scm.com/download/win>`_.

1) Generate the Key
-------------------
Open the git bash command line and enter:

.. code-block:: bash
   
   $ ssh-keygen

Follow the prompts. 
It is highly recommended that you use a secure password for your key.
It is recommended that you use the default location suggested to stopre the key. 
You should see something like this:

.. code-block:: bash

   Generating public/private rsa key pair.
   Enter file in which to save the key (/c/Users/user/.ssh/id_rsa):
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   Your identification has been saved in /c/Users/user/.ssh/id_rsa.
   Your public key has been saved in /c/Users/user/.ssh/id_rsa.pub.
   The key fingerprint is:
   SHA256:2mrihQwvnsIx8gDp8pO01EmCT4PgnTSVgv8Xj1vKNOg user@May2015b
   The key's randomart image is:
   +---[RSA 2048]----+
   |  . ...          |
   |.. + .           |
   |o++ +            |
   |=.++.  .         |
   |oo.=... S        |
   |++++o+ B o       |
   |+*+o= * *        |
   |.o*o.E.=         |
   | .oo.o.          |
   +----[SHA256]-----+

We can check the contents of the ``.ssh`` directory with 

.. code-block:: bash
   
   $ ls ~/.ssh
   id_rsa  id_rsa.pub 

``id_rsa`` is the private key and ``id_rsa.pub`` is the public key

2) Add key to ``ssh-agent``
---------------------------
Start the agent by running

.. code-block:: bash
   
   $ eval "ssh-agent"

Add the key

.. code-block:: bash
   
   # Windows and Linux
   $ ssh-add ~/.ssh/id_rsa # or wherever your private key is stored

.. code-block:: bash
   
   # MacOS
   $ ssh-add -K ~/.ssh/id_rsa # or wherever your private key is stored

For MacOS to remember your private key password, create a file called ``~/.ssh/config`` 
and input the following:
::

	Host *
	UseKeychain yes

3) SSH agent forwarding
-----------------------
If a ``~/.ssh/config`` does not already exist, create it. Add to the file the following:
::

    Host cedar
      Hostname  cedar.computecanada.ca
      User  username
      ForwardAgent  yes
    
    Host graham
      Hostname  graham.computecanada.ca
      User  username
      ForwardAgent  yes

    Host beluga
      Hostname  beluga.computecanada.ca
      User  username
      ForwardAgent  yes

Where ``username`` is your username on the remote computer. You can add other blocks like these 
for other remote computers if you wish. 

Now, you should be able to log in to a remote machine using only ``ssh <host>`` instead of ``ssh <username@host.address.com>`` e.g. 

.. code-block:: bash

    $ ssh cedar

Instead of 

.. code-block:: bash

    $ ssh user@cedar.arc.ubc.ca


4) Install your ssh public key on the remote machines
-----------------------------------------------------
Copy your public key to each of the remote machines in your ``~/.ssh/config`` file, for instance:

.. code-block:: bash

    $ ssh-copy-id -i $HOME/.ssh/id_rsa cedar

You will be prompted for your password on the remote machine and the key will be installed.

Once your key is installed, you should be able to run commands like ``ssh``, ``scp``, ``sftp`` and ``rsync`` 
without having to enter your password.

.. Note::

   You may be prompted for the password to your key when you first log into the remote server via ``SSH``

5) (Optional) Add SSH key to GitHub Account
-------------------------------------------
You can also add your ssh key to your GitHub account to avoid entering your password each time 
you push to the cloud. 
Instructions are available `here <https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account>`_.
