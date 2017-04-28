# Route53
* Managed DNS Service
* Can register TLDs

## Hosted Zones
* Route53 organizes your DNS records into hosted zones
* Zone records consists of any of the DNS supported domain extensions
  * **ANAME** - root record (amazon.com)
  * **CNAME** - alias (www.amazon.com)
  * **MX** - mail exchanger (mx.amazon.com)

#### [Supported DNS Resource Record Types](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html#MXFormat)
* A
* AAAA
* CNAME
* MX
* NAPTR
* NS
* PTR
* SOA
* SPF
* SRV
* TXT

### IPv6
* **AAAA**  is for an IPv6 address
* **ANAME** is for an IPv4 address

## AWS resources you can create alias records for
* ELB
* Elastic Beanstalk
* CloudFront*
* S3 website*

\* *DNS name must exactly match CloudFront alternate domain name or S3 bucket name*

## TXT record
* **Text record** - can store arbitrary bits of text
* For:
  * Email validation
  * Web analytics
  * Certificates

## General
* Domain names are registered with domain registrars that in turn register the domain
name with InterNIC (a service of ICANN)
  * Each domain is registered in a central WhoIs database
* Domains are defined by their top level domains (TLD)
  * TLDs are controlled by IANA in a root zone database

## Routing Policy
* Simple
* Weighted
* Latency
* Failover
* Geolocation

## DNS Failover
* Redirect to another location
* Can redirect to ELB pointing to static S3 website (common use case)

## Questions
* Where do you register a domain name?
  * With a Domain Registrar
* What is a PTR (Pointer) record?
  * Used for reverse DNS

## Commands

```
dig example.com

dig NS example.com

dig example.com +trace
```

## Advanced

### Private DNS in VPC
* Can use for VMs to talk to each other
* Don't have to own the domain names
* Only visible within VPC

### Health checks and failover

### Multi-region
* Latency
* Geolocation

### Traffic flow
* Web console flow chart
* Policy
