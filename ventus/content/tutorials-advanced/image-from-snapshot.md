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
  *To find more detailed instructions see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/).*

  - **Ubuntu Virtual Machine (IP: 88.218.53.162, Name: vm-1)**; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH; and has a previously installed Openstack client.    
  *To find more detailed instructions see the next articles:*  
    *[Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);*    
    *[Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);*        
    *[Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/).*  

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

1. Connect to the preiviously created Virtual Machine in the current Project *dev-1*:  
    `ssh -i ~/.ssh/id_rsa ubuntu@88.218.53.162`  

{{% notice note %}}
Please note, that the Openstack client has already installed on the current VM.  
{{% /notice %}} 

{{% notice tip %}}
To find detailed instructions, how to Install and configure OpenStack CLI, see the article: [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)*
{{% /notice %}} 

2. Place RC File of the created CLI User, named *dev1CLIuser*, to your Virtual Machine and execute it starting with dot:  
    `vi dev1-openrc`    
    `. dev1-openrc`  

{{% notice note %}}
Please note, that RC file of the current CLI User has already loaded.   
{{% /notice %}} 

{{% notice tip %}}
To find detailed instructions, how to load RC Files, see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)
{{% /notice %}}   

3. Get a list of all Volumes created in the corresponding Project and to which your User has access:  
    `openstack volume list`      

    In our case the output will be next:    
    ```
    ubuntu@vm-1:~$ openstack volume list
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    | ID                                   | Name        | Status    | Size | Attached to                   |
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    | 95ed1f4c-1b74-407c-bf9c-9f13da36530e | vol-from-sn | available |   10 |                               |
    | 48124dc6-2bce-4592-8b41-283ad14d06ae |             | in-use    |   10 | Attached to vm-2 on /dev/vda  |
    | 777b8334-ab4a-4f4a-bf5f-9eeb40e34180 |             | in-use    |   10 | Attached to vm-1 on /dev/vda  |
    +--------------------------------------+-------------+-----------+------+-------------------------------+
    ```
4. Create an Image from the selected Volume:    

    `openstack image create --disk-format qcow2 --volume 95ed1f4c-1b74-407c-bf9c-9f13da36530e img-migrated`    

    In our case the output will be next:    
    ```
    ubuntu@vm-1:~$ openstack image create --disk-format qcow2 --volume 95ed1f4c-1b74-407c-bf9c-9f13da36530e img-migrated
    +---------------------+--------------------------------------+
    | Field               | Value                                |
    +---------------------+--------------------------------------+
    | container_format    | bare                                 |
    | disk_format         | qcow2                                |
    | display_description | volume created from the snapshot     |
    | id                  | 95ed1f4c-1b74-407c-bf9c-9f13da36530e |
    | image_id            | cc326302-2c4d-490e-b3f0-4d6b9e3c98d6 |
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

5. Get a list of Images related to the current Project:  
    `openstack image list`    

In our case the output will be next:
    ```
    ubuntu@vm-1:~$ openstack image list
    +--------------------------------------+--------------------------------------------------+--------+
    | ID                                   | Name                                             | Status |
    +--------------------------------------+--------------------------------------------------+--------+
    | 75dbd50c-ff5a-4036-819b-b6df6fce33de | centos-6.10-1907                                 | active |
    | 3d26614c-a95a-4898-acc3-132e8dbcc359 | centos-7.9-2009                                  | active |
    | f5716ea3-5476-4b44-8825-be1907167cee | centos-8.2-2004                                  | active |
    | 7b0cc2f9-430d-489c-9c51-9f716b4418ac | debian-buster-10.8.3-20210304                    | active |
    | 8a356368-3f03-4f41-8205-03cb9f564377 | debian-stretch-9.13.16-20210219                  | active |
    | f07d4696-9d62-41d8-8d6a-d79d848b928f | fedora-coreos-31.20200127.3.0                    | active |
    | 9a3ac5d4-a9e1-4416-bf31-27feb501463f | fedora-coreos-33.20210117.3.2                    | active |
    | 85785454-523c-46d1-841c-225bf67f6c90 | fedora-coreos-34.20210427.3.0                    | active |
    | cc326302-2c4d-490e-b3f0-4d6b9e3c98d6 | img-migrated                                     | active |  <--
    | 0206848f-e705-4f62-aafa-7080f9048d5b | ubuntu-server-16.04-LTS-20201111                 | active |
    | 82a7dd1f-f8de-40c9-918d-87183c97f2f3 | ubuntu-server-18.04-LTS-20201111                 | active |
    | d36eba41-7a45-4015-bdd9-99ed08f07fb1 | ubuntu-server-20.04-LTS-20201111                 | active |
    | bf4724b6-1df6-48e6-86d4-b98083449fbb | windows-server-2019-datacenter-1809-17763.737-en | active |
    +--------------------------------------+--------------------------------------------------+--------+
    ```

After these steps, the newly created Image will be added to the *Images page* and you can use to create new Virtual Machines:
![](../../assets/images/tutorials/0-9.png?classes=border,shadow) 
