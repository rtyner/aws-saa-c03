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
	- ![[Pasted image 20221030115612.png | 500]]
	
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
- 2 types of VPC - **Default and Custom** - 1 default VPC per region **ON EXAM**
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
	- ![[Pasted image 20221101172808.png | 700]]

### Cloudwatch Basics
- Collects and manages operational data
	- metrics - AWS products, apps, on-premises
	- CloudWatch Logs - AWS products, apps, on-premises
	- CloudWatch Events - AWS services and schedules
- Namespace - container for monitoring data
	- AWS data goes into AWS/service - AWS/ec2
- Collects metrics - CPU, disk io, network data
- Time ordered set of data points
- Datapoint - time stamped metric that is recorded
- Dimension - named value pairs that separate items sending data to cloudwatch
	- instance id, instance type
	- ![[Pasted image 20221101184436.png | 600]]
- Alarms - alerts that a specifically defined metric has entered a defined state
	- you can set actions to happen upon alarm

### Shared Responsibility Model
- ![[Pasted image 20221101194642.png | 900]]

### High Availability vs Fault Tolerance vs Disaster Recovery
- High Availability - aims to **ensure** an agreed level of operational **performance**, usually **uptime**, for a **higher than normal period**
	- Minimize outages
- Fault Tolerance - the property that enables a system to **continue operating properly** in the event of the **failure of some** (one or more faults within) of its **components**.
	- Operates through failure
- Disaster Recovery - a set of policies, tools, and procedures to **enable the recovery** or **continuation** of vital **technology** infrastructure and systems f**ollowing a natural or human-induced disaster**
	- Used when these don't work

### Route53 Fundamentals
- Register domains
- Host zones on managed nameservers
- Global service with single database
- Globally resilient

- Hosted Zones
	- Can be public or private
	- stores DNS records as **recordsets**

- DNS Record Types
	- Nameserver (NS) - allow delegation to occur
	- A and AAAA - map hostnames to IP addresses
	- CNAME - host to host records ftp,mail,www all on same server
		- **cannot point directly to IP, only to hostnames**
	- MX - mail server records
		- MX records have priority and value
			- value is the hostname
			- priority determines which record is used, lower is first
	- TXT - adds arbitrary text to domain
		- prove ownership, identification
- TTL
	- numeric value in seconds that can be set on a record
	- how long records can be cached for
	- useful to cache records closer to the user, at the non-authoritative server so the query doesn't have to go to the root server everytime

### Fundamentals Section Quiz
1. What Permissions options does an AMI have? - **RIGHT**
	1. Public access, owner only, specific AWS accounts
2. What is NOT stored in an AMI? - **WRONG**
	1. Instance settings and Network settings
3. EC2 is an example of which service model? - **RIGHT**
	1. IaaS
4. What is true of an AWS Public Service? - **WRONG**
	1. Located in the AWS public zone and Anyone can connect, but permissions are required to access the service
5. What is true of an AWS Private Service? - **WRONG**
	1. Accessible from the VPC it's located in
	2. Located in a VPC
	3. Accessible from other VPCs or on prem networks as long as private networking is enabled
6. What is true of Simple Storage Service (S3)? - **RIGHT**
	1. S3 is a public service
	2. S3 is an object storage system
	3. Buckets can store an unlimited amount of data
7. What is a CloudFormation Logical Resource? - **RIGHT**
	1. A resource defined in a CloudFormation template
8. What is a CloudFormation Physical resource? - **RIGHT**
	1. A physical resource created by creating a CloudFormation stack
9. What is a simple and correct definition of High Availability? - **RIGHT**
	1. A system which maximized uptime
10. Which of the following is a correct definition of a fault tolerant system? - **RIGHT**
	1. A system which allows failure, and can continue to operate without disruption
11. How many DNS root servers exist? - **RIGHT**
	1. 13
12. Who manages the DNS Root Servers? - **WRONG**
	1. 12 large organizations
13. Who Manages the DNS Root Zone? - **RIGHT**
	1. IANA
14. Which DNS Record Type converts a HOST into an IPv4 Address? - **RIGHT**
	1. A
15. Which DNS Record type is how the root zone delegates control of .org to the .org registry? - **RIGHT**
	1. NS
16. Which type of organisation maintains the zones for a TLD (e.g .ORG)? - **RIGHT**
	1. Registry
17. Which type of organisation has relationships with the .org TLD zone manager allowing domain registration? - **RIGHT**
	1. Registrar 
18. How many subnets are in a default VPC? - **RIGHT**
	1. Equal to the number of AZs in the region the VPC is located in
19. What is the IP CIDR of a default VPC? - **RIGHT**
	1. 172.31.0.0/16