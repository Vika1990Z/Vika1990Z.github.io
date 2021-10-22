---
title: SSH Keys
weight: 30
---
___
On this page, you can find an explanation of how to create, delete SSH Keys and instructions for other steps to manage SSH Keys in Cloud Console.

# Table of contents

1. [SSH Keys page](#ssh-keys-page)
2. [Create SSH Key Pair](#create-ssh-key-pair)
3. [Add Public Key](#add-public-key)
4. [Copy Public Key](#copy-public-key)
5. [Delete SSH Key Pair](#delete-ssh-key-pair)

## SSH Keys page
To get to the *SSH Keys page* **Security** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **SSH Keys TAB:**
![](../../../assets/images/cli/1.png?classes=border,shadow) 
![](../../../assets/images/ssh/1.png?classes=border,shadow) 

On this page you can find all created SSH Keys with their *Headers*, *Create and Add buttons*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Keypair:
![](../../../assets/images/ssh/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions with the selected Keypair:
- *Copy public key to clipboard* - this option is used to copy public key;
- *Delete* - this option is for SSH Key deletion.

## Create SSH Key Pair
To create a new SSH Key Pair do the following:
- go to the *SSH Keys page* and click the CREATE SSH KEY PAIR icon in the upper left corner;
- specify the **Name** on the next opened *Create SSH Key window* and click on the CREATE icon:
![ssh![](../../../assets/images/ssh/3.png?classes=border,shadow)

The next open page will provide your *Private Key* and you can copy it or upload the *pem file* by choosing the action that suits you best:
![ssh![](../../../assets/images/ssh/4.png?classes=border,shadow)

>**NOTE:** You will have access to the private key only after creation, please save it to your private server if necessary.

After these steps, the newly created SSH Key Pair will be added to the *SSH Keys page*.

## Add Public Key 
If you want to use your own SSH Key Pair, you can add its public key in Cloud Console.
For this do the following:
- go to the *SSH Keys page* and click the ADD PUBLIC KEY icon:
![ssh![](../../../assets/images/ssh/5.png?classes=border,shadow)

- specify the **Name** on the next opened *Add public key window*, paste the public key and click on the ADD icon:
![ssh![](../../../assets/images/ssh/6.png?classes=border,shadow)

After these steps, this SSH Key Pair will be added to the *SSH Keys page*.

## Copy Public Key
To copy the Public Key of the SSH Key Pair do the following:
- identify this desired SSH Key Pair on the *SSH Keys page*;
- click the **Actions** icon and select the **Copy public key to the clipboard** in the list of available options.

After these steps, the *Public Key* of the selected SSH Key Pair will be copied to the clipboard.

## Delete SSH Key Pair
To remove the SSH Key Pair do the following:
- identify this unnecessary SSH Key Pair on the  *SSH Keys page*;
- click the **Actions** icon and select the **Delete** in the list of available options;
- confirm the SSH Key Pair deletion on the next opened *Confirmation window*.

After these steps, the selected SSH Key Pair will be deleted.

