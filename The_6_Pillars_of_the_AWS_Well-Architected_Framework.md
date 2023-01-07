# The 6 Pillars of the AWS Well-Architected Framework

## 1. Operational Excellence

* Run workloads effectively

* Gain insight on operation

* Improve supporting processes

### Design Principals

* Perform operations as code

* Make frequent, small, reversible changes

* Refine operations procedures frequently

* Anticipate failure

* Learn from all operational failures

### Best Practices

* Understand the customer needs

* Create procedures to respond to operational events

* Validate their effectiveness to support needs

* Collect metrics used to measure outcomes

## 2. Security

* Protect data, systems and assets

### Design Principles

* Implement a strong identity foundation

* Enable traceability

* Apply security at all layers

* Automate security best practices

* Protect data in transit and at rest

* Keep people away from data

* Prepare for security events

### Best Practices

* Before you architect a workload, put in place practices that influence security

* Identify and control who can do what

* Recognize how to best identify security incidents, protect systems and services

* Have a well-defined process for responding to security incidents

* Keep in mind objectives to prevent financial loss and regulation noncompliance

## 3. Reliability

* Reliability encompasses the ability of a workload to perform its intended function correctly and consistently

* This includes operational and test workloads throughout a lifecycle

### Design Principles

* Automatically recover from failure

* Test recovery procedures

* Scale horizontally to increase aggregate workload availability

* Stop guessing capacity

* Manage change in automation

### Best Practices

* Keep in mind sufficient bandwidth to your data center

* With AWS this is taken care of

* Reliablity
  * Loosely coupled dependencies
  * Graceful degradation
  * Limiting retries

* Take steps to implement resiliency
  * Fault isolation
  * Automated failover
  * Disaster recovery strategy

## 4. Performance Efficiency

* Efficiency is the abililty to use computing resources to efficiently meet system requirements, including as apps and technology evolves

### Design Principles

* Democratize advanced technologies

* Go global in minutes

* Use serverless architectures

* Experiment more often

* Consider mechanical sympathy

### Best Practices

* Take a data-driven aprproach to building high performance

* Gather data on all aspects of the architecture
  * Including from high-level design, to selection and configuration of resource types

* Review your choices on a regular basis to ensure you take advantage of the evolving AWS cloud

* Monitoring ensures you are aware of any deviance in performance

* Make trade-offs to perform improvements
  * Use compression or caching
  * Relax consistency requirements

## 5. Cost Optimization

* Cost pillar includes ability to run systems and deliver business value at the lowest price point

### Design Principles

* Implement cloud financial management

* Adopt a consumption model

* Measure overall efficiency

* Stop spending money on undifferentiated heavy lifting

* Analyze and attribute expenditure

### Best Practices

* It's up to you what to optimize, and depends on your application needs

* Use the appropriate resources and services to identify configurations at which your workload can operate efficiently at its best cost

## 6. Sustainability

* Sustainability addresses long-term environmental, economic, and societal impact of your business activity

### Design Principles

* Understand your impact

* Establish sustainability goals

* Maximize utilization

* Anticipate and adopt new, more efficient hardware and software offerings

* Use managed services

* Reduce the downstream impact of your cloud workloads

### Best Practices

* Choose Regions where you will implement workloads based on your business requirements and sustainability goals

* User behavior patterns can help you identify improvements to meet sustainability goals.

* Implement software and architecture patterns to perform load smoothing and maintain consistent high utilization of deployed resources

* Analyze data patterns to implement data management practices that reduce the provisioned storage

* Analyze hardware patterns to identify opportunites to reduce workload sustainablity impacts
