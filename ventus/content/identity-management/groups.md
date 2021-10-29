---
title: Groups
weight: 30
---
___
On this page, you can find an explanation of how to create and manage a new Group in the Cloud Console.

# Table of contents
1. [Groups page](#groups-page)
2. [Create Group](#create-group)
3. [Configure Group](#configure-group) 
    1. [Manage Users in Group](#manage-users-in-group)
    2. [Manage Projects in Group](#manage-projects-in-group)
4. [Edit Group](#edit-group)
5. [Delete Group](#delete-group)

## Groups page

{{% notice note %}}
Using Groups in the Cloud Console you can add additional Users to the Project. 
{{% /notice %}}  

To get to the *Group page*, select the **Groups** from the *side-bar menu*.

On this page you can find all created Groups, related to the selected Organization with the *Add Group button, Search bar*, and *Actions icon*, which opens a list of available management actions for the selected Group:
![](../../assets/images/groups/1-gr.png?classes=border,shadow)  

**Actions** icon opens the next list of available management actions:
- *Edit* - this option is using to change the Group name;
- *Delete* - this option is using to remove the Group.

## Create Group
To create a new Group, do the following:
- go to the *Groups page* and click on the CREATE GROUP icon in the upper left corner;
- specify the **Name** of the Group on the next opened *Create Group window* and click on the CREATE icon:
![](../../assets/images/groups/2-gr.png?classes=border,shadow) 

After these steps, the newly created Group will be added to the *Groups page*.  
The next step is to configure the created Group.

## Configure Group
To set up the Group membership and permissions you can from the *Group details page.*  
To get to the *Group details page* click on the **Name** of the corresponding Group:
![](../../assets/images/groups/3-gr.png?classes=border,shadow) 

On the *Group details page* you can see two blocks: the first top block is for the Users, and the second one is for the Projects, that you want to share with Users from the top block:
![](../../assets/images/groups/4-gr.png?classes=border,shadow) 

So, from this page you can:
- **review** which Users have access to which Projects;
- **add** more Users to the selected Projects;
- **assign** more Projects to the selected Users;
- **remove Users** from the selected Projects;
- **remove Projects** from access of selected Users;

### Manage Users in Group

{{% notice note %}}
You can add as many Users and Projects to the Group as you need.
{{% /notice %}}

To add a new User to the selected Group, do the next:
- go to the *Group details page* and click on the ADD USER icon;
- specify the **E-mail address** of the User, that you want to add to the group, and click on the ASEND INVITATION icon:
![](../../assets/images/groups/5-gr.png?classes=border,shadow) 

After this, the User, whose email address you entered in the invitation, will receive an email with the *Accept invitation link*. By clicking on this link, the user will be redirected to the Cloud Console, where he need to click the *ACCEPT INVITATION* icon.      

And on the yours *Group details page* you will see the added information about your invitation with the active **Actions** icon:
![](../../assets/images/groups/6-gr.png?classes=border,shadow)
**Actions** icon in this step opens the next list of available management actions:  
- *Resend invitation* - this option is using to send one more invitation with the *Accept invitation link*.
- *Delete invitation* - this option is using to block the *Accept invitation link* in the invitation.

When the invited User accepts your invitation, he will get access to the projects, that you provided in the appropriate Group, and on your *Group details page* you will see this newly added User with active *Actions icon*:
![](../../assets/images/groups/7-gr.png?classes=border,shadow) 
**Actions** icon after accepting invitation opens the next list of available management actions:  
- *Remove* - this option is using to delete the User from the Group.

### Manage Projects in Group
To add the Project to the selected Group, do the following:
- go to the *Group details page* and click on the ASSIGN TO THE PROJECT icon;
- select the Project, to which you want to assign Users, from the first block, and click on the ASSIGN icon:
![](../../assets/images/groups/8-gr.png?classes=border,shadow)

After these steps, the newly added Project will appear in the second block of the *Group details page* with active *Actions icon*: 
![](../../assets/images/groups/9-gr.png?classes=border,shadow)
**Actions** icon after accepting invitation opens the next list of available management actions:  
- *Remove* - this option is using to delete the Project from the Group.

Users from the first block will have access to this Project and, accordingly, to all resources in this Project, but they will not be able to manage the Groups and Administrators of the Organization that owns this Project:
![](../../assets/images/groups/10-gr.png?classes=border,shadow)

## Edit Group
To edit a Group, do the following:
- identify the Group, that you want to edit, on the *Groups page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Name of the selected Group on the next opened *Edit Group window*,  and click on the SAVE icon.

After these steps, the selected Group will be updeted.

## Delete Group
To delete a Group, do the following:
- identify the unnecessary Group on the *Groups page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Group deletion on the next opened *Confirmation window*.

After these steps, the selected Group will be deleted.


