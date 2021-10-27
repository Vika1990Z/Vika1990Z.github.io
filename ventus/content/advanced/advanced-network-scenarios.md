---
title: Advanced network scenarios
weight: 22
---
___
On this page, we will discuss scenarios that can help you to build software upgrade friendly and fault-tolerant cloud infrastructure.

>Most of the topics described below considered advanced. Basic Linux and Networking skills are required. Please contact support if you need guidance and best practices for your specific use case.  
> 
>Most of the features described below are in beta state, thus not available at the Console portal, and can be configured through CLI and IaC tools like Terraform and Ansible.

# Table of contents


## Prerequisites
1. CLI User created. To find more detailed instructions see the article - [CLI Users]().
2. Openstack Client Configured. To find more detailed instructions see the article - [Installation OpenStack CLI]().

## Port Migration
Port migration can be used in drop-in replacement of instances in case of major software upgrades or recovery scenarios, especially when you need to preserve initial networking settings and you didn't plan for such actions in advance by leveraging Floating IPs or Load Balancers. 

**Scenarios:**
* Install and configure new instance nearby to old one, verify internally that it works as expected and then switch production traffic to it with preserving ability to rollback to previous version (instance).
* In case of major failures - restore instance from backup and leverage previously used IP.

![](../assets/images/adv/12.png?classes=border,shadow) 

**Configuration:**

Make sure that CLI user has SSH key:   
`openstack key list`  

Create SSH key if needed:  
`openstack key create --public-key .ssh/id_rsa.pub ssh_key_name`  

Create ports for your planned servers:  
`openstack port create --network public server-1-port`   
`openstack port create --network public server-2-port`   

Choose images and flavors for servers:    
`openstack image list`  
`openstack flavor list`  

Create servers with corresponding ports:  
```
openstack server create \
--image 'centos-8.2-2004' \
--boot-from-volume 100 \
--flavor VC-4 \
--security-group default \
--port server-1-port \
--key-name ssh_key_name \
server1

openstack server create \
--image 'centos-8.2-2004' \
--boot-from-volume 100 \
--flavor VC-4 \
--security-group default \
--port server-2-port \
--key-name ssh_key_name \
server2
```

Verify created servers:  
`openstack server list`  
`openstack port list`  

{{% notice info %}}
**Optionally:**  
Install Nginx web server on server1 and Apache on server2 and configure Ventus firewall rule to allow TCP port 80 from your workstation:
**Centos:**     
Server1:    
`yum install nginx`  
`systemctl enable nginx`  
`systemctl start nginx`  
Server2:   
`yum install httpd`  
`systemctl enable httpd`  
`systemctl start httpd`  
**Ubuntu:**  
Server1:  
`apt update`  
`apt install nginx`  
`systemctl enable nginx`  
`systemctl start nginx`  
Server2:   
`apt install apache2`  
`systemctl enable apache2`  
`systemctl start apache2`  
Verify that IP addres of server-1-port is served by nginx webserver and IP addres of server-2-port served by Apache: 
`curl <IP addres of server-1-port>`  
`curl <IP addres of server-2-port>`
{{% /notice %}}

**Perform failover.** 

Detaching ports from servers:
```
openstack server remove port <server> <port>
openstack server remove port server1 server-1-port
openstack server remove port server2 server-2-port
```

Attaching port of server1 to server2 and vice versa:
```
openstack server add port <server> <port>
openstack server add port server1 server-2-port
openstack server add port server2 server-1-port
```

Reboot servers if needed:
```
openstack server reboot server1
openstack server reboot server2
```

Verify that ports were switched:
```
openstack server list
openstack port list
```
{{% notice info %}}
**Optionally:**
Verify that IP address of server-1-port is now served by Apache webserver and IP address of server-2-port is now served by Nginx web servers. It will mean that we successfully switched ports of our servers. 
`curl <IP addres of server-1-port>`  
`curl <IP addres of server-2-port>`  
{{% /notice %}}

{{% notice tip %}}
**Pro Tips:**
Use "--fixed-ip" argument during port creation for better control of IP allocation in private networks e.g.:  
>openstack port create --network <network_name> --fixed-ip \
subnet=<subnet_name>,ip-address=<ip_address> <port_name>
e.g.:
openstack port create --network network1 --fixed-ip \
subnet=subnet1,ip-address=10.0.0.10 server-1-port*

You can assign multiple ports to one instance e.g.:  
`openstack server add port server1 server-1-port`  
`openstack server add port server1 server-2-port`  

Remove IP address from port:
openstack port set --no-fixed-ip <port_id>
e.g.:
openstack port set --no-fixed-ip 68c763c4-d523-4a47-baf9-XXXXXXXXXXXX

Assign Desired IP to port:
___
openstack port set --fixed-ip subnet=<subnet_name>,ip-address=<ip_address> <port_id>
e.g.:
openstack port set --fixed-ip subnet=subnet1,ip-address=10.0.0.10 68c763c4-a293-68f9-anr6-XXXXXXXXXXXX
___
Assign multiple IP addresses to one port:
openstack port set --fixed-ip subnet=subnet1,ip-address=10.0.0.11 68c763c4-a293-68f9-anr6-XXXXXXXXXXXX
openstack port set --fixed-ip subnet=subnet1,ip-address=10.0.0.12 68c763c4-a293-68f9-anr6-XXXXXXXXXXXX
openstack port set --fixed-ip subnet=subnet1,ip-address=10.0.0.13 68c763c4-a293-68f9-anr6-XXXXXXXXXXXX

You can use a custom MAC address for port. Contact support if you need it. 
{{% /notice %}}

{{% notice %}}
A notice disclaimer
{{% /notice %}}



