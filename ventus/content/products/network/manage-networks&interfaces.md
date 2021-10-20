---
title: VM's Networks and Interfaces
weight: 25
---
___
On this page, you can find an explanation of how to manage Networks and Interfaces related to the selected Virtual Machine in Cloud Console.

# Table of contents
1. [VM's NETWORKS & SECURITY TAB](#vm's-networks-&-security-tab)
2. [Add Interface](#add-interface)
3. [Remove Interface](#remove-interface)

## VM's NETWORKS & SECURITY TAB
To find all Networks and Interfaces related to the selected Virtual Machine you need:
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/conn-lin/7.png?classes=border,shadow)

- open the *Virtual Machine details page* - for this click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/conn-lin/8.png?classes=border,shadow)

- open the *NETWORKS & SECURITY page of this VM* - for this click on the NETWORKS & SECURITY TAB:

On the opened page you can find *two blocks*:
1. the first upper block contains information about all Networks related to the selected VM;
2. the second one contains information about all Firewalls related to this VM:

In this article, we are interested in the first upper block of the opened page, where you can find all Networks related to the corresponding VM with their *Headers*, *Add Interface button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network: 
![](../../../assets/images/networks/9.png?classes=border,shadow)    
Information about the second block of this page you can find in the article [VM's Firewalls]().

## Add Interface
To add additional Interface to the selected VM do the following:
- click on the ADD INTERFACE icon;
- select one of the available Networks, specify *Fixed IPs* on the next opened *Add interface window* and click on the ADD icon:
![](../../../assets/images/networks/10.png?classes=border,shadow)

>**NOTE:** You can select only Networks that have associated Subnets.  
The Fixed IPs should be selected from the Allocation pools of the corresponding Subnet.

After these steps, the newly added Interface will appear in the first top block of the NETWORKS & SECURITY TAB of the *selected VM detailed page* with the status ACTIVE.  
Now you can open its *Subnets page* by clicking on the **Name** of the corresponding Network:
![](../../../assets/images/networks/11.png?classes=border,shadow)  

On this page you can find all Subnets related to the selected Network with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Subnet:
![](../../../assets/images/networks/12.png?classes=border,shadow) 
   
For more information about Networks and their Subnets, please, see the next articles:  
[Networks]()  
[Subnets]()

## Remove Interface
To remove the Interface from the corresponding VM do the following:
- identify unnecessery Interface that you want to remove on the NETWORKS & SECURITY TAB of the *selected VM detailed page*;
- click on the **Actions** icon  and select the **Remove** in the list of available options;
- confirm the Interface deletion on the next opened *Confirmation window*.

After these steps, the selected Interface will be deleted.
