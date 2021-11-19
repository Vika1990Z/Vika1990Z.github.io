---
title: Transfer Images between Regions
weight: 24.5
---
___
On this page, we will discuss a workflow to help you to transfer Images between Projects in the different Region.

# Table of contents
1. [Prerequisites](#prerequisites)
2. [Workflow](#workflow)
    1. [Prepare custom Image](#prepare-custom-image)
    2. [Save custom Image](#save-custom-image)
    3. [Upload custom Image](#upload-custom-image)

## Prerequisites
In this article, we will assume that we have already created two Projects, belonging to different Regions, and the following resources within these Projects:

- **Project-1** named *v-dev*, that related to the *Vienna* Region, with the following resources:
  - **CLI User** named *v-CLIuser* and which RC file has already been loaded;  
  - **Ubuntu Virtual Machine (IP: 88.218.53.162, Name: vm-1)**; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH;

- **Project-2** named *sw-dev*, that related to the *Eastern-Switzerland* Region, with the following resources:
  - **CLI User** named *sw-CLIuser* and which RC file has already been loaded;  

**For more information on the prerequisites discussed, see the following articles:**   
    [Projects](https://docs.ventuscloud.eu/getting-started/projects/);  
    [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/);   
    [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);        
    [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);  
    [Images](https://docs.ventuscloud.eu/products/storage/custom-images/);  
    [Create Image from Snapshot](https://docs.ventuscloud.eu/tutorials-advanced/image-from-snapshot/).

## Workflow
In this article, le look at a scenario where it is needed to share a custom Image, uploaded to the Project-1 named *v-dev* related to the *Vienna* Region, with the Project-2 named *sw-dev* related to the Eastern-Switzerland Region.
This workflow consists of the next steps:
1. Prepare custom Image in the Project-1
2. Save custom Image on the VM
3. Upload custom Image to the Project-2

Let's take a closer look at each of them.

### Prepare custom Image
You can upload any custom Image that was already saved locally, or create the neccessery Image from an Snapshot.
Please choose, what is better for you, and see detailed instructions in the next articles:  
    [Images](https://docs.ventuscloud.eu/products/storage/custom-images/);  
    [Create Image from Snapshot](https://docs.ventuscloud.eu/tutorials-advanced/image-from-snapshot/)

### Save custom Image
To save custom Image on the VM do the following:
- connect to the preiviously created Virtual Machine in the current Project-1 *v-dev*; 

{{% notice tip %}}
To find detailed instructions, how to connect to the Linux VM, see the article: [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)
{{% /notice %}} 

- install Openstack client on the current VM;

{{% notice tip %}}
To find detailed instructions, how to Install and configure OpenStack CLI, see the article: [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)
{{% /notice %}} 

- use CLI User named *v-CLIuser* created in the Project-1 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:  
    `vi v-openrc`    
    `. v-openrc`  

{{% notice note %}}
Please note, that RC file of the current CLI User has already loaded.   
{{% /notice %}} 

{{% notice tip %}}
To find detailed instructions, how to load RC Files, see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)
{{% /notice %}}   

- find the ID of the Image you want to transfer:  
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
- save the selected Image on your VM:  
    `openstack image save --file <file-name>.raw <image-id>`  

    In our case the command will look like:  
    ```
    ubuntu@vm-1:~$ openstack image save --file image.raw cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    ```

### Upload custom Image
To Upload custom Image to the Project-2 do the following:

* use CLI User named *sw-CLIuser* created in the Project-2 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:  
    `vi sw-openrc`    
    `. sw-openrc` 

{{% notice note %}}
Make sure you are logged in to the correct OpenStack platform with your CLI tools
{{% /notice %}} 

* upload your image that you’ve just downloaded using the following command:  
    `openstack image create --container-format bare --disk-format qcow2 --property os_platform='linux' --file <image_file_name> <image_name>`
    
* check that the Image is added:  
    `openstack image list`  

    In our case the output will be next:    
    ```
    ubuntu@vm-1:~$ openstack image list  
    +--------------------------------------+--------------------------------------------------+--------+
    | ID                                   | Name                                             | Status |
    +--------------------------------------+--------------------------------------------------+--------+
    | ....                                 | ....                                             | ....   |
    | af1c886b-XXXX-XXXX-XXXX-XXXXXXXXXXXX | transfered-img                                   | active |  <--
    | ....                                 | ....                                             | ....   |
    +--------------------------------------+--------------------------------------------------+--------+
    ```

After these steps, the newly created Image will be added to the *Images page* of the the Project-2 related to the *Eastern-Switzerland* Region and you can use it to create new Virtual Machines within this Region:   
![](../../assets/images/tutorials/0-0.png?classes=border,shadow) 
