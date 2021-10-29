---
title: Ventus Console 2.4.4
weight: 20
---
___
Successfully delivered to Production: 25.03.2021
___

*Ventus Console 2.4.4 was successfully delivered to Production.*  
Here are the list of updates:

* MariaDB was added as DBaaS – all DBaaS UI was changed to support multiple DB engines
* VM Console logs were added to VM details – might be useful for customers to troubleshoot Linux VMs
* “Download RDP” action was removed for non-Windows VMs – a leftover bug, now fixed
* Image information was added to VM details
* Max length of organization name was changed to 255 chars
* Max length of cli user name was changed to 218 chars
* Max length of project name was changed to 27 chars
* Action to create Volume from Snapshot was added to the Storage -> Snapshots page . We are also working on creation of VMs from Volumes/Snapshots. Should be added in the next release.
* Object Storage (S3 compatible) was added to the Storage page - Object Storage is now available for our customers. 
* IP ACLs were added to the Create/Edit database – with this users can restrict from which networks connections to the database is allowed
 