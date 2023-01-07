# Amazon RDS

## What is Amazon RDS?

* A managed service that makes it easy to set up, operate and scale
* Amazon RDS gives you access to capabilities of SQL
* Pay-as-you-go

### When would I use Amazon RDS vs Amazon EC2 Relational Database AMIs?

* To offload database administration

### Are there hybrid or on-premises deployment options for Amazon RDS?

* Yes, using Amazon RDS on Outposts

### Can I get help to learn more about and onboard to Amazon RDS?

* RDS specialists are available to answer questions and provide support

### How do I set up a connection between an application or a SQL based client running an EC2 instance and my RDS instance?

* Connect between an EC2 instance and an RDS database using the RDS console
* Additionally you can set up an existing RDS with an EC2 instance

## Database Instances

### What is a database instance?

* Contains compute and storage resources you specify
* Define infrastructure attributes of your DB instance
* Control access/security via
  * AWS Management Console
  * Amazon RDS APIs
  * AWS Command Line (CLI)
  * Run one or more DB instances
    * Each can support one or more databases or database schemas

### How do I create a DB instance?

* Using AWS Management Consold
* Amazon RDS APIs
* Amazon CLI
* CreateDBInstance API
* Define a backup retention policy, backup window, scheduled maintenance

### How do I access my running DB instance?

* Retrieve its endpoint via the DB instance description in the AWS Management Console
* Using this endpoint you can construct the connection string required to connect directly with your DB instance using your favorite database tool or programming language.
* You will need to authorize the access

### How many DB instances can I run with RDS?

* By default customers are allowed up to 40 Amazon RDS DB instances
* Of those 40
  * Up to 10 may be Oracle or SQL Server DB instances under the "Licenses included"
  * All 40 can be used for Amazon Aurora, MySQL, MariaDB, PostgreSQL, and Oracle under the "BYOL" model.
  * RDS for SQL has a limit of 100 databases on a single instance

### How many databases or schemas can I run within a DB instance?

* RDS for Amazon Aurora
  * No limit
* RDS for MySQL
  * No limit
* RDS for MariaDB
  * No limit
* RDS for Oracle
  * 1 database per instance
  * No limit on schemas per database
* RDS for SQL Server
  * Up to 100 databases per instance
* RDS for PostgreSQL
  * No limit

### How do I import data into an Amazon RDS DB instance?

* For MySQL
  * mysqldump
  * mysqlimport
* For Oracle
  * Data Pump
  * import/export
  * SQL Loader for Oracle
* SQL Server
  * Import/Export wizard
  * full .bak files
  * Bulk Copy Program (BCP)
* PostgreSQL
  * pg_dump

### What is a maintenance window? Will my DB instance be available during maintenance events?

* You control the window
* Maintenance window controls
  * Modifications
  * Engine version upgrades
  * Software patching
* Events that require your DB to go offline are sale compute operations
  * Generally take only a few minutes
* 30min default value is assigned if undeclared
* Running your DB instance as a Multi-AZ deployment can further reduce the impact

### What should I do if my queries seem to be running slowly?

* For production DBs we encourage you to enable Enhanced Monitoring
  * Provides access to over 50 different metrics
  * You choose the granularity
* If you are using RDS for MySQL or MariaDB
  * You can access slow query logs
* If you are using RDS for Oracle
  * You can use the Oracle trace file
* If you are using RDS for SQL Server
  * you can use the SQL Server traces client-side

## Database Engine Versions

### Which relational database engine versions does Amazon RDS support?

* Refer to the documentation for each engine

### How does Amazon RDS distinguish between "major" and "minor" DB engine versions

* Refer to the FAQs page for each engine

### Does Amazon RDS provide guidelines for support of new DB engine versions?

* We aim to support new engine versions within 5 months of their availability

### How do I specify which supported DB engine version I would like my DB instance to run?

* Through the management console or CreateDBInstance API
* Not every engine version is available

### How do I control if and when the engine version of my DB instance is upgraded to new supported versions?

* If a minor version does not benefit RDS customers it may not be made available
* To manually upgrade a database instance to a supported engine version use Modify DB Instance command in the AWS Management Console or ModifyDBInstance API and set the DB Engine Version parameter to the desired version.
* By default it will be applied during your next maintenance window.
* You may upgrade immediately by selecting the Apply Immediately option in the console API
