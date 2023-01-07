# Amazon Elastic Load Balancing

## What is Elastic Load Balancing?

* Automatically distriubtes incoming traffic across multiple targets
  * Such as EC2 instances
  * Containers
  * IP addresses
  * In one or more AZs

* It monitors health of its registered targets, and routes traffic only to healthy targets

* Elastic Load Balancing scales your load balancer capacity automatically in response to changes in incoming traffic

## Load balancer benefits

* A load balancer distributes workloads across multiple compute resources

* Increases fault tolerance

* You may add and remove compute resources as your needs change

* Configure health checks, which monitor the health of the compute resources

* Load balancer sends requests only to healthy ones

* Offload the work of encryption and decryption to your load balancer so that your compute resources can focus on their main work.

## Features of Elastic Load Balancing

* Elastic Load Balancing supports the following
  * Application Load Balancers
  * Network Load Balancers
  * Gateway Load Balancers
  * Classic Load Balancers

* You select the balancer that suits your needs

## Accessing Elastic Load Balancing

* AWS Management Console

* AWS CLI

* AWS SDKs

* Query APIs

## Related services

* Elastic Load Balancing works with the following services to improve availability and scalability
  * EC2
  * EC2 Auto Scaling
  * AWS Certificate Manager
  * Amazon CloudWatch
  * Amazon ECS
  * AWS Global Accelerator
  * Route 53
  * AWS WAF

## Pricing

* Only pay for what you use
