# Security


## Security in the Cloud
* **Data Protection** - Protecting data *at rest* and *in transit* *(customer)*
* **Privilege Management** - Ensuring users have least privileges *(customer)*
* **Infrastructure Protection** - Keeping facilities and network secure *(aws)*
* **Detective Controls** - Regular monitoring and testing to avoid compromise *(customer)*

## AWS Shared Responsibility Model
* AWS manages security **of** the cloud
  * Facilities
  * Network infrastructure
  * Virtualization
* Customers manage security **in** the cloud
  * *Confidentiality, Availability, Integrity*
  * OS
  * AMIs
  * Applications
  * Data rest & transit
  * Data stores
  * Credentials
  * Policies & Configuration

## Compliance

## Penetration Testing
* Need permission from AWS first

## Security Best Practices
* Use security groups
* Use Network ACLs
* Use IPSec or AWS Direct Connect for trusted connections to other sites
* Use Virtual Gateway (VGW) where Amazon VPC-based resources require remote network connectivity
* Protect data in transit
* Defense in Depth - design network security in layers

## AWS Encryption Services
* KMS (Key Management Service)
* CloudHSM

#### Services that offer encryption
* S3
* EBS
* Glacier
* Storage Gateway
* RDS
* Redshift
* Workspaces

## Inline threat protection
* Third-party firewall devices installed on EC2 instances (also known as *soft blades*)
* Unified threat management (UTM) gateways
* Intrusion prevention systems
* Data loss management gateways
* Anomaly detection gateways
* Advanced persistent threat detection gateways

## Exam extras
* If administrator leaves the company
  * Change the password and add MFA to the root account
  * Rotate keys and change the passwords for IAM user accounts
  * Delete the user's personal account
  * Put an IP restriction on the root account
* EC2 instances cannot send spoofed or anonymous network traffic.
  * Cannot run an instance in stealth or promiscuous mode
* AWS CloudFront enables private content via Signed URLs, Signed cookies and Origin Access Identities
  * **Signed URLs and Signed cookies** control how users access resources through CloudFront
  * **Origin Access Identities** ensures only your CloudFront distribution can access your origin files in S3
* **Port scans** are not allowed under the AWS usage policy
* **Penetration Testing** is allowed but need to ask permission first
* EC2 uses public key cryptography to encrypt and decrypt log in information
  * **Linux** instances have *no password*.  You use a key pair to log in using SSH
  * **Windows** instances you use a key pair to obtain the *admin password* and then log in using RDP
* **AWS KMS** *(Key Management Service)* - a managed service that makes it easy to manage encryption keys
* **AWS CloudHSM** *(Hardware Security Module)* - dedicated key management appliance *(based on the SafeNet appliances)*
  * Helps meet corporate or regulatory standards *(because keys are stored in a separate appliance)*
  * Upfront fee and hourly rental fee
