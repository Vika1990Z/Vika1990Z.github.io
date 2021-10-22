---
title: Object Storage
weight: 10
---
___
On this page, you can find an explanation of what is Object Storage in Cloud Console, how to create, delete buckets and instructions for other steps to manage an Object Storage in Cloud Console.

# Table of contents
1. [Introduction](#introduction)
2. [Use Object Storage with Python API](#use-object-storage-with-python-api)
   1. [Creating connection](#creating-connection)
   2. [Listing owned buckets](#listing-buckets)
   3. [Creating bucket](#creating-bucket)
   4. [Creating object](#creating-object)
   5. [Listing bucket's content](#listing-bucket's-content)
   6. [Changing object's ACL](#changing-bucket's-acl)
   7. [Generating object's download-URL](#generating-object's-download-url)
   8. [Deleting object](#deleting-object)
   9. [Deleting a bucket](#deleting-bucket)
3. [Use Object Storage with S3 Browser](#use-object-storage-with-s3-browser)

## Introduction

The Cloud Console Object Storage makes it possible to store data simply and cost-effectively. It provides a fully distributed, API-accessible storage platform that can be integrated directly into applications or used for backup, archiving, and data retention.

It’s built for scale and optimized for durability, availability, and concurrency across the entire data set. 

An Object Storage API differs from a conventional filesystem: instead of directories and files, you manipulate containers where you store objects. A container can hold millions of objects.

There is no notion of hierarchy with containers: you cannot nest a container within another, however, you can emulate a nested folder structure with a naming convention for your objects.

Before we start to configure and use Object Storage we need to create credentials that include the access key and secret key.   
To find instructions of how to create Object Storage Credentials in Cloud Console, please, see the article - [Object Storage Credentials]()

## Use Object Storage with Python API  
Python support is provided through a fork of the *boto3* library with features to make the most of Cloud Console Object Storage. 
To start use the Object Storage with the Python API do the following:
- install boto library by running the command:  
`pip install boto`    

>**NOTE:** As well as Python API you can select other programming languages for using the Object Storage.

Now let's take a closer look at each block of code to deal with possible interactions with Object Storage via the Python API:

### Creating connection

To create a connection for interacting with the server use next block of code:  
```python
import boto
import boto.s3.connection
s3_access_key = '**your_access_key**'
s3_secret_key = '**your_secret_key**'
s3_host = '**upper-austria.ventuscloud.eu**
conn = boto.connect_s3(
    aws_access_key_id=s3_access_key,
    aws_secret_access_key=s3_secret_key,
    host=s3_host,
    port=8080,
    calling_format=boto.s3.connection.OrdinaryCallingFormat(),
)
```
Remember to replace the *your_access_key* and *your_secret_key* part with your credential information, and also check if the s3_host is correct - if it matches the correct Region.

### Creating bucket
To create a new Bucket use the next block of code:
```python
bucket = conn.create_bucket('**1-bucket-using-python**')
print(f"New bucket created:\n{bucket_name}\t{bucket}")
```

The *1-bucket-using-python* is the name of the new bucket, please enter the desired name for your bucket here.

### Listing owned buckets
To get a list of Buckets that you own use the next block of code:
```python
for bucket in conn.get_all_buckets():
    print ("{name}\t{created}".format(
            name = bucket.name,
            created = bucket.creation\_date,
    ))
```
It also prints out the bucket name and creation date of each bucket.

### Creating object
To create a new object in the bucket use the next block of code:
```python
key = bucket.new_key('hello.txt')
key.set_contents_from_string('Hello World!')

key = bucket.new_key('private_info.txt')
key.set_contents_from_filename('/home/usr/private_data.txt')
```

So, it creates a file 'hello.txt' with the string "Hello World!" and a file 'private_info.txt' with the data from the local file.

### Listing bucket's content
To list a bucket's content use the next block of code:
```python
for key in bucket.list():
    print "{name}\t{size}\t{modified}".format(
            name = key.name,
            size = key.size,
            modified = key.last_modified,
            )
```

It also prints out the object name, size and creation date of each object.

### Changing object's ACL
>ACL = access control lists

To make objects to be publicly readable or to be private, use the next block of code:
```python
hello_key = bucket.get_key('hello.txt')
hello_key.set_canned_acl('public-read')

private_key = bucket.get_key('private_info.txt')
private_key.set_canned_acl('private')
```

So, this code makes the object 'hello.txt' to be publicly readable, and the object 'private_info.txt' to be private.

### Generating object download URL
**For *publicly readable* objects** we can generate an unsigned download URL.   
To do this use the next block code:
```python
private_key = bucket.get_key('hello.txt')
hello_url = hello_key.generate_url(0, query_auth=False, force_http=False)
print (hello_url)
```

**For *private* objects** we can generate a signed download URL that will work for the time period (when the time period is up, the URL will stop working).   
To do this use the next block code:
```python
private_key = bucket.get_key('private_data.txt')
private_url = private_key.generate_url(3600, query_auth=True, force_http=False)
print (private_url)
```

Please, notice here, when a client application accesses buckets, it always operates with the credentials of a particular user. As every user belongs to a particular project, therefore, for using this links you should *add your project ID before your bucket name*, and the working links in both examples will look like this:    
**for publicly readable objects** - "https://upper-austria.ventuscloud.eu:8080/**Your_Project_ID:**new-bucket-using-python/hello.txt";   
**for private objects** - "https://upper-austria.ventuscloud.eu:8080/**Your_Project_ID:**new-bucket-using-python/private_info.txt?Signature=XXX&Expires=1316027075&AWSAccessKeyId=XXX"     

Find your Project ID you can:
* on the *Projects page* in Cloud Console:
![](../../../assets/images/store/6.png?classes=border,shadow) 

* in the link, when you use Cloud Console:
![](../../../assets/images/store/7.png?classes=border,shadow) 

### Deleting object
To delete an object from the bucket use the next code block:
```python
bucket.delete_key('hello.txt')
```

It deletes a file "hello.txt" from the bucket.

Deleting bucket
To delete a whole bucket use the next code block:
```python
conn.delete_bucket("**1-bucket-using-python"**)
```

It deletes the whole bucket called "1-bucket-using-python".

## Use Object Storage with S3 Browser
The **S3 Browser** is another way how we can use the Cloud Console Object Storage and manage data stored in it.  
To download and install it on your computer, go to the next page <https://s3browser.com/>.  

After installation, you can open on your computer **S3 Browser** and see the next interface of this program:
![](../../../assets/images/store/8.png?classes=border,shadow) 

To start work with the Cloud Console Object Storage provide your credential information, for this do the following:
- on the main *Navigation Panel* go to *Accounts*, choose **Add new account:**
![](../../../assets/images/store/9.png?classes=border,shadow) 
![](../../../assets/images/store/10.png?classes=border,shadow) 
- fill in fields on the following page as shown below press **Add new account**:
![](../../../assets/images/store/11.png?classes=border,shadow)

After these steps, a connection to the Cloud Console Object Storage through the **S3 browser** is established and you can see all owned buckets and to manage them:
- To **add** a new bucket or **delete** a bucket just by clicking on the one of the buttons:
![](../../../assets/images/store/12.png?classes=border,shadow)
- To make bucket **public** or **private** go to **Permissions tab** and select the necessary option:
![](../../../assets/images/store/13.png?classes=border,shadow)

So, as you can see, using the Cloud Console Object Storage through the **S3 Browser** is as easy as using programming languages.

