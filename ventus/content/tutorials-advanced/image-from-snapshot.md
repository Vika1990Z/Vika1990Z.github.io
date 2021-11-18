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
        To find more detailed instructions see the article:  
            [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/);  
    - **Ubuntu Virtual Machine (IP: 88.218.53.162, Name: vm-1)**; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH; and has a previously installed Openstack client.
        To find more detailed instructions see the articles:  
            [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);  
            [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);      
            [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/); 

## Workflow    
**Step 1 - Prepare the Snapshot**   
1. Connect to the preiviously created Virtual Machine in the current Project *dev-1*:  
    `ssh -i ~/.ssh/id_rsa ubuntu@88.218.53.162`  
To find more detailed instructions see the article:  
    [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/).
2. Create some txt file:  
    `echo "BeforeMigration" > file.txt`
3. Check that file was created:
```
ubuntu@vm-1:~$ ll
total 36
drwxr-xr-x 5 ubuntu ubuntu 4096 Nov 18 12:39 ./
drwxr-xr-x 3 root   root   4096 Nov 18 12:29 ../
-rw-r--r-- 1 ubuntu ubuntu  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3771 Feb 25  2020 .bashrc
drwx------ 3 ubuntu ubuntu 4096 Nov 18 12:37 .cache/
drwx------ 4 ubuntu ubuntu 4096 Nov 18 12:37 .local/
-rw-r--r-- 1 ubuntu ubuntu  807 Feb 25  2020 .profile
drwx------ 2 ubuntu ubuntu 4096 Nov 18 12:29 .ssh/
-rw-r--r-- 1 ubuntu ubuntu    0 Nov 18 12:30 .sudo_as_admin_successful
-rw-rw-r-- 1 ubuntu ubuntu   16 Nov 18 12:39 file.txt               <---
```

4. Create a Snapshot from the current state of the VM:
{{% notice note %}}
It is recommended to stop the virtual machine before taking a snapshot because snapshots taken from a volume with a "in-use" status may contain corrupted data
{{% /notice %}} 
![](../../../assets/images/tutorials/0-5.png?classes=border,shadow) 
To find more detailed instructions see the article:  
    [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/). 

5. Check that the newly added Snapshot is working correctly:
- Create Virtuale Machine from this Snapshot:
![](../../../assets/images/tutorials/0-4.png?classes=border,shadow)
To find more detailed instructions see the article:  
    [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/)   

- Loggin to the newly created VM and check if the file.txt exists there after creation:
`ssh -i ~/.ssh/id_rsa ubuntu@88.218.55.69`   
```
ubuntu@vm-2:~$ ll
total 36
drwxr-xr-x 5 ubuntu ubuntu 4096 Nov 18 12:39 ./
drwxr-xr-x 3 root   root   4096 Nov 18 12:29 ../
-rw-r--r-- 1 ubuntu ubuntu  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3771 Feb 25  2020 .bashrc
drwx------ 3 ubuntu ubuntu 4096 Nov 18 12:37 .cache/
drwx------ 4 ubuntu ubuntu 4096 Nov 18 12:37 .local/
-rw-r--r-- 1 ubuntu ubuntu  807 Feb 25  2020 .profile
drwx------ 2 ubuntu ubuntu 4096 Nov 18 12:29 .ssh/
-rw-r--r-- 1 ubuntu ubuntu    0 Nov 18 12:30 .sudo_as_admin_successful
-rw-rw-r-- 1 ubuntu ubuntu   16 Nov 18 12:39 file.txt              <---
```

**Step 2 - Create Volume from the Snapshot**   
1. Open the *Snapshots page*, click on the **Actions** icon of the selected Snapshot and select the **Create volume** in the list of available options:
![](../../assets/images/tutorials/15.png?classes=border,shadow) 

3. Fill in the form on the next opened *Create volume from snapshot window* and click on the CREATE icon:
![](../../assets/images/tutorials/16.png?classes=border,shadow) 

4. Check that the newly created Volume was added to the *Volumes page* with the status *available*:
![](../../assets/images/tutorials/16.png?classes=border,shadow) 

To find more detailed instructions see the article:  
    [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/) 

**Step 3 - Create Image of the Volume**  
1. Connect to the preiviously created Virtual Machine in the current Project *dev-1*:  
    `ssh -i ~/.ssh/id_rsa ubuntu@88.218.53.162`  

{{% notice note %}}
Please note, that the Openstack client has already installed on the current VM.  
To find more detailed instructions see the article:  
[Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)
{{% /notice %}} 

2. Place RC File of the created CLI User, named *dev1CLIuser*, to your Virtual Machine and execute it starting with dot:  
{{% notice note %}}
Please note, that RC file of the current CLI User has already been loaded;   
To find more detailed instructions see the article:    
[CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/) 
{{% /notice %}} 

`vi dev1-openrc`    

`. dev1-openrc`    

3. Get a list of all Volumes created in the corresponding Project and to which your User has access:  
`openstack volume list`    

In our case the output will be next:  
```
ubuntu@vm-1:~$ openstack volume list
+--------------------------------------+-------------+-----------+------+-------------------------------+
| ID                                   | Name        | Status    | Size | Attached to                   |
+--------------------------------------+-------------+-----------+------+-------------------------------+
| 091b4641-7edb-42df-a7b7-0e89c84bbc59 | vol-from-sn | available |   10 |                               |
| 7fbbc2e6-ca7e-4e09-9659-40c9ef560c6c |             | in-use    |   10 | Attached to vm-2 on /dev/vda  |
| 777b8334-ab4a-4f4a-bf5f-9eeb40e34180 |             | in-use    |   10 | Attached to vm-1 on /dev/vda  |
+--------------------------------------+-------------+-----------+------+-------------------------------+
```
- use command next command to create an Image from the selected Volume:    
`openstack image create --disk-format qcow2 --volume 091b4641-7edb-42df-a7b7-0e89c84bbc59 img-migrated`  

{{% notice note %}}
It may take a long time to create images from a volume, please wait until its status becomes active.
{{% /notice %}} 

- get a list of Images related to the current Project:  
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
/
| 0206848f-e705-4f62-aafa-7080f9048d5b | ubuntu-server-16.04-LTS-20201111                 | active |
| 82a7dd1f-f8de-40c9-918d-87183c97f2f3 | ubuntu-server-18.04-LTS-20201111                 | active |
| d36eba41-7a45-4015-bdd9-99ed08f07fb1 | ubuntu-server-20.04-LTS-20201111                 | active |
| bf4724b6-1df6-48e6-86d4-b98083449fbb | windows-server-2019-datacenter-1809-17763.737-en | active |
+--------------------------------------+--------------------------------------------------+--------+
```

