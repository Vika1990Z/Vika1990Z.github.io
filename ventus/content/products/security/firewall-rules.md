---
title: Firewall Rules
weight: 20
---
___
On this page, you can find an explanation of how to create, delete Firewall Rules and instructions for other steps to manage Firewall Rules in Cloud Console.

# Table of contents
1. [Firewall Rules page](#firewall-rules-page)
2. [Characteristics of Firewall Rules](#characteristics-of-firewall-rules)
3. [Create Firewall Rule](#create-firewall-rule)
4. [Firewall Rule details page](#firewall-rule-details-page)
5. [Delete Firewall Rule](#delete-firewall-rule)
6. [Firewall Rule for SSH Protocol](#firewall-rule-for-ssh-protocol)
7. [Firewall Rule for SSH Protocol](#firewall-rule-for-rdp)

## Firewall Rules page
To get to the *Firewall Rules page* click on the **Name** of the corresponding Firewall on the *Firewalls page*:
![](../../../assets/images/fw/5.png?classes=border,shadow) 

On this page you can find all Rules related to the selected Firewall with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Rule:
![](../../../assets/images/fw/4.png?classes=border,shadow)  

**Actions** icon opens the next list of available management actions:
- *Delete* - this option is for Firewall Rule deletion.

After creating a new Firewall, two rules have been automatically added to the *Firewall Rules page* - the default rules that allow all outgoing traffic. 
You can remove them if needed.

## Firewall Rules Characteristics 
**Firewall Rules** control the inbound traffic that's allowed to reach the VMs that are associated with the corresponding Firewall. The rules also control the outbound traffic that's allowed to leave them.

Firewall Rules have the following characteristics:
- By default, Firewalls allow all outbound traffic.
- Firewall Rules are always permissive; you can't create rules that deny access.
- Firewall Rules enable you to filter traffic based on protocols and port numbers.
- You can add and remove rules at any time. Your changes are automatically applied to the VMs that are associated with the corresponding Firewall.
- You can assign multiple Firewalls to the VMs. The rules from each Firewall are effectively aggregated to create one set of rules, but we recommend that you condense your rules as much as possible.

## Create Firewall Rule
To create a new Firewall Rule do the following:
- go to the *Firewall Rules page* and click on the CREATE FIREWALL RULE icon in the upper left corner;
- fill in the form on the next opened *Create Firewall Rule window*:
![](../../../assets/images/conn-lin/20.png?classes=border,shadow)
  - *Description* - set a description for the Rule;
  - *Direction* - select a direction for the Rule: *ingress* or *egress*;
  - *Protocol* - select the type of protocol for the Rule: TCP, UDP, ICMP;
  - *Port options* - this field is available only for rules with **TCP** and **UDP** protocols; select one of the option, that you will provide below: 
    - *Port* - use this option, if your rule will be for one specific port;
    - *Port range* - use this option, if your rule will be for some specific port range;
    - *All Ports* - use this option, if your rule will be for all ports between 0 and 65535.
  - *Remote* - select one of the option, that you will provide below:  
    - *Firewall* - use this option, if you want to apply this rule for the another Firewall; the selected Firewall will be associated with this rule;
    - *CIDR* - use this option, if you want to apply this rule for the IP Addresses range.

After these steps, the newly created Firewall Rule will be added to the *Firewall Rules page*
![](../../../assets/images/fw/6.png?classes=border,shadow) 

## Firewall Rule details page
To get to the *Firewall Rule details page* click on the **ID** of the corresponding Firewall Rule:
![](../../../assets/images/fw/7.png?classes=border,shadow) 

On this page you can find additional information about this Rule and **quick actions** icon for rule deletion:
![](../../../assets/images/fw/8.png?classes=border,shadow) 

## Delete Firewall Rule
To delete a Firewall Rule do the following:
- identify this unnecessary Rule on the *Firewall Rule page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Firewall Rule deletion on the next opened *Confirmation window*.

After these steps, the selected Firewall Rule will be deleted.
Also, you can delete the rule from the *this Rule details page*, by clicking on the appropriative **quick actions** icon.

## Firewall Rule for SSH Protocol
By default, all created Virtual Machines belong to the *default* Firewall, which allows access to the Internet from the VM, but denies almost all access on the VM from outside, except for objects belonging to the same default Firewall.
Thus, to open connection to the selected Linux Virtual Machine remotely via SSH we need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 22 on the Virtual Machines and assign this Firewall to the VM too, or just add the required rule to the Firewall that is already assigned to the Virtual Machine. 
Example of such rule you can see below:
![](../../../assets/images/conn-lin/5.png?classes=border,shadow)
To find more information about how to connect to the Linux Virual Machine created in Cloud Console using SSH Protocol, please use the article - [Connect Linux VM]()

## Firewall Rule for RDP
By default, all created Virtual Machines belong to the *default* Firewall, which allows access to the Internet from the VM, but denies almost all access on the VM from outside, except for objects belonging to the same default Firewall.
Thus, to open connection to the selected Windows Virtual Machine remotely via RDP we need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 54000 on the Virtual Machines and assign this Firewall to the VM too, or just add the required rule to the Firewall that is already assigned to the Virtual Machine. 
Example of such rule you can see below:
![](../../../assets/images/conn-lin/20.png?classes=border,shadow)
To find more information about how to connect to the Windows Virtual Machine created in Cloud Console using Remote Desktop Protocol, please, use the article - [Connect Windows VM ]()