---
layout: post
title: "AWS SA-A review notes"
subtitle: ""
date: 2020-06-01 00:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - infrastructure
  - AWS
---

# SA-A blue print

## Domain 1: Design Resilient Architectures

1.   Design a multi-tier architecture solution
2.   Design highly available and/or fault-tolerant architectures
3.   Design decoupling mechanisms using AWS services
4.   Choose appropriate resilient storage

## Domain 2: Design High-Performing Architectures

1. Identify elastic and scalable compute solutions for a workload
2. Select high-performing and scalable **storage** solutions for a workload
3. Select high-performing **networking** solutions for a workload
4. Choosehigh-performing database solutions for a workload

## Domain 3: Design Secure Applications and Architectures

1 Design secure access to AWS resources 
2 Design secure application tiers
3 Select appropriate data security options

## Domain 4: Design Cost-Optimized Architectures

1. Identify cost-effective storages olutions
2. Identify cost-effective compute and database services 
3. Design cost-optimized network architectures



# Topics

## Management - Identity Access Management

![Screen Shot 2020-06-02 at 22.20.28](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-02%20at%2022.20.28.png)

Things I didn't know:

#### Features

- Supports PCI DSS compliance;
- Can be use for your users' management as well

? IAM integrates with **existing active directory** account allowing single sign-on.



- **Power User Access** allows Access to all AWS services except the management of groups and users within IAM.
- What is Resource Based Access Control List (ACL) 
- What is Setting up a cross account IAM Role for?

> An application you are working on has a new app. The development team for this app requires access to a bucket that is located within your team's aws account. The other team requires programmatic and console level access to your team's bucket. How would you share this bucket with this other team's account?
>
> [link](https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/)



### Q&A

- When updating the policy used by an IAM Role attached to an EC2 instance, what needs to happen for the changes to take effect?

  > Nothing - It will take effect immediately

## Storage - S3

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

### Storage Classes

> what are they? what features they have? cost? what fits what?

![Screen Shot 2020-06-04 at 14.07.03](https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/06/Screen%20Shot%202020-06-04%20at%2014.07.03.png)

#### Performance table

|                                    |      S3 Standard       | S3 Intelligent-Tiering* |     S3 Standard-IA     |    S3 One Zone-IA†     |       S3 Glacier        | S3 Glacier Deep Archive |
| :--------------------------------: | :--------------------: | :---------------------: | :--------------------: | :--------------------: | :---------------------: | :---------------------: |
|      Designed for durability       | 99.999999999% (11 9’s) | 99.999999999% (11 9’s)  | 99.999999999% (11 9’s) | 99.999999999% (11 9’s) | 99.999999999% (11 9’s)  | 99.999999999% (11 9’s)  |
|     Designed for availability      |         99.99%         |          99.9%          |         99.9%          |         99.5%          |         99.99%          |         99.99%          |
|          Availability SLA          |         99.9%          |           99%           |          99%           |          99%           |          99.9%          |          99.9%          |
|         Availability Zones         |           ≥3           |           ≥3            |           ≥3           |           1            |           ≥3            |           ≥3            |
| Minimum capacity charge per object |          N/A           |           N/A           |         128KB          |         128KB          |          40KB           |          40KB           |
|  Minimum storage duration charge   |          N/A           |         30 days         |        30 days         |        30 days         |         90 days         |        180 days         |
|           Retrieval fee            |          N/A           |           N/A           |    per GB retrieved    |    per GB retrieved    |    per GB retrieved     |    per GB retrieved     |
|         First byte latency         |    **milliseconds**    |    **milliseconds**     |    **milliseconds**    |    **milliseconds**    | select minutes or hours |      select hours       |
|            Storage type            |         Object         |         Object          |         Object         |         Object         |         Object          |         Object          |
|       Lifecycle transitions        |          Yes           |           Yes           |          Yes           |          Yes           |           Yes           |           Yes           |



#### data consistency model

- Amazon S3 provides **read-after-write** consistency for PUTS of new objects in your S3 bucket in all Regions with one caveat. `??` 
- Amazon S3 offers **eventual consistency** fo**r overwrite PUTS and DELETES** in all Regions.
- Updates to a single key are **atomic**. For example, if you PUT to an existing key, a **subsequent read** might return the old data or the updated data, but it **never** returns **corrupted or partial data**.
- 
- more "currently no"
  - object locking; race case need to be solved by application level
  - atomic updates across keys; need to design&implement our own on application level;

| Eventually consistent read | Consistent read                 |
| :------------------------- | :------------------------------ |
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

1. You run a popular photo-sharing website that depends on S3 to store content. Paid advertising is your primary source of revenue. However, you have discovered that other websites are linking directly to the images in your buckets, not to the HTML pages that serve the content. This means that people are not seeing the paid advertising, and you are paying AWS unnecessarily to serve content directly from S3. How might you resolve this issue?

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
   >
   



##### cost of retrieval from Glacier

You have been asked to set up a **recovery process** that generates the **lowest possible cost** for **retrieving information from Glacier**. There is petabytes of information that need to be retrieved if this process is to be enacted. Which of the following retrieval options would allow you to achieve this?

> It dependents on the speed and size of the data is request

- Expedited retrievals allow you to **quickly** access your data stored in the S3 Glacier storage class when occasional urgent requests for a **subset** of archives are required, but at the **highest** cost. 

- Standard retrievals allow you to access any of your archived objects **within several hours**, this is faster than bulk (averaging around 12 hours) but more expensive. 
- Bulk retrievals are the lowest-cost retrieval option in Amazon S3 Glacier, enabling you to **retrieve large amounts**, even petabytes, of data inexpensively. 
- Further information: https://docs.aws.amazon.com/AmazonS3/latest/user-guide/restore-archived-objects.html





#### others

1. How many S3 buckets can I have per account by default?  => 100
2. 
3. 
4. 
5. 
6. 
7. 
8. 



## storage - EBS

- Can I delete a snapshot of an EBS Volume that is used as the root device of a registered AMI?

  > If the original snapshot was deleted, then the AMI would not be able to use it as the basis to create new instances. For this reason, AWS protects you from accidentally deleting the EBS Snapshot, since it could be critical to your systems. To delete an EBS Snapshot attached to a registered AMI, first remove the AMI, then the snapshot can be deleted

- Which AWS CLI command should I use to create a snapshot of an EBS volume?

  > `aws ec2 create-snapshot`

- 

## Compute - EC2 (EBS), Lambda

### Spread Placement Groups

- Can Spread Placement Groups be deployed across multiple Availability Zones? __Yes.__



#### cluster placement group

- The use of a cluster placement group is ideal _______  

  > Your fleet of EC2 instances requires high network throughput and low latency within a single availability zone.

#### EBS

- Which of the following provide the lowest cost EBS options? =>  Cold (sc1) and Throughout Optimized (st1) types are HDD based and will be the lowest cost options.

#### Hypervisor

- Hypervisor for EC2: `Nitro` and `Xen`

- What feature allows to utilize `SR-IOV`? =>  **Enhanced Networking**

  > SR-IOV, or Single Root I/O Virtualization, is a feature of **Enhanced Networking** used to provide higher networking performance. On a normal EC2 instance, multiple EC2 instances may share a single physical network interface on the EC2 Host. SR-IOV effectively dedicates the interface to a single instance, and bypasses parts of the Hypervisor, allowing for better performance Further information:

### Q&A

- Will an Amazon EBS root volume persist independently from the life of the terminated EC2 instance to which it was previously attached? In other words, if I terminated an EC2 instance, would that EBS root volume persist? 

  > Yes - Unless 'Delete on Termination' is not unchecked for the volume

- You need to know both the private IP address and public IP address of your EC2 instance. You should ________.

  > Retrieve the instance Metadata from http://169.254.169.254/latest/meta-data/.

#### regions

- Standard Reserved Instances can be moved between regions? __False__

## DB

### migration

- Which AWS service would simplify the migration of a database to AWS?

A) AWS Storage Gateway 

B) AWS Database Migration Service (AWS DMS) 

D) Amazon AppStream 2.0



## Route 53

unable to health check: simple routing; 

### DNS 101

- ELBs don't have pre-defined IPv4 addresses; you resolve to them using a DNS name.

- Diff: Alias Record vs CNAME

- Common DNS Types:

  -  NS Records; A Records;  CNAME;

  - SOA Records: Start of Authority record containing administrative information about the zone, especially regarding zone transfers.

  - MX Records: mail exchanger record. 

    > ```
    > Domain			    TTL   Class    Type  Priority      Host
    > example.com.		1936	IN	     MX	   10         onemail.example.com
    > example.com.		1936	IN	     MX	   10         twomail.example.com
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

  



## Network

- Which AWS networking service enables a company to create a virtual network within AWS? => Amazon Virtual Private Cloud (Amazon VPC)
- What does CloudFront use to ensure **low-latency delivery**? => Edge locations

## overview/ biz

- Which AWS offering enables users to find, buy, and immediately start using software solutions in their AWS environment?  => AWS Marketplace

- Which service can identify the user that **made the API call** when an Amazon EC2 instance is terminated?  A) AWS Trusted Advisor B) __AWS CloudTrail __C) AWS X-Ray

  > AWS `CloudTrail` helps users enable **governance, compliance, and operational and risk auditing** of their AWS accounts. Actions taken by a user, role, or an AWS service are recorded as events in `CloudTrail`. Events include actions taken in the AWS Management Console, AWS Command Line Interface (CLI), and AWS SDKs and APIs.

- [AWS shared responsibility model]()

  - AWS responsibility __“Security of the Cloud”__
  - Customer responsibility __“Security in the Cloud”__

## Q&A

- what is store data `on-premise` ?

> On-**Premises Data Storage**
>
> The term "on **premises**" refers to local hardware, meaning **data** is **stored** on local servers, computers or other devices. For example, a company may purchase a server on which to **store data**. After buying the server, the company sets it up at their headquarters and uploads their **data**.