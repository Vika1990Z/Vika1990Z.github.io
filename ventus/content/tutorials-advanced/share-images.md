---
title: Share Images between Projects
weight: 24
---
___
On this page, we will discuss a workflow to help you to share Images between Projects in the same Region.

# Table of contents
1. [Prerequisites](#prerequisites)
2. [Workflow](#workflow)
    1. [Share Image with another Project](#share-image-with-another-project)
    2. [Accept shared Image](#accept-shared-image)
    3. [Unshare Image](#unshare-image)

## Prerequisites
In this article, we will assume that we have already created two Projects, belonging to different Organizations, but to the same Region, and the following resources within these Projects:

- **Project 1** named *dev-1*, that was created in the Organization named *Test1* and related to the Vienna Region, with the following resources:
  - **CLI User** named *dev1CLIuser* and which RC file has already been loaded;  
  - **Ubuntu Virtual Machine (IP: 88.218.53.162, Name: vm-1)**; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH;
  - **Custon Image** named *img-migrated*, that was created from the VM's Snapshot;   
  For detailed instructions on how to do this, see here: [Create Image from Snapshot](https://docs.ventuscloud.eu/tutorials-advanced/image-from-snapshot/)

{{% notice tip %}}
You can upload any custom Image to your Project. Please see detailed instructions, if you need:: [Images](https://docs.ventuscloud.eu/products/storage/custom-images/)
{{% /notice %}} 

- **Project 2** named *dev-2*, that was created in the Organization named *Test2* and related to the Vienna Region, with the following resources:
  - **CLI User** named *dev2CLIuser* and which RC file has already been loaded;  

{{% notice note %}}
If you want to share an Image with another Project, you need to know the ID of this Project. 
{{% /notice %}} 

**For more information on the prerequisites discussed, see the following articles:**   
    [Projects](https://docs.ventuscloud.eu/getting-started/projects/);  
    [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/);   
    [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);        
    [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);  
    [Images](https://docs.ventuscloud.eu/products/storage/custom-images/);  
    [Create Image from Snapshot](https://docs.ventuscloud.eu/tutorials-advanced/image-from-snapshot/).


## Workflow
In this article, we will look at a scenario where it is needed to share a custom Image, uploaded to the Project-1 named *dev-1*, with the Project-2 named *dev-2*.
This workflow consists of the next steps:
1. Share an Image with another Project
2. Accept a shared Image
3. Unshare an Image

Let's take a closer look at each of them.

### Share Image with another Project
To share Image with another Project you need to know the ID of this Project (we will use 8726fcdXXXXXXXXXXXXXXXXXXXXXXXXX) and to do the following:

- connect to the preiviously created Virtual Machine in the current Project *dev-1*; 

{{% notice tip %}}
To find detailed instructions, how to connect to the Linux VM, see the article: [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)
{{% /notice %}} 

- install Openstack client on the current VM;

{{% notice tip %}}
To find detailed instructions, how to Install and configure OpenStack CLI, see the article: [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)
{{% /notice %}} 

- use CLI User named *dev1CLIuser* created in the Project-1 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:    
    `vi dev1-openrc`    
    `. dev1-openrc` 

{{% notice note %}}
Please note, that RC file of the current CLI User has already loaded.   
{{% /notice %}} 

{{% notice tip %}}
To find detailed instructions, how to load RC Files, see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)
{{% /notice %}} 

-  find the ID of the Image you want to share:  
    `openstack image show <image name>`  
    
    In our case the output will be next:    
    ```  
    ubuntu@vm-1:~$ openstack image list  
    +--------------------------------------+--------------------------------------------------+--------+
    | ID                                   | Name                                             | Status |
    +--------------------------------------+--------------------------------------------------+--------+
    | ....                                 | ....                                             | ....   |
    | cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX | img-migrated                                     | active |  <--
    | ....                                 | ....                                             | ....   |
    +--------------------------------------+--------------------------------------------------+--------+
    ```

- share the selected Image with your Project-2 *dev-2*:    
    `openstack image add project <image ID> <project ID>`  

    In our case the output will be next:    
    ```  
    ubuntu@vm-1:~$ openstack image add project cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX 8726fcdXXXXXXXXXXXXXXXXXXXXXXXXX
    +------------+--------------------------------------+
    | Field      | Value                                |
    +------------+--------------------------------------+
    | created_at | 2021-11-18T18:14:05Z                 |
    | image_id   | cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
    | member_id  | 8726fcdXXXXXXXXXXXXXXXXXXXXXXXXX     |
    | schema     | /v2/schemas/member                   |
    | status     | pending                              |
    | updated_at | 2021-11-18T18:14:05Z                 |
    +------------+--------------------------------------+
    ```

- verify the Image is now shared:  
    `openstack image member list <image ID>`  

    In our case the output will be next:    
    ```  
    ubuntu@vm-1:~$ openstack image member list cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    +--------------------------------------+----------------------------------+---------+
    | Image ID                             | Member ID                        | Status  |
    +--------------------------------------+----------------------------------+---------+
    | cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX | 8726fcdXXXXXXXXXXXXXXXXXXXXXXXXX | pending |
    +--------------------------------------+----------------------------------+---------+
    ```

{{% notice info %}}
The status field should say pending until your collaborator accepts the Image.
{{% /notice %}} 

### Accept shared Image
To accept shared Image do the following:

* use CLI User named *dev2CLIuser* created in the Project-2 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:    
    `vi dev2-openrc`    
    `. dev2-openrc` 

* accept the shared Image:  
    `openstack image set --accept <image ID>`

    In our case the command will look like:  
    ```  
    ubuntu@vm-1:~$ openstack image set --accept cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    ```

* verify the Image is now available to your Project:  
    `openstack image list`  

    In our case the output will be next:  
    ```  
    ubuntu@vm-1:~$ openstack image list  
    +--------------------------------------+--------------------------------------------------+--------+
    | ID                                   | Name                                             | Status |
    +--------------------------------------+--------------------------------------------------+--------+
    | ....                                 | ....                                             | ....   |
    | cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX | img-migrated                                     | active |  <--
    | ....                                 | ....                                             | ....   |
    +--------------------------------------+--------------------------------------------------+--------+
    ```

After these steps, the newly created Image will be added to the *Images page* of the the Project-2 named *dev-2* and you can use it to create new Virtual Machines within this Project:   
![](../../assets/images/tutorials/0-9.png?classes=border,shadow) 

### Unshare Image
To unshare an Image use the command:    
    `openstack image remove project <image ID> <project ID>`   
    
In our case the command will look like:    
    ```
    ubuntu@vm-1:~$ openstack image remove project cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX 8726fcdXXXXXXXXXXXXXXXXXXXXXXXXX
    ```

