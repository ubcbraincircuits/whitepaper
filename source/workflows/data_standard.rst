====================
Data Standardization
====================

A critical but often overlooked aspect of data sharing is data standardization. Currently, there is likely variability in data organization even between neuroscientists from the same lab. However, data is shareable only if it is understandable and interoperable, hence feasible data pooling requires universal standards. Data must be structured and organized in a way that is intuitive and readily usable by researchers within the lab and in the greater neuroscience community. When choosing a system or format, it is best to focus on the following:

* Simplicity: Does the format reflect the contents of my files, my lab practices?
* Accessibility: Is it widely used and recognized by researchers in my field?
* Adoptability: Can members of my lab learn it quickly? Can data be handed off easily?

Minimum Information about a Neuroscience Investigation (MINI)
=============================================================

Best use: electrophysiology data 

Minimum Information about a Neuroscience Investigation (MINI) is a minimum information standard for reporting electrophysiological studies. MINI is registered with Minimum Information for Biological and Biomedical Investigations (MIBBI), a collection of guidelines for reporting bioscience data organized by method of collection. MINI is a metadata standard; it specifies recommended metadata fields pertaining to an electrophysiology dataset to ensure it is accurately interpreted, analyzed, and corroborated by the neuroscience community. The MINI reporting requirements has seven subdivisions: General features, study subject, task, stimulus, behavioral event, recording, and time series data. The `original paper <precedings.nature.com/documents/1720/version/2>`_ can be consulted for definitions. 

Brain Imaging Data Structure (BIDS)
===================================

Use Case Demo: EEG  
------------------

This demo aims to familiarize members of the cluster with the BIDS format and its documentation, most importantly
the `BIDS Specification <https://bids-specification.readthedocs.io/en/stable/03-modality-agnostic-files.html>`__ which this demo is heavily based on. 

The following example uses a BIDS-compliant dataset `eeg_rishikesh <https://github.com/bids-standard/bids-examples/tree/master/eeg_rishikesh>`_. 
It may be helpful to click around the dataset as you go through the demo. Note that the raw data files are empty but they have been shared by the authors
on `Zenodo <https://zenodo.org/record/2536267#.XRUJfLxKi71>`_.

The corresponding paper is "Reduced mind wandering in experienced meditators and associated EEG correlates". *Brandmeyer T, Delorme A. Reduced mind wandering in experienced meditators and associated EEG correlates. 
Exp Brain Res. 2018;236(9):2519-2528. doi:10.1007/s00221-016-4811-5*.

.. image:: /Images/eeg_overview.png
   :width: 750px
   :height: 750px
   :scale: 100 %
   :alt: Overview of the dataset in BIDS format
   :align: center

First, let's check out the metadata ``dataset_description.json`` 
which is required for all datasets. 

Dataset description
~~~~~~~~~~~~~~~~~~~

.. code-block:: json

	{
	  "Name": "Meditation study",
	  "ReferencesAndLinks": [
	    "https://www.ncbi.nlm.nih.gov/pubmed/27815577"
	  ],
	  "License": "CC0",
	  "BIDSVersion": "1.1.1"
	}
	

Of the four fields, only "Name" and "BIDSVersion" are required.
A full list of fields for dataset_description.json is available in the
`BIDS Specification <https://bids-specification.readthedocs.io/en/stable/03-modality-agnostic-files.html>`__.

README
~~~~~~

	"This meditation experiment contains 24 subjects. Subjects were
	meditating and were interupted about every 2 minutes to indicate
	their level of concentration and mind wandering. The scientific
	article (see Reference) contains all methodological details

	-Arnaud Delorme (October 17, 2018)"

A README file is a description of the dataset. It is recommended by BIDS
but must be in ASCII or UTF-8 encoding (text file). 

CHANGES
~~~~~~~

	"Revision history for meditation dataset

	version 1.0 beta - 17 Oct 2018
	 - Initial release

	version 2.0 - 9 Jan 2019
	 - Fixing event field names and various minor issues"
	 
This is an optional text file detailing any changes, updates, and corrections
made to the dataset, i.e. a version history. Note that BIDS requires adherence to the
`CPAN Changelog convention <https://metacpan.org/pod/release/HAARG/CPAN-Changes-0.400002/lib/CPAN/Changes/Spec.pod>`_.

Participants file
~~~~~~~~~~~~~~~~~

.. csv-table:: participants.tsv
	:file: /Users/User/galejo/whitepaper/source/participants.csv
   	:widths: 25, 25, 25, 25
   	:header-rows: 1
	
This is an optional document that contains a table of participants
and their properties as a Tab-Separated Values (TSV) file. 

You may notice that a JSON file of the same name also exists, which simply
contains descriptions of each column.

.. code-block:: json

	{
	  "gender": {
	    "Description": "sex of the participant",
	    "Levels": {
	      "M": "male",
	      "F": "female"
	    }
	  },
	  "participant_id": {
	    "Description": "unique participant identifier"
	  },
	  "age": {
	    "Description": "age of the participant",
	    "Units": "years"
	  },
	  "group": {
	    "Description": "group, expert or novice meditators",
	    "Levels": {
	      "expert": "expert meditator",
	      "novice": "novice meditator"
	    }
	  }
	}
	
Code
~~~~

The folder ``code/`` contains a MATLAB script called ``run_mw_experiment6.m``.
In general, this folder should contain scripts used on the dataset,
such as deface.py and other anonymization tools. Identifiable information should 
be eliminated. 

BIDS Folder Hierarchy
~~~~~~~~~~~~~~~~~~~~~

Before examining the data, let's take a look at the four levels of the BIDS folder hierarchy.

Project
^^^^^^^

In this case, it is ``eeg_rishikesh/``.
	
Subject
^^^^^^^

It must have the following structure:

.. code-block:: python

	sub-<participant label>

with *participant label* typically being a padded number.

Session
^^^^^^^

It must have the following structure:

.. code-block:: python

	ses-<session label>

with *session label* typically being a padded number.

According to the BIDS specification, a session is 

	"a logical grouping of neuroimaging and behavioral data consistent across 
	subjects. Session can (but doesn't have to) be synonymous to a visit in a 
	longitudinal study. In general, subjects will stay in the scanner during one 
	session. However, for example, if a subject has to leave the scanner room and 
	then be re-positioned on the scanner bed, the set of MRI acquisitions will 
	still be considered as a session and match sessions acquired in other 
	subjects. Similarly, in situations where different data types are obtained 
	over several visits (for example fMRI on one day followed by DWI the day after) 
	those can be grouped in one session. Defining multiple sessions is appropriate when 
	several identical or similar data acquisitions are planned and performed on all -or most- 
	subjects, often in the case of some intervention between sessions (e.g., training)."

Acquisition
^^^^^^^^^^^
This can be one of eight types: 

.. code-block:: python

	func (task based & resting state functional MRI)
	dwi (diffusion weighted imaging)
	fmap (field inhomogeneity mapping data such as field maps)
	anat (structural imaging such as T1, T2, etc)
	meg (magnetoencephalography)
	beh (behavioural)
	eeg (electroencephalography)
	ieeg (intracranial electroencephalography)

In this case, it is ``eeg/``.

The location of a raw data file in BIDS format will therefore have the following structure:   

.. code-block:: python

	<project>/sub-<participant label>/ses-<session label>/<acquisition>/<data>

Modality Specific File: EEG
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Notice the 24 subject folders; one for each of the 24 participants. The folders are
almost identical in content so let's focus on one of them.

The folder ``sub-017/`` contains two sessions:

.. code-block:: python

	ses-01
	ses-02

There is only one acquisition per session, ``eeg/``. Let's take a look inside
``ses-01/eeg``.

.. code-block:: python

	sub-017_ses-01_task-meditation_channels.tsv
	sub-017_ses-01_task-meditation_eeg.bdf
	sub-017_ses-01_task-meditation_eeg.json
	sub-017_ses-01_task-meditation_events.tsv

Note the structure of the file names. The template for EEG data is given in the `BIDS
Specification <https://bids-specification.readthedocs.io/en/stable/04-modality-specific-files/03-electroencephalography.html>`_ 
and re-stated below.

.. code-block:: python

	sub-<label>/
	    [ses-<label>]/
	      eeg/
	        sub-<label>[_ses-<label>]_task-<label>[_acq-<label>][_run-<index>]_eeg.<manufacturer_specific_extension>
	        sub-<label>[_ses-<label>]_task-<label>[_acq-<label>][_run-<index>]_eeg.json

Sidecar JSON
^^^^^^^^^^^^

The metadata file ``sub-017_ses-01_task-meditation_eeg.json`` contains the following information
describing the corresponding raw data file of the same name. 

.. code-block:: json

	{
	  "InstitutionAddress": "Centre de Recherche Cerveau et Cognition, Place du Docteur Baylac, Pavillon Baudot, 31059 Toulouse, France",
	  "InstitutionName": "Paul Sabatier University",
	  "InstitutionalDepartmentName": "Centre de Recherche Cerveau et Cognition",
	  "PowerLineFrequency": 50,
	  "ManufacturersModelName": "ActiveTwo",
	  "TaskName": "meditation",
	  "EEGReference": "CMS/DRL",
	  "Manufacturer": "BIOSEMI",
	  "EEGChannelCount": 64,
	  "MiscChannelCount": 15,
	  "RecordingType": "continuous",
	  "RecordingDuration": 2787,
	  "SamplingFrequency": 256,
	  "EOGChannelCount": 0,
	  "ECGChannelCount": 0,
	  "EMGChannelCount": 0,
	  "SoftwareFilters": "n/a"
	}

"TaskName" is a required generic field, while "EEGReference", "SamplingFrequency",
"PowerLineFrequency", and "SoftwareFilters" are required specific EEG fields. The rest
are recommended fields, either generic or specific to EEG. The full list is in
the `BIDS Specification <https://bids-specification.readthedocs.io/en/stable/04-modality-specific-files/03-electroencephalography.html>`__.

Raw data
^^^^^^^^

The file ``sub-017_ses-01_task-meditation_eeg.bdf`` stores the EEG data. BIDS
allows four EEG formats: 

	- Europena data format (.edf)
	- BrainVision data format (.vhdr, .vmrk, .eeg) 
	- EEGlab, a MATLAB toolbox (.set, .fdt)
	- Biosemi data format (.bdf)
	
If the original data is not in one of the formats above, then it must be made available
in a separate folder called ``/sourcedata`` (more on this at the end of the demo).

Channels description
^^^^^^^^^^^^^^^^^^^^

Let's check out ``sub-017_ses-01_task-meditation_channels.tsv``.

.. csv-table:: sub-017_ses-01_task-meditation_channels.tsv
	:file: /Users/User/galejo/whitepaper/source/sub-017_ses-01_task-meditation_channels.csv
   	:widths: 33, 33, 33
   	:header-rows: 1

This table has all three of the required columns in the proper order: name, type, and units. 
Other recommended columns as well as a list of types is in the `BIDS Specification <https://bids-specification.readthedocs.io/en/stable/04-modality-specific-files/03-electroencephalography.html>`__.

Task Events
^^^^^^^^^^^

BIDS defines an event as "a stimulus or subject response recorded during a task" (see the
Common Principles section in the `specification <https://bids-specification.readthedocs.io/en/stable/02-common-principles.html>`_ 
for more definitions). Since this study is on mind wandering during meditation, it involves stimuli
and responses which is why there exists a file called ``sub-017_ses-01_task-meditation_events.tsv``. 

Note that `Task Events <https://bids-specification.readthedocs.io/en/stable/04-modality-specific-files/05-task-events.html>`_ 
are classified separately from EEG.

.. csv-table:: sub-017_ses-01_task-meditation_events.tsv
	:file: /Users/User/galejo/whitepaper/source/sub-017_ses-01_task-meditation_events.csv
   	:header-rows: 1

The first two columns, onset and duration, are required whereas trial_type, response_time,
sample, and value are optional.

One might ask, *'Where is the accompanying JSON file?'*. Now is a good time to introduce the `Inheritance 
Principle <https://bids-specification.readthedocs.io/en/stable/02-common-principles.html>`_.

The Inheritance Principle
~~~~~~~~~~~~~~~~~~~~~~~~~

The Inheritance Principle states that values from a metadata file defined at the top directory level are 
inherited by all lower levels unless overriden by a file at a lower level. 

Return to the project folder ``eeg_rishikesh/``. Observe that the JSON file ``task-meditation_events.json``
for the events file discussed above lives here. This file applies to all participants therefore
it is defined at the top level and its values are then *inherited* by all subfolders.

.. code-block:: json

	{
	  "onset": {
	    "Description": "Event onset",
	    "Units": "second"
	  },
	  "duration": {
	    "Description": "Event duration",
	    "Units": "second"
	  },
	  "trial_type": {
	    "Description": "Type of event (different from EEGLAB convention)",
	    "Levels": {
	      "stimulus": "Onset of first question",
	      "response": "Response to question 1, 2 or 3"
	    }
	  },
	  "response_time": {
	    "Description": "Response time column not use for this data"
	  },
	  "sample": {
	    "Description": "Event sample starting at 0 (Matlab convention starting at 1)"
	  },
	  "value": {
	    "Description": "Value of event (numerical)",
	    "Levels": {
	      "2": "Response 1 (this may be a response to question 1, 2 or 3)",
	      "4": "Response 2 (this may be a response to question 1, 2 or 3)",
	      "8": "Response 3 (this may be a response to question 1, 2 or 3)",
	      "16": "Indicate involuntary response",
	      "128": "First question onset (most important marker)"
	    }
	  }
	}

As expected, it describes each column of ``sub-017_ses-01_task-meditation_events.tsv``. 

A more detailed explanation of the Inheritance Principle is in the `Common Principles
<https://bids-specification.readthedocs.io/en/stable/02-common-principles.html>`_. section
of the BIDS specification. 

Stimuli
~~~~~~~

Last but not least, the audio files used as stimuli are stored in ``eeg_rishikesh/stimuli``.

Source and Derived Data
~~~~~~~~~~~~~~~~~~~~~~~

Other datasets in the GitHub repository `bids-examples <https://github.com/bids-standard/bids-examples>`_
have ``sourcedata/`` and ``derivatives/`` folders. The BIDS format segregates
**raw** (unprocessed), **source** (pre-file format conversion or pre-harmonization), 
and **derived** (processed) data into separate folders to prevent accidental changes to the raw data. 

These folders preserve the same folder and file name structure as the the folders containing the raw data. 

References
~~~~~~~~~~

Original paper:
Gorgolewski KJ, Auer T, Calhoun VD, et al. `The brain imaging data structure, a format for organizing and describing outputs of neuroimaging experiments. Sci Data. 2016;3. doi:10.1038/sdata.2016.44 <https://www.nature.com/articles/sdata201644>`_

BIDS Extension Proposal:
Pernet CR, Appelhoff S, Flandin G, Phillips C, Delorme A, Oostenveld R. `BIDS-EEG: an extension to the Brain Imaging Data Structure (BIDS) Specification for electroencephalography. PsyArXiv. 2018. doi:10.31234/osf.io/63a4y <https://psyarxiv.com/63a4y/>`_
















	
	

	






	








	


