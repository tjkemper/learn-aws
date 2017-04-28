# RDS
* Relational Database Service

### Databases
* MySQL
* PostgreSQL
* OracleDB
* SQLServer
* MariaDB
* Amazon Aurora

### Availability & Durability
* Automated backups
* Database snapshots (user initiated)
* Multi-AZ deployments
* Automated host replacement

### Storage Types
* General Purpose (SSD)
* Provisioned IOPS (SSD)
* Magnetic

### Maintenance
* Automated
* Maintenance windows (can schedule)
* For Multi-AZ
  1. Perform maintenance on standby
  +  Promote standby to primary
  +  Perform maintenance on old primary (which is now standby)

### Security
* Database Security Groups are deprecated
  * Used when RDS instance is not in a VPC (EC2-Classic)
  * Only EC2-VPC is supported for accounts created after Dec 4, 2013

### Best Practices
* Monitor memory, CPU, and storage with CloudWatch
  * Use SNS to send notifications based on metric events
* Scale RDS instance when needed
* Enable automated backups with appropriate backup window (Daily low in Write IOPS)

### [Read Replicas](https://aws.amazon.com/rds/details/read-replicas/)
* Scale for **read-heavy** workloads
* **Asynchronous** replication
* Can promote read replicas to become standalone RDS instances

### [Multi-AZ Deployments](https://aws.amazon.com/rds/details/multi-az/)
* Automatic failover to a standby RDS instance *(Endpoint remains the same after failover)*
* **Synchronously** replicates data to a standby instance in another AZ
* **Amazon Aurora** can failover to a read replica
* Can initiate forced failover when rebooting your instance. [link1](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_RebootInstance.html) [link2](https://aws.amazon.com/rds/faqs/#46)

### Push-Button Scaling

| Database       | Vertical Scaling |
| :------------: | :--------------: |
| [MySQL](https://aws.amazon.com/rds/mysql/) | 1,000 to 10,000 IOPS *(1,000 increments)* |
| [PostgreSQL](https://aws.amazon.com/rds/postgresql/) | 1,000 to 30,000 IOPS *(1,000 increments)* |
| [Oracle](https://aws.amazon.com/rds/oracle/) | 1,000 to 30,000 IOPS *(1,000 increments)* |
| [MariaDB](https://aws.amazon.com/rds/mariadb/details/) | 1,000 to 30,000 IOPS *(1,000 increments)* |
| [SQL Server](https://aws.amazon.com/rds/sqlserver/) | N/A |

### [RDS Metrics](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/rds-metricscollected.html)
