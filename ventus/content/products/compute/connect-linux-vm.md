---
title: Connect to Linux VM
weight: 15
---
___
On this page, you can find an explanation of how to connect to the Linux Virual Machine created in the Cloud Console using SSH Protocol

# Table of contents
1. [Prerequisites](#prerequisites)
1. [Configuring Firewalls](#configuring-firewalls)
1. [Connect using SSH](#connect-using-ssh)

## Prerequisites
In this article, we will assume that we have already created the following resources, that refer to the Project named *dev1* that was created in the Organization named *Test-Shop*:
- **SSH Key,** that was created with the next parameters:
  - *Name*: mykey;
  - *Public key* is placed on the Linux VM during its creation;
  - *Private Key* was copied to the clipboard and saved on the local system in the next text file (for example: ~/.ssh/id\_rsa).
- **Linux Virtual Machine** - that was created with the next parameters and has IP: 185.226.41.42:
  - *Name*: test-1;
  - *Flavor*: VC-2;
  - *Image*: ubuntu-server-18.04-LTS-20201111;
  - *Key pair*: mykey;
  - *Networks*: public;
  - *Firewalls*: default;
  - *Volume size*: 10.

For more information on creating and configuring these resources, see the following articles:  
[SSh Keys](https://kb.ventuscloud.eu/knowledge/ssh-keys);      
[Virtual Machines](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines)   

## Configuring Firewalls
By default, all created Virtual Machines belong to the *default* Firewall, which allows access to the Internet from the VM, but denies almost all access on the VM from outside, except for objects belonging to the same default Firewall. Thus, using only the default Firewall, we cannot connect to the selected Virtual Machine remotely via SSH.

>**NOTE**: *Default* *Firewall* allows all outbound traffic and controls the inbound traffic that's allowed to reach the VMs that are associated with the *default* *Firewall* too. 

To resolve this, we need to add an additional Firewall with a rule that will allow incoming traffic to port 22 on the Virtual Machines and assign this Firewall to the VM too, or just add the required rule to the Firewall that is already assigned to the Virtual Machine. 

**To create new Firewall do the following:**
- open the *Firewalls page -* for this select the **Security** from the VIRTUAL DATACENTER block and click on the FIREWALL TAB:

![](../../../assets/images/conn-lin/1.png?classes=border,shadow)
![](../../../assets/images/conn-lin/2.png?classes=border,shadow)

- on the *Firewalls page* click on the CREATE FIREWALL icon in the upper left corner;
- fill in the form on the next opened *Create Firewall window* and click on the CREATE icon:
![](../../../assets/images/conn-lin/3.png?classes=border,shadow)

**To add the described above rule to the newly created Firewall do the following:** 
- open the *Firewall Rules page* - for this click on the **Name** of the corresponding Firewall:
![](../../../assets/images/conn-lin/4.png?classes=border,shadow)

- on the *Firewall Rules page* you can see that rules that allow all outbound traffic have been already created by defaul and to add additional rule here click on the CREATE FIREWALL RULE icon in the upper left corner:
![](../../../assets/images/conn-lin/16.png?classes=border,shadow)

- fill in the form on the next opened *Create Firewall Rule window* as shown below  and click on the CREATE icon:
![](../../../assets/images/conn-lin/5.png?classes=border,shadow)

This newly added rule will allow access to the TCP port 22 on the all VMs in the default Firewall over the public Internet, but if you want to allow access only on the one selected VM you need to specify *IP of this VM / 32* in the field named *Remote IP prefix* - example is shown below:
![](../../../assets/images/conn-lin/6.png?classes=border,shadow)

**To add this newly created Firewall to our Virtual Machine, do the following:**
- open the *Virtual Machines page -* for this select the **Virtual Machines** from the VIRTUAL DATACENTER block:
![](../../../assets/images/conn-lin/7.png?classes=border,shadow)

- open the *Virtual Machine details page* - click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/conn-lin/8.png?classes=border,shadow)

- click on the NETWORKS & SECURITY TAB and click on the ADD FIREWALL icon in the upper left corner of the opened page:
![](../../../assets/images/conn-lin/9.png?classes=border,shadow)

- select our newly created firewall on the following *Add firewall window* and click on the ADD icon:
![](../../../assets/images/conn-lin/10.png?classes=border,shadow)

This is the first option, how we can configure the Firewall for SSH access - by creating a new one with the required rule. But we can just add this rule to the default Firewall that is already assigned to our VM, and these changes will automatically be applied to the VMs. 

>**NOTE**: You can add and remove rules at any time. Your changes are automatically applied to the VMs that are associated with the corresponding Firewall.

**To add required rule to the default Firewall you need to do next:**
- open the *Firewalls page -* for this select the **Security** from the VIRTUAL DATACENTER block and click on the FIREWALL TAB:
![](../../../assets/images/conn-lin/1.png?classes=border,shadow)
![](../../../assets/images/conn-lin/11.png?classes=border,shadow)

- open the *Firewall Rules page* of the default Firewall- for this click on the **Name** of the corresponding Firewall:
![](../../../assets/images/conn-lin/12.png?classes=border,shadow)

- on the *Firewall Rules page* click on the CREATE FIREWALL RULE icon in the upper left corner;
- fill in the form on the next opened *Create Firewall Rule window* as shown below  and click on the CREATE icon:
![](../../../assets/images/conn-lin/5.png?classes=border,shadow)

And that's all, this newly created Firewall Rule will be automatically applied to our Virtual Machine.

## Connect using SSH
Since we have the public key deployed on our Linux VM, the private key on our local system (for example ~/.ssh/id_rsa) and a Firewall configured to allow incoming traffic on port 22, we can connect to this Virtual Machine remotely from our local server via SSH, just use the next command: 
`ssh -i ~/.ssh/id_rsa username@*10.111.22.333*`

>**NOTE**: Username for VMs created with *Ubuntu image* will be **ubuntu**;   
with *Centos image* - **centos.**

Replace *username* and *10.11.22.333* in the command with your data and specify the appropriate path to your private key. In our example, the command will look like this:
`sudo ssh -i ~/.ssh/id_rsa ubuntu@185.226.41.42`
![](../../../assets/images/conn-lin/13.png?classes=border,shadow)

After successfully connecting, you can check your internet access and try pinging [google.com](http://google.com/):
![](../../../assets/images/conn-lin/14.png?classes=border,shadow)
