# learn-aws
Preparing for AWS certifications

# TODO
* Levels of support: Enterprise, Business, Developer, Basic (free)
* EC2
  * Spot instance
    * Termination scenarios
  * Host vs Dedicated vs Default
  * ENI *cold attach* (when the instance is being launched)
* S3
  * Multi-part uploads (benefits)
  * Put - S3 Request Headers
  * key namespace
* DynamoDB
  * multi-az deployment
  * Partition key
  * Table
  * ProvisionedThroughputExceededException
  * Local Secondary Indexes
* Termination policy (Autoscaling)
* Direct Connect
* SQS
  * VisibilityTimeout (12 hours)
  * DelayedSeconds
  * ReceiveMessageWaitTimeSeconds
  * FIFO! / LIFO?
* AMIs
  * Launch permissions (who can launch this AMI), user-defined tags, s3 bucket permissions
* WAF (Web Application Firewall)
* VPN connections (on-premise to VPC)
* EMR
  * Core and Task nodes
* Storage Gateway
  * VTL
* Import/Export Service

**Owner** refers to the identity and email address used to create the AWS account

# Known
* VPC Peering does not support edge to edge routing
* The names of the AZs are randomly applied, so "eu-west-1b" is not necessarily the same physical location for all three accounts.
* S3 minimum size: **0 bytes**
* Entire VPC can be set to **dedicated hosting**
  * Must recreate VPC if you want **default hosting**
* S3, SQS & DynamoDB are already built in a fault tolerant fashion, you do not need to provision these services across multiple availability zones. Therefore the correct answers are RDS and EC2
* A placement group can span peered VPCs
* You can have one Elastic IP (EIP) address associated with a running instance at no charge *(multiple EIPs on one instance incurs a charge)*
* Route53 supports the following DNS record types: **NAPTR** & **SPF**
* Default network interface (eth0) of an instance
* Make objects in S3 public by either the **object ACL** or **bucket policy** *(recommended)*

Can you **stop** and Instance store backed instance?
