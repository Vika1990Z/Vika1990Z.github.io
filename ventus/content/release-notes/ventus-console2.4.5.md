---
title: Ventus Console 2.4.5
weight: 15
---
___
Successfully delivered to Production: 07.04.2021
___

Ventus Console 2.4.5 was successfully delivered to Production. Here are the list of updates:

* “Create VM” dialog was changed:
    * Added ability to create VM from volume – volume should be in available state and it will be attached to the new VM.
    * Added ability to create VM from snapshot – new volume will be created from the snapshot and will be attached to the new VM.
    * OS platform parameter was added to distinguish Windows from Linux VMs.
    * When creating VM from volume/snapshot user should provide new keypair/password for it and VM will be created with it (it can be an old one too, but user should specifically choose it).
* PostgreSQL was added to the list of database services with 5 latest versions.
* Versions of all database services were updated to the latest ones.
* Start/stop database actions were added for all databases – if user don’t need its database right now, it will be stopped and resources will not be consumed (we will not bill it when the billing will be ready).
* Support of creating database in private network was added to the API. With one of next releases it will be added to the UI.
* UI notifications were updated – several bugs regarding auto-hide were fixed with this.
* Fixed bug when error appeared if no image information was provided – now image information will not be showed in this case (rare one).
* Fixed bug that owner was not able to edit/delete organization.
* Role “owner” is displayed in the list of administrators for the organization’s owner.
* Length of group names was increased to 255 characters.
* Support of volume and network limits were added to the API. With next release it will be added to the UI (already done in DEV).
