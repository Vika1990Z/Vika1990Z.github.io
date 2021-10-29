---
title: CLI Users
weight: 35
---
___
On this page, you can find an explanation of how to create, edit, delete CLI Users and instructions for other steps to manage CLI Users in the Cloud Console.

# Table of contents
1. [CLI Users page](#cli-users-page)
1. [Create CLI User](#create-cli-user)
1. [Download RC File](#download-rc-file)
1. [Edit CLI User ](#edit-cli-user)
1. [Change the password](#change-the-password)
1. [Delete CLI User ](#delete-cli-user)

## CLI Users page
To get to the *CLI Users page*, select the **Security** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **CLI Users TAB:**
![](../../../assets/images/cli/1.png?classes=border,shadow) 
![](../../../assets/images/cli/2.png?classes=border,shadow) 

On this page you can find all created CLI Users, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected CLI User:
![](../../../assets/images/cli/3.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions with the selected CLI User:
- *Download RC File* - this option is used to get the RC file of the selected CLI User;
- *Edit* - this option is used to change the Name of the selected CLI User;
- *Change password* - this option is used to change the password of the selected CLI User;
- *Delete* - this option is for the CLI User deletion.

## Create CLI User
To create a new CLI User, do the following:
- go to the *CLI Users page* and click on the CREATE CLI USER icon in the upper left corner;
- fill in the form on the next opened *Create CLI User window*:
![](../../../assets/images/cli/3.png?classes=border,shadow) 
  - *Name* - set a name for the CLI User; 
  - *Password* - set the password for the CLI User; 
  - *Confirm password*.

After these steps, the newly created CLI User will be added to the *CLI Users page*:

## Download RC File
To download the RC File that pertains to the CLI User, do the following:
- identify this desired CLI User on the *CLI Users page*;
- click on the **Actions** icon and select the **Download RC File** in the list of available options.

After these steps, the *RC file* of the selected CLI User will be downloaded.

For the next work with CLI User you need:
- to place RC File of the created CLI User to your Virtual Machine:  
`vi openrc`  
Сheck that there were indicated the correct OS_USERNAME and  OS_PROJECT_ID and press *Esc:wq*, then *Enter* to save the changes:  
```
#!/usr/bin/env bash
	export OS_AUTH_URL=https://upper-austria.ventuscloud.eu:443/v3
	export OS_PROJECT_ID=e6370ed9ff7c4122b2b89cde7ff7d29f
	export OS_PROJECT_NAME="e6370ed9ff7c4122b2b89cde7ff7d29f"
	export OS_USER_DOMAIN_NAME="ventus"
	if [ -z "$OS_USER_DOMAIN_NAME" ]; then unset OS_USER_DOMAIN_NAME; fi
	export OS_PROJECT_DOMAIN_ID="e1780e7170674d5684076a726f683cfd"
	if [ -z "$OS_PROJECT_DOMAIN_ID" ]; then unset OS_PROJECT_DOMAIN_ID; fi
	unset OS_TENANT_ID
	unset OS_TENANT_NAME
	export OS_USERNAME="48529f99-8e10-4694-9412-70e1012de805:test-user"
	echo "Please enter your OpenStack Password for project $OS_PROJECT_NAME as user $OS_USERNAME: "
	read -sr OS_PASSWORD_INPUT
	export OS_PASSWORD=$OS_PASSWORD_INPUT
	export OS_REGION_NAME="Upper-Austria"
	if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
	export OS_INTERFACE=public
	export OS_IDENTITY_API_VERSION=3
```   

- execute *openrc* starting with dot:  
`. openrc`  

- provide the password of the created CLI User and hit *Enter*; this password will be used to authenticate you in the Cloud Console.

## Edit CLI User 
To edit the CLI User, do the following:
- identify CLI User, that you want to edit, on the *CLI Users page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the CLI User *Name* on the next opened *Edit CLI User window* and click on the SAVE icon.

After these steps, the selected CLI User Name will be updated.

## Change the password
To change the password of the CLI User, do the following:
- identify CLI User, whose password you want to change, on the *CLI Users page*;
- click on the **Actions** icon and select the **Change password** in the list of available options;
- update the password on the next opened *Change password window*, confirm it and click on the SAVE icon.

After these steps, the password of the selected CLI User will be updated.

## Delete CLI User
To delete the CLI User, do the following:
- identify this unnecessary CLI User on the *CLI Users page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the CLI User deletion on the next opened *Confirmation window*.

After these steps, the selected CLI User will be deleted.

