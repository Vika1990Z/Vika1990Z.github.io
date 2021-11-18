---
title: Create Image from Snapshot
weight: 23
---
___
On this page we will discuss the workflow, that can help you to create an Image from Snapshot.

# Table of contents
1. [Prerequisites](#prerequisites)
2. [Workflow](#workflow)



## Prerequisites
In this article we will assume, that we have already created the following resources, that refer to the Project named *dev-1* that was created in the Organization named *Test1*: 

  - **CLI User** named *dev1CLIuser* and which RC file has already been loaded;  
  - **Ubuntu Virtual Machine (IP: 88.218.53.162, Name: vm-1)**; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH.    
  
**To find more detailed instructions see the next articles:** 
    [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/);   
    [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);      
    [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);        

## Workflow    
### Prepare the Snapshot
To create a Snapshot from the current state of the VM do the following:
- open the *Virtual Machine details page* by clicking on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/tutorials/0-6.png?classes=border,shadow) 

{{% notice note %}}
It is recommended to stop the Virtual Machine before taking a Snapshot.  
{{% /notice %}} 

{{% notice warning %}}
Snapshots, taken from a volume with a "in-use" status, may contain corrupted data.
{{% /notice %}} 

- go to the SNAPSHOTS TAB and click the CREATE icon in the upper left corner:
![](../../../assets/images/tutorials/0-7.png?classes=border,shadow) 

- fill in the form on the next opened *Create Snapshot window* and click on the CREATE icon:
![](../../../assets/images/tutorials/0-8.png?classes=border,shadow)

After these steps, the newly created Snapshot will be added on the *Snapshots page*.

{{% notice tip %}}
To find more detailed instructions about Snapshot creation, see the article: [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).
{{% /notice %}} 

You can check if this Snapshot is working correctly by creating Virtuale Machine from it:
![](../../../assets/images/tutorials/0-4.png?classes=border,shadow)


### Create Volume from the Snapshot
To create a Volume from the Snapshot do the following:

- open the *Snapshots page*, click on the **Actions** icon of the selected Snapshot and select the **Create volume** in the list of available options:
![](../../assets/images/tutorials/15.png?classes=border,shadow) 

- fill in the form on the next opened *Create volume from snapshot window* and click on the CREATE icon:
![](../../assets/images/tutorials/16.png?classes=border,shadow) 

After these steps, the newly created Volume will be added to the *Volumes page* with the status *available*:
![](../../assets/images/tutorials/16.png?classes=border,shadow) 

{{% notice tip %}}
To find detailed instructions about Volume creation, see the article: [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/) 
{{% /notice %}} 

### Create Image of the Volume
To create a Image of the Volume do the following:

- connect to the preiviously created Virtual Machine in the current Project *dev-1*; 

{{% notice tip %}}
To find detailed instructions, how to connect to the Linux VM, see the article: [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)
{{% /notice %}} 

- install Openstack client on the current VM;

{{% notice tip %}}
To find detailed instructions, how to Install and configure OpenStack CLI, see the article: [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)*
{{% /notice %}} 

- place RC File of the created CLI User, named *dev1CLIuser*, to your Virtual Machine and execute it starting with dot:  
    `vi dev1-openrc`    
    `. dev1-openrc`  

{{% notice note %}}
Please note, that RC file of the current CLI User has already loaded.   
{{% /notice %}} 

{{% notice tip %}}
To find detailed instructions, how to load RC Files, see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)
{{% /notice %}}   

- get a list of all Volumes created in the corresponding Project and to which your User has access:  
    `openstack volume list`      

    In our case the output will be next:    
    ```
    ubuntu@vm-1:~$ openstack volume list
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    | ID                                   | Name        | Status    | Size | Attached to                   |
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    | 95ed1f4c-XXXX-XXXX-XXXX-XXXXXXXXXXXX | vol-from-sn | available |   10 |                               |
    | 48124dc6-XXXX-XXXX-XXXX-XXXXXXXXXXXX |             | in-use    |   10 | Attached to vm-2 on /dev/vda  |
    | 777b8334-XXXX-XXXX-XXXX-XXXXXXXXXXXX |             | in-use    |   10 | Attached to vm-1 on /dev/vda  |
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    ```
- create an Image from the selected Volume:    

    `openstack image create --disk-format qcow2 --volume 95ed1f4c-XXXX-XXXX-XXXX-XXXXXXXXXXXX img-migrated`    

    In our case the output will be next:    
    ```
    ubuntu@vm-1:~$ openstack image create --disk-format qcow2 --volume 95ed1f4c-XXXX-XXXX-XXXX-XXXXXXXXXXXX img-migrated    
    +---------------------+--------------------------------------+
    | Field               | Value                                |
    +---------------------+--------------------------------------+
    | container_format    | bare                                 |
    | disk_format         | qcow2                                |
    | display_description | volume created from the snapshot     |
    | id                  | 95ed1f4c-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
    | image_id            | cc326302-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
    | image_name          | img-migrated                         |
    | protected           | False                                |
    | size                | 10                                   |
    | status              | uploading                            |
    | updated_at          | 2021-11-18T14:25:35.000000           |
    | visibility          | shared                               |
    | volume_type         | __DEFAULT__                          |
    +---------------------+--------------------------------------+
    ```

{{% notice note %}}
It may take a long time to create Images from a Volume, please wait until its status becomes active.
{{% /notice %}} 

- get a list of Images related to the current Project:  
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

After these steps, the newly created Image will be added to the *Images page* and you can use to create new Virtual Machines:   
![](../../assets/images/tutorials/0-9.png?classes=border,shadow) 
