Backup Snapshots
================

To prevent the loss of work and data, as well as to keep it secure and enable versioning, the use of backup software is recommended for all live storage in a lab, including data storage drives, servers and workstations.

Backup snapshots create images of your filesystems at configurable intervals, for instance, storing hourly snapshots for 7 days, storing weekly snapshots for 6 months and monthly snapshots indefinitely. File duplication is minimised as unchanged files are not backed up again, and features such as checksum verification exist to maintain integrity. In addition, the files can be encrypted to maintain high levels of security. This enables researchers to easily revert their filesystem to its state in an earlier snapshot or retrieve an earlier version of a file. The number of redundancies can also be configured, enabling automatic backups across different backup locations and media.

There are also free open source software solutions available, including `Duplicati <http://duplicati.com>`_, `Restic <http://restic.net>`_ and `Borg <http://borgbackup.org>`_. Various paid software solutions are also available, such as `Crashplan <http://crashplan.com>`_ and `Acronis True Image <http://acronis.com>`_. Labs considering such an automated backup solution should consider their needs and resource availability when making their decision.