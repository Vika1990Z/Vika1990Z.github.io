---
title: Access K8S Cluster
weight: 15
---
___
On this page, you can find an explanation of several ways how to access a Kubernetes Cluster created in Cloud Console

# Table of contents
1. [Prerequisites](#prerequsites)
1. [Get access from Ubuntu VM to K8S Cluster using CLI User](#get-access-from-ubuntu-vm-to-k8s-cluster-using-cli-user)
1. [Get access from Centos VM to K8S Cluster using CLI User](#get-access-from-centos-vm-to-k8s-cluster-using-cli-user)
1. [Connect to Cluster Master-Node via SSH](#connect-to-cluster-master-node-via-ssh)

## Prerequisites
In this article, we will assume that we have already created the following resources, that refer to the Project named *dev1* that was created in the Organization named *Test-Shop*:
- **SSH Key,** that will be specified during creating the Virtual Machine and Kubernetes Cluster for further connection to them via SSH; it was created with the next parameters:
  - *Name*: mykey;
  - *Public key* is placed on the Linux VM during its creation;
  - *Private Key* was copied to the clipboard and saved on the local system in the next text file (for example: ~/.ssh/id_rsa).
- **Firewall (Name: for-ssh),** that will be specified during creating the Virtual Machine for further connection to it via SSH - it was created with additional rule allowing incoming traffic on port 22; this rule was created with the next parameters:
  - *Description:* for ssh;
  - *Direction*: ingress;
  - *Protocol*: TCP;
  - *Port option*: Port;
  - *Port*: 22;
  - *Remote*: CIDR;
  - *Remote IP range:* 0.0.0.0/0
- **Ubuntu Virtual Machine (IP: 185.226.42.187)**, from which we will get access to the Kubernetes Cluster API; it was created with the next parameters and with additional Firewall named *for ssh,* configured to allow incoming traffic on port 22,so we can connect to this Virtual Machine remotely from our local server via SSH:
  - *Name*: test-2;
  - *Flavor*: VC-2;
  - *Image*: ubuntu-server-20.04-LTS-20201111;
  - *Key pair*: mykey;
  - *Networks*: public;
  - *Firewalls*: default, for ssh
  - *Volume size*: 10.  
- **Centos Virtual Machine (185.226.42.237)**, from which we will get access to the Kubernetes Cluster API; it was created with the next parameters and with additional Firewall named *for-ssh*, configured to allow incoming traffic on port 22,  so we can connect to this Virtual Machine remotely from our local server via SSH:
  - *Name*: test-3;
  - *Flavor*: VC-2;
  - *Image*: centos-8.2-2004;
  - *Key pair*: mykey;
  - *Networks*: public;
  - *Firewalls*: default, for-ssh;
  - *Volume size*: 10.  
- **Kubernetes Cluster (Master node IP:185.226.41.220)**,  created with the next parameters:
  - *Name*: test-cl-2;
  - *Cluster Template*: v1.21.1;
  - *Master Flavor*: VC-4;
  - *Node Flavor:* VC-2;
  - *Keypair*: mykey;
  - *Docker image size (GB):* 50 GB;
  - *Master Count*: 1;
  - *Node Count*: 1.
- **API User**, created with the following parameters and its RC file has already been loaded:
  - *Name*: test-conn;
  - *Password*: P@ssword.

For more information on creating and configuring these resources, see the following articles:

- [SSh Keys](https://kb.ventuscloud.eu/knowledge/ssh-keys)
- [Firewalls and Firewall Rules](https://kb.ventuscloud.eu/knowledge/firewalls)
- [Linux Virtual Machines](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines)
- [Kubernetes Cluster](https://kb.ventuscloud.eu/knowledge/kubernetes-cluster)
- [CLI Users](https://kb.ventuscloud.eu/knowledge/cli-users)
- [Connect to Linux VM via SSH](https://kb.ventuscloud.eu/knowledge/connect-vm-by-ssh)

## Get access from Ubuntu VM to K8S Cluster using CLI User
To get the access from the Ubuntu Virtual Machine to the created Kubernetes cluster using CLI follow the next steps:
- Loggin to your Ubuntu Virtual Machine from which you want to get access to the Kubernetes Cluster API;
  for this we use SSH protocol - to find additional information about, it see the article: [Connect Linux VM via SSH:](https://kb.ventuscloud.eu/knowledge/connect-vm-by-ssh)   
`ssh -i ~/.ssh/id_rsa ubuntu@185.226.42.187`

- Update Ubuntu package sources by running the following command:   
`sudo apt update`  

- Install Kubernetes Python Client by running the next command:  
`sudo apt install python3-pip`  

- Install openstack cli tool by running two next commands one by one:   
`sudo pip3 install python-openstackclient`  
`sudo pip3 install python-magnumclient`  

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
- Run the next command to get a list of all clusters created in the corresponding Project and to which your User has access:  
`openstack coe cluster list`  

In our case the output will be next:
![](../../../assets/images/clusters/13.png?classes=border,shadow)

- Run the following command to get the *kubeconfig file* for the Cluster named *test-cl-2,* that you will be accessing:  
`mkdir ~/test-cl-2`  
`openstack coe cluster config --dir ~/test-cl-2 test-cl-2`  

The output will be next:
![](../../../assets/images/clusters/14.png?classes=border,shadow)
 
- Export path to created config for as KUBECONFIG env variable:  
`export KUBECONFIG=/home/ubuntu/test-cl-2/config`  

- Install *kubectl* by running the next command:  
`sudo snap install kubectl --classic`  

- Run the next commands to test that you have access to the selected Cluster and all pods are running:  
`kubectl get nodes`  
`kubectl get pods --all-namespaces`  

If everything is fine, the output should be close to the following:
![](../../../assets/images/clusters/15.png?classes=border,shadow)


## Get access from CentOS VM to K8S Cluster using CLI User
To get the access from the CentOS Virtual Machine to the created Kubernetes cluster using CLI follow the next steps:
- Loggin to your CentOS Virtual Machine from which you want to get access to the Kubernetes Cluster API;
  for this we use SSH protocol - to find additional information about, it see the article: [Connect Linux VM:](https://kb.ventuscloud.eu/knowledge/connect-vm-by-ssh)   
`ssh -i ~/.ssh/id_rsa centos@185.226.42.237`

- Enable the OpenStack repository  
On CentOS, the extras repository provides the RPM that enables the OpenStack repository. CentOS includes the extras repository by default, so you can simply install the package to enable the OpenStack repository. For CentOS 8, you will also need to enable the PowerTools repository:  
`sudo yum install centos-release-openstack-ussuri`   
`sudo yum config-manager --set-enabled PowerTools`  

- Update CentOS package sources by running the following command:   
`sudo yum upgrade`  

- Install the appropriate OpenStack client for your CentOS version:  
`sudo yum install python3-openstackclient`      
`sudo yum install python3-magnumclient`   

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
- Run the next command to get a list of all clusters created in the corresponding Project and to which your User has access:  
`openstack coe cluster list`  

In our case the output will be next:
![](../../../assets/images/clusters/17.png?classes=border,shadow)

- Run the following command to get the *kubeconfig file* for the Cluster named *test-cl-2,* that you will be accessing:  
`mkdir ~/test-cl-2`  
`openstack coe cluster config --dir ~/test-cl-2 test-cl-2`  

The output will be next:
![](../../../assets/images/clusters/18.png?classes=border,shadow)
 
- Export path to created config for as KUBECONFIG env variable:  
`export KUBECONFIG=/home/centos/test-cl-2/config`  

- Install the latest release of  *kubectl*, make the kubectl binary executable and move the binary into your PATH by running the next commands:   
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl   
chmod +x ./kubectl   
sudo mv ./kubectl /usr/local/bin/kubectl   
```

- Run the next commands to test that you have access to the selected Cluster and all pods are running:  
`kubectl get nodes`  
`kubectl get pods -A`  

If everything is fine, the output should be close to the following:
![](../../../assets/images/clusters/19.png?classes=border,shadow)

## Connect to Cluster Master-Node via SSH
Since we created an SSH Keypair (see Prerequsutus of this article), the public key of which is deployed on our Cluster nodes, and the private key on our local system (for example, ~ / .ssh / id_rsa), we can connect to this Kubernetes Cluster remotely from our local server - via SSH to the Master Node of the selected Cluster, which IP is 185.226.41.220. For this, just use the following command:  
`ssh -i ~/.ssh/id_rsa username@*10.111.22.333*`  

>**NOTE**: *Username* for Cluster nodes is **core.**  

Replace *username* and *10.11.22.333* in the command with your data and specify the appropriate path to your private key. In our example, the command will look like this:   
`ssh -i ~/.ssh/id_rsa core@185.226.41.220`

After successfully connecting, you can test that you have access to the selected Cluster and all pods are running, just run the following commands:  
```
kubectl get nodes
kubectl get pods --all-namespaces
```

If everything is fine, the output should be close to the following:

!![](../../../assets/images/clusters/16
.png?classes=border,shadow)



