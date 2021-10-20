---
title: Networks
weight: 15
---
___
On this page, you can find an explanation of how to create, edit and delete Networks in Cloud Console.

# Table of contents
1. [Networks page](#networks-page)
2. [Create Network](#create-network)
3. [Edit Network](#edit-network)
4. [Delete Network](#delete-network)

## Networks page
To get to the *Networks page* select the **Networks**  from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/networks/1.png?classes=border,shadow) 

On this page you can find the default *public* Network, all your own Networks created, and the Networks created during Cluster creation, with their *Headers*, *Create button*, *Search* *bar* and *Actions icon* which opens a list of available management actions for the selected Network:
![](../../../assets/images/networks/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions but isn't active for default public Network:
- *Edit* - this option attempts to change the name, description of the selected Network and its administrative state;
- *Delete* - this option is for Network removing.

## Create Network
To create a new Network do the following:
- go to the *Networks page* and click on the CREATE NETWORK icon in the upper left corner;  
- fill in the form on the next opened *Create Network window* and click on the CREATE icon:
![](../../../assets/images/networks/3.png?classes=border,shadow)  
  - *Name* - set a name for the Network; 
  - *Description* - set a description for the Network;
  - make a mark if the Network need the *administrative* state to be up.

After these steps, the newly created Network will be added to the *Networks page* with the status ACTIVE.  

Now you can open the *Subnets page* related to this Network - for this click on the **Name** of the corresponding Network:
![](../../../assets/images/networks/4.png?classes=border,shadow) 

On this page you can find all Subnets related to the selected Network with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Subnet and panel with available **quick actions**:
![](../../../assets/images/networks/12.png?classes=border,shadow)   
For more information about Subnets, please, see the next article - [Subnets]()

## Edit Network
To edit a Network do the following:
- identify the Network that you want to edit on the *Networks page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Name or/and Description of the selected Network, change its administrative state on the next opened *Edit Network window* and click on the SAVE icon.

After these steps, the selected Network will be updated.  
Also, you can edit the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there.

## Delete Network
To delete a Network do the following:
- identify this unnecessary Network on the *Networks page*;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Network deletion on the next opened *Confirmation window*.

After these steps, the selected Network will be deleted.  
Also, you can delete the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there.

