---
title: Working with OpenStack API
weight: 15
---
___
On this page, you can find an explanation of how to work with OpenStack API using Ventus Cloud account.

# Table of contents
1. [Introduction](#introduction)
2. [Configure credentials file ](#configure-credentials-file)
3. [Dot source credentials file](#dot-source-credentials-file)
4. [Run test commands](#run-test-commands)
5. [Change region](#change-region)
6. [Find resources](#find-resources)
7. [Conclusion](#conclusion)

## Introduction
We encourage clients to use [CLI Users]() to work directly with OpenStack API, but it has a limitation - it's bonded to the specific project in the specific region.  
When you need to manage resources in all regions and all projects using the same credentials, you can use the Ventus Cloud account.   

**Required endpoints:** 
* *login.ventuscloud.eu* - used for authentication;
* Specify the scope of resources(region) to work with:
	* vienna.ventuscloud.eu;
	* upper-austria.ventuscloud.eu;
	* eastern-switzerland.ventuscloud.eu.

## Configure credentials file
Take an example template below to configure your credentials file, you need to adjust only:  

* OS_USERNAME - User email used to login to Ventus Cloud; 
* OS_PASSWORD - User's password;  
* OS_PROJECT_ID - Id of created projects in Ventus Cloud; can be found on the project details page;   
* OS_AUTH_URL - Endpoint to the region where your project created.

```output
cat << EOF > ./ventus_credentials

export OS_USERNAME="username@company.domain"
export OS_PASSWORD="password"

export OS_PROJECT_ID=95fXXXXXXXXXXd0
export OS_AUTH_URL=https://vienna.ventuscloud.eu/v3/

#export OS_AUTH_URL=https://upper-austria.ventuscloud.eu/v3/
#export OS_PROJECT_ID=42fXXXXXXXXXXb3

#export OS_AUTH_URL=https://eastern-switzerland.ventuscloud.eu/v3/
#export OS_PROJECT_ID=eafXXXXXXXXXXb4

export OS_PROJECT_DOMAIN_NAME=ventus
export OS_IDENTITY_API_VERSION=3
export OS_AUTH_PLUGIN=openid
export OS_AUTH_TYPE=v3oidcpassword
export OS_IDENTITY_PROVIDER=keycloak-ventus-oidc-idp
export OS_PROTOCOL=openid
export OS_DISCOVERY_ENDPOINT=https://login.ventuscloud.eu/auth/realms/ventus/.well-known/openid-configuration
export OS_CLIENT_ID=ventus
export OS_CLIENT_SECRET=b950c9f444f90431939bf1da322363ce5c495be8a73b0ac672a9386fbea8e3d0
EOF
```

## Dot source credentials file
Use next command:  

`. ventus_credentials`  

This will export environment variables to your shell and let OpenStack CLI client required information for authentication using the Ventus account.

## Run test commands
Use next command: 

`openstack project list`  

Expected result - list of all projects in your currently active region:

```output
+------------------+--------------------------+
| ID | Name |
+------------------+--------------------------+
| 3c6XXXXXXXXXXa32 | 4e7XXXXXXXXXX609:swiss-3 |
| ba8XXXXXXXXXX1c3 | 4e7XXXXXXXXXX609:Swiss-2 |
| ea7XXXXXXXXXXab4 | 4e7XXXXXXXXXX609:Swiss-1 |
+------------------+--------------------------+
```

## Change region
To change the region do the dollowing:

* Edit your *ventus_credentials file*, change currently selected region to another one;
* Dot source your ventus_credentials file:  
`. ventus_credentials`;  
* Check projects:  
`openstack project list`;  

Expected result - you can see your"
```output
+------------------+--------------------------+
| ID | Name |
+------------------+--------------------------+
| 424XXXXXXXXXXcb3 | 4e7XXXXXXXXXX609:Upper-1 |
| a01XXXXXXXXXXacc | 4e7XXXXXXXXXX609:Upper-2 |
+------------------+--------------------------+
```

## Find resources 
To find resources in the specific region in the specific project do the following:

* Configure your *credentials file (ventus_credentials)* to refer to the specific region and specific project: 

`export OS_PROJECT_ID=95fXXXXXXXXXXd0`  
`export OS_AUTH_URL=https://vienna.ventuscloud.eu/v3/`  

* Dot source credentials file:  
`. ventus_credentials`;  
* Check servers available in this project:  
`openstack server list`    

Expected result - list of servers deployed in this project:
```output
+-----------------+---------+--------+---------------------+----------------------------------+--------+
| ID | Name | Status | Networks | Image | Flavor |
+-----------------+---------+--------+---------------------+----------------------------------+--------+
| a02XXXXXXXXXX5d4|vienna-1 | ACTIVE | public=88.218.52.10 | ubuntu-server-20.04-LTS-20201111 | VC-2   |
+-----------------+---------+--------+---------------------+----------------------------------+--------+
```
* Edit your credentials file to refer to another project (in this or another region):

`export OS_PROJECT_ID=ea7XXXXXXXXXXab4`  
`export OS_AUTH_URL=https://eastern-switzerland.ventuscloud.eu/v3/`  

* Dot source credentials file:  
`. ventus_credentials`  

* Check servers available in this project:  
`openstack server list`  

Expected result - list of servers deployed in this project:
```output
+-----------------+---------+--------+---------------------+----------------------------------+--------+
| ID | Name | Status | Networks | Image | Flavor |
+-----------------+---------+--------+---------------------+----------------------------------+--------+
| a02XXXXXXXXXX5d4|swiss-1 | ACTIVE | public=178.238.0.10 | ubuntu-server-20.04-LTS-20201111 | VC-2    |
+-----------------+---------+--------+---------------------+----------------------------------+--------+
```

## Conclusion
You can leverage your Ventus account to work with any OpenStack resources in any available regions in any available projects using the same credentials.

 