# Chapter 1: AWS Introduction

## What is AWS?
Amazon Web Services (AWS) is a comprehensive and widely adopted cloud platform, offering over 200 fully-featured services from data centers globally. AWS enables businesses, developers, and individuals to access computing power, storage, databases, machine learning, and more over the internet, on-demand, and with a pay-as-you-go pricing model.

## AWS Cloud facts:

- In 2019, AWS had $35.02 billion in annual revenue.
- AWS accounts for 47% of the market in 2019 (Microsoft 2nd with 22%)
- Pioneer and Leader of the AWS Cloud Market for the 9th consecutive year.
- over 1,000,000 active users.

## AWS Cloud use cases:
- AWS enables you to build sophisticated, scalable applications.
- Applicable to a diverse set of industries.
- Use cases include: Enterprise IT, Backup and storage, Big sata analytics, Website hosting, mobile and social apps, Gaming

## AWS Regions
- AWS has regios all around the world
- Names can be us-east-1, eu-west-2, etc.
- A region is a cluster of data centers
- Most AWS services are region-scoped

## How to choose an AWS Region
- Compliance with data governance and legal requirments: data never leaves a region without your explicit permission.
- Proximity to customers; reduced latency
- Available services within a region: new services and new features arent available in every region.
- Pricing: pricing varies region to region and is transparent in the service pricing range.

## AWS Availability Zones
- Each region has many availability zones (usually 3, min is 3, max is 6). Example: eu-west-2a, eu-west-2b,eu-west-2c
- Each availability zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity.
- Theyre seprate from each other, so that theyre isolated from disasters.
- They're connected with high bandwidth, ultra-low latency networking.

## AWS Points of presence (Edge Locations)
- Amazon has 400+ points of presence (400+ Edge locations & 10+ regional caches) in 90+ cities across 40+ countries.
- Contewnt is delivered to end users with lower latency


## Tour of the AWS Console
AWS has glocal services:
- Identity and access managment (IAM)
- Route 53 (DNS service)
- CloudFront (Content delivery network)
- WAF (WEB Application Firewall)

Most AWS services are Region-scoped:
- Amazon EC2 (Infrastructure as a service)
- Elastic Beanstalk (Platform as a service)
- Lambda (Function as a service)
- Rekognition (Software as a Services


## Billing
AWS billing is based on a pay-as-you-go pricing model, meaning you only pay for the services and resources you use. AWS offers a variety of pricing models, payment tools, and features to help users manage and optimize costs.

AWS Budgets:

AWS Budgets allows you to set customized budgets for cost and usage tracking.
Alerts notify you when your actual or forecasted usage exceeds your budget thresholds.

Billing Dashboard:

The AWS Billing Dashboard provides an overview of your current and historical usage and costs.
Accessible from the AWS Management Console, it shows your monthly charges, forecasts, and cost breakdown by services and regions.

## MFA
AWS Multi-Factor Authentication (MFA) is an additional layer of security for protecting your AWS account. It requires users to provide two forms of authentication: something they know (password) and something they have (an MFA device).

Benefits of MFA:

- Enhanced Security: MFA adds a layer of security by requiring users to present a second piece of information (typically a one-time code) in addition to their username and password.
- Protection from Unauthorized Access: Even if someone steals your password, they cannot access your account without the second factor (the MFA code).

MFA device options in AWS:

Virtual MFA device - Support for multiple tokens on a single device.

Universal 2nd factor security key - support for multiple root and IAM users using a single security key.

Hardware key fob MFA device - provided by Gernalto (3rd party)

Hardware key fob MFA device for AWS GocCloud (US) - Support for multiple tokens on a single device.

# Chapter 2: IAM
IAM stands for Identity and Access Management

## Users and Groups:
- Root account created by default, shouldnt be used or shared.
- Users are people within your organization, and can be grouped.
- Groups only contain users, not other groups.
- Users dont have to belong to a group, and a user can belong to multiple groups.

## IAM Permissions:
- Users or Groups can be asigfned JSON documents called policies.
- These policies define the permissions of the users
- In AWS apply the least privilege principle: dont give more permissions than the user needs.

## IAM Policies structure:
![image](https://github.com/user-attachments/assets/23bb2860-912b-414b-8ad6-cc66caea3fc0)

## How can Users access AWS:

To access AWS there are three options:
- AWS management console: protected by password + MFA
- AWS command Line Interface (CLI): protected by access keys
- AWS Software Developer Kit (SDK) for code: protected by access keys

Access keys are generated through the AWS Console

Users manage their own access keys, access keys are a secret just like a password.
- Access Key ID = Username
- Secret access key = Password

### What's the AWS CLI:
- A tool that enables you to interact with AWS services using commands in your command-line shell.
- Direct access to the public APIs of AWS services i.e S3 buckets
- Can develop scripts to manage your resources.
- Its open-source
- Alternative to using AWS Management Console.

### What's the AWS SDK:
- AWS Software development Kit (AWS SDK)
- Lanuage specifiC APIs (set pf libraries)
- Enables you to access and manage AWS services programmatically
- Embedded within your application]
- supports: SDKs (i.e Javascript, P[ython, PHP), mobile SDKs (i.e. Android, IOS), IoT Device SDKs (Embedded C, Arduino)
- Example: AWS CLI is built on AWS SDK for python AWS SDK

## AWS IAM roles for services:
In AWS Identity and Access Management (IAM), roles are a way to delegate permissions to services and applications running on AWS, allowing them to perform specific tasks without the need for hard-coded credentials. 

IAM roles are especially useful when services like EC2, Lambda, or ECS need to interact with other AWS services (like S3, DynamoDB, or RDS) on behalf of users.

## IAM security tools:
- IAM Credentials report (account level) - A report that lists all your accounts users and the status of their various credentials.
- IAM Access advisor (user level) - Access advisor shows the service permissions granted to a user and when those sevices were last accessed. This informartion is use to revise policies.

---

# Chapter 3: EC2 & Compute

## Amazon EC2

EC2 = Elastic Compute Cloud = Infrastructure as a service.

EC2 is one of the most populaar of AWS offerings, It mainly consists in the capability of:
- Renting virtual machines (EC2)
- Storing data on virtual drives (EBS)
- Distributing load across machines (ELB)
- Scaling the services using an auto-scaling group (ASG)

Knowing EC2 is fundamental to understand how the cloud works.

### EC2 sizing & configuartion options

- Operating System (OS): Linux, Windows or Mac OS
- How much compute power & cores (CPU)
- How much random-access memory (RAM)
- How much storage space: Network-attached (EBS & EFS), hardware (EC2 Instance Store)
- Network card: speed of the card, Public IP address
- Firewall rules: security group
- Bootstrap script (configure at first launch): EC2 User Data

### EC2 User Data

- It is possible to bootstrap our instances using an EC2 User data script. Bootstrapping means launching commands when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as: Installing updates, Installing software, Downloading common files from the internet
- Any automation task you want to run on your machine when it first loads up.
- The EC2 User Data Script runs with the root user

### EC2 Instance types 

Different types of EC2 Instances:
- General Purpose
- Compute Optimized
- Memory Optimized
- Storage Optimized
- HPC Optimized
- Accelerated Computing

## Basic Format of EC2 Instance Types

The naming convention for an EC2 instance type typically follows this pattern:

(Family)(Generation) . (Size)

For example: m5.large, t3.micro, c5.2xlarge

Breakdown of the Naming Convention Components:

### 1. Instance Family (e.g., m, t, c, r, p, etc.):

This indicates the primary use case or performance characteristic of the instance. Different families are optimized for specific workloads:

| FAMILY CODE  | PURPOSE  | 
|-------|------|
| t  | General purpose |
| m | General purpose | 
| c | Compute Optimized   | 
| r | Memory Optimized   |
| i | Storage Optimized   |
| p | Accelerated Computing   |

### 2. Generation (e.g., 5, 6, etc.):

The generation number represents updates to hardware and capabilities within each family.

Each subsequent generation improves on performance, networking, and sometimes pricing (e.g., m5 is the fifth generation of m family instances).


### 3. Size (e.g., large, xlarge, 2xlarge, etc.):

This suffix defines the virtual CPU (vCPU) count and memory size. Size often determines the amount of compute power (CPU cores) and memory provided by the instance type.

Sizes generally scale in the following progression (though some families have additional or fewer options):
nano < micro < small < medium < large < xlarge < 2xlarge < 4xlarge < 8xlarge < 16xlarge < 32xlarge

## Running a webserver on an EC2 instance

#### 1. Launch an EC2 Instance

1. Go to the EC2 Dashboard in the AWS Console and click Launch Instance.

2. Choose an Amazon Machine Image (AMI). For simplicity, you might use: Amazon Linux 2023 AMI 

3. Choose an Instance Type: t2.micro is a good starting choice since it’s part of the Free Tier and provides enough resources for basic web server tasks.

4. Configure instance details: For most setups, default settings work fine.

5. Create a new key pair and save to Desktop.

6. Configure Network settings: Click on the check box group with rules to allow HTTP (port 80) and HTTPS (port 443) traffic.

7. Scroll down on Advanced details until User-data is found. Type the following:
```
#!/bin/bash

yum update -y
yum install -y httpd

systemctl start httpd
systemctl enable httpd

echo "<h1>Hello CoderCo from $(hostname -f)</h1>">
/var/www/html/index.html
```
If you type or run the script written in an EC2 instance’s user data it will:

- Update the OS Packages: yum update -y updates all installed packages to their latest versions using the yum package manager. The -y flag automatically confirms all prompts.
- Install Apache Web Server: yum install -y httpd installs the Apache HTTP Server (httpd package). Again, the -y flag auto-confirms the installation.
- Start and Enable Apache: systemctl start httpd starts the Apache service. systemctl enable httpd enables Apache to start automatically on boot, so it will continue running even after a reboot.
- Create a Simple HTML Page: `**echo "<h1>Hello CoderCo from $(hostname -f)</h1>" > /var/www/html/index.html**` writes a simple HTML message into the Apache default document root (/var/www/html/index.html). 
- The $(hostname -f) part is replaced with the fully qualified domain name (FQDN) of the instance, so it will dynamically show the server’s hostname in the HTML content.

After running this script:

An Apache web server will be up and running on your EC2 instance.
When you navigate to the instance’s public IP in a web browser (e.g., http://<instance-public-ip>), you’ll see the message Hello CoderCo from instance-hostname displayed in an HTML h1 heading.

## EC2 Instances Purchasing Options 

- On-Demand Instances - short workload, predictable pricing, pay by second
- Reserved (1 & 3 years)
  - Reserved Instances - long workloads
  - Convertible Reserved Instances - long workloads with flexible instances
- Savings Plans (1 & 3 years) -commitment to an amount of usage, long workload
- Spot Instances - short workloads, cheap, can lose instances (less reliable)
- Dedicated Hosts - book an entire physical server, control instance placement
- Dedicated. Instances - no other customers will share your hardware
- Capacity Reservations - reserve capacity in a specific AZ for any duration

---

# Chapter 4: Security Groups & Cloud Networking

## Introduction to Security Groups

- Security Groups are the fundamental of network security in AWS.
- They control how traffic is allowed into or out of our EC2 Instances.
- Security groups only contain allow rules.
- Security group rules can reference by IP or by security group.

Security groups are acting as a 'Firewall' in EC2 instances

They regulate:
- Access to ports
- Authorised IP ranges - IPv4 and IPv6
- Control of inbound network (from their to the instance)
- Control of outbound network (from the instance to other)

![image](https://github.com/user-attachments/assets/be3c7f15-ed9a-489d-9abc-abd700bea0a8)

### How security groups work:

![image](https://github.com/user-attachments/assets/78588792-000e-4551-b5b0-8c60897ee985)

### Security groups additional information:

- Can be attached to multiple instances
- Locked down to a region / VPC combination
- Does live "outside2 the EC2 - if traffic is blocked the EC2 instance wont see it
- Good to maintain one seperate security group for SSH access
- If your application ias not accessible (time out), then its a security group issue
- If your application gives a "connection refused" error, then its an application error or its not launched
- All inbound traffic is blocked by default
- All outbound traffic is authorised by default

### Referencing other security groups:

In AWS, referencing security groups allows you to create rules that control access between instances based on security group membership rather than IP addresses. This makes it easier to manage communication between different parts of an application, especially as resources and instances scale or change.

How Security Group Referencing Works

When you create a rule within a security group, you can set another security group as the source or destination. By referencing security groups this way, you allow traffic between instances in those groups without specifying IP addresses.

![image](https://github.com/user-attachments/assets/1a006531-97cd-45f5-a38b-582f8fc4d483)

### Classic Ports to know:

- 22 = SSH (Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) - upload files into a file share
- 22 = SFTP (Secure File Transfer Protocol) - upload files using SSH
- 80 = HTTP - access unsecured websites
- 443 = HTTPS - access secured websites
- 53 - DNS - for DNS queries and resolving
- 3389 - RDP (Remote Desktop Protocol) - log into a Windows instance

## IPv4 vs IPv6

- Netowking has two sorts of IP adrdress types. IPv4 and IPv6;
  - IPv4: 10.160.10.240
  - IPv6: 3ffe:1900:4545:3:200:f8ff:fe21:67cf
- IPv4 is still the most common format
- IPv6 is newer and solves problems for the Internet of Things (IOT)
- IPv4 allows for 3.7 billion different adresses in the public space
- IPv4 [0-255].[0-255].[0-255].[0-255].  
    

## Private vs Public IP (IPv4) Example:

<img width="817" height="451" alt="image" src="https://github.com/user-attachments/assets/0a8e9022-c8a6-4469-abb2-f99582066c5a" />


Private IPs used inside private networks (e.g., home, office, or company LANs). Cannot be routed directly on the public internet. Can be reused across different organizations (e.g., Company A and Company B both use 192.168.1.0/24 internally).

Public IPs are globally unique and routable on the internet. Assigned to organizations or ISPs so devices can communicate externally.

Internet Gateway / Router acts like your home router at scale. Performs NAT (Network Address Translation):

- Translates private IPs → public IPs when sending traffic out.
- Translates public IPs → private IPs when receiving responses.

Essential for private networks to access public websites and services.

### Why It Matters:

Without an internet gateway (or home router), a private network would be isolated from the internet. NAT ensures devices in private networks can securely connect to external servers.
Public IPs remain unique, while private IPs can be reused across organizations.

## Private vs Public (IPv4) differences

### Public IP

- Public IP means the machine can be identified on the internet (WWW)
- Must be unique across the whole web (not two machines can have the same public IP)
- Can be geo located easily

### Private IP

- Private IP means the machine can only be identified on a private network only.
- The IP must be unique across the private network
- Two different private networs (two companies) can have the3 same ips.
- Machines connect to WWQ using a NAT + internet gateway (a proxy)
- Only specified range of ips can be used as a private IP.

  
## Elastic IPs

- When you stop and then start an EC2 instance, it can change its Public IP
- If you need to have a fixed oublic IP for your instance, you need an Elastic IP
- An Elastic IP is a public IPv4 IP you own as long as you dont delete it.
- You can attach it one instance at a time.
- AWS charges for Elastic IPs when they are not in use.

### How to asign an Elastic IP address to an EC2 instance:

- Go to the EC2 Dashboard in AWS Management Console. In the left menu, select Elastic IPs.
- Click Allocate Elastic IP address → choose Amazon’s pool → Allocate.
- Select the newly created Elastic IP → click Actions → Associate Elastic IP address.
- Choose your EC2 instance (or its private IP) from the dropdown.
  - If creating a new instance make sure to select Private IP instead of Public IP
- Then Click Associate.

Now your EC2 instance has a static public IP that won’t change on reboot.

### When to use Elastic IPs

- With an Elastic IP address, you can mask the faliure of an instance or software by rapidly remapping the address to another instance in your account. Useful in instances when you need to switch traffic from one instance to another without downtime.
- You can only have **5 Elastic IP** in your acount (you can ask AWS to increase that)
- Overall try avoiding using Elatic IP
  - Often reflect poor architectural decisions.
  - Instead use a random publuc IP address and register a DNS name to it
  - or, use a load balancwer and dont use a public IP.

---

# Chapter 5: Storage

## What's an EBS Volume?

- An EBS (Elastic Block Store) volume is a network drive you can attach to your instances while they run.
- It allows your instances to persist data, even after their termination
- They are bound to a specific availability zone
- **Analogy**: Think of them as a **Network USB Stick**
- **Free tier**: 30 GB of free EBS storage of type General Purpose (SSD) or magnetic per month

## AMI Overview

AMI = Amazon Machine Image

- AMI are a customization of an EC2 instance
  - You add your own software, configuration, operating system, monitoring...
  - Faster boot / configuration time because all your software is pre-packaged
-AMI are built for a specific region (and can be copied across regions)

You can launch EC2 instances from:
- A Public AMI: AWS provided
- Your own AMI: you make and maintain them yourself
- An AWS Marketplace AMI: an AMI someone else made (and potentially sells)

## Amazon EFS - Elastic File system

- What it is: AWS-managed network file system (NFS) for shared storage.
- Multi-AZ design: Data is automatically replicated across Availability Zones → high availability & durability.
- Scalable: Storage automatically grows/shrinks with usage → no need to provision or resize volumes.
- Shared access: Can be mounted to multiple EC2 instances at once → ideal for shared workloads.

- Use cases:
  - Content management systems.
  - Applications needing shared data across instances.
  - Distributed workloads.

- Trade-off: More expensive (~3× cost of GP2 EBS volumes). Best used when shared storage is essential.

Works like standard Linux NFS mounts, but fully managed by AWS.

---

# Chapter 6: Load balancing & scalability

## Scalability & high availability
Scalability means that an application / system can handle greater loads by adapting to demand

- There are two kinds of scalability:
  - Vertical scalability
  - Horizontal scalability (= elasticity)
 
Scalability is linked but different to high availability

### Vertical scalability
- Vertical scalability means increasing the size of the instance
- Fpor example, your application run on t2.micro - scaling the application vertically means running it on a t2.large.
- Vertical scalability is very cpommon for non distributed systems, such as a database 
- RDS, ElastiCache are services that can scale vertically.
- Theres usually a limit to how much you can vertically scale (hardware limit)

### Horizontal scalability
- Horizomntal scalability means increasing the number of instances / systems for your application
- Horizontal scaling implies distributed systems
- Very common for web applications / modern applications
- Its easy to horizontally scale thanks to the cloud offerings such as Amazon EC2

### High avaialability
- High Availability usually goes hand in hand with horizontal scaling
- High availability means running your application / system in at least 2 data centers (== Availability Zones)
- The goal of high availability is to survive a data center loss
- The high availability can be passive (for RDS Multi AZ for example)
- The high availability can be active (for horizontal scaling)


### High availability & scalability for EC2
- Vertical Scaling: Increase instance size (- scale up / down)
  - From: t2.nano - 0.5G of RAM, 1 vCPU
  - To: u-12tb1 metal - 12.3 TB of RAM, 448 vCPUs
- Horizontal Scaling: Increase number of instances (- scale out / in)
  - Auto Scaling Group
  - Load Balancer
- High Availability: Run instances for the same application across multi-AZ
  - Auto Scaling Group multi-AZ
  - Load Balancer multi-AZ

## Load balancing

- Definition: Distributes incoming traffic across multiple servers/EC2 instances to prevent overload and improve performance.

- Analogy: Like a restaurant with multiple chefs:
  - One chef (single instance) = overwhelmed.
  - Multiple chefs + manager (Load Balancer) = smooth operations.

### How it works (AWS ELB):
- Sits between users and EC2 instances.
- Routes requests only to healthy instances.
- Automatically redirects traffic if an instance fails.
- Keeps applications available and responsive.

### Why use a load balancer?
- Traffic Distribution: Spreads incoming requests across multiple downstream instances to avoid overload.
- Single Point of Access: Users connect via the load balancer’s DNS endpoint, not individual instance IPs.
- Failure Handling: Stops sending traffic to unhealthy instances and reroutes to healthy ones automatically.
- Health Checks: Continuously monitors instance health and redirects traffic when failures occur.
- SSL Termination (HTTPS): Handles SSL certificates and encryption/decryption, offloading work from instances.
- Sticky Sessions (Session Persistence): Ensures users remain connected to the same instance when needed.
- High Availability Across AZs: Distributes traffic across multiple Availability Zones for resilience.
- Traffic Separation: Can route public traffic (user-facing) separately from private traffic (internal).

### Why use an Elastic load balancer
- An Elastic Load Balancer is a managed load balancer
  - AWS guarantees that it will be working
  - AWS takes care of upgrades, maintenance, high availability
  - AWS provides only a few configuration knobs
- It costs less to setup your own load balancer but it will be a lot more effort on your end
- It is integrated with many AWS offerings / services
  - EC2, EC2 Auto Scaling Groups, Amazon ECS
  - AWS Certificate Manager (ACM), CloudWatch
  - Route 53, AWS WAF, AWS Global Accelerator

### Health checks

- Health checks are crucial for mload balancers
- They enable the load balancer to know if instances it forwards traffic to are available to reply to requests
- The health check is done on a port and a route (/health is comnmon)
- If the response is not 200 (OK), then the instance is unhealthy and the load balancer will stop sending traffic to it


## Types of load balancers on AWS

AWS has 4 kinds of managed Load Balancers
-Classic Load Balancer (v1 - old generation) - 2009 - CLB
  - HTTP, HTTPS, TCP, SSL (secure TCP)
- Application Load Balancer (v2 - new generation) - 2016 - ALB
  - HTTP, HTTPS, WebSocket
- Network Load Balancer (v2 - new generation) - 2017 - NLB
  - TCP, TLS (secure TCP), UDP
- Gateway Load Balancer - 2020 - GWLB
  - Operates at layer 3 (Network layer) - IP Protocol

Overall, it is recommended to use the newer generation load balancers as they provide more features

Some load balancers can be setup as internal (private) or external (public) ELBs

### Load Balancer security groups
<img width="816" height="457" alt="image" src="https://github.com/user-attachments/assets/ee5bdc60-09f8-4a80-97fc-104506258253" />

- **Security Groups (SGs)** = Virtual firewalls controlling inbound/outbound traffic in AWS.  
- **Load Balancer SG**:  
  - Allows **HTTP (80)** and **HTTPS (443)** traffic from the internet (`0.0.0.0/0`).  
  - Ensures users can connect publicly to your application.  
- **Application/EC2 Instance SG**:  
  - Restricts access so only the **Load Balancer SG** can send traffic.  
  - Prevents direct internet access to instances → adds protection.  
- **Two-Tier Setup**:  
  - Users → Load Balancer (public access).  
  - Load Balancer → EC2 instances (controlled private access).  
- **Benefits**:  
  - Shields backend instances from direct exposure.  
  - Ensures secure, controlled, and scalable traffic flow.  
  - Common cloud architecture best practice.
 
### Application Load Balancer

- Application load balancers is Layer 7 (HTTP)
- Load balancing to multiple HTTP applications across machines (target groups)
- Load balancing to multiple applications on the same machine (ex: containers)
- Support for HTTP/2 AND Websocket
- Support redirects (from HTTP to HTTPS)
- Routing tables to different target groups:
  - Routing based on path in URL (coderco.io/users & coderco.io/posts)
  - Routing based on hostname in URL (blog.coderco.io & news.coderco.io)
  - Routing based on Query String, Headers(coderco.io/users?id=456&order=false)
- ALB are a great fit for micro services & container-based application(example: Docker & Amazon ECS)
  - Has a port mapping feature to redirect to a dynamic port in ECS
- In comparison, we'd need multiple Classic Load Balancer per application


### Application Load balancer (HTTP Based Traffic)

<img width="814" height="460" alt="image" src="https://github.com/user-attachments/assets/975b7316-72d7-474c-836e-2810367861d7" />

Routes HTTP/HTTPS requests to backend resources.

- Target Groups:
  - Consist of EC2, ECS, or Lambda functions.
  - Each group handles a specific service (e.g., user profiles, product search).

- Routing Rules:
  - Direct traffic based on path, host, or headers.
  - Ideal for microservices or apps with multiple features.

Health Checks: Continuously monitor instances in each target group. Unhealthy instances are removed from routing automatically.

Key Benefits:
- Supports multiple services behind a single load balancer.
- Isolates services so one does not impact another.
- Improves scalability, performance, and reliability for web applications.

### Application Load Balancer (Target Groups)
- EC2 instances (can be managed by an Auto Scaling Group) - HTTP
- ECS tasks (managed by ECS itself) - HTTP
- Lambda functions - HTTP request is translated into a JSON event
- IP Addresses - must be private IPs
- ALB can route to multiple target groups
- Health checks are at the target group level


### Application Load Balancer - Good to know

<img width="815" height="458" alt="image" src="https://github.com/user-attachments/assets/e4911feb-f6db-486b-9b6d-0b9bcce21fca" />


### Network Load Balancer

- Network load balancers (Layer 4) allow to:
  - Forward TCP & UDP traffic to your instance
  - Handle millions of requests per seconds
  - Less latency - 100 ms (vs 400 ms for ALB)
- NLB has one static IP per AZ and supports assigning Elastic IP (Helpful for whitelisting specific IP)
- NLB are used for extreme performance, TCP or UDP traffic
- Not included in AWS free tier. 

### Network Load Balancer - TCP (Layer 4)

<img width="817" height="459" alt="image" src="https://github.com/user-attachments/assets/e2d61147-740d-4134-9d69-0c1347042481" />

- Users → Network Load Balancer (NLB)
  - Users send TCP/UDP requests.
  - NLB receives traffic at Layer 4 (transport layer).

- NLB Function
  - Forwards traffic based on ports/protocols (not application-level details).
  - Does not inspect HTTP headers or handle SSL termination.
  - Focuses on fast, efficient packet forwarding.

- Target Groups
  - NLB routes traffic to different target groups (EC2, services, etc.).
  - Each target group can handle a specific application.
    - Example: User Application → traffic routed via TCP rules.
    - Example: Search Application → routed through TCP, though HTTP rides on TCP.

### Sticky sessions (Session Affinity)

- It is possible to implement stickiness so that the same client is always redirected to the same instance behind a load balancer.
- This works for Classic Load Balancer, Application Load Balancer, and Network Load Balancer.
- or both CLB & ALB, the "cookie" used for stickiness has an expiration date you control.
- Use Case: Make sure the user doesn't lose his session data.
- Enabling Stickiness may bring imbalance to the load over the backend EC2 instances.


## SSL/TLS - Basics

- An SSL Certificate allows traffic between your clients and your load balancer to be encrypted in transit (in-flight encryption)
- SSL refers to Secure Socket Layer, used to encrypt connections
- TLS refers to Transport L;ayer Security, which is a newer version
- TLS Certifications are mainly used, but people still refer to SSL
- Public SSL certificates are used by certificate authorities (CA) e.g. Comodo, symantec, GoDaddy, GlobalSign, Digicert, Letsencrypt
- SSL certificates have an expiration date (You set) and must be renewed

### Load Balancer - SSL Certificates

- The load Balancer uses an X.509 certificate ( SSL/TLS server certificate)
- You can manage certificates using ACM (AWS Certificate Manager)
- You can create upload your own certificates alternatively
- HTTPS listener:
  - You must specify a default certificate
  - You can add an optional list of certs to support multiple domains.
  - Clients can use SNI (Server Name Indication) to specify the hostname they reach
  - Ability to specify a security policy to support older versions of SSL/TLS (legacy clients)


### SSL - Server Nasme Indication (SNI)

- SNI solves the problem of loading multiple SSL Cerificates onto one web server (to serve multiple websites)
- Its a newer protocol, and requires the client to indicate the hostname of the target server in the inital SSL handshake.
- The server will then find the correct certificate, or return the default one.
- Note:
  - Only works for ALB & NLB(newer genration), CloudFront
  - Does not work for CLB (Older gen)


### Elastic Load Balancers - SSL Certificates

- Classic Load Balancer (v1)
  - vSupport only one SSL certificate
  - Must use multiple CLB for multiple hostname with multiple SSL certificates.
- Application Load Balancer (v2)
  - Supports multiple listener with multiple SSL certificates
  - Uses server name indication (SNI) to make it work
- Network Load Balancer (v2)
  - Supports multiple listeners with multiple SSL certificates.
  - Uses server name indication (SNI) to make it work.


### Connection Draining

- Purpose: Ensures smooth user experience when removing an instance from a load balancer.

- How it works:
  - Load balancer stops sending new requests to the instance.
  - Existing in-flight requests are allowed to finish.
- Feature naming:
  - Classic Load Balancer (CLB) → Connection Draining.
  - ALB & NLB → Deregistration Delay.
- Configurable timeout range: 1 – 3,600 seconds. Default is 300 seconds (5 minutes). Can be set lower for short requests, or 0 for instant cutoff.
- Use case:
  - Helpful during scaling or when removing unhealthy instances.
  - Prevents abrupt disconnections and maintains seamless user experience.

## Auto Scaling Group

In real life, the load on your websites and application can change. In the cloud you can create or get rid of servers very quickly.

- The goal of an auto scaling group (ASG) is to:
  - Scale out (add EC2 instances) to amtch an increased load
  - Scale in (remove EC2 instances) to match a decreased load
  - Ensure we have a minimum and a maximum number of EC2 instances running
  - Automatically register new instances to a load balancer
  - Re-Create an EC2 instance in case a previos one is terminated ( example: if unhealthy)


### Auto scaling in AWS

<img width="819" height="449" alt="image" src="https://github.com/user-attachments/assets/de31e8f9-b946-4ffa-aab5-2810437d1a9d" />

### Auto Scaling Groups (ASG) in AWS  

- Purpose: Automatically adjusts the number of EC2 instances based on demand.  
- Core settings:  
  - **Minimum Capacity** → lowest number of instances always running.  
  - **Desired Capacity** → target/normal number of instances.  
  - **Maximum Capacity** → upper limit of instances allowed.  
- Scaling actions:  
  - **Scale Out** → add instances when traffic increases (up to max).  
  - **Scale In** → remove instances when traffic decreases (down to min).  
- Benefits:  
  - Keeps applications responsive during high load.  
  - Saves costs by reducing instances when demand is low.  
  - Ensures capacity always stays within configured limits.  

### Auto scaling group in AWS with load balancer

<img width="815" height="460" alt="image" src="https://github.com/user-attachments/assets/379d8884-6929-4c30-bb65-791605c21694" />

### Auto Scaling Group in AWS with Load Balancer  

- Users: Send traffic to your application (website, mobile app, or service).  
- Load Balancer (ALB):  
  - Distributes incoming traffic across EC2 instances.  
  - Prevents any single instance from being overloaded.  
  - Performs continuous **health checks** on instances.  
  - Stops routing traffic to unhealthy instances.  
- Auto Scaling Group (ASG):  
  - Dynamically adjusts the number of EC2 instances based on demand.  
  - **Scale Out** → adds more instances during high traffic.  
  - **Scale In** → removes instances during low traffic to save costs.  
- **Custom AMIs**:  
  - ASG can launch new instances from **preconfigured Amazon Machine Images (AMIs)**.  
  - Ensures each new instance is ready with the required software/configuration.  

### Auto Scaling Group Activities – Key Attributes  

- Launch Templates (replacing older launch configurations): Define consistent setup for all new EC2 instances.  

- Core attributes:  
  - AMI (Amazon Machine Image) → ensures all instances have the same pre-configured setup.  
  - Instance Type → defines compute, memory, or storage optimization (e.g., T2, C, M, R families).  
  - EC2 User Data (optional) → startup scripts for installing packages or configuring software.  
  - EBS Volumes→ persistent storage for instances.  
  - Security Groups → virtual firewalls controlling inbound/outbound traffic.  
  - SSH Key Pair → secure remote access to instances.  
  - IAM Roles → grant instances permissions to access other AWS services without storing keys.
  - Network & Subnets → specify VPC and subnets where instances launch.  
  - Load Balancer Info → automatically register new instances with a load balancer.  

- ASG-specific attributes:  
  - Minimum Size → lowest number of instances always running.  
  - Maximum Size → upper limit of instances.  
  - Desired/Initial Capacity → starting/target number of instances.  
  - Scaling Policies → rules for scaling in/out based on metrics like traffic or performance.  

- Benefit: Ensures every instance launched by the ASG follows the same configuration, maintaining consistency, scalability, and reliability.  

### Auto Scaling - Cloud Watch Alarms & Scaling

- It is possible to scale an ASG based on CloudWatch alarms
-  An alarm monitors a metric (such as Average CPU, or a custom metric)
- Metrics such as Average CPU are computed for the overall ASG instances
- Based on the alarm:
  - We can create scale-out policies (increase the number of instances)
  - We can create scale-in policies (decrease the number of instances)


### Auto Scaling Groups - Scaling Policies

There are 3 main types of dynamic scaling policies:

- 1. Target Tracking Scaling:
  - Simple to set up
  - Example: I want the average ASG CPU to stay at around 40%

- 2. Simple / Step Scaling:
   - When a CloudWatch alarm is triggered (example CPU > 70%), THEN ADD 2 UNITS
   - When a CloudWatch alarm is triggered (example CPU < 30%), THEN REMOVE 1

- 3. Scheduled Scaling:
  - Anticipate a scaling based on known usage patterns
  - Example: increase the min capacity to 10 at 5pm on Fridays

---

# Chapter 7: Containers

## Containers on AWS – Introduction to Docker and Containers  

- What is Docker?  
  - A platform to build, ship, and run applications anywhere.  
  - Packages app code, libraries, dependencies, and runtime into a portable container.  
  - Ensures applications run consistently across environments.  

- What is a Container?  
  - A lightweight, portable unit that holds everything an app needs to run.  
  - Provides the same runtime environment across local machines, servers, and cloud.  
  - Solves the classic “works on my machine” problem.  

- Why use Docker? 
  - **Portability** → run containers on any system with Docker installed.  
  - **Consistency** → same behavior across dev, staging, and production.  
  - **Speed** → lightweight, start quickly, and use fewer resources than VMs.  
  - **Simplicity** → deployment is easier since everything is bundled into the container.  

- How it works:  
  - Applications are packaged into a container image (blueprint).  
  - Docker uses the image to create running containers (instances of the app).  
  - Containers can be deployed on local servers, colleagues’ machines, or the cloud → same behavior everywhere.  


## Docker on an OS

- How Docker runs on an OS:  
  - Docker Engine (container runtime) is installed on a server (EC2, local machine, etc.).  
  - Instead of installing apps directly on the host OS, apps are packaged into **containers**.  

- Containers on the OS:  
  - Each container runs an isolated application (e.g., Java, Nginx, MySQL).  
  - Containers share the **host OS kernel** but keep processes, memory, and files separate.  
  - Multiple versions of the same software can run without conflicts (e.g., two different Java versions).  

- Why containers are lightweight:  
  - They don’t include a full OS → share host kernel.  
  - Faster startup and lower resource usage compared to VMs.  

- Benefits:  
  - Isolation between applications → avoids version/dependency conflicts.  
  - Consistency across environments (dev, staging, production).  
  - Run multiple applications side by side without interference.  


### Where are docker images stored?

- Docker images are stored in Docker repositories.
- Docker Hub
  - Public repository
  - Find the base images for amny technologies or OS (e.g. Ubuntu, MYSQL)
- Amazon ECR (Amazon Elastic Container Registry)
    - Private repository
    - Public repository (Amazon ECR Public Gallery)

### Docker vs Virtual Machines  

<img width="816" height="455" alt="image" src="https://github.com/user-attachments/assets/3310fa6a-0975-4a0a-b9a0-fb2b15b24842" />


| Feature              | Virtual Machines (VMs)                          | Docker (Containers)                                  |
|----------------------|-------------------------------------------------|-----------------------------------------------------|
| **Isolation**        | Full system virtualization with its own OS      | OS-level isolation, apps share host OS kernel       |
| **Guest OS**         | Each VM has its own OS (Ubuntu, Windows, etc.)  | No separate OS, only app + dependencies             |
| **Resource Usage**   | Heavy, high CPU & memory usage                  | Lightweight, low overhead                           |
| **Boot Time**        | Slow to start/stop                              | Very fast to start/stop                             |
| **Manager**          | Managed by a **Hypervisor**                     | Managed by the **Docker Daemon**                    |
| **Portability**      | Limited, tied to VM image and OS                | Highly portable, runs anywhere Docker is installed  |
| **Scalability**      | Fewer VMs per host (due to resource overhead)   | Many containers per host (lightweight)              |
| **Virtualization**   | Virtualizes **hardware**                        | Virtualizes the **OS**                              |
| **Use Case**         | When full OS isolation is required              | When speed, efficiency, and portability are needed  |

**Key Difference:**  
- VMs **virtualize hardware** (full operating systems on one machine).  
- Docker **virtualizes the operating system** (isolated apps running on the same kernel).  


### Getting Started With Docker:

<img width="816" height="455" alt="image" src="https://github.com/user-attachments/assets/f36a5222-771d-49a7-8a5d-0afb6f8997c4" />

The diagram above shows the basic flow of working with Docker:  

1. **Dockerfile (Blueprint)**  
   - A text file with instructions on how to build a Docker image.  
   - Example steps:  
     - `FROM ubuntu:18.04` → choose a base image.  
     - `COPY . /app` → copy app files into the image.  
     - `RUN make /app` → run commands to set up dependencies.  
     - `CMD python3 /app/app.py` → default command when the container runs.  

2. **Build the Image**  
   - Run `docker build` to create an image from the Dockerfile.  
   - This packages your app, its dependencies, and environment into one portable unit.  

3. **Run the Container**  
   - Start the container with `docker run <image-name>`.  
   - The application (e.g., a Python app) runs inside the container.  

4. **Push & Pull from Registries**  
   - Images can be **pushed** to registries like **Docker Hub** or **Amazon ECR**.  
   - Later, they can be **pulled** to run on any system with Docker installed.  

**Summary**:  
- The **Dockerfile** is the recipe.  
- **Build** creates an image.  
- **Run** launches a container from that image.  
- **Push/Pull** share or deploy the image via a registry.  

This flow ensures your app runs consistently across local, staging, and production environments.  

### Container Related Service on AWS

- Amazon Elastic Container Service (Amazon ECS) - Amazon own cpontainer platform.
- Amazon Elastic Kubernetes Service (Amazon EKS) - Amazon managed Kubernetes (open source)
- Amazon Fargate - Amazons own serverless container platform, works with ECS and EKS
- Amazon ECR - Store container images


## Amazon ECS 

### EC2 Launch type

<img width="361" height="381" alt="image" src="https://github.com/user-attachments/assets/a6497e1d-9fc2-4217-83d6-ae3b28a45d45" />


- ECS = Elatic Container Service
- Launch Docker containers on AWS = Launch ECS Tasks on ECS Clusters
- EC2 Launch type: you must provision & maintain the infrastructure (the EC2 instances)
- Each EC2 instance must run the ECS agent to register in the ECS cluster
- AWS takes care of starting/stopping containers

### Fargate Launch Type

<img width="322" height="312" alt="image" src="https://github.com/user-attachments/assets/84dce803-8947-42fd-978f-404d876c32c2" />

- Launch Docker Containers on AWS
- You do not provision the infrastructure (no EC2
instances to manage)
- Its all Serverless!
- You just create task definitions
- AWS just runs ECS tasks for you based on the CPU / RAM you need.
- To scale, just increase the number of tasks. Simple - no more EC2 instances.

### IAM Roles for ECS

- EC2 instance Profile (EC2 Launch Type only):
  - Used by the ECS agent
  - Makes API calls to ECS service
  - Send container logs to CloudWatch Logs
  - Pull Docker image from ECR
  - Reference sensitive data in Secrets
  - Manager or SSM Parameter Store
- ECS Task Role:
  - Allows each task to have a specific role.
  - Use different roles for the different ECS services you run
  - Task role is defined in the task definition

### Load Balancer Integrations

- Application Load Balancer supported and works for most use cases.
- Network Load Balancer recommended only for high throughput/high performance use cases, or to pair it with AWS Private Link.
- Classic Load Balancer supported but not recommended (no advanced features - no Fargate)

### ECS Service Auto Scaling

- Automatically increase/decrease the desired number of ECS tasks
- Amazon ECS Auto Scaling uses AWS Application Auto Scaling to make keys decisions based on metrics like: 
  - ECS Service Average CPU Utilization
  - ECS Service Average Memory Utilization - Scale on RAM
  - ALB Request Count Per Target - metric coming from the ALB

Scaling strategies:

- Target tracking - Scale based on target value for a specific CloudWatch metric.
- Step Scaling - Scale based on a specified CloudWatch Alarm
- Scheduled Scaling - Scale based on a specified date/time (predictable changes)

- ECS Service Auto Scaling (Task Level) - EC2 Auto Scaloing (EC2 instance level)
- Fargate Auto Scaling is much easier to setup because serverless

## Amazon ECR

 Amazon ECR is a fully managed container image registry on AWS. Works like a cloud-based Docker Hub for storing and managing images.  

- Repository Types:  
  - Private Repositories → for internal, sensitive images.  
  - Public Repositories → for open-source or shared images (Amazon ECR Public Gallery).  

- Seamlessly integrated with Amazon ECS (ECS tasks can pull images directly from ECR). Images are stored securely in Amazon S3 behind the scenes.  
- Access is controlled by IAM policies (only authorized users/services can access private images).  

- Additional Features:  
  - Versioning → tag and manage multiple image versions.  
  - Lifecycle policies → automatically clean up old/unneeded images.  
  - Supports vulnerability scanning for security checks.  

## Amazon EKS 

Amazon EKS = Amazon Elastic Kubernetes Service. It is a way to launch managed Kubernetes clusters on AWS

- Kubernetes is an open-source system for automatic deployment, scaling and management of containerized (usually Docker) application. Its an alternative to ECS, Similar goal but different API.
- EKS supports EC2 if you want to deploy worker nodes or Fargate to deploy serverless containers.
- Use case: If your company is already using Kubernetes on- premises or in another cloud and wants to migrate to AWS using Kubernetes.
- Kubernetes is cloud-agnostic (can be used in any cloud - Azure, GCP...)
- For multiple regions, deploy one EKS cluster per region.
- Collect logs and metrics using CloudWatch Container Insights.


### Amazon EKS Diagram

<img width="792" height="408" alt="image" src="https://github.com/user-attachments/assets/41e2a770-f62d-4416-875f-5f71a8af4297" />

The diagram above shows the key components of an Amazon EKS (Elastic Kubernetes Service) setup.  

- EKS Worker Nodes  
  - EC2 instances running Kubernetes worker processes.  
  - Managed in an **Auto Scaling Group (ASG)** → scale in/out automatically with traffic.  

- EKS Pods
  - Smallest unit in Kubernetes, running inside worker nodes.  
  - Each pod = one or more containers grouped to handle tasks.  

- VPC (Virtual Private Cloud  
  - Provides a private, isolated network for EKS resources.  
  - Ensures secure communication between components.  

- Availability Zones (AZs  
  - Setup spans multiple AZs for high availability.  
  - If one AZ fails, workloads continue in others.  

- Private Subnets  
  - Worker nodes run inside private subnets → not exposed directly to the internet.  

- Elastic Load Balancer (ELB  
  - Distributes incoming user traffic across EKS nodes.  
  - Routes requests only to healthy nodes for reliability.  

- NAT Gateway (NGW  
  - Allows nodes in private subnets to access the internet securely.  
  - Used for pulling Docker images, updates, and patches.  
  - Prevents direct public exposure of nodes.  

Summary:  
Amazon EKS provides a scalable, secure, and fault-tolerant Kubernetes environment on AWS.  
- **Load Balancers** handle incoming traffic.  
- **NAT Gateways** enable safe outbound internet access.  
- **Worker Nodes + Pods** run your workloads.  
- **Multi-AZ architecture** ensures resilience and high availability.  


### Amazon EKS - Node Types

-Managed Node Groups
  - Creates and manages nodes 9EC2 instances) for you
  - Nodes are part of an ASG Managed by EKS
  - Supports On-Demand or Spot instances
- Self-Managed Nodes
  - Nodes created by you and registered to the EKS cluster and managed by an ASG
  - You can use prebuilt AMI - Amazon EKS optimized AMI
  - Supports On-Demand or Spot Instances
- AWS Fargate
  - No maintenance required; no nodes managed

---

Chapter 8: Serverless
































































































































