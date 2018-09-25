# AWS Certified Solution Architect Prep Material

### What is cloud computing

- Cloud computing is an architecture where computing resources are delivered over the
network to the user. 
- Businesses uses cloud computing to start their operation quickly without investing 
months to setup an IT infrastructure or data center.


### IAAS, PAAS and SAAS

 - *Infrastruture As A Service* : IaaS allows users to rent the infrastructure itself: servers, data center space, and software. The biggest advantage of renting, as opposed to owning, infrastructure is that users can scale up the amount of space needed at any time. During busy holiday seasons, online retailers may require more server space to handle the heavy traffic than in the off-season. Using IaaS allows the retailer to save money by only paying for what they will use within a certain time frame.

 - *Platform As A Service* : PaaS allows developers to create applications, collaborate on projects, and test application functionality without having to purchase or maintain infrastructure. Development platforms can be accessed as long as there is an internet connection, allowing team members to stay connected and keep working.

 - *Software As A Service* : When a company wanted to purchase new software in the past, it could be a very expensive and time consuming process. But with SaaS, software can be quickly deployed,since it is already installed on the cloud server. As with PaaS, users only need access to a computer with internet connection to use the software, and they never have to worry about upgrading or patching the software. SaaS can reduce costs, since users only pay for exactly what is needed and do not have to maintain the software.

 ### Public cloud, Private Cloud and Hybrid Cloud

 - *Public Cloud* : 
     - In public cloud, resources like servers and data centres and managed by third party        service providers. AWS, Azure are examples of public cloud.
     - In a public cloud, same hardware, storage and network devices are shared by                organizations using the cloud
     - low cost, no maintenance, unlimited scalability via on demand facility, high reliability

- *Private Cloud* : 
     - Private cloud consists of resources that are used by one business or organization          exclusively
     - They can be hosted physically at organization's data center or by a third party.
     - Hardware, software and infrastructure is completely dedicated to the organization needs
     - Used by government agencies, financial institutions and large corporations.
     - more flexibility, improved security and high scalability

- *Hybrid Cloud* :
     - It combines best features of both private and public cloud
     - In hybrid cloud, data and applications can move between private and public clouds
     - For example, using public cloud for high traffic, lower security apps such as web based
       email and using private cloud for sensitive, business critical operations like financial
       operations.
     - Cloud bursting, it means when high traffic is expected then the private cloud can use      more resources from the public cloud to handle the high volume.
     - control, cost-effectiveness, ease of transitioning to cloud

 
### Cloud Types
![alt text](cloud.png)

### Advantages of Cloud
- Low cost
- Easily upgrade
- Always up and running
- Disaster and Recovery management
- No IT maintenanace cost
- Offsite data storage
- Access from anywhere

### Disadvantages of Cloud
- Without internet, you cannot access your servers and data
- Securtiy and Privacy issues, like storing confidential information on cloud
- Vendor Lockin
- Limited Control


## Introduction to AWS

- Amazon Web Services launched in 2006, to provide computing resources to businesses in the form
  of web services.

- As of Sept-2018, AWS provides various services ranging from Compute, Mobile, Machine Learning   ... and many others services.

- Services Provided By AWS
![alt text](awsservices.png)


### AWS Account Creation

- [Creating an AWS Account](https://www.youtube.com/watch?v=WviHsoz8yHk)

- AWS has Identity and Access Management service, to create users account for specific job roles and to ensure secure access to services.
  We will look at IAM later, for now just checkout the video below to see how an IAM user is created.
  [Creating user with IAM](https://youtu.be/G_4pRb8HsWs)


### AWS Services Description

- [Amazon S3](#amazon-s3)
- [Amazon Glacier](#amazon-glacier)



### Amazon S3

- *Amazon Simple Storage Service* :
	- Amazon S3 is an object storage service for storing data on cloud. It is simple, durable and comes with 99.9999% availability.
	- It is also possible to run analytics on stored data.
	- *Usecases* :
		- Backup and Recovery
		- Data Archiving
		- Big Data Analytic
		- Hybrid Cloud Storage
		- Cloud Native Application Data
		- Disaster Recovery 

- Cloud Object Storage makes it possible to store practically limitless amounts of data in its native format.

- *Advantages* :
	- Buckets are the fundamental container in Amazon S3 for data storage.
	- Each object can contain upto 5TB of data and we can store as many objects as we like in a bucket.
	- Can grant or deny access to data. Grant upload and download permissions.
	- Standard interfaces for uploading and retrieving data, SOAP and REST based interfaces. 

- *Limitations* :
	- By default, 100 buckets are allowed in an AWS account.
	- Bucket limit can be increase with a request.
	- Bucket nesting is not allowed.
	- High availability is for get,put,list and delete opertions.

- S3 normally used for storing media files.

#### Storage Classes

- Storage classes for frequently accessed objects
	- STANDARD
	- REDUCED_REDUNDANCY

- Storage Classes for Infrequently Accessed Objects
	- STANDARD_IA
	- ONEZONE_IA

- The GLACIER storage class is suitable for archiving data where data access is infrequent. 
  Archived objects are not available for real-time access. You must first restore the objects before you can access them.

- We can use Storage Classes Analysis to find perfect storage class for objects by looking at S3 access logs

- More details of storage classes at [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html)


#### Bucket Policy

- Bucket policy and user policy are two of the access policy options available for you to grant permission to your Amazon S3 resources. Both use JSON-based access policy language.

	- [AWS S3 Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html)

#### Bucket Naming Convention

- Bucket name must follow the standard DNS naming convention.

#### Versioning

- Versioning enables you to keep multiple versions of an object in one bucket in order to be safe from
  unintented overwrites and deletions and it is also used as backup.

- It can be set by enabling Versioning option in bucket properties.

#### Lifecycle Configurations

- Lifecycle configs of objects means that setting policies transition and expiration actions.
- Transition actions: to change storage class of objects that have not been accessed since 30 days to STANDARD_IA or after 1 year to GLACIER
- Expiration actions: to delete objects after certain amount of time
- We can enable this option to manage lifecycle of objects

&nbsp;
&nbsp;
&nbsp;
&nbsp;
- [Using AWS S3 via Python](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/s3-examples.html)

- [Hosting Static website on AWS S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)

- [More Details](https://docs.aws.amazon.com/s3/index.html)

&nbsp;
&nbsp;
 
### Amazon Glacier

- Amazon Glacier is another cloud storage service related to Amazon S3, but optimized for data archiving and long-term backup at extremely
  low cost. It is suitable for data which is rarely accessed and have acceptable retrieval time of about 3-5 hours.

- *Vault* : It is a container in AWS Glacier for storing archives. Each vault resource has a unique address.

- You can store unlimited archives in a vault.

- *Archive* : An archive can be any data such as photo, video or document and is a base unit of storage in Amazon Glacier.
- example url to an archive : https://region-endpoint/account-id/vaults/vault-name/archives/archive-id

- *Job* : Retrieving an archive and vault inventory (list of archives) are asynchronous operations in Amazon Glacier
  in which you first initiate a job, and then download the job output after Amazon Glacier completes the job. With
  Amazon Glacier, data retrieval requests are queued and most jobs take about four hours to complete.

- *Notification Configuration* : Because jobs take time to complete, Amazon Glacier supports a notification mechanism to
  notify you when a job is completed. You can configure a vault to send notification to an Amazon Simple Notification Service
  (SNS) topic when jobs complete.

	- One SNS topic per vault

- *Amazon Glacier Supported Operations* :
	- create and delete vaults
	- set, retrieve and delete a notification

	- upload and delete archives
	- There is no update archive option, you have to delete an existing archive in order to update it.
	
	- initiate a job, get job description, retrieve a list of jobs associated with a vault, 
	
- Following operations are asynchronous : Retrieving an archive and Retrieving a list of archives

- [AWS Glacier Documentation](https://docs.aws.amazon.com/glacier/index.html)

