---
title: Organization's management over API
weight: 20
---
___
On this page, you can find the workflow for management of your Organization in Ventus Cloud using API.

# Table of contents
1. [Required endpoints](#required-endpoints)
2. [Example using CURL](#example-using-curl)
3. [Example using Postman](#example-using-postman) 

## Required endpoints
- **auth.ventuscloud.eu** - use it to get ID and Access tokens from basic credentials
- **api.ventuscloud.eu** - use it to work with organization's resources 

## Example using CURL
**Get ID and Access tokens**  
To get ID and Access tokens use next command: 
```
curl -XGET https://auth.ventuscloud.eu/get-tokens -d '
{
    "username":"username@company.domain",
    "password":"password"
}'
```

Response example:
```output
{
"id_token":"eyJ......kRg",
"access_token":"eyJ......6Tg"
}
```

Export variables to reuse them in the next steps: 
```
export ID_TOKEN="eyJh......XIbA"
export ACCESS_TOKEN="eyJh......AsrA"
export ORGANIZATION_ID="c19......e50"
export REGION_NAME="eastern-switzerland" //must be in lower case
export PROJECT_ID="f5......45"
```

Organization ID can be extracted from URL in Ventus Console, e.g.:
```
https://console.ventuscloud.eu/organizations/c19XXXX-XXXX-XXXX-XXXX-XXXX50/projects
```

**List all Projects**  
To list all Projects use next command:
```
curl -XGET https://api.ventuscloud.eu/v1.0/invoke/gotham-enterprises/method/orgs/$ORGANIZATION_ID/projects \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN"
```

Response example:
```output
[
{
"id":"a8dxxxxxxxxxxxxxxxxxddf",
"name":"Swiss",
"region":"Eastern-Switzerland"
},
{
"id":"766xxxxxxxxxxxxxxxxxcdf",
"name":"Upper",
"region":"Upper-Austria"
},
{
"id":"17axxxxxxxxxxxxxxxxxdf9",
"name":"Vienna",
"region":"Vienna"
}
]
```

**Create new Project**  
To create new Project use next command:
```
curl -XPOST https://api.ventuscloud.eu/v1.0/invoke/gotham-$REGION_NAME-identity/method/$ORGANIZATION_ID/projects/PROJECT_NAME \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN"
```

Response example:
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"PROJECT_NAME"
}
```

**Get Project by ID**  
To get Project by ID use next command:
```
curl -XGET https://api.ventuscloud.eu/v1.0/invoke/gotham-$REGION_NAME-identity/method/projects/$PROJECT_ID \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN"
```

Response example:
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"PROJECT_NAME"
}
```

**Edit Project name**  
To edit Project name use next command:
```
curl -XPUT https://api.ventuscloud.eu/v1.0/invoke/gotham-$REGION_NAME-identity/method/$ORGANIZATION_ID/projects/$PROJECT_ID \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN" -d '{"name":"NEW_PROJECT_NAME"}'
```

Response example:
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"NEW_PROJECT_NAME"
}
```

**Delete Project**  
To delete Project use next command:
```
curl -XDELETE -I https://api.ventuscloud.eu/v1.0/invoke/gotham-$REGION_NAME-identity/method/$ORGANIZATION_ID/projects/$PROJECT_ID \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN"
```

Response example:
```output
HTTP/2 200
```


**Get Prices**  
To get Prices use next command:
```
curl -XGET https://api.ventuscloud.eu/v1.0/invoke/gotham-bank/method/prices \
-H "Authorization: Bearer $ID_TOKEN" \
-H "Access: Bearer $ACCESS_TOKEN"
```

Response example:
```output
{
    "chf": {
        "storage": 0.0003,
        "flavors": [
            {
                "id": "0000-0020-vc-1",
                "name": "VC-1",
                "price": {
                    "base": 0.0121,
                    "windows": 0.01815
                }
            },
            {
                "id": "0000-0040-vc-4",
                "name": "VC-4",
                "price": {
                    "base": 0.0484,
                    "windows": 0.0726
                }
            },

.....
}
.....
]
```

## Example using Postman
**Get ID and Access tokens**  
To get ID and Access tokens do the following:

* Create new Request with the next parameters:
    * *Option*: GET;
    * *URL*: https://auth.ventuscloud.eu/get-tokens;
    * *Body*: as a row. 
```
{
"username":"username@company.domain",
"password":"password"
}
```

![](../../assets/images/adv/1.png?classes=border,shadow) 

* Click on the **Send** icon and in Response block you will receive:
```output
{
"id_token":"eyJ......kRg",
"access_token":"eyJ......6Tg"
}
```

To save this tokens as variables for the reusing them in the next steps do the following:
* go to the **Environments** tab:
![](../../assets/images/adv/2.png?classes=border,shadow) 

* select **Globals** if you need make this variables *global accessible*, or create additional environment for them;
* enter *key/value* of your variables and click on the **Save** icon:
![](../../assets/images/adv/3.png?classes=border,shadow)

**List all Projects**  
To list all Projects do the following:  

* Create new Request with the next parameters:
    * *Option*: GET;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-enterprises/method/orgs/ORG-ID/projects;  
    * *Headers*: 
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN;  

{{% notice note %}}
*ORG-ID* - Organization ID that was extracted from URL in Ventus Console, and saved as a variable.  
*ID_TOKEN* and *ACCESS_TOKEN* - tokens that were received with previous "Get ID And Access tokens" request and saved as a variables.
{{% /notice %}}

![](../../assets/images/adv/4.png?classes=border,shadow)    

* Click on the **Send** icon and in Response block you will receive:
```output
[
{
"id":"a8dxxxxxxxxxxxxxxxxxddf",
"name":"Swiss",
"region":"Eastern-Switzerland"
},
{
"id":"766xxxxxxxxxxxxxxxxxcdf",
"name":"Upper",
"region":"Upper-Austria"
},
{
"id":"17axxxxxxxxxxxxxxxxxdf9",
"name":"Vienna",
"region":"Vienna"
}
]    
```

**Create new Project**  
To create new Project do the following:

* Create new Request with the next parameters:
    * *Option*: POST;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-REGION_NAME-identity/method/ORG-ID/projects/newPROJECT;  
   * *Headers*: 
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN.

{{% notice note %}}
*REGION_NAME* - region name that was entered in lowercase and saved as a variable;    
*newPROJECT* - name of the new Project.
{{% /notice %}}  

![](../../assets/images/adv/5.png?classes=border,shadow)    

* Click on the **Send** icon and in Response block you will receive:     
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"newPROJECT"
}
```

**Get Project by ID**  
To get Project by ID do the following:

* Create new Request with the next parameters:
    * *Option*: GET;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-REGION_NAME-identity/method/projects/PROJECT_ID;
    * *Headers*:
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN.  

{{% notice note %}}    
*PROJECT_ID* - ID of the desired project that was saved as a variable.  
{{% /notice %}}  

![](../../assets/images/adv/6.png?classes=border,shadow)  

* Click on the **Send** icon and in Response block you will receive:     
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"PROJECT_NAME"
}
```        

**Edit Project name**  
To edit Project name do the following: 

* Create new Request with the next parameters:
    * *Option*: PUT;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-REGION_NAME-identity/method/ORG-ID/projects/PROJECT_ID;
    * *Headers*:
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN.
    * *Body*: as a row - `{"name":"NEW_PROJECT_NAME"}`  

    ![](../../assets/images/adv/7.png?classes=border,shadow)   
    ![](../../assets/images/adv/8.png?classes=border,shadow) 

* Click on the **Send** icon and in Response block you will receive:     
```output
{
"id":"efexxxxxxxxxxxxxxxxxf9b",
"name":"NEW_PROJECT_NAME"
}
```     

**Delete Project**  
To delete Project do the following:

* Create new Request with the next parameters:
    * *Option*: DELETE;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-REGION_NAME-identity/method/ORG-ID/projects/PROJECT_ID;  
    * *Headers*: 
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN.

{{% notice note %}}
PROJECT_ID - ID of the project, that you want to delete, saved as a variable.
{{% /notice %}}

![](../../assets/images/adv/9.png?classes=border,shadow) 

* Click on the **Send** icon and the selected project will be deleted.     

**Get Prices**   
To get Prices do the following:

* Create new Request with the next parameters:
    * *Option*: GET;
    * *URL*: https://api.ventuscloud.eu/v1.0/invoke/gotham-bank/method/prices;
    * *Headers*: 
        * *Authorization*: Bearer ID_TOKEN;
        * *Access*: Bearer ACCESS_TOKEN.

    ![](../../assets/images/adv/10.png?classes=border,shadow) 

* Click on the **Send** icon and in Response block you will receive:     
```output
{
    "chf": {
        "storage": 0.0003,
        "flavors": [
            {
                "id": "0000-0020-vc-1",
                "name": "VC-1",
                "price": {
                    "base": 0.0121,
                    "windows": 0.01815
                }
            },
            {
                "id": "0000-0040-vc-4",
                "name": "VC-4",
                "price": {
                    "base": 0.0484,
                    "windows": 0.0726
                }
            },

.....
}
```         