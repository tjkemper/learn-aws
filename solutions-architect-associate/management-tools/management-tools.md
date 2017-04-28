# Management Tools
* CloudWatch
* CloudFormation
* CloudTrail
* Config
* OpsWorks
* Service Catalog
* Trusted Advisor
* Managed Services


## CloudWatch
* **Basic** monitoring is free
* **Detailed** monitoring comes at an additional cost

### Detailed monitoring
* Aggregate metrics you define
  * **Cannot** aggregate across regions
  * **Can** aggregate across AZs within a region
* Enables you to set a TIME value

### Metrics
* Available for 2 weeks
  * Can move to S3 or Glacier (good use case for Lambda)
* Can create **custom metrics**
* EC2
  * CPU, Disk, Network
  * **5 minute** intervals by default
  * **1 minute** intervals allowed when **detailed monitoring** is enabled
  * 7 pre-selected metrics @ 5 min frequency
  * 3 status check metrics @ 1 min frequency
  * CloudWatch cannot report on memory by default (would need to install some reporting agent on each EC2 instance to send custom data to CloudWatch)
* RDS
* DynamoDB
* ELB
* EBS

### Alarms
* Watch metrics over given time period
* Limit 5,000 alarms per account
* Send notifications to:
  * SNS topic (no additional actions are invoked)
  * Auto scale policy (continues invoking for every period the alarm remains in the new state)
* Alarm states
  * **OK** - metric is in defined threshold
  * **ALARM** - metric is outside defined threshold
  * **INSUFFICIENT DATA** - usually the alarm has just started




## CloudFormation
* Infrastructure as code
* JSON DSL


## CloudTrail
* Audits
* Logs to S3 bucket
  * Identity of caller
  * Time of caller
  * Source IP
  * Request parameters
  * Response elements
* Delivers event within 15 minutes of API call
* Delivers log files to S3 bucket every 5 minutes


## Config
* An inventory and configuration history service
* Provides information about the configurations and changes in infrastructure over time


## OpsWorks
* Chef
* Limit 40 (Stacks, Layers per stack, Instances per stack, Apps per stack)


## Service Catalog
*


## Trusted Advisor
*


## Managed Services
*
