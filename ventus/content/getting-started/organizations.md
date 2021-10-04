---
title: Organizations
weight: 15
---

# Organizations and Administrators

In this article, you can find an explanation of how to create a new Organization and how to manage it and its Administrators in the Cloud Console.

# Table of contents

1. [Organizations page](https://kb.ventuscloud.eu/knowledge/organizations#org-page)
   1. [Create an Organization](https://kb.ventuscloud.eu/knowledge/organizations#create-org)
1. [Administrators of the Organization](https://kb.ventuscloud.eu/knowledge/organizations#users)
   1. [Add Administrator to the Organization](https://kb.ventuscloud.eu/knowledge/organizations#add-user)
   1. [Remove Administrator from the Organization](https://kb.ventuscloud.eu/knowledge/organizations#remove-user)

## Organizations page  

If you are a new user and have just created new account you will be automatically redirected to the *Organizations page* where you can create your first Organization or find a list of Organizations to which Projects your User has access as a *Member*:  

![](../../assets/images/organizations/1-org.png?classes=shadow)  

If you aren't a new User, but want to see information about created Organizations or find information about Organizations to which Projects your User has access you need on the *Homepage* to select the **Organizations** from the *side-bar menu:*  

![](../../assets/images/organizations/2-org.png?classes=shadow)  

This action will redirect you to the *Organizations page* where you can find all created Organizations and Organizations to which Projects your User has access with their *Headers, Add Organization button, Search bar, and Actions icon* which opens a list of available management actions for the selected Organization:  

![](../../assets/images/organizations/3-org.png?classes=shadow)  

Organizations **headers** include:  

- **Name**: shows the name of the Organization;  
- **ID**: shows the Organizations ID;  
- **Role**: shows the User Role in the Organization;  

**Actions** icon opens the next list of available management actions (are active only if User is an **Owner or Administartor** in the selected Organization):  

- **Edit** - this option is using to change the name of the selected Organization.  
- **Delete** - this option is using to delete the Organization.  

As you see, in the Organizations User can have next Roles:  

- **Owner** - this role is assigned to a User, who created this Organization (this User will also be considered the *Administrator* of this Organization) and opens access to all resources of the Organization including the management of Groups, Projects and their all Users;  
- **Administrator** - this role can be assigned to a User by another Administrator of the Organization. Administrators have access to all resources of the Organization, including the management of Groups, Projects and their Users;  
- **Member** - this role is assigned to a User who is granted access to the Organization's Project and, accordingly, to all resources within this Project. Member can't add/remove other Users in the Project and even can't see information about them.  

### Create an Organization  

To create a new Organization do the following:  

- go to the *Organizations page* and click the **CREATE ORGANIZATION** icon in the upper left corner: ![](../../assets/images/organizations/4-org.png)  
- on the next opened *Create Organization window* specify the **Name** of the Organization and click on the **CREATE** icon:  

![](../../assets/images/organizations/5-org.png?classes=shadow)  

After these steps the newly created Organization will be added to the *Organizations page* and your User Role there will be *Owner*:  

![](../../assets/images/organizations/6-org.png?classes=shadow)  

## Administrators of the Organization  

{% include alert.html type="info" title="Note: " content="To see information about Administrators of the Organization and to manage them you can only if your User Role in this Organization is an *Administrator* or *Owner*." %}    

To see information about Administrators of the Organization and to manage them go to the *Organizations page* and  click on the **Name** of the Organization:  

![](../../assets/images/organizations/7-org.png?classes=shadow)  

It will open next additional sections on the *side-bar menu,* from which you need to select *Administrators*:  

![](../../assets/images/organizations/8-org.png?classes=shadow)  

This action will redirect you to the *Administrators page*, where you can find all Administrators related to this Organization with their *Headers, Add Administrator button and Search bar:  

![](../../assets/images/organizations/9-org.png?classes=shadow)  

Administrators **headers** include:  

- **Full name**: shows the Administrators full name;   
- **E-mail**: shows the e-mail address of the Administrators;   
- **Role**: shows the Administrators Role in the selected Organization;  

### Add Administrator to the Organization  

{% include alert.html type="info" title="Note: " content="You can add only those Users who have already passed the registration stage in the Cloud Console and aren't members of one of the Projects of this Organization" %}     

To add new Administrator to the selected Organization do the following:   

- go to the *Administrators page* and click the **ADD ADMINISTRATOR** icon in the upper left corner: ![](../../assets/images/organizations/10-org.png?classes=shadow)          
- on the next opened *Add Administrator window* specify the **E-mail address**, and click on the **Send invitation** icon:      

![](../../assets/images/organizations/11-org.png?classes=shadow)    

After these steps the newly added Administrator will appear on the *Administrators page* of the selected Organization, but with marked with the message **pendig invitation**:  

![](../../assets/images/organizations/12-org.png?classes=shadow)  

At the same moment, the User to whom you sent the invitation received the following message to the email you specified:    

![](../../assets/images/organizations/13-org.png?classes=shadow)  

When the invited User accepts your invitation by clicking on the link sent to him, he will be  added on the *Administrators page* as a **Administrator** and with active *Actions icon* which opens a list of available management actions for the selected Administrator:  

![](../../assets/images/organizations/14-org.png?classes=shadow)  

**Actions** icon opens the next list of available management actions:  

- **Transfer an organization** - this option is using to change the Owner of the selected Organization.  
- **Remove** - this option is using to delete the Administrator from the Organization.  

### Transfer the Organization  

To Transfer the Organization means to change its Owner. 
For this you need:  

- to identify the Administrator to whom you want to Transfer the Organization on the *Administrators page*;    
- click on the **Actions** icon ![](../../assets/images/organizations/15-org.png?classes=shadow) and select the **Transfer the Organization** in the list of available options;    
- on the next opened *Confirmation window* confirm your actions and click on the **Send** icon:      

![](../../assets/images/organizations/17-org.png?classes=shadow)     

After confirming this action, the selected User will recieve the following message: an dif he accept it, his Role in the selected Organization will be changed from *Administrator* to *Owner*.    

![](../../assets/images/organizations/18-org.png?classes=shadow)   

### Remove Administrator from the Organization    

To remove Administrator from the selected Organization do the following:

- to identify this unnecessary Administrator on the *Administrators page*;   
- click on the **Actions** icon ![](../../assets/images/organizations/15-org.png?classes=shadow) and select the **Remove** in the list of available options;    
- on the next opened *Confirmation window* confirm the User deletion:    

![](../../assets/images/organizations/16-org.png?classes=shadow)     

After confirming this action, the selected User will be removed from the selected Organization.


