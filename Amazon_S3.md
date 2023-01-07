# AWS Cloud Practitioner

## [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

* *Definition* - Amazon Simple Storage Service (S3) is an object storage service

---

## Features

### [Storage classes](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html)

* S3 Standard
* S3 One Zone-IA
* S3 Glacier Instant Retrieval
* S3 Glacier Flexible Retrieval
* S3 Glacier Deep Archive

### Storage management

* [S3 Lifecycle](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html)
* [S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html)
* [S3 Replication](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html)
* [S3 Batch Operations](https://docs.aws.amazon.com/AmazonS3/latest/userguide/batch-ops.html)

### Access management

* S3 Block Public Access
* AWS Identity and Access Management (IAM)
* Bucket policies
* Amazon S3 access points
* Access control lists (ACLs)
* S3 Object Ownership
* Access Analyzer for S3

### Data processing

* S3 Object Lambda
* Event notifications

### Storage logging and monitoring

* Automated monitoring tools
  * Amazon CloudWatch metrics for Amazon S3
  * AWS CloudTrail
* Manual monitoring tools
  * Server access logging
  * AWS Trusted Advisor

### Analytics and insights

* Amazon S3 Storage Lens
* Storage Class Analysis
* S3 Inventory with Inventory reports

### Strong consistency

* S3 provides strong read-after-write consistency for PUT and DELETE requests of objects in your Amazon S3 bucket in all AWS Regions. This behavior applies to both writes of new objects as well as PUT requests that overwrite existing objects and DELTE requests. In addition, read operations on Amazon S3 Object Tags, and object metadata (for example, the HEAD object) are strongly consistent. For more information, see Amazon S3 data consistency model.*

---

## How Amazon S3 works

### Storage classes

An *object* is a file and any metadata that describes the file.
A *bucket* is a container for objects.

1. Create the bucket
2. Specify a bucket name
3. Specify a bucket region
4. Upload your data to the bucket.

* Each object has a *key* (or *key name*) which is a unique identifier for the object within the bucket.
* S3 provides versioning support to allow you to backup and restore objects that are deleted or overwritten.
* Buckets and the objects in them are private and may only be accessed if you grant access permissions.
  * Bucket Policies
  * AWS Identity and Access Management (IAM)
  * access control lists (ACLs)
  * S3 Access Points to manage access

---

## Buckets

* You may have up to 100
* After 100 you must request an increase from the Service Quotas Console
* All objects are contained within buckets.
* Are given a name and region, which cannot be changed afterwards
* Every object can be unqiuely addressed through a URL

### S3 Versioning

* May be used to keep variants of an object in the same bucket.
* Easily recover from failures or deletions

### Version ID

* Must be enabled
* Generates a unique version ID for each bucket added to the bucket.
* Objects that already existed when you enable versioning have a version ID of *null*
* If you modify these objects they will receive a version ID

### Bucket policy

* Resource-based AWS Identity and Acess Management policy that you can use to grant access permissions to your bucket and objects within it.
* Only the owner can associate a policy to a bucket
* Permissions attached to a bucket apply to all objects within the bucket that are owned by the bucket owner.
* Use JSON based language
* May use wildcard characters with Amazon Resource Names (ARNs) to grant permissions

### S3 Access Points

* Named network endpoint
* Describes how data can be accessed
* Attached to buckets
* Simplify managing data access at scale
* Each access point has its own policy
* May be restricted to accept requests only from a VPC

### Access control lists (ACLs)

* Grant read/write permissions to authorized users for individual buckets and objects.
* Each bucket has an ACL attached as a subresource
* The ACL defines which AWS accounts or groups are granted access and the type of access
* ACLs predate IAM and resource policies
* A majority of modern use cases in Amazon S3 no longer require the use of ACLs

### Regions

* Objects stored in a region never leave the region unless you explicitly tranfer or replicate them to another Region.

### S3 Data Consistency model

* Strong read-after-write consistency
* Read operations on Amazon S3 Select, Amazon S3 ACLs, Amazon S3 Object Tags and metadata are strongly consistent
* Updates are atomic
* Bucket configurations have an eventual consistency model.
* If you delete a bucket and immediately list all buckets, the deleted bucket might still appear in the list.
* If you enable versioning on a bucket for the first time, it might take a short amount of time for the change to be fully propogated
