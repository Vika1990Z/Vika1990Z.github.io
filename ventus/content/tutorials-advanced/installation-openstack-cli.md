---
title: Installation OpenStack CLI
weight: 10
---
___
On this page, you can find an explanation of how to install OpenStack CLI on Linux VM in the Cloud Console.

# Table of contents
1. [Prerequisites](#prerequisites)
1. [Install OpenStack CLI on Ubuntu VM](#install-openstack-cli-on-ubuntu-vm)
1. [Install OpenStack CLI on Centos VM](#install-openstack-cli-on-centos-vm)

## Prerequisites
In this article we will assume, that we have already created the following resources, that refer to the Project named *dev1*, that was created in the Organization named *Test-Shop*:
- **API User**, created with the following parameters and its RC file has already been loaded:
  - *Name*: testCLIuser;
  - *Password*: P@sword.

For more information, see the article -[CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)

## Install OpenStack CLI on Ubuntu VM
- Create and log in to your Ubuntu Virtual Machine on which you want to install OpenStack CLI;  
  for more information, see articles - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/) and [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);  

- Update Ubuntu package sources by running the following command:    
`sudo apt update` 

- Install Kubernetes Python Client by running the next command:    
`sudo apt install python3-pip`  

- Install openstack cli tool by running two next commands one by one:   
`sudo pip3 install python-openstackclient`    
`sudo pip3 install python-magnumclient`   
`sudo pip3 install python-octaviaclient`  

- Place RC File of the created CLI User to your Virtual Machine:  
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
	export OS_USERNAME="48529f99-8e10-4694-9412-70e1012de805:test-conn"
	echo "Please enter your OpenStack Password for project $OS_PROJECT_NAME as user $OS_USERNAME: "
	read -sr OS_PASSWORD_INPUT
	export OS_PASSWORD=$OS_PASSWORD_INPUT
	export OS_REGION_NAME="Upper-Austria"
	if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
	export OS_INTERFACE=public
	export OS_IDENTITY_API_VERSION=3
```    

- Execute *openrc* starting with dot:  
`. openrc`  

- Provide the password of the created CLI User and hit *Enter* - this password will be used to authenticate you in the Cloud Console.  
- For testing that OpenStack CLI works, run the next command to get a list of all clusters created in the corresponding Project and to which your User has access:   
`openstack coe cluster list`  
In our case the output will be next:
```output
ubuntu@test-2:~$ openstack coe cluster list
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
| uuid                                 | name      | keypair | node_count | master_count | status          | health_status |
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
| 63fe23ab-eaab-46af-9173-131db353c993 | test-cl-1 | mykey   |          3 |            1 | UPDATE_COMPLETE | HEALTHY       |
| 315c90c5-d74c-429d-b53f-fe0f68025a6e | test-cl-2 | mykey   |          1 |            1 | CREATE_COMPLETE | HEALTHY       |
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
```

## Install OpenStack CLI on Centos VM
- Create and log in to your Ubuntu Virtual Machine on which you want to install OpenStack CLI;  
  for more information, see articles - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/) and [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/);      

- Enable the OpenStack repository;  
on CentOS, the extras repository provides the RPM that enables the OpenStack repository. CentOS includes the extras repository by default, so you can simply install the package to enable the OpenStack repository. For CentOS 8, you will also need to enable the PowerTools repository:  
`sudo yum install centos-release-openstack-ussuri`   
`sudo yum config-manager --set-enabled PowerTools`  

- Update CentOS package sources by running the following command:   
`sudo yum upgrade`  

- Install the appropriate OpenStack client for your CentOS version:  
`sudo yum install python3-openstackclient`      
`sudo yum install python3-magnumclient`
`sudo yum install python3-octaviaclient`     

- Place RC File of the created CLI User to your Virtual Machine but first install the nano text editor, if not yet installed:    
`sudo yum install -y nano`  
`nano openrc`  
Сheck that there were indicated the correct OS_USERNAME and  OS_PROJECT_ID and press *Ctrl+S*, then *Ctrl+X* to save the changes:  
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
	export OS_USERNAME="48529f99-8e10-4694-9412-70e1012de805:test-conn"
	echo "Please enter your OpenStack Password for project $OS_PROJECT_NAME as user $OS_USERNAME: "
	read -sr OS_PASSWORD_INPUT
	export OS_PASSWORD=$OS_PASSWORD_INPUT
	export OS_REGION_NAME="Upper-Austria"
	if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
	export OS_INTERFACE=public
	export OS_IDENTITY_API_VERSION=3
```    

- Execute *openrc* starting with dot:  
`. openrc`  

- Provide the password of the created CLI User and hit *Enter* - this password will be used to authenticate you in the Cloud Console.  
- For testing that OpenStack CLI works, run the next command to get a list of all clusters created in the corresponding Project and to which your User has access:   
`openstack coe cluster list`  
In our case the output will be next:
```output
[centos@test-3 ~]$ openstack coe cluster list
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
| uuid                                 | name      | keypair | node_count | master_count | status          | health_status |
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
| 63fe23ab-eaab-46af-9173-131db353c993 | test-cl-1 | mykey   |          3 |            1 | UPDATE_COMPLETE | HEALTHY       |
| 315c90c5-d74c-429d-b53f-fe0f68025a6e | test-cl-2 | mykey   |          1 |            1 | CREATE_COMPLETE | HEALTHY       |
+--------------------------------------+-----------+---------+------------+--------------+-----------------+---------------+
```