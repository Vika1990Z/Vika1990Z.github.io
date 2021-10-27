---
title: Snapshots
weight: 30
---
___
On this page, you can find an explanation of how to create, edit, delete Snapshots and how to create Volumes from the Snapshots in Cloud Console.

# Table of contents
1. [Snapshots page](#snapshots-page)
1. [Create Snapshot](#create-snapshot)
3. [Create Volume from Snapshot](#create-volume-from-snapshot)
1. [Edit Snapshot](#edit-snapshot)
1. [Delete Snapshot](#delete-snapshot)

## Snapshots page
To get to the *Snapshots page* select **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Snapshots TAB**:
![](../../../assets/images/vol/1.png?classes=border,shadow) 
![](../../../assets/images/snap/1.png?classes=border,shadow) 

On this page you can find all created Snapshots with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Snapshot:
![](../../../assets/images/snap/2.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:
- *Create volume* - this option is used to create a Volume from the selected Snapshot;
- *Edit* - this option is used to change Name and/or Description of the selected Snapshot;
- *Delete* - this option is for the Snapshot removing.

There are two ways to *create*, *edit* and *delete* Snapshots:
1. from the *Snapshots page*;
2. from the *SNAPSHOTS TAB* on the *Virtual Machine details page*.

In this article, we will explain the first way - to manage Snapshots from the *Snapshots page*. Information about the second one you can find in the next article - [VM's Snapshots]().  

## Create Snapshot
To create new Snapshot from the *Snapshots page* do the following:
- go to the *Snapshots page* and click the *CREATE SNAPSHOT* icon in the upper left corner;
- fill in the form on the next opened *Create Snapshot window* and click on the CREATE icon:
![](../../../assets/images/snap/3.png?classes=border,shadow)
  - *Name* - set a name for the Snapshot;
  - *Description* - set a description for the Snapshot;
  - *Volume* - select volume from what you want to create a Snapshot.

{{% notice warning %}}
Snapshot created from the volume with "in-use" status can contain corrupted data.
{{% /notice %}}  

After these steps, the newly created Snapshot will be added to the *Snapshots page*:
![](../../../assets/images/snap/4.png?classes=border,shadow)

Also, if the Snapshot was created from the Volume that had been attached to some VM, this Shapshot will be displayed on the *SNAPSHOTS TAB* on the *Virtual Machine details page*:
![](../../../assets/images/snap/5.png?classes=border,shadow)

## Create Volume from Snapshot
To create a Volume from the selected Snapshot do the following:
- identify Snapshot from which you want to create a Volume on the *Snapshots page*;
- click on the **Actions** icon and select the **Create volume** in the list of available options;
- fill in the form on the next opened *Create volume from snapshot window* and click on the CREATE icon:
![](../../../assets/images/snap/7.png?classes=border,shadow)
  - *Name* - set a name for the Volume;
  - *Description* - set a description for the Volume.

After these steps, the newly created Volume will be added to the *Volumes page* with the status *available*:
![](../../../assets/images/snap/8.png?classes=border,shadow)

How to manage Volumes you can find in the next articles:   
[Volumes]();  
[VM's Volumes]().  

## Edit Snapshot 
To edit a Snapshot from the *Snapshots page* do the following:
- identify Snapshot that you want to edit on the *Snapshots page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Snapshot Name or/and Description on the next opened *Edit Snapshot window* and click on the SAVE icon:
![](../../../assets/images/snap/6.png?classes=border,shadow)

After these steps, the selected Snapshot will be updated.

## Delete Snapshot
To delete a Snapshot from the *Snapshots page* do the following:
- identify this unnecessary Snapshot on the *Snapshots* *page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Snapshot deletion on the next opened *Confirmation window*.

After these steps, the selected Snapshot will be deleted.
