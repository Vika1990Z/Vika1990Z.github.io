---
title: VM's Firewalls
weight: 22
---
___
On this page, you can find an explanation of how to manage Firewalls related to the selected Virtual Machine in Cloud Console.

# Table of contents
1. [VM's NETWORKS & SECURITY TAB](#vm's-networks-&-security-tab)
2. [Add Firewall](#add-firewall)
3. [Remove Firewall](#remove-firewall)

## VM's NETWORKS & SECURITY TAB
To find all Firsewall related to the selected Virtual Machine you need:
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/conn-lin/7.png?classes=border,shadow)

- open the *Virtual Machine details page* - for this click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/conn-lin/8.png?classes=border,shadow)

- open the *NETWORKS & SECURITY page of this VM* - for this click on the NETWORKS & SECURITY TAB:

On the opened page you can find *two blocks*:
1. the first upper block contains information about all Networks related to the selected VM;
2. the second one contains information about all Firewalls related to this VM:

In this article, we are interested in the second block of the opened page, where you can find all Firewalls related to the corresponding VM with their *Headers*, *Add Firewall button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network:
![](../../../assets/images/fw/9.png?classes=border,shadow)

Information about the first block of this page you can find in the article [VM's Networks and Interfaces]().

## Add Firewall
To add additional Firewall to the selected VM do the following:
- click on the ADD FIREWALL icon;
- select one of the available priviously added Firewalls and click on the ADD icon:
![](../../../assets/images/fw/10.png?classes=border,shadow)

After these steps, the newly added Firewall will be added to the selected.    
Now you can open this *Firewall Rules page* by clicking on the **Name** of the corresponding Firewall:
![](../../../assets/images/fw/11.png?classes=border,shadow)  

On this page you can find all Rules related to the selected Firewall with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Rule:
![](../../../assets/images/fw/12.png?classes=border,shadow) 
   
For more information about Firewalls and their Rules, please, see the next articles:  
[Firewalls]()  
[Firewall Rules]()

## Remove Firewall
To remove the Firewall from the corresponding VM do the following:
- identify unnecessery Firewall that you want to remove on the NETWORKS & SECURITY TAB of the *selected VM detailed page*;
- click on the **Actions** icon  and select the **Remove** in the list of available options;
- confirm the Firewall deletion on the next opened *Confirmation window*.

After these steps, the selected Firewall will be deleted from this VM.
