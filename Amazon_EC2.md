# Amazon Elastic Cloud Compute (EC2)

* Known as instances

* Various configurations known as instance types

* Secure login information using key pairs

* Storage voumes for temporary data known as *instance store volumes*

* Persistent storage voulmes for your data using Amazon Elastic Block Store (EBS)

* Metadata known as *tags* you can create and assign to EC2 resources

* Virtual networks you can create that are logically isolated from the rest of the AWS Cloud

## Instances and Amazon Machine Images (AMIs)

* An *AMI* is a template that contains a software configuration.

* Your AWS account has a limit on the number of instances that you can have running.

## Storage for your instance

* The root device for your instance contains the image used to boot the instance.

* The root device is either Amazon EBS or an instance store volume

* May include a local storage volume known as instance store volume

* If your instance fails, or your instance is stopped or terminated, the **data is lost**

* To keep important data safe, use a replication strategy or store your data in S3 or EBS

## Security best practices

* Use IAM to control access to your AWS resources, including your instances

* Create IAM users and groups under your AWS account to control access

* Restrict access by only allowing trusted hosts or networks to access your instance.

* Review the rules in your security groups regularly

* Apply the principle of least privilege

* Create different security groups which require different security requirements

* Consider creating a bastion security group that allows external logins

* Keep the remaining instances in a group that does not allow external logins

* Disable password-based logins for instances launched from your AMI. Passwords can be found or cracked and are a security risk.

## Stop and terminate instances

* The instance performs a normal shutdown, and then transitions to *stopped*.

* If the instance type was changed while stopped, you will be charged the rate for the new instance type

* All of the associated Amazon EBS usage of your instance, including root device usage, is billed using EBS storage.

## Terminate an instance

* When an instance is terminated the instance performs a shutdown

* The root device volume is deleted but any attached EBS volumes are preserved

* The instance itself is also deleted, and you can't start the instance again at a later time.
