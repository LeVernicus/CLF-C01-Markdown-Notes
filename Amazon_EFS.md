# Amazon Elastic File System (EFS)

* Serverless fully elastic file storage without managing storage capacity or performance
* Accessible to EC2, ECS, EKS, Fargate, Lambda
* Strong consistency
* EFS storage is ideal for workloads requiring highest levels of durability and availability
* EFS One Zone storage classes are ideal for workloads such as development

## When should I use EFS vs EBS vs S3

* EFS is for use with EC2 and on-premise
* EFS provides strong consistency and file locking, concurrently accesible storage
* EBS is for workloads which require lowest latency access to data from a single EC2 instance
* S3 makes data available through an API that can be accessed anywhere.

### How can I start using EFS?

* EFS may be created through the console, AWS CLI, or EFS API

### How do I access a file system from an EC2 instance?

* Using a Linux EC2 instance
  * Use the mount command
  * Attach the file system using the DNS name
* Recommended to use the Amazon EFS mount helper utility.
* EFS uses the Network File System version 4 (NFS V4) protocol.

### How do I manage a file system?

* Amazon EFS infrastructure is fully managed.
* You may manage EFS through the console, API, and SDK

### How do I load data into a file system?

* [AWS DataSync](https://aws.amazon.com/datasync/) provides a fast way to securely sync existing file systems with Amazon EFS.
* Including AWS Direct Connect or AWS VPN. EFS DataSync and Direct Connect without Amazon or AWS.

## Scale and Performance

### How much data can I store?

* You can store petabytes of data with EFS

### How many EC2 instances can connect to a file system?

* Amazon EFS supports one to thousands of EC2 instances

### How many file systems, mount targets, or access points can I create?

* Visit the [Amazon EFS Limits page](https://docs.aws.amazon.com/efs/latest/ug/limits.html#limits-efs-resources-per-account-per-region) for more information on Amazon EFS limits

### What latency, throughput, and IOPS performance can I expect for my EFS file system?

* It depends on the configuration, storage class and throughput model.

### What throughput modes are available for my file system?

* By default, Amazon EFS is built to provide throughput that scales with the amount of storage in your file system and supports bursting to higher levels for up to 12 hours a day.
* For throughput-intensive workloads EFS offers two options:
  * Elastic Throughput
  * Provisioned Throughput
* Use Elastic throughput if you're unsure of your applications throughput needs or still very spiky with low baseline activity.
* Elastic throughput scales with your workload and you only pay for what you use
* Provisioned throughput expects a workload to consume a higher share of your application's peak throughput capacity.
* Provisioned thorughput is designed to offer high levels of consistency with predictable billing

### How do I monitor my read and write throughput usage?

#### [Amazon Cloudwatch](https://aws.amazon.com/cloudwatch/)

* TotalIOBytes
* ReadIOBytes
* WriteIOBytes
* MetadataIOBytes
* All metrics reflect the actual throughput your applications are driving.

### How will I be billed in Elastic Throughput mode?

* Billed for the amount of data transferred (reads and writes)
* If you access Infrequent Access storage class you also pay the IA data access charge

### How will I be billed in Provisioned Throughput mode?

* In Provisioned Throughput mode you're billed independently for storage used and provisioned.
* Billed hourly in dimensions
  * Storage (per GB-month)
  * Throughput (per MB/second-month)

### What happens to my burst credits when I switch to Elastic Throughput?

* You do not accure or consume your burst credits in Elastic Throughput

### What is the throughput of my file system if the Provisioned Throughput mode is set to less than the Baseline Throughput I am entitled to in Bursting Throughput mode?

* Your system may be alotted to default Bursting Throughput mode in that case if the baseline for Provisioned falls below Bursting Throughput.
* There is no additional charge

## Storage classes and lifecycle management

### What storage classes does Amazon EFS offer?

* EFS Standard
  * EFS Standard
  * EFS Standard-Infrequent Access
* One Zone
  * EFS One Zone
  * EFS One Zone-Infrequent Access

### How do I move files to EFS Standard-IA and EFS One Zone-IA?

* Enable Amazon EFS Lifecycle Management and choosing an age-off policy for your files.
* Lifecycle Management automatically moves your data from Standard to IA
* E.G. You may move files that have not been accessed after one day

### What is EFS Intelligent-Tiering?

* Designed to deliver automatic cost savings for workloads with changing access paterns.
* EFS Intelligent-Tiering uses EFS Lifecycle Management to monitor the access patterns of your workload.
* It automatically moves files that aren't accessed for the duration of the Lifecycle policy to their corresponding cost-optimized Infrequent Access storage class.
* If access patterns change and that data is accessed again, Lifecycle Management automatically moves the files back to EFS Standard/OneZone

### When should I use EFS Intelligent Tiering?

* When data access patterns are unknown.

### What Amazon EFS features are supported when using EFS Standard-IA and EFS One Zone-IA storage classes?

* All features are supported
* Files smaller than 128KiB are not eligible for Lifecycle Management and will always be stored as standard.

### What is the latency difference between the performance-optimized storage classes (EFS Standard, EFS One Zone) and the cost-optimized storage classes (EFS Standard-IA, EFS One Zone-IA)?

* For IA, your first-byte latency is higher than Standard or One Zone.
* IA classes are designed to provide double-digit ms latencies on average

### What throughput can I drive against files stored in the EFS Standard-IA or EFS One Zone-IA storage class?

* Under Bursting throughput mode, the throughput you drive against an Amazon EFS file system scales linearly with the amount of data stored.
* All EFS file systems regardless of size can burst to 100 MiB/s
* File systems more than 1TiB in size can burst to 100 MiB/s per TiB stored
* If you require higher amounts of throughput to EFS classes use Amazon EFS Elastic Throughput or Provisioned Throughput.

## Data Protection and availability

### How is Amazon EFS designed to provide high durability and availability?

* Every object is redundantly stored across AZs for file systems using Standard
* If you select One Zone, your data is redundantly stored within a single AZ
* A file system can be accessed concurrently from all AZs in that Region

### How durable is Amazon EFS?

* Standard storage classes are designed to sustain data if an AZ is lost
* One Zone is stored in a single AZ, so storage in these may be lost during disaster.
* Best practice is to have a backup, and put in place safeguards against accidental deltion.

### What failure modes should I consider when using Amazon EFS One Zone compared to standard?

* During an AZ outage, you will experience a loss of availability

### How can I guard my One Zone file system against the loss of an AZ?

* Use Amazon EFS Replication or AWS Backup
* Amazon EFS Replication replicates your file system to another Region or within the same Region
* Replication is nearly continuous and designed to provide a recovery point objective (RPO) and a recovery time Objective (RTO) of minutes

### What is Amazon EFS Replication?
