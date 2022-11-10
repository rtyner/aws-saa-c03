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


## **EXAM POWERUP**
- ![[Pasted image 20221030111953.png | 800]]

### Public vs. Private vs. Multi vs. Hybrid Cloud
### **WILL BE ON EXAM**
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
		- ![[Pasted image 20221030112824.png | 150]]
		- Parts you manage, parts managed by the vendor
	- Unit of consumption - The part you pay for within the stack, VM, OS, network, service
- On Premises vs DC Hosted
	- On prem - you control the whole stack
	- DC hosted - you control from the network up
- Service Models
- ![[Pasted image 20221030113424.png | 600]]
	- IaaS - Provider handles facilities, infrastructure, servers, virtualization you handle the OS up
		- ![[Pasted image 20221030113145.png | 150]]
		- EC2 is IaaS
	- PaaS
		- ![[Pasted image 20221030113227.png | 150]]
		- Heroku
	- SaaS
		- ![[Pasted image 20221030113332.png | 150]]
		- Netflix