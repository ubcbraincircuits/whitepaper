Federated Research Data Repository (FRDR)
=========================================
`Portage <https://portagenetwork.ca/>`_, `Compute Canada (CC) <https://www.computecanada.ca/>`_ 
and the `Canadian Association of Research Libraries (CARL) <http://www.carl-abrc.ca/about-carl/>`_ 
have collaborated to produce the `Federated Research Data Repository <https://www.frdr.ca/repo/>`_.


Storage and Backup
------------------
Location
~~~~~~~~
From frdr.ca/docs/en/about:

    Data submitted to FRDR is housed on Compute Canada managed infrastructure at the University of Victoria, 
    BC or at the University of Waterloo, ON. Research data submitted to FRDR does not leave Canada.
    The metadata related to datasets is housed in a database the University of Victoria. 
    Most of that metadata is shared with Globus, running on Amazon Web Services services in the USA, 
    to be indexed and made available for discovering datasets. Certain metadata fields, 
    for example, submitter contact information, are not shared with Globus.

Larger uploads are made using Globus. While globus is hosted in the USA on AWS, 
only the public metadata is stored there; the datasets themselves are transferred 
securely between the endpoints so the data does not leave Canada.

Size limits
~~~~~~~~~~~
There is a theoretical dataset limit of 4TB due to the limitation of the Archivematica
data preservation system. There has not been further comment on whether they will 
impose their own upload size limit.

However, they do have limited resources so they may impose restrictions during curation 
if datasets of unreasonable magnitude are uploaded.

Changes
-------
Only authorised curators can make changes to submitted data. 
A request must be made via email in case any changes need to be made.

Curation 
~~~~~~~~
Curators will perform tasks like:
* Checking metadata record for completeness
* Linking DOIs for related publications 
* Validation of data, for instance, flagging tabular null data with no explanation, corrupt files
* Checking documentation
* Checking for copyright and ethical violations

They typically take up to 48 hours to complete this process, after which it takes 15 minutes to 
complete DOI registration, and a further 2 hours for the dataset to appear for download 
in the FRDR portal.

Data Sharing and Collaboration
------------------------------
FRDR includes search functionality for its own datasets and datasets 
that it harvests from other sources such as the Scholars Portal Dataverse. 
Users can search for/deposit datasets using the online web interface or by using an API. 
Note that while depositing data requires authorisation, anybody can search for datasets.
FRDR is also format agnostic, and allows users to manage the dataset file hierarchy. 
It also support embargos. They also issue DOIs for all deposited datasets.
Other features include data integrity checks using checksums, curation and upload authentication.
Through the use of Globus, FRDR also enables secure transfer of large datasets with the ability 
to make asynchronous and resumable transfers that are automatically managed.