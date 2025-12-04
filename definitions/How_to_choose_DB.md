## How to choose DB? RDS which db to choose?
It depends on the type of application, the nature of the data, and the CAP Consideration.

CAP:
CAP stands for Consistency, Availability, and Partition tolerance. The theorem states that you cannot achieve all the properties at the best level in a single database, as there are natural trade offs between the items. You can only pick two out of three at a time and that totally depends on your prioritize based on your requirements. For example, if your system needs to be available and partition tolerant, then you must be willing to accept some latency in your consistency requirements. 
Traditional relational databases are a natural fit for the CA side whereas Non-relational database engines mostly satisfy AP and CP requirements. 
* Consistency means that any read request will return the most recent write. Data consistency is usually “strong” for SQL databases and for NoSQL database consistency may be anything from “eventual” to “strong”.
* Availability means that a non-responding node must respond in a reasonable amount of time. Not every application needs to run 24/7 with 99.999% availability but most likely you will prefer  a database with higher availability.
* Partition tolerance means the system will continue to operate despite network or node failures.

Nature of the data:
Whether the data is structured (SQL), semi-structured, or mixed (NoSQL).

Amazon RDS:
Amazon RDS (Relational Database Service) is a managed SQL database service that supports multiple database engines, including MySQL, PostgreSQL, MariaDB, Microsoft SQL Server, and Oracle. It simplifies database management by automating provisioning, patching, backups, and monitoring.
Key Features of Amazon RDS
* Multi-Engine Support: Supports MySQL, PostgreSQL, MariaDB, Microsoft SQL Server, and Oracle.
* Automated Backups: Periodic snapshots and point-in-time recovery.
* Multi-AZ Deployment: Ensures high availability by maintaining a standby replica in a separate AZ.
* Manual Scaling: Allows scaling of storage and compute resources as needed.
* Automatic Software Patching: Keeps database instances secure and updated.

Amazon Aurora:
Amazon Aurora is a fully managed relational database service designed for cloud applications. It is compatible with MySQL and PostgreSQL, offering high performance, scalability, and automatic failover. Aurora integrates the advantages of traditional databases with the cost-effectiveness of open-source database engines.
Key Features of Amazon Aurora
* High Performance: Up to 5x better performance than standard MySQL and 2x better than PostgreSQL.
* Fault Tolerant Storage: Data is stored in 6 copies across three Availability Zones (AZs) for durability.
* Auto Scaling: Seamlessly scales storage from 10 GB to 128 TB without downtime.
* Automatic Failover: Quickly promotes read replicas to the primary database in case of failure.
* Aurora Serverless: Automatically scales compute resources based on demand.


Amazon Aurora vs Amazon RDS
Feature	Amazon Aurora	Amazon RDS
Database Engines	MySQL, PostgreSQL	MySQL, PostgreSQL, MariaDB, SQL Server, Oracle
Performance	Up to 5x faster than MySQL and 2x faster than PostgreSQL	Standard performance based on the chosen instance type
Storage	Automatically scales from 10 GB to 128 TB	Storage scales up to 64 TB (SQL Server: 16 TB)
Replication	Supports up to 15 read replicas	Supports up to 5 read replicas
Failover	Automatic failover to read replicas	Manual failover (unless Multi-AZ is enabled)
Availability	Highly available with 6 copies of data across 3 AZs	High availability with Multi-AZ feature
Backup	Continuous, incremental backups with no performance impact	Periodic backups with potential performance impact
Pricing	More expensive but offers better performance and resilience	Cheaper but requires more manual management
