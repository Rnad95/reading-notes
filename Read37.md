# Read 37 - S3

## What is Amazon S3?

---

![s3](https://miro.medium.com/max/640/1*B9CIOrxdROHvtdmouQA1_A.png)

AWS Simple Storage Service (S3): From the aforementioned list, S3, is the object storage service provided by AWS. It is probably the most commonly used, go-to storage service for AWS users given the features like extremely high availability, security, and simple connection to other AWS Services. AWS S3 can be used by people with all kinds of use cases like mobile/web applications, big data, machine learning and many more.

## Terms

---
AWS S3 Terminology:

1. **Bucket:** Data, in S3, is stored in containers called buckets.

- Each bucket will have its own set of policies and configuration. This enables users to have more control over their data.
- Bucket Names must be unique.
- Can be thought of as a parent folder of data.
- There is a limit of 100 buckets per AWS accounts. But it can be increased if requested from AWS support.

2. **Bucket Owner:** The person or organization that owns a particular bucket is its bucket owner.

3. **Import/Export Station:**  A machine that uploads or downloads data to/from S3.

4. **Key:** Key, in S3, is a unique identifier for an object in a bucket. For example in a bucket ‘ABC’ your GFG.java file is stored at javaPrograms/GFG.java then ‘javaPrograms/GFG.java’ is your object key for GFG.java.

- It is important to note that ‘bucketName+key’ is unique for all objects.
- This also means that there can be only one object for a key in a bucket. If you upload 2 files with the same key. The file uploaded latest will overwrite the previously contained file.

5. **Versioning:**  Versioning means to always keep a record of previously uploaded files in S3. Points to note:

- Versioning is not enabled by default. Once enabled, it is enabled for all objects in a bucket.
- Versioning keeps all the copies of your file, so, it adds cost for storing multiple copies of your data. For example, 10 copies of a file of size 1GB will have you charged for using 10GBs for S3 space.
- Versioning is helpful to prevent unintended overwrites and deletions.
- Note that objects with the same key can be stored in a bucket if versioning is enabled (since they have a unique version ID).

6. **null Object:**Version ID for objects in a bucket where versioning is suspended is null. Such objects may be referred to as null objects.

7. **Object:**Fundamental entity type stored in AWS S3.

8. **Access Control Lists (ACL):** A document for verifying the access to S3 buckets from outside your AWS account. Each bucket has its own ACL.

9. **Bucket Policies:** A document for verifying the access to S3 buckets from within your AWS account, this controls which services and users have what kind of access to your S3 bucket. Each bucket has its own Bucket Policies.

10. **Lifecycle Rules:** This is a cost-saving practice that can move your files to AWS Glacier (The AWS Data Archive Service) or to some other S3 storage class for cheaper storage of old data or completely delete the data after the specified time.

## Features of Amazon S3

---

**Storage classes:**
Amazon S3 offers a range of storage classes designed for different use cases. For example, you can store mission-critical production data in S3 Standard for frequent access, save costs by storing infrequently accessed data in S3 Standard-IA or S3 One Zone-IA, and archive data at the lowest costs in S3 Glacier Instant Retrieval, S3 Glacier Flexible Retrieval, and S3 Glacier Deep Archive. These four access tiers include two low-latency access tiers optimized for frequent and infrequent access, and two opt-in archive access tiers designed for asynchronous access for rarely accessed data. For more information, see Using Amazon S3 storage classes. For more information about S3 Glacier Flexible Retrieval, see the Amazon S3 Glacier Developer Guide.

**Storage management:**

Amazon S3 has storage management features that you can use to manage costs, meet regulatory requirements, reduce latency, and save multiple distinct copies of your data for compliance requirements. S3 Lifecycle – Configure a lifecycle policy to manage your objects and store them cost effectively throughout their lifecycle. You can transition objects to other S3 storage classes or expire objects that reach the end of their lifetimes. You can use Object Lock to help meet regulatory requirements that require write-once-read-many (WORM) storage or to simply add another layer of protection against object changes and deletions. S3 Batch Operations – Manage billions of objects at scale with a single S3 API request or a few clicks in the Amazon S3 console. You can use Batch Operations to perform operations such as Copy, Invoke AWS Lambda function, and Restore on millions or billions of objects.

**Access management:**

Amazon S3 provides features for auditing and managing access to your buckets and objects. By default, S3 buckets and the objects in them are private. You have access only to the S3 resources that you create. To grant granular resource permissions that support your specific use case or to audit the permissions of your Amazon S3 resources, you can use the following features. AWS Identity and Access Management (IAM) – Create IAM users for your AWS account to manage access to your Amazon S3 resources. Bucket policies – Use IAM-based policy language to configure resource-based permissions for your S3 buckets and the objects in them.

**Data processing:**

To transform data and trigger workflows to automate a variety of other processing activities at scale, you can use the following features. S3 Object Lambda – Add your own code to S3 GET requests to modify and process data as it is returned to an application. Filter rows, dynamically resize images, redact confidential data, and much more. Event notifications – Trigger workflows that use Amazon Simple Notification Service (Amazon SNS), Amazon Simple Queue Service (Amazon SQS), and AWS Lambda when a change is made to your S3 resources.

**Storage logging and monitoring:**

Amazon S3 provides logging and monitoring tools that you can use to monitor and control how your Amazon S3 resources are being used. For more information, see Monitoring tools. Automated monitoring tools Amazon CloudWatch metrics for Amazon S3 – Track the operational health of your S3 resources and configure billing alerts when estimated charges reach a user-defined threshold. You can use server access logs for many use cases, such as conducting security and access audits, learning about your customer base, and understanding your Amazon S3 bill. You can then follow the recommendations to optimize your services and resources.

**Analytics and insights:**

Amazon S3 offers features to help you gain visibility into your storage usage, which empowers you to better understand, analyze, and optimize your storage at scale. S3 Storage Lens provides 29+ usage and activity metrics and interactive dashboards to aggregate data for your entire organization, specific accounts, AWS Regions, buckets, or prefixes. Storage Class Analysis – Analyze storage access patterns to decide when it's time to move data to a more cost-effective storage class. For example, you can report on the replication and encryption status of your objects. For a list of all the metadata available for each object in Inventory reports, see Amazon S3 Inventory list.

**Strong consistency:**

Amazon S3 provides strong read-after-write consistency for PUT and DELETE requests of objects in your Amazon S3 bucket in all AWS Regions. This behavior applies to both writes of new objects as well as PUT requests that overwrite existing objects and DELETE requests. In addition, read operations on Amazon S3 Select, Amazon S3 access control lists (ACLs), Amazon S3 Object Tags, and object metadata (for example, the HEAD object) are strongly consistent.

## How Amazon S3 works

---

Amazon S3 is an object storage service that stores data as objects within buckets. An object is a file and any metadata that describes the file. Then, you upload your data to that bucket as objects in Amazon S3. Each object has a key (or key name), which is the unique identifier for the object within the bucket. S3 provides features that you can configure to support your specific use case.

**Buckets:**

A bucket is a container for objects stored in Amazon S3. For example, if the object named photos/puppy.jpg is stored in the DOC-EXAMPLE-BUCKET bucket in the US West (Oregon) Region, then it is addressable using the URL `https://DOC-EXAMPLE-BUCKET.s3.us-west-2.amazonaws.com/photos/puppy.jpg`. 

For more information, see Accessing a Bucket. When you create a bucket, you enter a bucket name and choose the AWS Region where the bucket will reside. You can also configure a bucket to use S3 Versioning or other storage management features. Identify the account responsible for storage and data transfer charges.

**Objects:**

Objects are the fundamental entities stored in Amazon S3. Objects consist of object data and metadata. The metadata is a set of name-value pairs that describe the object. These pairs include some default metadata, such as the date last modified, and standard HTTP metadata, such as Content-Type. For more information about objects, see Amazon S3 objects overview.

**Keys:**

An object key (or key name) is the unique identifier for an object within a bucket. Every object in a bucket has exactly one key. Every object in Amazon S3 can be uniquely addressed through the combination of the web service endpoint, bucket name, key, and optionally, a version. For example, in the URL `https://DOC-EXAMPLE-BUCKET.s3.us-west-2.amazonaws.com/photos/puppy.jpg`, DOC-EXAMPLE-BUCKET is the name of the bucket and photos/puppy.jpg is the key. For more information about object keys, see Creating object key names.

**S3 Versioning:**

You can use S3 Versioning to keep multiple variants of an object in the same bucket. With S3 Versioning, you can preserve, retrieve, and restore every version of every object stored in your buckets. You can easily recover from both unintended user actions and application failures. For more information, see Using versioning in S3 buckets.

**Version ID:**
When you enable S3 Versioning in a bucket, Amazon S3 generates a unique version ID for each object added to the bucket.

**Bucket policy:**
A bucket policy is a resource-based AWS Identity and Access Management (IAM) policy that you can use to grant access permissions to your bucket and the objects in it.

For more information, see Managing data access with Amazon S3 access points.

Because S3 is strongly consistent, R1 and R2 both return color = ruby.

The following are the services that you might use most frequently: Amazon Elastic Compute Cloud (Amazon EC2) – Provides secure and scalable computing capacity in the AWS Cloud.

Amazon S3 REST API The architecture of Amazon S3 is designed to be programming language-neutral, using AWS-supported interfaces to store and retrieve objects.
