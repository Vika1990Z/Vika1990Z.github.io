---
title: Projects
weight: 20
---
___
In this article, you can find an explanation of how to create a new Project, and how to manage it in the Cloud Console.

# Table of contents
1. [Projects page](#project-page)
2. [Create a Project](#create-pr)
3. [Edit a Project](#edit-pr)
4. [Delete a Project](#delete-pr)
5. [Add Users to the Project](#add-users) 

## Projects page
___
>To see information about Projects of the Organization and to manage them you can only if your User Role in this Organization is an *Administrator* or *Owner*. 

To see information about created Projects in the Organization or create more Projects in it, you need on the *Organizations page* click on the **Name** of the appropriating Organization:
![](../../assets/images/projects/1-pr.png?classes=border,shadow) 

This action will open additional sections on the *side-bar menu* and redirect you to the *Projects page* where you can find all created Projects related to the selected Organization with their *Headers, Create button, Search bar and Actions icon*, which opens a list of available management actions for the selected Project:
![](../../assets/images/projects/2-pr.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions:
- **Edit** - by selecting this option you can change the Project name;
- **Delete** - this option is for Project removing.

## Create a Project <a id="create-pr"></a>
___
To create a new Project do the following:
- go to the *Projects page* and click on the **CREATE PROJECT** icon in the upper left corner:
![](../../assets/images/projects/3-pr.png?classes=border,shadow) 
- on the next opened *Create Project window* specify: 
  - **Name**: in this field you set a name for the Project;
  - **Region**: here you specify which region this Project will belong to. All other cloud resources that will be created in this Project will belong to this region too.
![](../../assets/images/projects/3-pr.png?classes=border,shadow) 

>**NOTE:** All subsequent services provided by the Cloud Console within the one Project will be created in the corresponding Region in which this Project was created.

After fields were specified, click on the **CREATE** icon and the newly created Project will be added to the *Projects page:*
![](../../assets/images/projects/5-pr.png?classes=border,shadow) 


## Edit a Project <a id="edit-pr"></a> 
___
To edit a Project do the following:
- identify Project you want to edit on the *Projects page*;
- click on the **Actions** icon and select the **EDIT** in the list of available options;
- on the next opened *Edit Project window*, update the Project Name and click on the **SAVE**  icon:
![](../../assets/images/projects/6-pr.png?classes=border,shadow) 
After these steps, the selected Project will be updated.

## Delete a Project <a id="delete-pr"></a>
___
To delete a Project do the following:
- to identify this unnecessary Project on the *Projects page*;
- click on the **Actions** icon  and select the **DELETE** in the list of available options;
- on the next opened *Confirmation window* confirm the Project deletion:
![](../../assets/images/projects/7-pr.png?classes=border,shadow) 
After these steps, the selected Project will be deleted.

## Add users to the Project <a id="add-users"></a>
___
To add Users to the Project, you need to create a Group in which you can create a list of Projects and a corresponding list of Users who will be added to this Project as *Members*.

For more details, please, see - [Groups]

>**NOTE:** Added Members of the Group will have access to Projects from this Group and, accordingly, to all resources in this Project, but will not be able to see information about each other and manage the Groups and Administrators of the Organization that owns this Project.