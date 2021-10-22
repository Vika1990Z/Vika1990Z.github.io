---
title: Firewalls
weight: 15
---
___
On this page, you can find an explanation of how to create, edit and delete Firewalls in the Cloud Console.

# Table of contents
1. [Firewalls page](#firewalls-page)
2. [Create Firewall](#create-firewall)
3. [Edit Firewall](#edit-firewall)
4. [Delete Firewall](#delete-firewall)

## Firewalls page
To get to the *Firewalls page* select the **Security** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Firewalls TAB:**
![](../../../assets/images/cli/1.png?classes=border,shadow) 
![](../../../assets/images/fw/1.png?classes=border,shadow) 

On this page you can find *default* Firewall, all your own Firewalls created in the current Project, and the Firewalls created during Cluster creation, with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Firewall:
![](../../../assets/images/fw/2.png?classes=border,shadow)

>**NOTE**: All VMs have a default Firewall which is applied to any VM.  
The user cannot delete default Firewall or change its Name or Description but can change its rules.  
Default Firewall allows access to the Internet from the VMs, but denies almost all access on the VMs from outside, except for objects belonging to the same default Firewall.  

**Actions** icon opens the next list of available management actions but isn't active for default Firewall:
- *Edit* - this option is used to change the name and/or description of the selected Firewall;
- *Delete* - this option is for Firewall deletion.

## Create Firewall
To create new Firewall do the following:
- open the *Firewalls page* and click on the CREATE FIREWALL icon in the upper left corner;
- fill in the form on the next opened *Create Firewall window*:
![](../../../assets/images/fw/3.png?classes=border,shadow)
  - *Name* - set a name for the Firewall; 
  - *Description* - set a description for the Firewall.

After these steps, the newly created Firewall will be added to the *Firewalls page*.  

Now you can open this *Firewall Rules page* - for this click on the **Name** of the corresponding Firewall:
![](../../../assets/images/fw/5.png?classes=border,shadow)  

On this page you can find:
- panel with available **quick actions** for the selected Firewall: 
![](../../../assets/images/networks/13.png?classes=border,shadow) 
- all Rules related to the selected Firewall with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Rule:
![](../../../assets/images/fw/4.png?classes=border,shadow)  

As you can see, the rules, that allow all outbound traffic, have been already created by default, but you can delete them by using **Actions** icon or add additional rule here by using CREATE FIREWALL RULE button.   

For more information about Firewall Rules, please, see the next article - [Firewall Rules]()

## Edit Firewall
To edit a Firewall do the following:
- identify Firewall that you want to edit on the *Firewalls page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Firewall Name or/and Description on the next opened *Edit Firewall window*, and click on the SAVE icon.

After these steps, the selected Firewall will be updated.  
Also, you can edit the Firewall from *Firewall Rules page*, by clicking on the appropriative **quick actions** icon there.

## Delete Firewall
To delete a Firewall do the following:
- identify this unnecessary Firewall on the *Firewalls page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Firewall deletion on the next opened *Confirmation window*.

After these steps, the selected Firewall will be deleted.  
Also, you can delete the Firewall from *Firewall Rules page*, by clicking on the appropriative **quick actions** icon there.