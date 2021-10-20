---
title: VM's Volumes
weight: 27
---
___
On this page, you can find an explanation of how to manage Volumes related to the selected Virtual Machine in Cloud Console.

# Table of contents
1. [VM's VOLUMES TAB](#vm's-volumes-tab)
3. [Attach Volume](#attach-volume)
4. [Detach Volume](#detach-volume)
5. [Edit Volume](#edit-volume)
6. [Extend Volume](#extend-volume)

## VM's VOLUMES TAB
To find all Volumes related to the selected Virtual Machine you need:
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/conn-lin/7.png?classes=border,shadow)

- open the *Virtual Machine details page* - for this click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/conn-lin/8.png?classes=border,shadow)

- open the *VOLUMES page of this VM* - for this click on the VOLUMES TAB:
![](../../../assets/images/vol/12.png?classes=border,shadow) 

On this page you can find all Volumes attached to the corresponding VM with their *Headers*, *Attach button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Volume: 
![](../../../assets/images/vol/13.png?classes=border,shadow)    

**Actions** icon opens the next list of available management actions:
- *Attach* - this option attempts to attach the Volume to the VM; you can attach only Volumes with state *available*;  
- *Detach* -  this option attempts to detach the Volume to the VM; you can detach only Volumes with state *in-use*;  
- *Edit* - this option attempts to change the Volume name;
- *Extend* - this option attempts to change the Volume size; volume extension will restart the VM it is attached to.

There are two ways to *attach*, *detach*, *edit* and *extend* Volumes:
1. from the *Volumes page*;
2. from the *VOLUMES TAB* on the *Virtual Machine details page*.

In this article, we will explain the second way - to manage Volumes from the *VOLUMES TAB* on the *Virtual Machine details page*. Information about the first one you can find in the next article - [Volumes]().  

## Attach Volume
>**NOTE:** you can attach only Volumes with state *available*.  

To attach a Volume from the *VOLUMES TAB* on the *Virtual Machine details page* do the following:
- click on the ATTACH VOLUME icon in the upper left corner of the *VOLUMES TAB* on the *Virtual Machine details page*;
- select one of the available Volumes on the next opened *Attach volume window* and click on the ATTACH icon:
![](../../../assets/images/vol/14.png?classes=border,shadow)  

After these steps, the Volume will be attached to the selected VM and it will be displayed on the *VOLUMES TAB* on the *Virtual Machine details page*:
![](../../../assets/images/vol/10.png?classes=border,shadow)   

On the *Volumes page* its status will change to *in-use:
![](../../../assets/images/vol/9.png?classes=border,shadow) 

## Detach Volume
>**NOTE:** you can detach only Volumes with state *in-use*.

To detach a Volume from the *VOLUMES TAB* on the *Virtual Machine details page* do the following:
- identify Volume that you want to detach on the *VOLUMES TAB*;
- click on the **Actions** icon  and select the **Detach** in the list of available options;
- confirm the Volume detaching on the next opened *Confirmation window*.

After these steps, the Volume will be detached from the selected VM.   
On the *Volumes page* its status will change to *available*:
![](../../../assets/images/vol/11.png?classes=border,shadow) 

## Edit Volume
To edit a Volume from the *VOLUMES TAB* on the *Virtual Machine details page* do the following:
- identify Volume that you want to edit on the  *VOLUMES TAB*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Volume Name, Description or/and make the it bootable on the next opened *Edit Volume window* and click on the SAVE icon:
![](../../../assets/images/vol/6.png?classes=border,shadow)

After these steps, the selected Volume will be updated.

## Extend Volume
To extend a Volume from the *VOLUMES TAB* on the *Virtual Machine details page* do the following:
- identify Volume that you want to extend on the  *VOLUMES TAB*;
- click on the **Actions** icon and select the **Extend** in the list of available options;
- change the Volume Size on the next opened *Extend Volume window* and click on EXTEND icon:
![](../../../assets/images/vol/7.png?classes=border,shadow)

After these steps, the selected Volume will be updated.