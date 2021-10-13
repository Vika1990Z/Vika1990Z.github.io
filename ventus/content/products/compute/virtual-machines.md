---
title: Virtual Machines
weight: 10
---
___
On this page, you can find an explanation of how to create, resize, delete Linux and Windows Virtual Machine, and instructions for other steps to manage Virtual Machines in the Cloud Console.

# Table of contents
1. [Virtual Machines Page](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines#about-vm-page)
1. [Create Linux Virtual Machine](https://kb.ventuscloud.eu/knowledge/virtual-machines#create-linux-vm)
1. [Create Windows Virtual Machine](https://kb.ventuscloud.eu/knowledge/virtual-machines#create-windows-vm)
1. [Download RDP File](https://kb.ventuscloud.eu/knowledge/virtual-machines#rdp-file)
1. [Edit a Virtual Machine](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines#edit-vm)
1. [Resize a Virtual Machine](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines#resize-vm)
1. [Delete a Virtual Machine](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines#delete-vm)
1. [Virtual Machine details page](https://kb.ventuscloud.eu/knowledge/linux-virtual-machines#vm-details-page)

## Virtual Machines page
To get to the *Virtual Machines page* you need to select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*.
![](../../assets/images/vms/1-vm.png?classes=border,shadow)  

On this page you can find all created Virtual Machines in the current Project of the selected Organization with their *Headers, Create button, Search bar*, and *Actions icon* which opens a list of available management actions for the selected VM:
![](../../assets/images/vms/2-vm.png?classes=border,shadow)  

**Actions** icon opens the next list of available management actions:
- *Start* - this option attempts to start the VM if it was stoppedd; 
- *Stop* - this option attempts to stop the VM;
- *Soft reboot* - this option attempts a graceful shut down and restart of the VM;
- *Edit* - this option attempts to to change VM's name;
- *Resize* - this option attempts to change the Flavor for the VM;
- *Delete* - this option is for VM removing;
- *Remote console* - this option attempts to use remote console for VM.

## Create Linux Virtual Machine
To create a new Linux VM do the following:
- go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../assets/images/vms/3-vm.png?classes=border,shadow)
  - **Source** - choose the source wich you want to use for VM creating: image, volume or snapshot;
  - **OS Platform** - choose the OS Platform wich you want to use for VM creating: Linux or Windows;
  - **Image ID** - set the ID of the previousluy selected Source for VM creating (Image ID, Volume ID or Snapshot ID); 
  - **Name** - set a name for the VM;
  - **Tags** - this field is optional and use it if you need to set some tags for the VM; 
  - **Flavor** - select the size for new VM;
  - **Key pair** - this field is neccessery only for Linux VMs, select here the SSH Key that was previously created on the *SSH Keys page* or create a new one, which you will use to connect to the Linux VM;
  - **Networks**: here you can choose one or more networks;
  - **Firewalls**: in this field you can choose what collection of network access rules will control the traffic to this VM;  

    *to connect to the selected **Linux Virtual Machine** remotely via SSH you need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 22 (like shown below) - to find additional information about this please see the article **[Connect to Linux VM](https://kb.ventuscloud.eu/knowledge/connect-vm-by-ssh)**;*
    ![](../../assets/images/vms/4-vm.png?classes=border,shadow)

    >**NOTE** 
    *To connect to the selected **Windows Virtual Machine** remotely via RDP you need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 54000 like shown below - to find additional information about this please see the article **[Connect to the Windows VM via RDP](https://kb.ventuscloud.eu/knowledge/connect-windows-vm)**;*
    ![](../../assets/images/vms/5-vm.png?classes=border,shadow)
    
  - **Volume size (GB)**: here you provide the preferred disk size for the VM, it can be specified in the range from 10 GB to 1000 GB. Minimal available size 10 GB; and also just below this field you can make a mark ***for auto-deleting volume*** when the VM is terminated;   

After these steps the newly created VM will be added to the *Virtual Machine page* with the status ACTIVE:
![](../../assets/images/vms/6-vm.png?classes=border,shadow)

