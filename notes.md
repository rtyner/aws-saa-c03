# AWS Accounts
- Complex projects and businesses use multiple AWS accounts
- AWS account - **container** for identities and AWS resources
	- Identities = users
- Root users are per account
- Root user has full control over the account and resources
	- cannot be restricted 
- Can set alternate contacts for different functions of the account
- AWS Organization - connects AWS accounts

### Security of AWS Accounts
- IAM can be used to create identities within the AWS account
	- IAM users, groups, roles
	- Can be given granular permissions
	- Cross account permissions are possible
- AWS accounts can contain the impact of admin errors and bad actors
- **Use separate accounts for separate things, teams, products (test, dev, prod)**
- By default all external access to an AWS account and resources are denied except for the root account
- External identities can be granted access if needed

### Course AWS Accounts
- Types of accounts created
	- General account - services+cantrll-general@rtyner.com
	- Production account - services+cantrll-prod@rtyner.com
- Settings
	- 2FA
	- Budget
	- IAM User and Role Access to Billing Information
	- IAM user
- MFA
	- Factors - pieces of evidence which prove identity
		- Knowledge - something you know, UN/PW
		- Possession - something you have, MFA device/app
		- Inherent - something you are, biometrics
		- Location - Physical location (GPS), or specific network

### IAM Basics
- **Globally resilient**
- 3 identity objects
	- User - Human or apps that need access to AWS account
		- When you can identify an individual thing to login
	- Group - Collections of related users, dev, finance, hr
	- Role - Can be used by AWS services or for granting external access to your account
		- When number of users is uncertain
	- Policy - Policy document, can be used to allow or deny access to AWS services when attached to users, groups, or role

**- 3 main jobs
	- Manage identities - identity provider - create, modify users
	- Authenticate - Prove who you claim to be
	- Authorize - Allow or deny access to resources**
- No cost
- Globally resilient
- Allow or deny its identities on its AWS account
- No direct control on external accounts or users
- Identify federation and MFA (AD, other SSO)

##### Demo - Adding an IAM Admin
- Day to day usage is done by an IAM ID, not root account
- To have full admin control use the AdministratorAccess policy

### IAM Access Keys
- Long term credentials in AWS
- Used with cli apps (API access)
- IAM user can have **two access keys**
- Access keys can be created, deleted, made active, and made inactive
- Users are the only ID that uses access keys

- Specify profiles with awscli
	- `aws configure --profile iamadmin-prod`
	- `aws s3 ls --profile iamadmin-prod`

#  Cloud Computing Fundamentals

### What is it?
- On-Demand Self-Service
	- can provision capabilities as needed **without requiring human interaction**
- Broad Network Access
	- Capabilities are available over the **network** and accessed through **standard mechanisms** (https, ssh, etc)
- Resource Pooling
	- There is a sense of **location independence**... no **control** or **knowledge** over the exact **location** of the resources
	- Resources are **pooled** to serve multiple consumers using a **multi-tenant model**
- Rapid Elasticity
	- Capabilities can be **elastically provisioned** and **released** to scale rapidly **outward** and inward with demand
	- To the consumer, the capabilities available for provisioning often **appear** to be **unlimited**.
- Measured Service
	- Resource usage can be **monitored, controlled, reported, and billed.**
	- Pay as you go, on demand billing, opex

### Public vs. Private vs. Multi vs. Hybrid Cloud
## **WILL BE ON EXAM**
- Public - Cloud environment that's available to the public - AWS, Azure, Google
	- Using 1 public cloud
- Multi-Cloud - Using multiple cloud providers for your workloads - Servers in AWS and Azure redundantly 
	- Using 1 or more public cloud
- Private cloud - Cloud computing that meets the definitions of a cloud but is reserved explicitly for you - AWS Outposts
	- using on premises **REAL** cloud
- Hybrid Cloud - Using public cloud with private cloud, not cloud with on prem hardware
	- Public and private cloud

### Cloud Service Models
- X as a Service
- Terms and Concepts
	- Infrastructure stack 
		- Parts you manage, parts managed by the vendor
	- Unit of consumption - The part you pay for within the stack, VM, OS, network, service
- On Premises vs DC Hosted
	- On prem - you control the whole stack
	- DC hosted - you control from the network up
- Service Models
	- IaaS - Provider handles facilities, infrastructure, servers, virtualization you handle the OS up
		- EC2 is IaaS
	- PaaS
		- Heroku
	- SaaS
		- Netflix

# Tech Fundamentals

### YAML101
- Human readable data serialization language
- Unordered collection of key:value pairs
	- key: value - cat1: winkie
- YAML supports numbers (1 or 2 ...), floats (1.337), bools (true or failse), and null
- Lists
	- Ordered set of values
		- `adrianscats: ["roffle", "truffles", "penny", "winkie"]`
- Dictionary
	- Ordered set of key:value pairs
	- Using YAML key:value pairs, lists, and dicts, allows you to build complex data structures in a wat which is human readable
	- Cloudformation YAML template example
```yaml
Resources: #dictionary
  s3bucket: #dictionary
    Type: "AWS::S3::Bucket" #key
    Properties: #key 
      BucketName: "ac1337catpics" #value
```

### JSON101
- JavaScript Object Notation - Lightweight data-interchange format
- Object - unordered set of key:value pairs enclosed by { } - dictionary
- Array - ordered collection of values separated by commas and enclosed in [  ] - list
- Values = string, object, number, array, true, false, null
- {} at the top tells that what's enclosed is a json object
```json
{
  "cats": ["roffle", "truffles", "penny", "winkie"],
  "colors": ["mixed", "mixed", "grey", "white"],
  "numofeyes": ["2", "2", "2", "1"]
}
```

```json
{
  "Resources": {
  "s3bucket": {
     "Type": "AWS::S3::Bucket",
     "Properties": {
       "BucketName": "ac1337catpics"
     }
   }
 }
}
```

### Encryption 101
- Encryption approaches
	- Encryption at rest
		- designed to protect against a physical threat
	- Encryption in transit
		- designed to protect data while it's being transferred
- Encryption concepts
	- Plaintext - unencrypted data
	- Algorithm - code and math that encrypts data
		- Blowfish, AES, RC4, DES, RC5, RC6
	- Key - Password
	- Ciphertext - encrypted data
- Symmetric Encryption


## AWS Fundamentals

### AWS Public vs. Private Services
- Public internet, AWS public zone, AWS private zone
- AWS Private Zone
	- VPC
		- Isolated "networks" within AWS
		- VPCs are isolated unless configured otherwise
		- EC2
- AWS Public Zone
	- Services with public endpoints
		- S3

### AWS Global Infrastructure **KNOW THIS**
#### Regions  
- Full deployment of AWS 
- Geographically spread
- 3 main benefits
	- Separate geographically - **Isolated fault domain**
	- Geopolitical separation - **Different governance**
	- Location control - **Performance**
- Refer to with region code or region name
- What's in a region?
	- Multiple Availability Zones

#### Availability Zones
- Isolated infrastructure within a region
- Can distribute infra across multiple availability zones
- Logical separation within AWS, can be one DC or multiple
	
#### Edge locations
- Local distribution points
- Located in more areas than regions
- Usually just CDN stuff for better latency

#### Service Resiliency 
- Globally resilient
	- IAM, Route53
- Region resilient
	- Services that operate in a single region with one set of data in a region
	- Replicate data to multiple AZs in a region
- AZ resilient 
	- Run from single AZ

### VPC Basics
- Virtual network inside AWS
- **A VPC is within 1 account and 1 region**
- **Private** and **Isolated** unless you configure otherwise
- 2 types of VPC - **Default and Custom** - 1 default VPN per region **ON EXAM**
- **VPC is regionally resilient**
- **Can be subnetted across multiple AZs**
- Default VPC Facts
	- 1 per region
	- Some services assume default VPC is there
	- Default VPC CIDR - 172.31.0.0/16
	- /20 is created in each AZ of the region
	- Includes internet gateway (IGW), Security Group (SG) and NACL
	- Subnets assign public IPv4 addresses

### Elastic Compute Cloud EC2 Basics
- Provides access to VMs
- Features
	- IaaS - Unit of consumption is the instance
	- Private AWS service by default - uses VPC networking
	- **AZ resilient**
	- Can choose different sizes and capabilities
	- On demand per second billing
		- Charge for CPU, GPU, memory, storage, networking, and any paid software on top
	- Local on host storage or Elastic Block Storage (EBS)
- Instance states
	- Running
		- Charged for CPU, GPU, RAM, storage, and network
	- Stopped
		- Only charged for storage
	- Terminated
		- Charged for nothing, instance is deleted
- AMI - Amazon Machine Image
	- Can be used to create EC2 instance or be created from EC2 instance
	- Contains:
		- Permissions
			- Public - everyone allowed, AWS provided images
			- Owner - Only AMI owner can run - Implicit
			- Explicit - Specific AWS accounts or general public allowed
		- Root volume - boot
		- Block device mapping - links volumes that AMI has and how they're presented to OS
- Connecting to EC2
	- ssh, RDP

### Simple Storage Service S3 Basics
- Global storage platform - **regional** based/resilient
- Public service, unlimited data and multi user
- Movies, audio, photos, text, large data sets
- Economical and accessed via UI/CLI/API/HTTP
- Objects and buckets

- Objects
	- are essentially files
	- has 2 components and metadata
		- object key (filename)
		- value (data) - Content being served
		- **Value can be 0B to 5TB** **ON EXAM**
		- Version ID, access control, metadata, subresources

- Buckets
	- region specific
	- never leaves the region unless configured to
	- **bucket names are globally unique**
	- can hold an unlimited number of objects
	- buckets don't have folders, it looks like it does, but it's all flat
		- /old/koala1.jpg
			- it's just part of the key
		- referred to as prefixes
- S3 is an object storage system, not file or block
## EXAM POWERUP
- Bucket names are globally unique
- 3-63 characters, all lowercase, no underscores
- start with lowercase number or letter
- can't be IP formatted
- Soft limit of 100 buckets per account, hard limit of 1000 per account
	- if you need more you can divide buckets with prefixes
- unlimited objects in a bucket 0B to 5TB
- Key = Name, Value = Data

- AWS Patterns and anti patterns
	- Great for large scale data storage, distribution, or upload
	- Great for offload
	- Should be default input and output to many AWS products

### CloudFormation Basics
- Create, update, delete infrastructure in AWS using templates
- written in yaml or json
- Description has to immediately follow template format version if you have the version
	- 