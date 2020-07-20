---
layout: post
title: "AWS SA-A review - domain knowledge"
subtitle: ""
date: 2020-06-01 00:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - infrastructure
  - AWS
  - Certification
---

## IAM

> Identity Access Management

![Screen Shot 2020-06-02 at 22.20.28](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-02%20at%2022.20.28.png)

#### Role with EC2

##### Example

1. SSH to an new EC2 instance
2. try `aws s3 ls`. It will request you to configure credentials by running `aws configure` so that you can input your Access Key ID and Secret there. Don't do it but follow step 3.
3. Go to attach a admin role to this EC2 instance, then try step 2 again. You should be able to `ls`.

##### Conclusion

1. Roles are more secure than storing your access key and secret access key on individual EC2 instance
2. Roles are easier to manage.
3. Roles can be assigned to an EC2 instance after it is created.
4. Roles are non-regional. 

### AWS Directory Service

> Microsoft service

#### What Is AWS Directory Service

![image-20200702134252469](2020-06-01-AWS-domain-knowledge.assets/image-20200702134252469.png)

#### what is active directory

![image-20200702134059591](2020-06-01-AWS-domain-knowledge.assets/image-20200702134059591.png)

> ==LDAP== (Lightweight Directory Access Protocol) is a software protocol for enabling anyone to locate data about organizations, individuals and other resources such as files and devices in a network -- whether on the public internet or on a corporate intranet.

#### AWS managed Microsoft AD

![image-20200702134214496](2020-06-01-AWS-domain-knowledge.assets/image-20200702134214496.png)

AWS vs. customer responsibility

![image-20200702134425306](2020-06-01-AWS-domain-knowledge.assets/image-20200702134425306.png)

> DCs:  Domain Controllers

#### Simple AD

![image-20200702134529087](2020-06-01-AWS-domain-knowledge.assets/image-20200702134529087.png)

#### AD Connector

![image-20200702134601300](2020-06-01-AWS-domain-knowledge.assets/image-20200702134601300.png)

#### Cloud Directory

![image-20200702134624985](2020-06-01-AWS-domain-knowledge.assets/image-20200702134624985.png)

#### Amazon Congnito User Pools

![image-20200702134709942](2020-06-01-AWS-domain-knowledge.assets/image-20200702134709942.png)

#### AD v.s Non-AD compatible

![image-20200702134803071](2020-06-01-AWS-domain-knowledge.assets/image-20200702134803071.png)

### IAM Policies

ARN

#### Amazon Rousource Name (ARN)

![image-20200702135324466](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200702135324466.png)

#### IAM Policies

- JSON doc that defines permissions.
- No effect until attached 
- List of statements
  - statement structure: Effect, Action, Resource

![image-20200702140046192](2020-06-01-AWS-domain-knowledge.assets/image-20200702140046192.png)

![image-20200702140153543](2020-06-01-AWS-domain-knowledge.assets/image-20200702140153543.png)

> Sid is for human to read, like a commend in code.

- Not explicitly allowed == implicitly denied 

- ==Explicit deny== ==overrides== everything else 

- Only attached policies have effect 

- AWS ==joins== all applicable policies

- AWS-managed vs. customer-managed 

- [Identity policy  vs. Resource policy]([https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html#:~:text=A%20policy%20is%20an%20object,user%2C%20group%2C%20or%20role.](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html#:~:text=A policy is an object,user%2C group%2C or role.))
  
  > For same account? For cross-account request?
  > 
  > <img src="2020-06-01-AWS-domain-knowledge.assets/Types_of_Permissions.diagram.png" alt="          Identity-based vs resource-based policies       " style="zoom:80%;" />

#### Permission Boundaries

- Used to delegate administration to other users 
- Prevent privilege escalation or unnecessary broad permissions
- Control maximum permissions an IAM policy can grant 
- Use cases: 
  - Developers creating roles for Lambda functions 
  - Application owners creating roles for EC2 instances 
  - Admins creating ad hoc users 

### Resource Access Manager (RAM)

>  Account isolation / multi-account strategy 

![image-20200702143755118](2020-06-01-AWS-domain-knowledge.assets/image-20200702143755118.png)

![image-20200702143844158](2020-06-01-AWS-domain-knowledge.assets/image-20200702143844158.png)

Action: How to share a resource to another account through ARM?

### AWS Single Sign-On

#### What is AWS SSO?

![Screen Shot 2020-07-02 at 14.42.50](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-02 at 14.42.50.png)

#### Granular Account-Level Permissions

![image-20200702144616421](2020-06-01-AWS-domain-knowledge.assets/image-20200702144616421.png)

#### Active Directory and SAML Integration

> SAML: Security Assertion Markup Language

![image-20200702145031913](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200702145031913.png)

> IAM integrates with **existing active directory** account allowing single sign-on.

#### Others

- IAM Supports PCI DSS compliance
  
  > The Payment Card Industry Data Security Standard (==PCI DSS==) refers to payment security standards that ==ensure all sellers== safely and securely ==accept, store, process, and transmit== cardholder data (also known as your customers' credit card information) during a credit card transaction.

- IAM can be use for your users' management as well.

#### Things To search further

- **Power User Access** allows ==Access to all AWS services== except the management of groups and users within IAM.
- What is Resource Based Access Control List (ACL) 
- What is Setting up a cross account IAM Role for?

> An application you are working on has a new app. The development team for this app requires access to a bucket that is located within your team's aws account. The other team requires programmatic and console level access to your team's bucket. How would you share this bucket with this other team's account?
> 
> [link](https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/)

### Q&A

- When updating the policy used by an IAM Role attached to an EC2 instance, what needs to happen for the changes to take effect?
  
  > Nothing - It will take effect immediately

## S3

### Pricing Tiers & Storage Classes

> what are they? what features they have? cost? what fits what?

S3-Standard has an availability of ==99.99%==, S3-IA has an availability of ==99.9%== while S3-1Zone-IA only has ==99.5%==

![Screen Shot 2020-06-04 at 14.07.03](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-04%20at%2014.07.03.png)

#### Performance table

|                                    | S3 Standard            | S3 Intelligent-Tiering* | S3 Standard-IA         | S3 One Zone-IA†        | S3 Glacier              | S3 Glacier Deep Archive |
|:----------------------------------:|:----------------------:|:-----------------------:|:----------------------:|:----------------------:|:-----------------------:|:-----------------------:|
| Designed for ==durability==        | 99.999999999% (11 9’s) | 99.999999999% (11 9’s)  | 99.999999999% (11 9’s) | 99.999999999% (11 9’s) | 99.999999999% (11 9’s)  | 99.999999999% (11 9’s)  |
| Designed for availability          | 99.99%                 | 99.9%                   | 99.9%                  | 99.5%                  | 99.99%                  | 99.99%                  |
| Availability SLA                   | 99.9%                  | 99%                     | 99%                    | 99%                    | 99.9%                   | 99.9%                   |
| Availability Zones                 | ≥3                     | ≥3                      | ≥3                     | 1                      | ≥3                      | ≥3                      |
| Minimum capacity charge per object | N/A                    | N/A                     | ==128KB==              | 128KB                  | 40KB                    | 40KB                    |
| Minimum storage duration charge    | N/A                    | 30 days                 | 30 days                | 30 days                | 90 days                 | 180 days                |
| Retrieval fee                      | N/A                    | N/A                     | per GB retrieved       | per GB retrieved       | per GB retrieved        | per GB retrieved        |
| First byte latency                 | **milliseconds**       | **milliseconds**        | **milliseconds**       | **milliseconds**       | select minutes or hours | select hours            |
| Storage type                       | Object                 | Object                  | Object                 | Object                 | Object                  | Object                  |
| Lifecycle transitions              | Yes                    | Yes                     | Yes                    | Yes                    | Yes                     | Yes                     |

### Security And Encryption

### Version Control

### Lifecycle Management and Glacier

### Lock Policies & Glacier Vault Lock

![image-20200701170420086](2020-06-01-AWS-domain-knowledge.assets/image-20200701170420086.png)

`modes`

![image-20200701170443557](2020-06-01-AWS-domain-knowledge.assets/image-20200701170443557.png)

Glacier Vault Lock

![image-20200701170510604](2020-06-01-AWS-domain-knowledge.assets/image-20200701170510604.png)

### Performance

#### prefix

- S3 has extremely low latency. You can get the first byte out of S3 within 100-200 milliseconds 

- To achieve a high number of requests: 3,500 PUT/COPY/POST/DELEtE and 5,500 GET/HEAD requests per second Per prefix

- what are Prefixes? (basically folder path)
  
  ![image-20200629200636689](2020-06-01-AWS-domain-knowledge.assets/image-20200629200636689.png?lastModify=1593586635)

#### multipart upload & byte-range fetches

![Screen Shot 2020-06-29 at 22.21.56](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-29 at 22.21.56.png)

![Screen Shot 2020-06-29 at 20.14.09](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-29 at 20.14.09.png)

#### S3 KMS limitation

![Screen Shot 2020-06-29 at 20.12.23](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-29 at 20.12.23.png)

![Screen Shot 2020-06-29 at 20.12.10](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-29 at 20.12.10.png)

### Select & Glacier Select

![Screen Shot 2020-07-01 at 17.06.42](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.06.42.png)

![Screen Shot 2020-07-01 at 17.08.28](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.08.28.png)

![Screen Shot 2020-07-01 at 17.12.56](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.12.56.png)

![Screen Shot 2020-07-01 at 17.08.48](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.08.48.png)

![Screen Shot 2020-07-01 at 17.09.23](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.09.23.png)

- Note that Se Select isused to retrived ==only a subset== of data ==from an object== . `csv` for example
- get data by __rows or columns__ using SQL
- save money on data transfer and increase speed

> [Selcet v.s Athena]([https://stackoverflow.com/questions/49102577/what-is-difference-between-s3-select-and-athena#:~:text=S3%20Select%20makes%20it%20easy,to%20retrieve%20the%20entire%20object.&text=Amazon%20Athena%20is%20an%20interactive%20query%20service%20that%20makes%20it,Amazon%20S3%20using%20standard%20SQL.](https://stackoverflow.com/questions/49102577/what-is-difference-between-s3-select-and-athena#:~:text=S3 Select makes it easy,to retrieve the entire object.&text=Amazon Athena is an interactive query service that makes it,Amazon S3 using standard SQL.))
> 
> You can think about AWS S3 Select as a cost-efficient storage optimization that allows retrieving data that matches the predicate in S3 and glacier aka push down filtering.
> 
> AWS Athena is fully managed analytical service that allows running arbitrary ANSI SQL compliant queries - group by, having, window and geo functions, SQL DDL and DML.

### AWS Organizations & Sharing S3 Buckets Between Accounts

### Cross Region Replication

### Transfer Acceleration

### DataSync

- Majorly used for moving on-premises data center to cloud.

![Screen Shot 2020-07-01 at 17.17.06](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.17.06.png)

![Screen Shot 2020-07-01 at 17.17.44](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.17.44.png)

- Used to move large amount of data from on-premises to AWS. 
- Used with ==NFS-== and ==SMB==-compatible file systems.
- Replication can be done hourly, daily, or weekly.
- Install the ==DataSync agent== to start the replication. 
- Can be used to replicate ==EFS== to ==EFS==

### CloudFront Overview

![Screen Shot 2020-07-01 at 17.23.08](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-01 at 17.23.08.png)

### CloudFront Signed URLs and Cookies

> content access restriction

#### Use CloudFront Signed URLs or Signed Cookies

1. A signed URL is for individual files. 1 file => 1 URL
2. A signed cookie is for multiple files. 1 cookie => multiple files. ( 1 cookie for a user to use a peroid?)

#### Attach policy to Signed URL / Signed cookie

![image-20200701172600599](2020-06-01-AWS-domain-knowledge.assets/image-20200701172600599.png)

#### How Signed URLs work

![image-20200702132411646](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200702132411646.png)

#### CloudFront Signed URL

![image-20200702132436786](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200702132436786.png)

![Screen Shot 2020-07-02 at 13.23.43](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-02 at 13.23.43.png)

### Snowball Overview

### Storage Gateway

### Athena vs Macie

### Summary

Features

- Tiered Storage Available
- Lifecycle Management
- Versioning
- Encryption
- MFA Delete
- AC: **Access Control Lists** and **Bucket Policies**

-----

AC -- By default, all newly created buckets are PRIVATE. You setup access control to your bukets using:

- bucket policies
- access control lists

S3 beckets cna be configured to create access logs which log all requests made to the S3 bucket. This can be sent to another bucket and even another bucket in another account.

---

__Objects__: The Key fundaments of S3 Are:

- key (the name of the object)
- value (the object that is made up of a sequece of bytes )
- Version ID (important for versioning)
- Metadata (data about data you are storing)
- Subresources:
  - access control lists
  - torrent

-----

- Read after Write for PUTS of new Objects
- Eventual Consistency for overwrite PUTS and DELETES (can take some time to propagate)

---

#### data consistency model

- Amazon S3 provides **read-after-write** consistency for PUTS of new objects in your S3 bucket in all Regions with one caveat. `??` 
- Amazon S3 offers **eventual consistency** fo**r overwrite PUTS and DELETES** in all Regions.
- Updates to a single key are **atomic**. For example, if you PUT to an existing key, a **subsequent read** might return the old data or the updated data, but it **never** returns **corrupted or partial data**.
- 
- more "currently no"
  - object locking; race case need to be solved by application level
  - atomic updates across keys; need to design&implement our own on application level;

| Eventually consistent read | Consistent read                 |
|:-------------------------- |:------------------------------- |
| Stale reads possible       | No stale reads                  |
| Lowest read latency        | Potential higher read latency   |
| Highest read throughput    | Potential lower read throughput |

![Screen Shot 2020-06-04 at 14.04.30](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-04%20at%2014.04.30.png)

- AWS S3 has four different URLs styles. What are they. what are they used for?

### Q&A

#### Access control

1. Which of the following options allows users to have secure access to private files located in S3? (Choose 3)
   
   - **CloudFront Signed URLs**
   - Public S3 buckets
   - **CloudFront Signed Cookies**
   - **CloudFront Origin Access Identity**

2. You run a popular photo-sharing website that depends on S3 to store content. Paid advertising is your primary source of revenue. However, you have discovered that other websites are linking directly to the images in your buckets, not to the HTML pages that serve the content. This means that people are not seeing the paid advertising, and you are paying AWS unnecessarily to serve content directly from S3. How might you resolve this issue?
   
   > Remove the ability for images to be served publicly to the site and then use signed URLs with expiry dates.

#### URL

1. AWS S3 has four different URLs styles that it can be used to access content in S3. The Virtual Hosted Style URL, the Path-Style Access URL, the Static web site URL, and the Legacy Global Endpoint URL. Which of these represents a correct formatting of the Virtual Hosted Style URL style

2. AWS S3 has four different URLs styles that it can be used to access content in S3. The `Virtual Hosted Style` URL, the `Path-Style Access` URL, the` Static web site` URL, and the `Legacy Global Endpoint` URL. Which of these represents a correct formatting of the `Virtual Hosted Style` URL style
   
   - `http://my-bucket.s3-website-ap-southeast-2.amazonaws.com/index.php`
   - `https://s3.us-west-2.amazonaws.com/my-bucket/slowpuppy.tar`
   - `https://www.my-registered-domain-guru/index.html`
   - `https://my-bucket.s3.us-west-2.amazonaws.com/fastpuppy.csv`
   - `https://my-bucket.amazonaws.com/lazycat.docx`
   - `http://my-bucket.s3-website.us-east-2.amazonaws.com/index.htm`
   
   > Virtual style puts your bucket name 1st, s3 2nd, and the region 3rd. 
   > 
   > Path style puts s3 1st and your bucket as a sub domain. 
   > 
   > Legacy Global endpoint has no region. 
   > 
   > S3 static hosting can be your own domain or your bucket name 1st, s3-website 2nd, followed by the region. 
   > 
   > AWS are in the process of phasing out Path style, and support for Legacy Global Endpoint format is limited and discouraged. However it is still useful to be able to recognize them should they show up in logs. Further information:

#### performance

> Performance scales per prefix, so you can use as many prefixes as you need in parallel to achieve the required throughput. There are no limits to the number of prefixes.
> 
> What is prefixes

1. You have been asked to advise on a __scaling__ concern. The client has an elegant solution that works well. As the information base grows they use __CloudFormation__ to spin up another stack made up of an S3 bucket and supporting compute instances. The trigger for creating a new stack is when the PUT rate approaches 100 PUTs per second. The problem is that as the business grows that number of buckets is growing into the hundreds and will soon be in the thousands. You have been asked what can be done to reduce the number of buckets without changing the basic architecture.
   
   - Refine the key hashing to randomise the name Key to achieve the potential of 300 PUTs per second.
   - `I picked this` Upgrade all buckets to S3 provisioned IOPS to achieve better performance.
   - `correct` Change the trigger level to around 3000 as S3 can now accommodate much higher PUT and GET levels.
   - Set up multiple accounts so that the per account hard limit on S3 buckets is avoided.
   
   > Until 2018 there was a hard limit on S3 puts of `100` PUTs per second. To achieve this care needed to be taken with __the structure of the name Key to ensure parallel processing__. As of July 2018 the limit was raised to 3500 and the need for the Key design was basically eliminated. Disk IOPS is not the issue with the problem. The account limit is not the issue with the problem. Further information: 
   > 
   > - https://aws.amazon.com/about-aws/whats-new/2018/07/amazon-s3-announces-increased-request-rate-performance/
   > - https://docs.aws.amazon.com/AmazonS3/latest/dev/request-rate-perf-considerations.html
   > - https://aws.amazon.com/s3/storage-classes/

#### storage class; what fits what

1. What is the availability of S3-OneZone-IA?
   
   __99.50%__ 99.90% 100% 99.99%
   
   > OneZone-IA is only stored in one Zone. While it has the same Durability, it may be less Available than normal S3 or S3-IA. Further information: https://aws.amazon.com/s3/storage-classes/?nc=sn&loc=3

2. A company currently store data on-premise. They are looking to migrate to AWS S3 and to store their data in buckets. Each bucket will be named after their individual customers, followed by a random series of letters and numbers. Once written to S3 the data is **rarely changed**, as it has already been sent to the end customer for them to use as they see fit. However, on some occasions, customers may need certain files **updated quickly**, and this may be for work that has been done months or even years ago. **You would need to be able to access this data immediately to make changes in that case, but you must also keep your storage costs extremely low**. The data is not easily reproducible if lost. Which S3 storage class should you choose to minimize costs and to maximize retrieval times?

3. You work for a major news network in Europe. They have just released a new mobile app that allows users to post their photos of newsworthy events in real-time, which are then reviewed by your editors before being copied to your website and made public. Your organization expects this app to grow very quickly, essentially doubling its user base each month. The app uses S3 to store the images, and you are expecting sudden and sizable increases in traffic to S3 when a major news event takes place (as users will be uploading large amounts of content.) You need to keep your storage costs to a minimum, and it does not matter if some objects are lost. With these factors in mind, which storage media should you use to keep costs as low as possible?
   
   > > Answer is: __S3 - One Zone-IA__

##### cost of retrieval from Glacier

You have been asked to set up a **recovery process** that generates the **lowest possible cost** for **retrieving information from Glacier**. There is petabytes of information that need to be retrieved if this process is to be enacted. Which of the following retrieval options would allow you to achieve this?

> It dependents on the speed and size of the data is request

- Expedited retrievals allow you to **quickly** access your data stored in the S3 Glacier storage class when occasional urgent requests for a **subset** of archives are required, but at the **highest** cost. 

- Standard retrievals allow you to access any of your archived objects **within several hours**, this is faster than bulk (averaging around 12 hours) but more expensive. 

- Bulk retrievals are the lowest-cost retrieval option in Amazon S3 Glacier, enabling you to **retrieve large amounts**, even petabytes, of data inexpensively. 

- Further information: https://docs.aws.amazon.com/AmazonS3/latest/user-guide/restore-archived-objects.html

#### others

1. How many S3 buckets can I have per account by default?  => 100

## EC2

### Config

#### Using Boot Strap Scripts With EC2

> example

```bash
#!/bin/bash
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
echo "<html><h1>Hello World!</h1></html>" > /var/www/html/index.html
aws s3 mb s3://ajsdklfajsdlfjasl_asf2332
aws s3 cp /var/www/html/index.html s3://ajsdklfajsdlfjasl_asf2332
```

> Looks like this EC2 has the access right to S3 by default?

#### EC2 Instance Meta Data

- `curl http://169.254.169.254/latest/user-data` will get the boot strap script

- `curl http://169.254.169.254/latest/meta-data` will get a list of path.

- `curl http://169.254.169.254/latest/meta-data/public-ipv4`,  will get the public ip.

#### EC2 Placement Groups

- You cannot merge PG.
- You can move an instance into a PG via AWS CLI / SDK, only when the instance in the stopped state. (Not console yet.)

##### cluster placement group

- A group of instances within a ==single AZ==. Recommend homogenous instances within CPG.
- Only certain instances can be launched into a cluster placement group
- It's ideal when your fleet of EC2 instances requires high network throughput and low latency within a single availability zone.

##### Spread Placement Groups

- Spread instances to different hardware.
- Can be in same AZ or cross AZ. (But have to be ==same region==)
- Can Spread Placement Groups be deployed across multiple Availability Zones? __Yes.__

##### Partition Group

![IMG_B7FA8E69ED8F-1](2020-06-01-AWS-domain-knowledge.assets/IMG_B7FA8E69ED8F-1.jpeg)

#### EC2 Hibernate

![image-20200703172058333](2020-06-01-AWS-domain-knowledge.assets/image-20200703172058333.png)

- to use Hibernation, the root volume must be encrypted

![image-20200703172516872](2020-06-01-AWS-domain-knowledge.assets/image-20200703172516872.png)

> t2.micro inluded as well.

#### Spot Instances & Spot Fleet

Spot instance price history

![                         The Spot Instance pricing history tool in the Amazon EC2                             console.                     ](2020-06-01-AWS-domain-knowledge.assets/spot-instance-pricing-history.png)

- Good for
  
  - CI/CD; Testing
  - webservices
  - Big data and analytics
  - image and media rendering
  - containerized workload
  - high performance computing

- not good for 
  
  - Critical jobs
  - Persistent workload
  - DB

- You can block Spot Instances from terminating by using ==Spot Block==

##### Spot requests

![image-20200703171232802](2020-06-01-AWS-domain-knowledge.assets/image-20200703171232802.png)

##### Spot Fleet

![image-20200703171602197](2020-06-01-AWS-domain-knowledge.assets/image-20200703171602197.png)

you can have the following strategies with Spot Fleet

![image-20200703171542987](2020-06-01-AWS-domain-knowledge.assets/image-20200703171542987.png)

#### Hypervisor

- Hypervisor for EC2: `Nitro` and `Xen`

### [EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/?nc2=h_ql_prod_cp_ec2auto)

Amazon EC2 Auto Scaling helps you ==maintain application availability== and allows you to ==automatically add or remove EC2 instances according to conditions you define==. You can use the ==fleet management== features of EC2 Auto Scaling to maintain the health and availability of your fleet. You can also use the ==dynamic and predictive scaling== features of EC2 Auto Scaling to add or remove EC2 instances. ==Dynamic scaling== responds to changing demand and predictive scaling automatically schedules the right number of EC2 instances based on predicted demand. Dynamic scaling and predictive scaling can be used together to scale faster.

### EBS

Elastic Block Store (EBS) is an easy to use, high performance ==block storage service== designed for use with Amazon Elastic Compute Cloud (EC2) for both throughput and transaction intensive workloads at any scale.

- ==Termination Protection== is ==turned off== by default
  
  - Root volume will be deleted by default
  - Additional  colume would not
  
  > ( By default) If you turn off a EC2, what would happend to the root volume / addtional volume? 
  > 
  > Root one would be terminated as well; but additional ones will persistent.

- Can I delete a snapshot of an EBS Volume that is used as the root device of a registered AMI?
  
  > If the original snapshot was deleted, then the AMI would not be able to use it as the basis to create new instances. For this reason, AWS protects you from accidentally deleting the EBS Snapshot, since it could be critical to your systems. To delete an EBS Snapshot attached to a registered AMI, first remove the AMI, then the snapshot can be deleted

- Which AWS CLI command should I use to create a snapshot of an EBS volume?
  
  > `aws ec2 create-snapshot`

- Which of the following provide the lowest cost EBS options? =>  Cold (sc1) and Throughout Optimized (st1) types are HDD based and will be the lowest cost options.

![image-20200702180108477](2020-06-01-AWS-domain-knowledge.assets/image-20200702180108477.png)

#### volume types

The following table shows use cases and performance characteristics of current generation EBS volumes:

|                                | SSD                                                                                   | SSD                                                                                                      | HDD                                                                                  | HDD                                                                    |
|:------------------------------:|:-------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------:| ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| Volume Type                    | EBS Provisioned IOPS SSD (io1)                                                        | EBS General Purpose SSD (gp2)*                                                                           | Throughput Optimized HDD (st1)                                                       | Cold HDD (sc1)                                                         |
| Short Description              | Highest performance SSD volume designed for latency-sensitive transactional workloads | General Purpose SSD volume that balances price performance for a wide variety of transactional workloads | Low cost HDD volume designed for frequently accessed, throughput intensive workloads | Lowest cost HDD volume designed for less frequently accessed workloads |
| Price                          | ==\$0.125==/GB-month​ ==$0.065==/provisioned IOPS                                     | ==$0.10==/GB-month                                                                                       | $0.045/GB-month                                                                      | $0.025/GB-month                                                        |
| Volume Size                    | 4 GB - 16 TB                                                                          | 1 GB - 16 TB                                                                                             | ==500 GB== - 16 TB                                                                   | 500 GB - 16 TB                                                         |
| Use Cases                      | I/O-intensive NoSQL and relational databases                                          | Boot volumes, low-latency interactive apps, dev & test                                                   | Big data, data warehouses, log processing                                            | Colder data requiring fewer scans per day                              |
| Max IOPS**/Volume              | ==64,000==                                                                            | 16,000                                                                                                   | 500                                                                                  | 250                                                                    |
| Max Throughput***/Volume       | 1,000 MB/s                                                                            | 250 MB/s                                                                                                 | 500 MB/s                                                                             | 250 MB/s                                                               |
| Max IOPS/Instance              | 80,000                                                                                | Same                                                                                                     | Same                                                                                 | Same                                                                   |
| Max Throughput/Instance        | 2,375 MB/s                                                                            | Same                                                                                                     | Same                                                                                 | Same                                                                   |
| API Name                       | io1                                                                                   | gp2                                                                                                      | st1                                                                                  | sc1                                                                    |
| Dominant Performance Attribute | IOPS                                                                                  | IOPS                                                                                                     | MB/s                                                                                 | MB/s                                                                   |

#### Volumes & Snapshots

1. region always be the same as the connected EC2. ( Of cause you want your hard disk be close to the compute)

2. You can change your volume (increase or decrease) on the fly ==even for the root device==! 
   
   > It's crazy. How?

3. Typical scenario: Your client want to move the root device EBS to another AZ. How?
   
   1. My guess: Make a Snapshot => make AMI from the Snapshot => copy the AMI to target region/AZ => Make a device from the Snapshot

4. Snapshots are incremental 

![image-20200702220450248](2020-06-01-AWS-domain-knowledge.assets/image-20200702220450248.png)

![image-20200702220356861](2020-06-01-AWS-domain-knowledge.assets/image-20200702220356861.png)

![image-20200702220432119](2020-06-01-AWS-domain-knowledge.assets/image-20200702220432119.png)

#### Encrypted Root Device Volumes & Snapshots

![image-20200703165635604](2020-06-01-AWS-domain-knowledge.assets/image-20200703165635604.png)

#### How to encrypt an unencrypted instance

![image-20200703165709947](2020-06-01-AWS-domain-knowledge.assets/image-20200703165709947.png)

#### AMI Types (EBS vs Instance Store)

You can select your AMI based on:

- Region 

- OS 

- Launch Permissions

- Storage for the Root Device (Root Device Volume)
  
  - Instance Store ( Emphemeral Storage )
    
    > The root device for an instance launched from the AMI is an instance store volume created form a template stored in Amazon S3
  
  - EBS Backed Voumes
    
    > The root device for an instance launched from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot

### EFS - Elastic File System

> Like EBS, but you can connect it to multi-EC2

- consistency model: read after write 
- can support thousands of concurrent NFS connections
- only pay for the storage you use
- Data is stored across multiple AZ
- there is life-cycle that can move data to EFS-IA to save money.

#### [AWS EFS vs. AWS EBS: Which one should you use?]([https://n2ws.com/blog/aws-ebs-snapshot/aws-fast-storage-efs-vs-ebs#:~:text=While%20EFS%20does%20cost%20more,you%20pay%20for%20each%20volume.](https://n2ws.com/blog/aws-ebs-snapshot/aws-fast-storage-efs-vs-ebs#:~:text=While EFS does cost more,you pay for each volume.))

While both EBS and EFS offer great features, these two storage solutions are actually built for two completely different uses. EBS volumes are limited to a single instance, and, more importantly, then can only be accessed by one instance at a time. With EFS, you can have hundreds or thousands of instances accessing the file system simultaneously. This makes AWS EFS a great fit for any use that requires a decent performing centralized shared storage—uses like media processing or shared code repositories.

You can also use AWS EFS to serve web content, keep various backups, and reduce storage spending. While EFS does cost more than EBS ($0.30 per GB for EFS vs. $0.10 per GB for EBS), you only pay once per EFS file system. This means that if you attach a dozen instances to it, you will still pay the same amount as if you only had one instance attached to it. With EBS volumes, you pay for each volume. Therefore, to save money on storage, EFS can sometimes serve as a replacement for EBS.

EFS scales performance along with capacity, and, while this can be very beneficial in some cases, it can also be a significant drawback. You might not have high enough utilization to reach the desired throughput of the file system. Because AWS EBS provides you with steady and predictable performance, EBS is almost always be a better fit, unless you require that multiple instances access your storage at the same time,

### FSx for Windows & FSx for Lustre

> Amazon FSx for Windows File Server provides fully managed, highly reliable, and scalable file storage that is accessible over the industry-standard Server Message Block (SMB) protocol. It is built on Windows Server, delivering a wide range of administrative features such as user quotas, end-user file restore, and Microsoft Active Directory (AD) integration. It offers single-AZ and multi-AZ deployment options, fully managed backups, and encryption of data at rest and in transit. You can optimize cost and performance for your workload needs with SSD and HDD storage options; and you can scale storage and change the throughput performance of your file system at any time. Amazon FSx file storage is accessible from Windows, Linux, and MacOS compute instances and devices running on AWS or on premises. 

#### Windows FSx vs. EFS

![IMG_02DE09A3BFFB-1](2020-06-01-AWS-domain-knowledge.assets/IMG_02DE09A3BFFB-1.jpeg)

#### Lustre FSx vs. EFS

![IMG_B47331459B4E-1](2020-06-01-AWS-domain-knowledge.assets/IMG_B47331459B4E-1.jpeg)

![IMG_44C6C6DDF000-1](2020-06-01-AWS-domain-knowledge.assets/IMG_44C6C6DDF000-1.jpeg)

#### How to chose: EFS vs. Windows FSx vs. Lustre FSx

![IMG_3F2E828D8AD7-1](2020-06-01-AWS-domain-knowledge.assets/IMG_3F2E828D8AD7-1.jpeg)

### ENI vs ENA vs EFA

#### Elastic Network Interface - Essentially a virtual network card

![image-20200703164432712](2020-06-01-AWS-domain-knowledge.assets/image-20200703164432712.png)

#### Enhanced Networking

![image-20200703164608843](2020-06-01-AWS-domain-knowledge.assets/image-20200703164608843.png)

- No additional charge! 

- use where you want good network performance ( inter-instance )

- Depending on your instance type, Enhanced Networking can be enabled using:

![image-20200703165200858](2020-06-01-AWS-domain-knowledge.assets/image-20200703165200858.png)

#### Elastic Fabric Adapter

> for Machine learning, HPC (high performance computing)

![image-20200703165346014](2020-06-01-AWS-domain-knowledge.assets/image-20200703165346014.png)

#### How to chose

![image-20200703165433281](2020-06-01-AWS-domain-knowledge.assets/image-20200703165433281.png)

### CloudWatch

![IMG_165B3C07248C-1](2020-06-01-AWS-domain-knowledge.assets/IMG_165B3C07248C-1.jpeg)

- on EC2 normally 5 mins; turning on ==detailed monitoring== 1 min intervals ( non-free tier )
- CloudWatch alarm example: "CPU > 90% in 3 mins out of 10mins".
- CloudTrail knows who did what. CloudWatch knows how heavy are their burden.

### HPC - High Performance Computing

#### Data transfer

- Snowball, Snowmobile 

- AWS ==DataSync== to store on S3, EFS, FSx for Windows, etc

- ==Direct Connect==
  
  ![IMG_FA470DB95D37-1](2020-06-01-AWS-domain-knowledge.assets/IMG_FA470DB95D37-1.jpeg)

- 

#### Compute and Network

![IMG_B1C1BF4DD001-1](2020-06-01-AWS-domain-knowledge.assets/IMG_B1C1BF4DD001-1.jpeg)

#### Storage

![IMG_20BDF76A5BE9-1](2020-06-01-AWS-domain-knowledge.assets/IMG_20BDF76A5BE9-1.jpeg)

#### Orchestration and automation

##### AWS Batch

![IMG_369E0E517DB3-1](2020-06-01-AWS-domain-knowledge.assets/IMG_369E0E517DB3-1.jpeg)

##### AWS ParallelCluster

![IMG_0435B989DD42-1](2020-06-01-AWS-domain-knowledge.assets/IMG_0435B989DD42-1.jpeg)

### WAF - Web Application Firewall

- Let you monitor the HTTP and HTTPS requests that are forwarded to ==Amazon CloudFront==, and Application Load Balancer or ==API Gateway==.

- Also lets you control access to your content.

- You can configure conditions such as what IP are allowed to make the request or what query string parameters need to be passed.

At its most basic level, allows 3 different behaviours:

- ==Allow== all requests except the ones you specify
- ==Block== all requests except the ones you specify
- Count the requests that match the properties you specify

![IMG_FF44B5F1965C-1](2020-06-01-AWS-domain-knowledge.assets/IMG_FF44B5F1965C-1.jpeg)

##### Application examples

- your country embargos a country, how do you achieve that? WAF is one solution. you can block request from a specific country.

- How to block malicious IP addresses?
  
  - Use WAF
  - Use Network ACLs
  - 

### Q&A

- Will an Amazon EBS root volume persist independently from the life of the terminated EC2 instance to which it was previously attached? In other words, if I terminated an EC2 instance, would that EBS root volume persist? 
  
  > Yes - Unless 'Delete on Termination' is not unchecked for the volume

- You need to know both the private IP address and public IP address of your EC2 instance. You should ________.
  
  > Retrieve the instance Metadata from http://169.254.169.254/latest/meta-data/.

- What feature allows to utilize `SR-IOV`? =>  **Enhanced Networking**
  
  > SR-IOV, or Single Root I/O Virtualization, is a feature of **Enhanced Networking** used to provide higher networking performance. On a normal EC2 instance, multiple EC2 instances may share a single physical network interface on the EC2 Host. SR-IOV effectively dedicates the interface to a single instance, and bypasses parts of the Hypervisor, allowing for better performance Further information:

- Standard Reserved Instances can be moved between regions? __False__

- Is cfn-init a component of EC2 AS? 
  
  > No. cfn-init is not a component of the EC2 Autoscaling service. Instead it is a feature which allows commands to be run, and software installed/configured on EC2 instances when they launch.

- ![image-20200709012019615](2020-06-01-AWS-domain-knowledge.assets/image-20200709012019615.png)

## DB

### Databases 101

### Let's Create An RDS Instance

### RDS Backups, Multi-AZ & Read Replicas

### RDS Backups, Multi-AZ & Read Replicas - Lab

### DynamoDB

DynamoDB makes use of parallel processing to achieve predictable performance. You visualise each partition as an independent DB server of fixed size. Each responsible for a defined block of data. In SQL terminology it is called sharding. The documentation is specific about the SSDs, but makes no mention of read-replicas or EBS-Optimised. Caching in-front of DDB is an option (DAX), but it is not inherent to DDB.

### Advanced DynamoDB

### Redshift

### Aurora

### Elasticache

### Database Migration Service (DMS)

### Caching Strategies on AWS

### EMR Overview

### Migration

- Which AWS service would simplify the migration of a database to AWS?

A) AWS Storage Gateway 

B) AWS Database Migration Service (AWS DMS) 

D) Amazon AppStream 2.0

### Quiz

![Screen Shot 2020-06-27 at 13.26.11](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-27 at 13.26.11.png)

![Screen Shot 2020-06-21 at 15.37.46](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-21 at 15.37.46.png)

## Route 53

unable to health check: simple routing; 

### DNS 101

- ELBs don't have pre-defined IPv4 addresses; you resolve to them using a DNS name.

- Diff: Alias Record vs CNAME

- Common DNS Types:
  
  - NS Records; A Records;  CNAME;
  
  - SOA Records: Start of Authority record containing administrative information about the zone, especially regarding zone transfers.
  
  - MX Records: mail exchanger record. 
    
    > ```
    > Domain                TTL   Class    Type  Priority      Host
    > example.com.        1936    IN         MX       10         onemail.example.com
    > example.com.        1936    IN         MX       10         twomail.example.com
    > ```
  
  - PTR Records: opsite of A record. resolves an IP address to a domain or host name.

- Register domain name might take up 3 days.

### [choosing routing policies](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html)

- Available policies types?

- simple routing policy
  
  - One record with multiple IP addresses. 
  - If specify multiple values in a record, Route 53 returs all value to users in random order.
  
  > No health check. When you don't care much about availability or you only have one machine.

- Multivalue answer: simple routing +
  
  - with health check on each record.

- weighted Routing policy
  
  - You set multiple records with weight values and Route 53 splits traffic based on weight. 
  - support health check and auto ignore unhealthy nodes
  - can set SNS norification for failure on health check

- Latency routing

![Screen Shot 2020-06-22 at 16.21.00](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-22%20at%2016.21.00.png)

![Screen Shot 2020-06-22 at 16.23.09](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-22%20at%2016.23.09.png)

- Failover routing
  
  - primary and secondary instances: Auto failover

- Geolocation routing
  
  - geography boundary based routing.
  - scenario: region price/legal/language diffrence. 

- Geoproximity routing (traffic flow only)
  
  - Highly customizable. Highly complicated.

### others

Alias record: 

#### ![Screen Shot 2020-06-22 at 17.03.42](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-22%20at%2017.03.42.png)

## VPCs

> SA-A are expected to be able to build a VPC by memory

### VPC general topic

- When you create a custom VPC, a default Security Group, Access control List, and Route Table are created automatically. You must create your own subnets, Internet Gateway, and NAT Gateway (if you need one.)

- By default, how many VPCs am I allowed in each AWS Region -- 5

- By default, instances in new subnets in a custom VPC can communicate with each other across Availability Zones.
  
  > In a custom VPC with new subnets in each AZ, there is a Route that supports communication ==across all subnets/AZs==. Plus a ==Default SG with an allow rule 'All traffic, All protocols, All ports, from anything using this Default SG'==.

- You can create a ==public-facing subnet== for your webservers that has access to the Internet, and place your backend systems such as databases or application servers in a ==private-facing subnet== with no Internet access. You can leverage multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet. 

- You can create a Hardware Virtual Private Network (VPN) cnnection between your corporate datacenter and your VPC and leverage the AWS cloud as an extension of your corporate datacenter.

- Security Group does not span accross VPCs

![image-20200704111310363](2020-06-01-AWS-domain-knowledge.assets/image-20200704111310363.png)

> Network ACL serves as first sec layer. 

#### subnet

- IP for subnet
  
  - 10 0 0.0 - 10.255 255 255 (10/8 prefix)
  - 172.16.0.0 - 172 31.255 255 (172.16/12 prefix)
  - 192.168.0.0 - 192.168.255.255 (192.168/16 prefix) 

- `/28` is the smallest subnet (16) you are allowed to use in AWS VPC.

- A subnet must be in ==1 AZ==

- 5 IP addresses are reserved:

![image-20200707150644678](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200707150644678.png)

#### What can we do with a VPC?

- Launch instances into a subnet of your choosing 
- Assign custom IP address ranges in each subnet 
- Configure route tables between subnets 
- Create intenet gateway and attach it to our VPC 
- Much better security control over your AWS resources 
- Instance security groups 
- Subnet network access control lists (ACLS) 

#### Default VPC vs Custom VPC

- Default VPC is user friendly, allowing you to immediately deploy instances.
- All Subsets in default VPC ==have a route out== to the internet. 
- Each EC2 instance has both a public and private IP address. 

#### VPC Peering

- connect one VPC with another via a direct network route using private IP addresses. 

- Instances behave as if they were on the same private network

- You can peer VPC's with other ==AWS accounts== as well as with other VPCs in the same account.
  
  >  ?? Peering is in a star configuration: ie 1 central VPC peers with 4 others. 

- ??  When you create a VPC a default Route Table, Network Access Control List (NACL) and a default Security Group. It won't create any ==subnets==, nor will it create a default ==internet gateway==. 

- US-East-1A in your AWS account can be a completely different availability zone to US-East-1A in another AWS account. The ==AZ's are randomized==. 

- Amazon always reserve 5 IP addresses within your subnets. (first 4 and the last)

- You can only have ==1 Internet Gateway per VPC==. 

- Allows you to connect one VPC with another via a direct network route using private IP addresses. 

- Instances behave as if they were on the same private network • You can peer VPC's with other AWS accounts as well as with other VPCs in the same account. 

- Peering is in a star configuration: ie 1 central VPC peers with 4 others. NO ==TRANSITIVE PEERING==!!! 

- You can peer ==across regions==. 

#### ELB on VPC

- you need at least 2 public subnet to create a LB.

#### Pen test on VPC

- Are you permitted to conduct your own vulnerability scans on your own VPC without alerting AWS first?
  - Depends on the type of scan and the service being scanned. Some scans can be performed without alerting AWS, some require you to alert. Until recently customers were not permitted to conduct Penetration Testing without AWS engagement. However that has changed. There are still conditions however.

### Practice - Build A Custom VPC

1. Creating a custom VPC
- When you create a VPC, a default Route Table, Network Access Control List (NACL) and a default Security Group is created.
- It won't create any subnets, nor will it create a default internet gateway.

![Screen Shot 2020-07-07 at 14.59.42](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/Screen%20Shot%202020-07-07%20at%2014.59.42.png)

2. create subnet

![image-20200707150425011](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200707150425011.png)

![image-20200707150743226](2020-06-01-AWS-domain-knowledge.assets/image-20200707150743226.png)

By default, any subnet will be associated to ==Main Route Table== if not explicitly associated with a route table.

Default Route Table is public accessable?

3. create a IGW and attach it to VPC
   
   > Note that 
   > 
   > 1. only one IGW per VPC.
   > 2. IGW are design (by AWS) to be aways available.

4. Create a Route table name "MyPublicRouteTable"  
   
   - Route table is inside a VPC
   - Adding public access :
   
   ![image-20200707152438453](2020-06-01-AWS-domain-knowledge.assets/image-20200707152438453.png)
   
   ==> 
   
   ![image-20200707152335060](2020-06-01-AWS-domain-knowledge.assets/image-20200707152335060.png)

5. We create two EC2 instances: `MyWebServer` in public subnet and `MyDBServer` in private subnet.

> We have the IP address for the first one, but we cannot access the one in private subnet.

Create a security group called `MyDBSG`

![image-20200707152836475](2020-06-01-AWS-domain-knowledge.assets/image-20200707152836475.png)

After accosiate this SG to the `MyDBServer`, now we can SSH from `MyWebServer` to `MyDBServer`. 

> Though in this lab we simply pass the private key as auth. It's best to use bastion host to avoid storing key in server. Will be discussed later.

Now we can SSH to `MyDBServer`. But if we try `yum update` we will have a timeout. That's because it's in private subnet.

Next section is `NAT Instance` and `NAT gateway` which will help to solve this. 

### Internet Gateway

- Egress-Only Internet Gateway

The purpose of an "Egress-Only Internet Gateway" is to allow IPv6 based traffic within a VPC to access the Internet, whilst denying any Internet based resources the possibility of initiating a connection back into the VPC.

- what is the purpose on an virtual IG?

### Access Control Lists (ACL)

#### Lab - create a NACL

1. Create `MyWebNACL` in a VPC
   
   > By default, all inbound and outbound traffic are ==DENY==
   
   All subnet would be associated with Default ACL.

2. Associate a public subnet with `MyWebNACL` which is currently DENY everything. 
   
   Check connecting to an instance in this subnet, it should fail as timeout.

3. Add rules on both in inbound and outbound traffic on HTTP, HTTPS and SSH.
   
   > Note that we also allow the `Ephemeral port`. And AWS NAT Gateway use 1024-65535 as Ephemeral Ports range.

![IMG_ABDE9268B993-1](2020-06-01-AWS-domain-knowledge.assets/IMG_ABDE9268B993-1.jpeg)

4. Try adding a DENY rule to reject port `80` as `Rule # 400`, it will not deny. Try same rule with number `99` will deny.
   
   ==The smaller `#` rule wins.==

5. ACL act before security groups.
- Your VPC automatically comes with a default network ACL, and by default it allows all outbound and inbound traffic. 
- You can create custom network ACLs. By default, each custom network ACL denies all inbound and outbound traffic until you add rules. 
- Each subnet in your VPC must be associated with a network ACL. If you don't explicitly associate a subnet with a network ACL, the subnet is automatically associated with the default network ACL. 
- Block IP Addresses using network ACLs not Security Groups 

#### Base points

- VPC automatically comes with a default network ACL 
  
  > by default it ==allows all== outbound and inbound traffic. 

- You can create custom network ACLs. 
  
  > by default, custom network ACL ==denies all== inbound and outbound traffic. 

- Each subnet in your VPC ==must be associated with a network ACL==. If you don't explicitly associate a subnet with a network ACL, the subnet is automatically associated with ==the default== network ACL. 

- Block IP Addresses using network ACLs not Security Groups. 

- `1-N ACL-subnet ` You can associate a network ACL with ==multiple subnets==; however, a subnet can be associated with only one network ACL at a time. 
  
  > When you associate a network ACL with a subnet, the previous association is removed.

- Network ACLs contain a numbered list of rules that is evaluated in order, ==starting with the lowest numbered rule.== 
  
  > ?? does the later override the previous?

- Network ACLs have separate inbound and outbound rules, and each rule can either allow or deny traffic. 

- Network ACLs are ==stateless==; responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa.) 

- 

### Security Groups

- regional

- allowing one inbound rule auto allows one outbound rule ( `Stateful` )

- DB type SG auto sets the port

- Cannot block specific IP addresses. Can specify allow rules, but not deny rules. (Deny by default)
  
  > instead use Network Access Control Lists (ACL)

- By default, all inbound traffic is `blocked` and all outbound traffic is allowed.

- Change take effect immediately.

- Security groups are ==stateful== — if you send a request from your instance, the response traffic for that request is allowed to flow in regardless of inbound security group rules. Responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules.

![Screen Shot 2020-07-03 at 14.34.44](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-07-03 at 14.34.44.png)

### Network Address Translation (NAT)

#### Create NAT Instance

> In order to download software, the private subnet need to communicate with IGW.
> 
> `NAT Gateway` and `NAT Instances` are to solve this issue. 
> 
> `NAT Gateway` are ==HA==, while  `NAT Instances` ( slight outdated ) are ==EC2 instances and might fail==. 

1. Create an EC2 instance call `NAT_Instance` by NAT AMI 

2. Disable ==source and destination check== for this instance
   
   > By default, EC2 instances do this check and forbid request that source or destination is not itself. But NAT Instances acting as gateway so we have to disable this check.

3. Add route that, for any out reaching destination, target  `NAT_Instance`.
   
   > By this config, our `NAT_Instance` acts as a bridge between private subnet and public subnet inorder to reach IGW.

![IMG_9E675FDE0D22-1](2020-06-01-AWS-domain-knowledge.assets/IMG_9E675FDE0D22-1.jpeg)

- When creating a NAT instance, Disable Source/Destination Check on the Instance. 
- ==NAT instances== must be in a ==public== subnet. 
- There must be a ==route out of the private subnet to the NAT instance==, in order for this to work. 
- The amount of ==traffic== that NAT instances can support depends on the ==instance size==. If you are bottlenecking, increase the instance size. 
- You can create ==high availability using Autoscaling Groups==, multiple subnets in different AZs, and a script to automate failover. 
- behind a SG

#### NAT Instances summary

- Single point of failure: Lost of subnet instances depend on it.

- Can be performance bottleneck: can auto scale and script to set rout

- When creating a NAT instance, Disable Source/Destination Check on the Instance. 

- NAT instances must be in a public subnet. 

- There must be a route out of the private subnet to the NAT instance, in order for this to work. 

- The amount of traffic that NAT instances can support depends on the instance size. If you are bottlenecking, increase the instance size. 

- You can create high availability using Autoscaling Groups, multiple subnets in different AZs, and ==a script to automate failover==. 

- Behind a Security Group. 

- If you have resources in multiple Availability Zones and they share one NAT gateway, in the event that the NAT gateway's Availability Zone is down, resources in the other Availability Zones lose internet access.
  
  To create an ==Availability Zone-independent architecture==, create a NAT gateway in each AZ and configure your routing to ensure that ==resources use the NAT gateway in the same AZ.== 

#### Create NAT Gateway

- Create a NAT Gateway:
  - in public subnet
  - create new EIP ( elastic IP ) and attach it to it.
- Add Route in Main Route Table: `0.0.0.0/0`  to this NAT-G

Now private-subnet instances can access to internet by this NAT-G

![image-20200707154721725](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/NAT-Gateway.png)

#### NAT Gateway summary

- HA: redendant inside the AZ  

- Redundant inside the Availability Zone 

- Preferred by the enterprise 

- Starts at 5Gbps and scales currently to 45Gbps 

- No need to patch  

- Automatically assigned a public ip address 

- Remember to update your route tables. 

- No need to disable Source/Destination Checks 

- ==Not associated with security groups==

### VPC Flow Logs

#### What it is

VPC Flow Logs is a feature that enables you to capture information about the IP ==traffic going to and from network interfaces in your VPC==. 

Flow log data is stored ==using Amazon CloudWatch Logs==. After you've created a flow log, you can view and retrieve its data in Amazon CloudWatch Logs. 

- Flow logs can be created at 3 levels
  
  - VPC
  - subnet 
  - Network Interface Level
  
  > Down to the ENI as well; But not ==Instance level==

#### Create one

1. Go to CloudWatch, create a Log group: `VPCFlowLogs`

2. Go to VPC, select one VPC, hit `create flow log`,
   
   we have options: 
   
   - Filter `[All, Accept, Reject]` on traffic type.
   - Destination [to S3, to CloudWatch Logs]
   - Destination log group, we just created it in step 1
   - IAM role. 

#### Some IP Traffic is not monitored:

- Traffic generated by instances when they contact the Amazon DNS server. 
  
  > If you use your own DNS server, then all traffic to that DNS server is logged. 

- Traffic generated by a Windows instance for Amazon Windows license activation. 

- Traffic to and from 169.254.169.254 for instance metadata.

- DHCP traffic. 

- Traffic to the reserved IP address for the default VPC router. 

#### Tips

- You cannot enable flow logs for a VPC that is not in your account
- You can tag flow logs
- You cannot change the IAM role of a flow log. You set it when you create it, that's it.

### Bastions

A bastion host is a special purpose computer on a network specifically designed and configured to ==withstand attacks==. The computer ==generally hosts a single application, for example a proxy server==, and ==all other services are removed or limited to reduce the threat to the computer==. It is hardened in this manner primarily due to its location and purpose, which is either on the outside of a firewall or in a demilitarized zone (DMZ) and usually involves access from untrusted networks or computers. 

![image-20200707170652084](2020-06-01-AWS-domain-knowledge.assets/image-20200707170652084.png)

- A NAT Gateway or NAT Instance is used to provide internet traffic to EC2 instances in a private subnets. 

- A Bastion is used to securely administer EC2 instances (Using SSH or RDP). 

- Bastions are called ==Jump Boxes== in Australia. 

- You cannot use a NAT Gateway as a Bastion host. 

### Direct Connect

#### What it is

AWS Direct Connect is a cloud service solution that makes it easy to establish a ==dedicated== network connection from your premises to AWS. Using AWS Direct Connect, you can ==establish private connectivity between AWS and your datacenter, office, or colocation environment==, which in many cases can ==reduce your network costs==, increase bandwidth ==throughput==, and provide a more consistent network experience than Internet-based connections.

![Derect-Connect-Visualization](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/Derect-Connect-Visualization.png)

#### Base point

- Direct Connect ==directly connects your data center to AWS==
- Useful for ==high throughput== workloads (ie lots of network traffic) 
- Useful when you need a ==stable and reliable secure== connection. 

#### Setting Up A VPN Over A Direct Connect Connection - [Official Video](https://www.youtube.com/watch?v=dhpTTT6V1So&feature=youtu.be)

![Steps-Setting-Up-Direct-Connect](2020-06-01-AWS-domain-knowledge.assets/Steps-Setting-Up-Direct-Connect.png)

### Global Accelerator

![How-GA-Works](2020-06-01-AWS-domain-knowledge.assets/How-GA-Works.png)

#### Base points

- By default, it provides you two __static IP address__; you can also bring your own.
- `Traffic dial`: For each endpoint group, you can set a traffic dial to control the percentage of traffic that is directed to the group.  ( Like weighted routing policy I assume. )
- `Network Zone`: isolated unit with its own set of physical infrastructure which is used to provide global accelerator services.
- Can also do weighted routing in a group

#### [FAQ](https://aws.amazon.com/global-accelerator/faqs)

##### ELB vs. GA

 ==ELB== provides load balancing ==within one Region==; AWS Global Accelerator provides traffic management ==across Regions==.

##### Benefits

- Instant regional failover

- HA

- No variability around clients that cache IP addresses

- Lower latency
  
  ![image-20200708155724673](2020-06-01-AWS-domain-knowledge.assets/image-20200708155724673.png)

### VPC End Points -- [Doc](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html)

There are two types of VPC endpoints: __interface endpoints__ and __gateway endpoints__. 

> Pick the type depends on the supported service.

#### Interface endpoints (powered by [AWS PrivateLink)](https://aws.amazon.com/privatelink/)

> Seems every AWS services support Inteface endpoint except two: ==S3 and DynamoDB== 

#### Gateway endpoints

A [gateway endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-gateway.html) is a gateway that ==you specify as a target for a route== in your route table for traffic destined to a supported AWS service. The following AWS services are supported:

- Amazon S3
- DynamoDB

Using Gateway endpoints, you can do the following transformation: 

<img src="2020-06-01-AWS-domain-knowledge.assets/image-20200708161729617.png" alt="image-20200708161729617" height="250" />  <img src="2020-06-01-AWS-domain-knowledge.assets/image-20200708161817017.png" alt="image-20200708161817017" height="250" />

By using VPC Gateway, you can stay in AWS cloud and communicate with these services without going through internet.

![VPC-Endpoint-example](2020-06-01-AWS-domain-knowledge.assets/VPC-Endpoint-example.png)

#### VPC best practices

> Because these best practices might not be appropriate or sufficient for your environment, treat them as helpful considerations rather than prescriptions.

- Use __multiple Availability Zone__ for HA
- Use SG and network ACLs. 
- Use IAM policies to control access.
- Use Amazon CloudWatch to monitor your VPC components and VPN connections.
- Use flow logs to capture information about IP traffic going to and from network interfaces in your VPC. 

## HA Architecture

### Load Balancers And Health Checks

#### Cross Zone Load Balancing

- enables you to load balance across ==multiple AZs==. 

<img src="https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200708172237533.png" alt="image-20200708172237533" style="zoom:50%;" />

#### Path Based routing

==Path patterns== allow you to direct traffic to different EC2 instances based on the ==URL== contained in the request. 

#### Sticky Sessions

It enable your users to stick to the same EC2 instance. Can be useful if you are storing information locally to that instance. 

- Only ALB and classical LB support this feature because [it is implemented by cookie](https://stackoverflow.com/questions/46912629/aws-network-load-balancing-session-stickiness-not-consistent).
  - ALB will stick the traffic to `Target Group Level`
  - CLB will stick to instance.

### Autoscaling

#### Price

There is no additional charge for AWS Auto Scaling. You pay only for the AWS resources needed to run your applications and [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) monitoring fees.

![image-20200708172705641](2020-06-01-AWS-domain-knowledge.assets/image-20200708172705641.png)

> 3 components: Group; Lauch Configuration ( or, Template --- AMI ID, instance type, key pair, SG ......);  Options

#### Functions

- **Monitor the health of running instances**
  
  Amazon EC2 Auto Scaling ensures that your application is able to receive traffic and that EC2 instances are working properly. Amazon EC2 Auto Scaling periodically performs health checks to identify any instances that are unhealthy.

- **Replace impaired instances automatically**
  When an impaired instance fails a health check, Amazon EC2 Auto Scaling automatically terminates it and replaces it with a new one. That means that you don’t need to respond manually when an instance needs replacing.

- **Balance capacity across Availability Zones**
  Amazon EC2 Auto Scaling can automatically balance instances across zones, and always launches new instances so that they are balanced between zones as evenly as possible across your entire fleet.

#### Scaling options

#### Dynamic Scaling

Scaling base on policy you set. Sey CPU utilization, or, you could set a target value using the new “Request Count Per Target” metric from Application Load Balancer.

##### Scheduled Scaling

Dynamic Scaling with policy on calendar. 

For example, every week the traffic to your web application starts to increase on Wednesday, remains high on Thursday, and starts to decrease on Friday. You can plan your scaling activities based on the known traffic patterns of your web application.

##### Predictive Scaling

ML-powered fancy thing.

#### Practice Lab

1. Create a Launch Configuration

2. Create an AS group
   
   > It starts working

3. You can check the `Activity Status`

4. When you delete a AS group, all the instances created by it will auto terminated

### HA Architecture

![image-20200708175823934](2020-06-01-AWS-domain-knowledge.assets/HA-example.png)

![image-20200708180036045](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/HA-quiz.png)

Answer is 3 AZ with 3 instances. 

### HA WebSite Lab -- WordPress

![image-20200708180345280](2020-06-01-AWS-domain-knowledge.assets/image-20200708180345280.png)

1. Create S3 Bucket
2. Create CloudFront Distribution
3. Create SG: `WebServer`, `DB` ( open the port for MySQL 3306 )
4. Create RDS Instance
   1. SG
   2. VPC
   3. Name
5. WP EC2 istance

#### Setting Up EC2

##### URL rewrite

1. In `htaccess` file, you can config URL `rewriterule` so that your website serves CloudFront/S3 urls rather than local storage files.

> Get the CloudFront url by combining it's domainname 

2. Config Apache to allow URL rewrite: edit  `/etc/httpd/httpd.conf`
   
   ![image-20200708182810662](2020-06-01-AWS-domain-knowledge.assets/image-20200708182810662.png)

3. Bucket policy update
   
    ![image-20200708183006522](2020-06-01-AWS-domain-knowledge.assets/image-20200708183006522.png)

### Adding Resilience And Autoscaling

![image-20200708195716076](2020-06-01-AWS-domain-knowledge.assets/image-20200708195716076.png)

A writer node for editing content.

A fleet of nodes for reading.

1. config a read node

Using `crond` to schedual work automatically

- edit `etc/crontab` 

![image-20200708195922019](2020-06-01-AWS-domain-knowledge.assets/image-20200708195922019.png)

`--delete` will delete the deleted files and make a perfect copy.

2. create an AMI from the __read node__ we just config
3. config a write node

![image-20200708200756230](2020-06-01-AWS-domain-knowledge.assets/image-20200708200756230.png)

This config does two things:

- sync the code to S3-code bucket

- sync the content to S3-media bucket
4. create an AMI from the __write node__ we just config

### RDS auto failover accross AZ

### CloudFormation

#### Create a Stack - Lab

1. Choose a Template

2. Fill in all specification

3. Config review
   
   ![image-20200708202630306](2020-06-01-AWS-domain-knowledge.assets/image-20200708202630306.png)

4. Here is the event log

![image-20200708202559280](2020-06-01-AWS-domain-knowledge.assets/image-20200708202559280.png)

Try [AWS Quick Starts](https://aws.amazon.com/quickstart/)

### Elastic Beanstalk

Elastic Beanstalk v.s LightSail

Developers describe **Amazon LightSail** as "*Simple Virtual Private Servers on AWS*". Everything you need to jumpstart your project on AWS—compute, storage, and networking—for a low, predictable price. Launch a virtual private server with just a few clicks. 

On the other hand, **AWS Elastic Beanstalk** is detailed as "*Quickly deploy and manage applications in the AWS cloud*". Once you upload your application, Elastic Beanstalk automatically handles the deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring.

#### Example

![image-20200708210006280](2020-06-01-AWS-domain-knowledge.assets/image-20200708210006280.png)

You can also config it

![image-20200708210101616](2020-06-01-AWS-domain-knowledge.assets/image-20200708210101616.png)

You only need to upload the code. And it will anto setup and grow to fit capacity need.

### Q&A

- ==Yes== Can I "force" a failover for any RDS instance that has Multi-AZ configured?

- ==NO==  When you have deployed an RDS database into multiple availability zones, can you use the secondary database as an independent read node?

- the likelihood that a resource will work as designed -- ==Reliability==

- the likelihood that a resource will continue to exist until you decide to remove it -- ==Durability==

- the likelihood that you can access a resource or service when you need it ==Availability==

- A product manager walks into your office and advises that the simple single node MySQL RDS instance that has been used for a pilot needs to be upgraded for production. She also advises that they may need to alter the size of the instance once they see how many people use the system during peak periods. The key concern is that there can not be any outages of more than a few seconds during the go-live period. What would you recommend?
  
  - Convert the RDS instance to a multi-AZ implementation.
  
  - Consider replacing it with Aurora before go live.
    
    > There are two issues to be addressed in this question.
    > 
    > - ==Minimizing outages==, whether due to required maintenance or unplanned failures. 
    > 
    > - the ==possibility of needing to scale up or down==. 
    > 
    > - Read-replicas can help you with high read loads, but are not intended to be a solution to system outages. 
    > 
    > - Multi-AZ implementations will increase availability because ==in the event of a instance outage one of the instances in another AZs will pick up the load with minimal delay.== 
    > 
    > - Aurora provided the ==same capability with potentially higher availability and faster response.==

## Architecture Topics

### Event-Driven Architecture

An event-driven architecture ==uses events to trigger and communicate== between ==decoupled services== and is common in modern applications built with microservices. ==An event is a change in state==, or an update, like an item being placed in a shopping cart on an e-commerce website. Events can either ==carry the state== (the item purchased, its price, and a delivery address) or events ==can be identifiers== (a notification that an order was shipped).

Event-driven architectures have three key components: ==event producers, event routers, and event consumers==. 

- A producer publishes an event to the router, which filters and pushes the events to consumers. 
- Producer services and consumer services are decoupled, which allows them to be scaled, updated, and deployed independently.

![1-SEO-Diagram_Event-Driven-Architecture_Diagram](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/1-SEO-Diagram_Event-Driven-Architecture_Diagram.b3fbc18f8cd65e3af3ccb4845dce735b0b9e2c54-20200708224946647.png)

#### Benefit

- Scale and fail independently

By decoupling your services, they are only aware of the event router, not each other. This means that your services are interoperable, but if one service has a failure, the rest will keep running. The event router acts as an elastic buffer that will accommodate surges in workloads.

- Develop with agility

You no longer need to write custom code to poll, filter, and route events; the event router will automatically filter and push events to consumers. The router also removes the need for heavy coordination between producer and consumer services, speeding up your development process.

- Audit with ease

An event router acts as a centralized location to audit your application and define policies. These policies can restrict who can publish and subscribe to a router and control which users and resources have permission to access your data. You can also encrypt your events both in transit and at rest.

- Cut costs

Event-driven architectures are push-based, so everything happens on-demand as the event presents itself in the router. This way, you’re not paying for continuous polling to check for an event. This means less network bandwidth consumption, less CPU utilization, less idle fleet capacity, and less SSL/TLS handshakes.

#### To think about

- The durability of your event source. Your event source should be reliable and guarantee delivery if you need to process every single event. 
- Your performance control requirements. Your application should be able to handle the ==asynchronous nature== of event routers. 
- Your event flow tracking. The indirection introduced by an event-driven architecture allows for dynamic tracking via monitoring services, but not static tracking via code analysis. 
- The data in your event source. If you need to rebuild state, your event source should be deduplicated and ordered.

[How to Use Amazon EventBridge to Build Decoupled, Event-Driven Architectures -- 7 Demos](https://pages.awscloud.com/AWS-Learning-Path-How-to-Use-Amazon-EventBridge-to-Build-Decoupled-Event-Driven-Architectures_2020_LP_0001-SRV.html?&trk=ps_a134p000003yBd8AAE&trkCampaign=FY20_2Q_eventbridge_learning_path&sc_channel=ps&sc_campaign=FY20_2Q_EDAPage_eventbridge_learning_path&sc_outcome=PaaS_Digital_Marketing&sc_publisher=Google)

### Dead-Leter Queue (DLQ)

![image-20200708223639854](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/image-20200708223639854.png)

![image-20200708223747231](2020-06-01-AWS-domain-knowledge.assets/image-20200708223747231.png)

### Fanout Pattern

### S3 Event Notification

## Application

### SQS - - Simple Queue Service

- SQS is a way to de-couple your infrastructure SQS is pull based, not pushed based. 

- Messages size are up to ==256 KB==.
  
  - It's not a hard limit, you can increase it. 
  - But then the message will be stored in S3

- ==retention period==:  can be ==1 minute to 14 days==; by ==default is 4 days==. 

- ==Visibility Time Out== is the amount of time that the message is invisible in the SQS queue after a reader picks up that message. ==Maximun is 12 hours==
  
  > Provided the job is processed before the visibility time out expires, the message will then be deleted from the queue. 
  > 
  > If the job is not processed within that time, the message will become visible again and another reader will process it. This could result in the same message being delivered twice. 

- Long polling vs. short polling
  
  - Long polling would not return a response untill a message arrives in the queue, or untill time out.
  - Short polling returns immidiately.
  - For an almost empty queue, using short polling would cost unnecessary money.

- Standard SQS vs FIFO SQS
  
  - Standard: order is not guaranteed and messages can be delivered more than once. 
  - FIFO: order is strictly maintained and messases are delivered only once. 
    - TPS limit: ==300==

> With standard SQS / FIFO SQS, how to ensure a message is processed once and only once?

#### FAQ

Q: Do Amazon SQS batch operations cost more than other requests?

No. Batch operations ([SendMessageBatch](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessageBatch.html), [DeleteMessageBatch](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessageBatch.html), and [ChangeMessageVisibilityBatch](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibilityBatch.html)) all cost the same as other Amazon SQS requests. ==By grouping messages into batches, you can reduce your Amazon SQS costs.==

Q: What can I do with the Amazon SQS Free Tier?

The Amazon SQS Free Tier provides you with ==1 million requests== per month at no charge.

### SWF

> Kind of a human-computer mix task version of SQS
> 
> Amazon use it in their warehouse.

#### SWF vs SQS

- Amazon SWF presents a ==task-oriented== API,  
  
  > SQS offers a ==message-oriented== API. 

- SWF, workflow execution, can last up to ==1 year== 
  
  > SQS has a retention period of ==up to 14 days==;

- Amazon SWF ensures that ==a task is assigned only once== ( never duplicated )
  
  > With Amazon SQS, you need to ==handle duplicated== messages and may also need to ensure that a message is processed only once. 

- Amazon SWF ==keeps track== of all the tasks and events in an application. 
  
  > With Amazon SQS, you need to implement your own ==application-level tracking==, ==especially== if your application uses ==multiple queues==. 

#### Actors

- Workflow Starters — An application that can initiate (start) a workflow. Could be your e-commerce website following the placement of an order, or a mobile app searching for bus times. 
- Deciders — Control the flow of activity tasks in a workflow execution. If something has finished (or failed) in a workflow, a Decider decides what to do next. 
- Activity Workers — Carry out the activity tasks. 

### SNS - Simple Notification Service

#### Benefits

- Instantaneous, ==push==-based delivery (no polling) 

- Simple APIs and easy integration with applications

- Flexible message delivery over multiple transport protocols 
  
  ==SMS, email, SQS message, calling any HTTP endpoint==

- Inexpensive, pay-as-you-go model with no up-front costs 

- Web-based AWS Management Console offers the simplicity of a point-and-click interface 

- HA -All msg stored multi AZ.

#### Topic

==Topic== is an "access point" for allowing recipients to dynamically subscribe for identical copies of the same notification.

One topic can support multiple endpoint type, e.g. iOS, Android and SMS. When you publish to a topic, SNS deliver appropriately formated copies to each subscriber.

### Elastic Transcoder

A media transcoder in the cloud. It converts media files from their original source format in to different formats that will play on smartphones, tablets, PCs, etc. 

### API Gateway

#### What it is

Amazon API Gateway is a ==fully managed service== that makes it easy for developers to ==create, publish, maintain, monitor, and secure APIs== at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services. Using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. API Gateway supports containerized and serverless workloads, as well as web applications.

API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including ==traffic management==, ==CORS== support, authorization and ==access control==, ==throttling==, monitoring, and API version management. API Gateway has no minimum fees or startup costs. You pay for the API calls you receive and the amount of data transferred out and, with the API Gateway tiered pricing model, you can reduce your cost as your API usage scales.

![image-20200708215037062](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/How-API-Gateway-Works.png)

#### What can it do?

- Expose ==HTTPS endpoints== to define a RESTful API 
- support ==cashing== to increase performance
- Maintain multiple ==versions== of your API 
- Send each API endpoint to a ==different target== 
- HA - auto scale 
  - ==Serverless-ly== connect to services like Lambda & DynamoDB 
- ==Throttle== requests to prevent attacks
- Connect to ==CloudWatch to log== all requests for monitoring 
- Track and control usage by API key
- Run efficiently with ==low cost== 

> - ==Enable CORS== to support JS/AJAX that use multiple domains

#### Deployment

- to a stage
  - use API Gateway domain, by default
  - can use custom domain
  - now supports AWS Certificate Manager: free SSL/TLS certs

#### Related topic

- CORS Cross-origin-resource-sharing
  - Is a mechanism that allows restriced resources (e.g fonts) on a web page to be requested from another domain outside the domain from which the first resource was served.
  - The server can relax the same-origin policy. 
- Same-origin policy 

![Screen Shot 2020-06-22 at 23.22.33](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-22 at 23.22.33-3234626.png)

### Kinesis

![Screen Shot 2020-06-22 at 23.11.57](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-22 at 23.11.57.png)

#### What Is Streaming Data?

Streaming Data is data that is generated continuously by thousands of data sources, which typically send in the data records simultaneously, and in small sizes (order of Kilobytes.)

> Purchases from online stores (think amazon.com)
> Stock Prices
> Game data (as the gamer plays)
> Social network data
> Geospatial data (think uber.com)

Firehose 

> Kind of consumes it right away. 

![Screen Shot 2020-06-27 at 13.04.33](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-22 at 23.13.59.png)

### Web Identity Federation & Cognito

Web Identity Federation lets you give your users access to AWS resources after they have successfully authenticated with a web-based identity provider like Amazon, Facebook, or Google.

Following successful authentication, the user receives an authentication code from the Web ID provider, which they can trade for temporary AWS security credentials.

Amazon Cognito provides Web Identitfy Federation with the following features:

- ==Sign-up and sign-in== to your apps
- Access for ==guest users==
- Acts as an ==Identity Broker== ==between your application and Web ID providers==, so you don't need to write any additional code.
- ==Synchronizes user data for multiple devices==
- Recommended for ==all mobile applications== running ==AWS services==
- Cognito is the recommended approach for Web Identity Federation using social media accounts like Facebook.

Cognito Brokers between app and Facebook or Google to provid==e temporary credentials== which map to an IAM role allowing access to the required resources.

No need for the application to embed or store AWS credentials locally on the device and it gives the users a seamless experience across all mobile devices.

It use SNS for ==Push Synchronization== to push update on user data cross multiple devices.

![image-20200708223118267](2020-06-01-AWS-domain-knowledge.assets/image-20200708223118267.png)

#### [Official Doc](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc.html)

> Imagine that you are creating a mobile app that accesses AWS resources, such as a game that runs on a mobile device and stores player and score information using Amazon S3 and DynamoDB.
> 
> When you write such an app, you'll make requests to AWS services that must be signed with an AWS access key. However, we **strongly** recommend that you ==do **not** embed or distribute long-term AWS credentials with apps== that a user downloads to a device, even in an encrypted store. Instead, build your app so that it requests temporary AWS security credentials dynamically when needed using *web identity federation*. The supplied ==temporary credentials== map to an AWS role that has only the permissions needed to perform the tasks required by the mobile app.

#### Case study: [Identifying Users and doing S3 access control with Web Identity Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc_user-id.html)

### Quiz

## Security

### Reducing Security Threats

### Key Management Service (KMS)

![image-20200708230423514](2020-06-01-AWS-domain-knowledge.assets/image-20200708230423514.png)

![image-20200708230448212](2020-06-01-AWS-domain-knowledge.assets/image-20200708230448212.png)

![image-20200708230602564](2020-06-01-AWS-domain-knowledge.assets/image-20200708230602564.png)

![image-20200708230735672](2020-06-01-AWS-domain-knowledge.assets/image-20200708230735672.png)

### CloudHSM - hardware security module

- Dedicated ==hardware security module== (HSM)

- generate&manage your own encryption keys with ==FIPS 140-2== ==Level 3==  ( level 2 is KMS )

- Run within a VPC

- industry-standard APIs --- no AWS APIs
  
  > such as `PKCS#11`, Java Cryptography Extensions (JCE), and Microsoft CryptoNG (CNG) libraries.

- ==standards-compliant== and enables you to export all of your keys to most other commercially-available HSMs, subject to your configurations. 

- fully-managed

- scale quickly by ==adding and removing HSM capacity on-demand==, with no up-front costs.

- If you lose your key, it's ==irretrievable==.

![CloudHSM_Diagrams_2-final](2020-06-01-AWS-domain-knowledge.assets/CloudHSM_Diagrams_2-final.6f427ebb14d021b9cd6120aeee72cf4d3723e89b.png)

A: AWS manages the hardware security module (HSM) appliance, but ==does not have access to your keys==

B: You control and manage your own keys

C: Application performance improves (due to close proximity with AWS workloads)

D: Secure key storage in tamper-resistant hardware available in multiple Availability Zones (AZs)

E: Your HSMs are in your Virtual Private Cloud (VPC) and isolated from other AWS networks.

![image-20200708231847679](2020-06-01-AWS-domain-knowledge.assets/image-20200708231847679.png)

#### Use cases

##### Offload the SSL processing for web servers

### Parameter Store

![image-20200708231949527](2020-06-01-AWS-domain-knowledge.assets/image-20200708231949527.png)

- Set TTL

Paras by Hierachies

![image-20200708232111878](2020-06-01-AWS-domain-knowledge.assets/image-20200708232111878.png)

![image-20200708232543693](2020-06-01-AWS-domain-knowledge.assets/image-20200708232543693.png)

example

![image-20200708232840094](2020-06-01-AWS-domain-knowledge.assets/image-20200708232840094.png)

You can store encrypted data. Then grant your reader function e.g lambda, access to KMS and use the key to decrypt the data.

### Secrets Manager

- secrete example: DB cridential, API keys and 

![image-20200708233319228](2020-06-01-AWS-domain-knowledge.assets/image-20200708233319228.png)

### AWS Shield

![image-20200708233521981](2020-06-01-AWS-domain-knowledge.assets/image-20200708233521981.png)

AWS Shield Standard defends against most common, frequently occurring network and transport layer DDoS attacks that target your web site or applications. ==FREE==

AWS Shield Advanced is available globally on all Amazon CloudFront, AWS Global Accelerator, and Amazon Route 53 edge locations. You can protect your web applications hosted anywhere in the world by deploying Amazon CloudFront in front of your application. ==3000$==

### Web Application Firewall (AWS WAF)

![image-20200708233842595](2020-06-01-AWS-domain-knowledge.assets/image-20200708233842595.png)

A front layer to detect and filter out basic attack?

Configure ==filtering rules== to allow/deny traffic

- IP address
  
  > Another way is ACL

![image-20200708234140624](2020-06-01-AWS-domain-knowledge.assets/image-20200708234140624.png)

#### AWS Firewall Manager

![image-20200708234234752](2020-06-01-AWS-domain-knowledge.assets/image-20200708234234752.png)

### Q&A

1. ![image-20200709005956338](2020-06-01-AWS-domain-knowledge.assets/image-20200709005956338.png)

2. ![image-20200709012952132](2020-06-01-AWS-domain-knowledge.assets/image-20200709012952132.png)

## Serverless

### What are them?

DynamoDB;  API Gateway; S3; Amazon Cognito; 

SQS/SNS/Kinesis

CodeCommit;

**Amazon EventBridge**

Amazon EventBridge is a serverless event bus that makes it easy to connect applications together using data from your own applications, Software-as-a-Service (SaaS) applications, and AWS services.

**AWS Fargate**

AWS Fargate is a compute engine for Amazon ECS that allows you to run containers without having to manage servers or clusters. 

**AWS Serverless Application Model (SAM)**

AWS SAM is an ==open-source framework for building serverless applications== using ==simple and clean syntax==. 

### Lambda

#### Concepts

![image-20200708234431079](2020-06-01-AWS-domain-knowledge.assets/image-20200708234431079.png)

#### Use case

![image-20200708234557803](2020-06-01-AWS-domain-knowledge.assets/image-20200708234557803.png)

![image-20200708234646560](2020-06-01-AWS-domain-knowledge.assets/image-20200708234646560.png)

Traditional HA Architecture v.s Serverless

![image-20200708234737296](2020-06-01-AWS-domain-knowledge.assets/image-20200708234737296.png)

- Langs it supports: Node.js`, `Java`, `C#`, `Go`, `Python`, `PowerShell`

- Price: #ofRequest & Duration & RAM usage

![image-20200708234943579](2020-06-01-AWS-domain-knowledge.assets/image-20200708234943579.png)

> Lambda billing is based on both The MB of RAM reserved and the execution duration in 100ms units.

- Benefit: No servers; Auto scale; ==Super Cheap== testified by `ACloudGuru`

- ==X-Ray== help you to debug

#### Trigger

ALB, Cognito, Lex, Alexa, API Gateway, CloudFront, and Kinesis Data Firehose are all valid direct (synchronous) triggers for Lambda functions. 

S3 is one of the valid asynchronous triggers.

### Case study --- Let's Build A Serverless Webpage

0. Architecture

![image-20200709000009663](2020-06-01-AWS-domain-knowledge.assets/image-20200709000009663.png)

1. Creat first Lambda function
   
   ![image-20200709000149971](2020-06-01-AWS-domain-knowledge.assets/image-20200709000149971.png)
   
   Support runtime env:
   
   ![image-20200709000233191](2020-06-01-AWS-domain-knowledge.assets/image-20200709000233191.png)
   
   1. Create a Role with policy template `Simple microservice permissions` 

2. Configuration
   
   1. Desiner
      
      Trigger: API Gateway
      
      > S3, SQS and SNS can do it as well.
   
   2. Code
      
      Fill this part with your code
   
   3. Configure Trigger

This ACloudGur tutorial is very cool. 

### Let's Build An Alexa Skill

Really cool.

### Serverless Application Model (SAM)

### Elastic Container Service (ECS)

#### What is ECS

![Screen Shot 2020-06-27 at 13.02.53](2020-06-01-AWS-domain-knowledge.assets/Screen Shot 2020-06-27 at 13.02.53.png)

#### Components

- Cluster
  - Logical collection of ECS resources — either ECS EC2 instances or Fargate instances
- Task Definition
  - Defines your application. Similar to a Dockerfile but for running containers in ECS. Can contain multiple containers.
- Container Definition
  - Inside a task definition, it defines the individual containers a task uses. Controls CPU and memory allocation and port mappings.
- Task
  - Single running copy of any containers defined by a task definition. One working copy of an application (e.g., DB and web containers).
- Service
  - Allows task definitions to be scaled by adding tasks. Defines minimum and maximum values.
- Registry
  - Storage for container images (e.g., Elastic Container Registry (ECR) or Docker Hub). Used to download images to create containers.

#### Related topics

##### Containers and Docker

### QUIZ

1. ![image-20200709004743494](2020-06-01-AWS-domain-knowledge.assets/image-20200709004743494.png)

A 500x increase is beyond the scope of a well designed single server system to absorb unless it is already hugely over-specialised to accommodate this sort of burst load. An AWS solution for this situation might include S3 static web pages with client side scripting to meet high demand of information pages. Plus use of a noSQL database to collect customer registration for asynchronous processing, and SQS backed by scalable compute to keep up with the requests. Lightsail does provide a scalable provisioned service solutions, but these still need to be designed an planned by you and so offer no significant advantage in this situation. A standby server is a good idea, but will not help with the anticipated 500x load increase.

## Combined

### Lightsail

Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan. Whether you’re new to the cloud or looking to get on the cloud quickly with AWS infrastructure you trust, we’ve got you covered.

![image-20200706115719181](2020-06-01-AWS-domain-knowledge.assets/image-20200706115719181.png)

### [Amplify](https://aws.amazon.com/amplify)

#### Develop App

![product-page-diagram_Amplify_How-it-works_1@2x](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/product-page-diagram_Amplify_How-it-works_1@2x.3b8b3286597fd65126095c47c579d7d5905468be.png)

#### Host Web App

![product-page-diagram_Amplify_How-it-works_2@2x](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/product-page-diagram_Amplify_How-it-works_2@2x.0a34bb88a6ea331eaef43e115d6f736fa42c3eff.png)

## overview/ biz

- Which AWS offering enables users to find, buy, and immediately start using software solutions in their AWS environment?  => AWS Marketplace

- Which service can identify the user that **made the API call** when an Amazon EC2 instance is terminated?  A) AWS Trusted Advisor B) __AWS CloudTrail __C) AWS X-Ray
  
  > AWS `CloudTrail` helps users enable **governance, compliance, and operational and risk auditing** of their AWS accounts. Actions taken by a user, role, or an AWS service are recorded as events in `CloudTrail`. Events include actions taken in the AWS Management Console, AWS Command Line Interface (CLI), and AWS SDKs and APIs.

- [AWS shared responsibility model]()
  
  - AWS responsibility __“Security of the Cloud”__
  - Customer responsibility __“Security in the Cloud”__

#### Q&A

![image-20200709010827575](2020-06-01-AWS-domain-knowledge.assets/image-20200709010827575.png)

## Q&A

- what is store data `on-premise` ?

> On-**Premises Data Storage**
> 
> The term "on **premises**" refers to local hardware, meaning **data** is **stored** on local servers, computers or other devices. For example, a company may purchase a server on which to **store data**. After buying the server, the company sets it up at their headquarters and uploads their **data**.
