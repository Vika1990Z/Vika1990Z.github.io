---
title: Volumes
weight: 25
---
___
On this page, you can find an explanation of how to create, edit, delete Volumes and instructions for other steps to manage Volumes in Cloud Console.

# Table of contents
1. [Volumes page](#volumes-page)
2. [Create Volume](#create-volume)
3. [Attach Volume](#attach-volume)
4. [Detach Volume](#detach-volume)
5. [Edit Volume](#edit-volume)
6. [Extend Volume](#extend-volume)
7. [Delete Volume](#delete-volume)

## Volumes page
To get to the *Volumes page* select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Volumes TAB:**
![](../../../assets/images/vol/1.png?classes=border,shadow) 
![](../../../assets/images/vol/2.png?classes=border,shadow) 

On this page you can find all your own Volumes created in the current Project, and the Volumes created during Cluster and VM creation, with their *Headers*, *Create button*, *Search bar* and *Actions icon* which opens a list of available management actions for the selected Volume:
![](../../../assets/images/vol/3.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions:
- *Attach* - this option attempts to attach the Volume to the VM; you can attach only Volumes with state *available*;  
- *Detach* -  this option attempts to detach the Volume to the VM; you can detach only Volumes with state *in-use*;  
- *Edit* - this option attempts to change the Volume name;
- *Extend* - this option attempts to change the Volume size; volume extension will restart the VM it is attached to;
- *Delete* - this option is for Volume deletion.

There are two ways to attach, detach, edit and extend a Volume:
1. from the *Volumes page*;
2. from the *VOLUMES TAB* on the *Virtual Machine details page*.

In this article, we will explain the first way - to manage Volumes from the *Volumes page*. Information about the second one you can find in the next article - [VM's Volumes]().  

>**NOTE**: You can't delete the Volume with the state *in-use,* firstly, you need to detach it.

## Create Volume
To create new Volume do the following:
- go to the *Volumes page* and click on the CREATE VOLUME icon in the upper left corner;
- fill in the form on the next opened *Create Volume window* and click on the CREATE icon:
![](../../../assets/images/vol/4.png?classes=border,shadow) 
  - *Name* - set a name for the Volume; if Volume was created during Cluster or VM creation, its name will be generated automatically;
  - *Description* - set a description for the Volume;
  - *Volume Type* - select Volume type from the list of available;
  - *Volume Size* - specify volume size; it can be in the range from 10 GB to 1000 GB; minimal available size 10 GB is selected by default.

After these steps, the newly created Volume will be added to the *Volumes page* with the status *available*:
![](../../../assets/images/vol/5.png?classes=border,shadow) 

## Attach Volume
>**NOTE:** you can attach only Volumes with state *available*.  

To attach a Volume from the *Volumes page* do the following:
- identify Volume you want to attach on the *Volumes page*;
- click on the **Actions** icon  and select the **Attach** in the list of available options;
- choose VM to which you want to attach selected Volume on the next opened *Attach Volume window* and on the ATTACH icon:
![](../../../assets/images/vol/8.png?classes=border,shadow) 

After these steps, the Volume will be attached to the selected VM.  
On the *Volumes page* its status will change to *in-use:
![](../../../assets/images/vol/9.png?classes=border,shadow) 

And also, this Volume will be displayed on the *VOLUMES TAB* on the *Virtual Machine details page*:
![](../../../assets/images/vol/10.png?classes=border,shadow) 

## Detach Volume
>**NOTE:** you can detach only Volumes with state *in-use*.

To detach a Volume from the *Volumes page* you need to do the following:
- identify Volume that you want to detach on the *Volumes page*;
- click on the **Actions** icon  and select the **Detach** in the list of available options;
- confirm the Volume detaching on the next opened *Confirmation window*.

After these steps, the Volume will be detached from the selected VM.  
On the *Volumes page* its status will change to *available*:
![](../../../assets/images/vol/11.png?classes=border,shadow) 

## Edit Volume
To edit a Volume from the *Volumes page* do the following:
- identify Volume that you want to edit on the *Volumes page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Volume Name, Description or/and make the it bootable on the next opened *Edit Volume window* and click on the SAVE icon:
![](../../../assets/images/vol/6.png?classes=border,shadow)

After these steps, the selected Volume will be updated.

## Extend Volume
To extend a Volume from the *Volumes page* do the following:
- identify Volume that you want to extend on the *Volumes page*;
- click on the **Actions** icon and select the **Extend** in the list of available options;
- change the Volume Size on the next opened *Extend Volume window* and click on EXTEND icon:
![](../../../assets/images/vol/7.png?classes=border,shadow)

After these steps, the selected Volume will be updated.

## Delete Volume
>**NOTE**: You can't delete the Volume with the state *in-use,* firstly, you need to detach it.  

To delete a Volume do the following:
- identify this unnecessary Volume on the *Volumes page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Volume deletion on the next opened *Confirmation window*.

After these steps, the selected Volume will be deleted.
