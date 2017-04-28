# Virtual Private Cloud (VPC)
* Core building block for designing HA, fault tolerant environments
* Logically isolated section of AWS Cloud
  * IP range
  * Subnets
  * Routing tables
  * Security
    * Security groups
    * Access control lists (ACL)
* Your own CIDR block / subnet blocks
  * Netmask from /16 to /28
* Cannot change size of VPC after created
  * Plan for number of nodes you will need

### Connection types
* Corporate or Home Network to Amazon VPC
* Amazon VPC to Amazon VPC
* End User to VPC

### VPC Configuration (Four Common Scenarios)
* VPC with a single public subnet
* VPC with public and private subnets
* VPC with public and private subnets and HW VPN access
* VPC with private subnet only and HW VPN access

### Components
* Subnet
* Internet Gateway (IGW)
* Hardware VPN connection
* Virtual Private Gateway (VGW)
* Customer Gateway (CGW)
* Router
* VPC Peering
* VPC endpoint for S3

### Subnet
* Always equals one AZ
* CIDR block within the IP range of VPC
  * Classless Inter-Domain Routing (CIDR)
* Cannot change size of subnet (after it's created)

##### IP Addresses in Subnet
* First four IP addresses and last in each subnet CIDR block are **not** available for use
  * With 10.0.0.0/24 CIDR block, following IPs are reserved:
  * 10.0.0.0   Network address
  * 10.0.0.1   For VPC router
  * 10.0.0.2   For mapping to Amazon-provided DNS
  * 10.0.0.3   For future use
  * 10.0.0.255 Network broadcast address. AWS does not support broadcast in a VPC, but this address is reserved.

##### Subnet Defaults & Limits
* Must be associated with **one** route table
  * Automatically associated with *main* route table for VPC
* Must be associated with **one** Network ACL
  * Automatically associated with *default* Network ACL
* 200 subnets per VPC

### Network Access Control Lists *(Network ACLs or NACLs)*
* **Stateless** - separate inbound and outbound rules (return traffic must be explicitly allowed by rules)
* **Subnet** level control  **(second layer of defense)**
* Numbered list of rules (read in order starting with lowest numbered rule)
  * Each rule can either **allow** or **deny** traffic
  * Can have up to **20 rules**
* **Default** NACL **allows** all inbound and outbound traffic (by default)
* **Custom**  NACL **denies** all inbound and outbound traffic (by default)
* Each subnet must have a NACL
  * If you do not specify one, it will be associated with the default NACL
  * When you associate a NACL with a subnet, previous association is removed
* One to many
  * NACL can have many subnets
  * Subnet can only have one NACL
* Automatically applies to all instances in the subnets it's associated with
* Good layer to block malicious IP / DDOS hosts

### Security Groups
* **Stateful** - return traffic is automatically allowed
* **Instance** level control **(first layer of defense)**
* **Virtual firewall** for resources in a VPC (ELB, instances, etc.)
* Only **allow** rules *(inbound and outbound)*
* All rules are evaluated before deciding whether to allow traffic
* Must specify **one or more security groups** when launching an instance

### [Internet Gateway (IGW)](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Internet_Gateway.html)
* **One per VPC**
* Amazon VPC side of a connection to the public internet
* Provides connectivity in and out of VPC
  * 1-1 relationship between VPC and IGW
* 2 key functions
  * Provide target (in VPC route tables) for Internet-routable traffic
  * Performs NAT (for instances with public IP addresses)
* **public subnet -** subnet associated with route table that has a route to an IGW
  * Instance is only accessible if it's in a public subnet and has either **public IP** or **elastic IP**
* Instances launched into a **default** subnet have a default IGW; so they can automatically communicate with the Internet.
* Manually configure public subnet:
  * Can scope the route to all destinations not explicitly known to the route table (0.0.0.0/0)
  * Can scope the route to specific IP addresses (Elastic IP addresses of other EC2 instances outside your VPC)
* Consider using host-based firewalls to further control access to each instance
* You can't detach an IGW if the VPC has instances with associated Elastic IPs


### [Route Tables](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Route_Tables.html)
* Interconnect subnets and direct traffic between IGW, VGW, Net Gateways, and subnets
* Each subnet in your VPC must be associated with **one** route table
* Route table can be associated with **many** subnets
* Don’t put route out to the internet on main route table


### Hardware VPN Connection
* Hardware based VPN between your Amazon VPC and your datacenter or colocation centre (colo)

### Virtual Private Gateway (VGW)
* Amazon VPC side of a VPN connection
* Connect existing networks to a VPC

### Customer Gateway (CGW)
* Your side of a VPN connection

### VPC Peering
* Route traffic by **private** IP addresses (between two peered VPCs in **same region**)
* Not transitive

### VPC endpoint for S3
* Access to S3 without using IGW or NAT
* Control access with VPC endpoint policies

### Elastic Network Interface (ENI) [link](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html)
* Virtual network interface that you can attach to an instance in a VPC
* A network interface can include the following attributes:
  * A primary private IPv4 address
  * One or more secondary private IPv4 addresses
  * One Elastic IP address (IPv4) per private IPv4 address
  * One public IPv4 address
  * One or more IPv6 addresses
  * One or more security groups
  * A MAC address
  * A source/destination check flag
  * A description

### VPC Limits - [link](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Appendix_Limits.html)
* 5 VPC's per region
  * Default VPC set up in each region
* 5 IGWs per region
* 5 Elastic IP addresses per region
*
* 500 security groups per VPC
* 10 VPNs per VPC
* 200 subnets per VPC

# Direct Connect
* Private, dedicated, connection between on-premise network and Amazon VPC
* Uses the 802.1 q VLAN standard

# Best practices for Network Security
* Use a layered security model (defense in depth)
* Use Security Groups and Network ACLs
* Use IAM to ensure separation of duties
* Use AWS Direct Connect or IPSec for connections to Internal Networks or other sites
* Protection of data

# NAT Instance
* *No longer recommended*
* Instance in public subnet that provides internet access for private subnet *(gateway to the internet)*
* NAT Security group
  * 80 and 443 inbound/outbound
* Disable source/destination checking
* Should use Elastic IP
* Route table
  * NAT instance must be in (public) subnet associated with this route table
  * Private subnet also must be associated with this route table
  * create route 0.0.0.0/0 to NAT Instance
* NAT Instance is behind a security group

### Architectural Considerations
* HA using autoscaling groups, multiple subnets in different AZ’s and a script to automate failover
* If bottlenecking, vertically scale NAT instance types (for high network throughput)

# NAT Gateways
* released in 2016
* preferred
* scale automatically up to 10Gbps
* no need to patch
* not associated with security groups
* Automatically assigned a public ip address
* put in public subnet
* use route table for private instance to point all traffic to NAT Gateway
* no need to disable source/destination checks
