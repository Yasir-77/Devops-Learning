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

- Availability Zones (AZs)  
  - Setup spans multiple AZs for high availability.  
  - If one AZ fails, workloads continue in others.  

- Private Subnets  
  - Worker nodes run inside private subnets → not exposed directly to the internet.  

- Elastic Load Balancer (ELB)  
  - Distributes incoming user traffic across EKS nodes.  
  - Routes requests only to healthy nodes for reliability.  

- NAT Gateway (NGW)  
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
  - Creates and manages nodes EC2 instances) for you
  - Nodes are part of an ASG Managed by EKS
  - Supports On-Demand or Spot instances
- Self-Managed Nodes
  - Nodes created by you and registered to the EKS cluster and managed by an ASG
  - You can use prebuilt AMI - Amazon EKS optimized AMI
  - Supports On-Demand or Spot Instances
- AWS Fargate
  - No maintenance required; no nodes managed

---

# Chapter 8: Serverless

## Serverless overview

- Serverless is a new paradigm in which th edevelopers dont have to manage servers anymore, they just depoly ccode and functions!
- Initially serverless = Faas (Function as a service)
- Serverless was pioneered by AWS lambda but now includes anything thats managed: "databases, messaging, storage, etc.."
- Serverless doent mean there are no servers - it means you just dont manage/provision/see them

### Serverless in AWS

### Serverless in AWS – Overview  

Serverless means you don’t manage servers — AWS provisions, scales, and manages the infrastructure for you.  
Here are the key AWS serverless services:  

- AWS Lambda: Core serverless compute service. Run code in functions without managing servers.  

- Amazon DynamoDB: Fully-managed, serverless NoSQL database. Scales automatically with demand.  

- Amazon Cognito: Handles **user authentication** (signups, logins). Simplifies scaling apps with secure user management.  

- Amazon API Gateway: Acts as a bridge between users and backend services. Routes requests to **Lambda** or other AWS services.  

- Amazon S3: Serverless object storage for files and static content. Automatically scales with data.  

- Amazon SNS (Simple Notification Service): Pub/sub messaging system for sending notifications.  

- Amazon SQS (Simple Queue Service): Message queuing between distributed system components.  

- Amazon Kinesis Data Firehose: Ingests and loads **real-time streaming data** into AWS. Useful for analytics pipelines.  

- Amazon Aurora Serverless: Managed **relational database** that auto-scales.  

- AWS Step Functions: Orchestrates workflows across multiple Lambdas/services. Useful for complex, multi-step applications.  

- AWS Fargate: Serverless compute for containers. No need to manage EC2 instances running your containers.  

**Summary**:  
AWS Serverless services cover compute, databases, storage, messaging, and orchestration — all designed to scale automatically while removing the need to manage servers.


## AWS Lambda vs. EC2  

**Amazon EC2 (Elastic Compute Cloud):**  
- Virtual servers (VMs) in the cloud.  
- You choose CPU, memory, and storage for each instance.  
- Billed for uptime → even when instances sit idle.  
- Scaling requires manual configuration or Auto Scaling setup.  
- Full control over OS, runtime, and infrastructure.  

**AWS Lambda:**  
- **Serverless** → no servers to manage.  
- Executes short-lived tasks (max runtime: **15 minutes**).  
- **Event-driven** → runs in response to triggers (e.g., file upload, API call).  
- **On-demand billing** → only pay for actual execution time.  
- **Automatic scaling** → from 1 user to 1 million users with no manual setup.  

**Summary:**  
- With **EC2**, you manage virtual machines and infrastructure.  
- With **Lambda**, you focus only on your code → AWS handles infrastructure, scaling, and billing efficiency.  


### Benefits of AWS Lambda

- Easy Pricing:
  - Pay per request and compute time
  - Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
- Integrated with the whole AWS suite of services
- Integrated with many programming languages
- Easy monitoring through AWS Cloud Watch
- Easy to get more resources per functions (up to 10GB of RAM!), increasing RAM will also improve CPU and network!

### AWS Lambda Language Support

- Node.js (JavaScript)
- Python
- Java
- C#(.NET Core)/Powershell
- Ruby
- Custom Runtime API

**Lambda with Container Images**  
- Package your application (including dependencies) into a **Docker container image**.  
- Lambda can run the container if it implements the **Lambda Runtime API**.  
- Useful for complex setups where standard runtimes aren’t enough.  

**Note**: For more general-purpose or custom Docker containers, **Amazon ECS with Fargate** may be a better fit since it offers more flexibility.  

### Examples: Serverless Thumbnail creation

<img width="813" height="448" alt="image" src="https://github.com/user-attachments/assets/95f3d9fb-0d46-4a58-b1e6-d1a460b39bd7" />

The diagram shows a real-world serverless workflow using **S3, Lambda, and DynamoDB**:  

1. Upload to S3 (Trigger Event): A user uploads a new image (e.g., beach photo) to an S3 bucket. This upload automatically triggers an event notification.  

2. AWS Lambda Function: The event invokes a Lambda function. The function’s job: create a smaller thumbnail version of the uploaded image.  

3. Output – Thumbnail in S3: Lambda pushes the generated thumbnail back into S3. Both the original image and the thumbnail are now stored.  

4. Output – Metadata in DynamoDB: Lambda also pushes image metadata (e.g., name, size, timestamp) into DynamoDB. This provides a record of the uploaded and processed image.  

**Why this is powerful**  
- Entire process is fully automated — no manual steps.  
- Serverless → no servers to manage, AWS handles everything.  
- Scales automatically → works whether you upload one image or thousands.  
- Cost-efficient → you only pay for: Lambda execution time, Storage in S3, Metadata storage in DynamoDB.  

---

# Chapter 9: AWS Networking

## Understanding CIDR – IPv4  

CIDR stands for Classless Inter-Domain Routing. It’s a method for allocating and representing IP address ranges.  

- Format:  
  - Written as an IP address + slash + number (e.g., `192.168.0.0/26`).  
  - The number after the slash (`/`) is called the subnet mask.  

- How it works:  
  - Base IP → starting point of the range (e.g., `192.168.0.0`).  
  - Subnet Mask → determines how many bits can vary → defines the size of the range.  

- Examples:  
  - `0.0.0.0/0` → all IPs (everything, everywhere).  
  - `192.168.0.1/32` → a single IP address.  
  - `192.168.0.0/26` → a block of 64 IP addresses.  
  - `/8`, `/16`, `/24`, `/32` → common CIDR notations.  

- Subnet mask:  
  - The smaller the number after the slash → the larger the IP range.  
  - The bigger the number after the slash → the smaller/more specific the range.  

Use Cases in AWS:  
- Defining VPC IP ranges.  
- Configuring security groups and network ACLs.  
- Restricting access to specific IPs or IP ranges.  

## Understanding CIDR - Subnet Mask

<img width="813" height="455" alt="image" src="https://github.com/user-attachments/assets/20ce6b40-9035-4fea-a42c-87edbf7df3e9" />

## Public Vs Private IP (IPv4)

- The Internet Assigned Numbers Authority (IANA) established certain blocks of IPv4 addresses for the use of private (LAN) and public (Internet) addresses
- Private IP can only allow certain values:
  - 10.0.0.0 - 10.255.255.255 (10.0.0.0/8) < in big networks
  - 172.16.0.0 - 172.31.255.255 (172.16.0.0/12) < AWS default VPC in that range
  - 192.168.0.0 - 192.168.255.255 (192.168.0.0/16) < e.g., home networks
• All the rest of the IP addresses on the Internet are Public

## Default VPC Walkthrough

- All new AWS aacounts have a default VPC
- New EC2 instances arae launched into the default VPC if no subnet is specified
- Default VPC has internet connectivity and all EC2 instancess inside it have public IPv4 addresses
- We also get a public and a private IPv4 DNS names 

## VPC - Subnet (IPv4)

AWS reserves 5 IP addresses (first 4 & last 1) in each subnet. These 5 IP addresses are not available for use and can't be assigned to an EC2 instance
- Example: if CIDR block 10.0.0.0/24, then reserved IP addresses are:
  - 10.0.0.0 - Network Address
  - 10.0.0.1 - reserved by AWS for the VPC router
  - 10.0.0.2 - reserved by AWS for mapping to Amazon-provided DNS (IP address of DNS server)
  - 10.0.0.3 - reserved by AWS for future use
  - 10.0.0.255 - Network Broadcast Address. AWS does not support broadcast in a VPC, therefore the address is reserved
- For example, if you need 29 IP addresses for EC2 instances:
  - You can't choose a subnet of size /27 (32 IP addresses, 32 - 5 = 27 < 29)
  - You need to choose a subnet of size /26 (64 IP addresses, 64 - 5 - 59 > 29)

## Internet Gateway (IGW)

- IGW allows resources (e.g. EC2 instances) in a VPC to connect to the internet
- It scales horizontally and is highly available and redundant.
- Must be created separately from a VPC - One VPC ccan only be attached to One IGW and vice versa
- Internet Gateways on their own do not allow internet access
- Route tables must also be updated - To enable traffic to go where it should

## Bastion Hosts

- We can use a Bastion Host to SSH into our private EC2 instances
- The bastion is in the public subnet which is then connected to all other private subnets
- Bastion Host security group must allow inbound from the internet on port 22 from restricted CIDR, for example
the public CIDR of your corporation
- Security Group of the EC2 Instances must allow the Security Group of the Bastion Host, or the private IP of the
Bastion host

<img width="310" height="386" alt="image" src="https://github.com/user-attachments/assets/d90687df-0323-49da-bc68-80e1b62c9baa" />

## NAT Gateway

### NAT Gateway in AWS Networking  

- NAT = Network Address Translation.  
- A NAT Gateway lets instances in a **private subnet** connect to the internet, while blocking any **inbound traffic** from the internet.  
- Common use: private EC2 instances downloading updates or accessing external APIs without being exposed publicly.  

Key details:  
- Managed service → AWS handles scaling, availability, and maintenance.  
- Billing → charged per hour + bandwidth used.  
- AZ-specific → tied to a single Availability Zone.  
  - For redundancy, create a NAT Gateway in each AZ.  
- Requires an **Internet Gateway** in the VPC to connect out. (Private Subnet => NATGW => IGW)  
- Cannot be used by EC2 instances in the same subnet → must be in another subnet.  
- Provides 5 Gbps bandwidth by default, scales up to 100 Gbps automatically.  
- Uses an Elastic IP for external connectivity.  
- No security groups required → simpler than NAT instances.  

Summary:  
A NAT Gateway enables **outbound internet access** for private subnets without exposing those instances directly to the internet. It’s secure, scalable, and low maintenance — ideal for production environments where you need tight control over inbound traffic.  


### NAT Gateway with High Availability  

A NAT Gateway is highly available, but only within a single Availability Zone (AZ). 

- Risk:  
  - If the AZ hosting your NAT Gateway goes down, all resources depending on it lose internet access.  
  - Even if EC2 instances in other AZs are healthy, they cannot reach the internet if they rely on that single NAT Gateway.  

- Solution:  
  - Create one NAT Gateway per AZ.  
  - Ensure that subnets in each AZ use the NAT Gateway in their own AZ.  
  - This prevents a single point of failure and keeps internet access available if one AZ fails.  

This would ultimately increases fault tolerance and ensures high availability and supports disaster recovery strategies.  

<img width="500" height="560" alt="image" src="https://github.com/user-attachments/assets/cc393dc1-9d63-4636-b744-ca5911cd86d0" />

### NAT Gateway vs NAT Instance  

| Feature              | NAT Gateway (Managed Service)                     | NAT Instance (EC2-based)                       |
|----------------------|---------------------------------------------------|------------------------------------------------|
| Availability         | Highly available within an AZ; add one per AZ for full redundancy | Use a script to manage failover between instances|
| Bandwidth            | Scales automatically, up to 100 Gbps              | Limited by EC2 instance type                   |
| Maintenance          | Fully managed by AWS (no patches or updates needed) | User-managed (OS updates, patches, software)   |
| Cost                 | Simple: per hour + data processed                 | Based on EC2 instance pricing + data charges   |
| Public IPv4          | Supported                                         | Supported                                      |
| Security Groups      | Not required (AWS manages security)               | Can attach security groups like any EC2        |
| Bastion Host Usage   | Not possible                                      | Can also serve as a bastion (jump box)         |
| Best For             | Hands-off, scalable, high-bandwidth setups        | Flexible, lower-cost, more manual control      |

## Networking Access Control List (NACL)

NACL are like firewall which control traffic from and to subnets - One NACL per subnet, new subnets are assigned to the Default NACL
- You define NACL rules:
  - Rules have a number (1-32766), higher precedence with a lower number
  - First rule match will drive the decision
  - Example: if you define a #100 ALLOW 10.0.0.10/32 and #200 DENY 10.0.0.10/32, the IP address will be allowed because 100 has a higher precedence over 200.
  - The last rule is an (*) and denies a request in case of no rule match
  - AWS recommends adding rules by increment of 100
- Newly created NACLs will deny everything
- NACL are a great way of blocking a specific IP address at a subnet level


## Security Groups & NACLs
<img width="814" height="401" alt="image" src="https://github.com/user-attachments/assets/efeaff00-f3d6-486e-a9f8-0b874701b743" />

Security Groups → work at the instance level (control traffic to/from EC2 instances).  

NACLs → work at the subnet level (control traffic at subnet boundaries, affecting all resources).  

- Statefulness: 
  - Security Groups are stateful:  
    - If inbound traffic is allowed, the response outbound traffic is automatically allowed.  
    - No need to create separate outbound rules for responses.  
  - NACLs are stateless:  
    - You must explicitly allow inbound and outbound traffic.  
    - Allowing one direction does not automatically allow the reverse.  

- **Incoming Request (from outside to EC2)**  
  1. Traffic hits **NACL inbound rules** (subnet level). Blocked if not allowed.  
  2. If allowed, traffic moves to **Security Group inbound rules** (instance level).  
  3. If SG allows it, EC2 processes the request. Outbound reply is automatically allowed (stateful).  
  4. Response must still pass through **NACL outbound rules**, or it will be blocked.  

- **Outgoing Request (from EC2 to outside)**  
  1. Traffic first checked by **SG outbound rules**.  
  2. If allowed, it moves to **NACL outbound rules**. Must be explicitly permitted.  
  3. When return traffic comes back, it passes **NACL inbound rules** first.  
  4. Finally, it reaches the **SG inbound rules** before the EC2 instance.  

## VPC Peering
 <img width="351" height="389" alt="image" src="https://github.com/user-attachments/assets/710c256b-d20c-4425-975a-46da7895455c" />

VPC peering is a way to privately connect two VPCs using AWS’s internal network. Once peered, the VPCs can communicate as if they were part of the same network, without using the public internet.  

Key features:  
- Private connection → all traffic stays on AWS’s internal, secure network.  
- No overlapping CIDRs allowed → VPCs must have unique IP ranges.  
- Non-transitive → if A is peered with B, and B with C, A cannot talk to C unless you explicitly peer them.  
- Route tables must be updated in each VPC’s subnets to enable communication.  

Use cases:  
- Connecting different departments’ VPCs (e.g., sales VPC and marketing VPC) to share resources securely.  
- Linking VPCs across different AWS accounts (e.g., dev and prod environments).  
- Keeping communication secure and internal without exposing data over the internet.  

Good to know::
- You can create VPC Peering connection between VPCs in different AWS accounts/regions
- You can reference a security group in a peered VPC (works cross accounts - same region)

### VPC Endpoints (ASWS PrivateLink)

By default, AWS services are accessed through public endpoints over the internet. VPC Endpoints (powered by AWS PrivateLink) let you connect to AWS services privately through the AWS network.  

Key benefits:  
- Security → traffic stays within AWS, no need to expose your VPC to the internet.  
- No need for an Internet Gateway or NAT Gateway to access AWS services.  
- Scalable and redundant → handles growing loads automatically.  

How it works:  
- Without VPC Endpoint → a private instance uses a NAT Gateway to reach AWS services via the internet.  
- With VPC Endpoint → the instance connects directly to the AWS service within AWS’s private network.  

Troubleshooting tips:  
- Check DNS resolution settings in the VPC.  
- Update route tables to direct traffic through the endpoint.

### Types of Endpoints

1- Interface Endpoints (Powered by PrivateLink)
- provisions an ENI(Private IP address) as an entry point (must attach a security group)
- Supports most AWS services
- $ per hour + $ per GB of data processed

2- Gateway Endpoints
- provisions a gateway and must be used as a target in a route table (does not use SG)
- Supports noth S3 and DynamicDB
- Free

## What is IPv6

IPv4 designed to provide 4.3 Billion addresses (they'll be exhausted soon)

IPv6 is the successor of IPv4 - IPV6 is designed to provide 3.4 × 10^38 unique IP addresses

Every IPv6 address in AWS is public and Internet-routable (no private range)

Format x.x.x.x.x.x.x.x (x is hexadecimal, range can be from 0000 to ffff)

- Examples:
  - 2001:db8:3333:4444:5555:6666:7777:8888
  - 2001:db8:3333:4444:cccc:dddd:eeee:ffff
  - :: all 8 segments are zero
  - 2001:db8:: -> the last 6 segments are zero
  - ::1234:5678 → the first 6 segments are zero
  - 2001:db8::1234:5678- the middle 4 segments are zero


### IPv6 in VPC

- IPv4 cannot be disabled for your VPC and subnets
- You can enable IPv6 (they're public IP addresses) to operate in dual-stack mode
- Your EC2 instacnes will get at least a private internal IPv4 and a public IPv6
- They can communicate using either IPv4 or IPv6 to the internet through an internet gateway

### IPv4 troubleshooting

IPv4 cannot be disabled for your VPC and subnets

So if you cannot launch an EC2 instance in your subnet:
- It is not because it cannot acquire an IPv6 (the space is very large)
- Its because there are no available IPv4 in your subnet

Solution: Create a new IPv4 CIDR in your subnet

### Egress-only Internet Gateway

- Works like a NAT Gateway but specifically for IPv6 traffic.  
- Purpose: allows outbound-only communication from your VPC to the internet over IPv6.  
- Blocks any inbound IPv6 connections from the internet.  

Key points:  
- Only for IPv6(does not apply to IPv4).  
- Ensures private subnets can make outbound connections securely.  
- Prevents external IPv6 hosts from initiating inbound connections.  
- Requires updating the route tables so traffic is directed through the Egress-Only Internet Gateway.  

Summary:  
Use an Egress-Only Internet Gateway when you need your instances to **access the internet over IPv6** but want to block any unsolicited inbound traffic.  

### IPv6 Routing

<img width="809" height="452" alt="image" src="https://github.com/user-attachments/assets/f81f33f9-1e4c-4624-ae03-4f109d47e358" />

This setup shows how IPv4 and IPv6 routing works in a dual-stack VPC (both protocols enabled).  

- VPC  
  - Configured with both IPv4 (`10.0.0.0/16`) and IPv6 (`2001:db8:1234:1a00::/56`) CIDR blocks.  
  - Subnets inside the VPC also have **dual CIDR blocks** (IPv4 + IPv6).  

- Public Subnet  
  - Instance has:  
    - Private IPv4 address.  
    - Public Elastic IPv4 address.  
    - Public IPv6 address.  
  - Can communicate with the internet using both IPv4 and IPv6.  
  - IPv4 internet traffic routes through the **Internet Gateway** (via Elastic IP).  
  - IPv6 traffic also routes directly through the **Internet Gateway**.  

- Private Subnet  
  - Instance has a private IPv4 and an IPv6 address.  
  - IPv4 traffic → routed through a **NAT Gateway** in the public subnet for outbound internet.  
  - IPv6 traffic → routed directly through the **Internet Gateway** (no NAT required).  

- NAT Gateway  
  - Needed only for **IPv4 private subnets**.  
  - Not used for IPv6 traffic — IPv6 can go straight out via the Internet Gateway.  

- Route Tables  
  - Public Subnet:  
    - Routes local traffic (`10.0.0.0/16` and `2001:db8:1234:1a00::/56`) within the VPC.  
    - Routes all other IPv4 (`0.0.0.0/0`) and IPv6 (`::/0`) to the Internet Gateway.  
  - Private Subnet:  
    - Routes IPv4 internet traffic (`0.0.0.0/0`) to the NAT Gateway.  
    - Routes IPv6 internet traffic (`::/0`) directly to the Internet Gateway.  

Summary:  
- In IPv4, private subnets require a NAT Gateway for outbound internet.  
- In IPv6, both public and private subnets can use the Internet Gateway directly.  

## VPC Summary


- CIDRs (Classless Inter-Domain Routing)  . Defines the IP range for your VPC (IPv4 and IPv6). Sets the boundaries for IP allocation.  

- VPC (Virtual Private Cloud) - An isolated virtual network within AWS using CIDRs.  

- Subnets - Divide the VPC into smaller segments. Each subnet is tied to a specific Availability Zone.  

- Internet Gateway - Provides internet access for IPv4 and IPv6. Created at the VPC level.  

- Route Tables - Define how traffic flows within the VPC and to external networks. Used for routing to internet gateways, VPC peering, and VPC endpoints.  

- Bastion Host - A public EC2 instance that acts as a secure bridge to access private EC2 instances.  

- NAT Instance - Legacy way of giving internet access to private EC2 instances. Requires manual setup and maintenance.  

- NAT Gateway - Managed, scalable replacement for NAT instances. Provides outbound IPv4 internet access for private subnets.  

- NACLs (Network Access Control Lists)  
  - Operate at the subnet level.  
  - Stateless (rules must be defined for both inbound and outbound).  

- Security Groups  
  - Operate at the instance level.  
  - Stateful (responses automatically allowed once traffic is permitted).  

- VPC Peering  
  - Private connection between two VPCs using AWS’s internal network.  
  - Non-transitive: each connection must be created explicitly.  

- VPC Endpoints  
  - Allow private access to AWS services (e.g., S3, DynamoDB) without using the public internet.  

- VPC Endpoint Services (PrivateLink)  
  - Connect privately from one VPC to another (e.g., provider to customer).  
  - Requires a Network Load Balancer or ENIs.  

- Egress-Only Internet Gateway  
  - Outbound-only internet access for IPv6 traffic.  
  - Blocks all inbound IPv6 connections.  

- Transit Gateway  
  - Provides transitive connectivity between multiple VPCs, VPNs, and Direct Connect links.  
  - Acts as a central hub for network communication.  

---

# DNS (Route53)

## Amazon Route 53

- A highly available, scalable, fully managed and authoritative DNS
- Authoritative = The customer can update the DNS records
- Route 53 is also a Domain Registrar
- Ability to check the health of your resources
- The only AWS service which provides 100% availability SLA - designed to never go down
- Why route 53? 53 is a reference to the traditional DNS port


### Route 53 - Hosted Zones

Hosted zones are a container for records nthat define how ro route traggiv to a domain and its subdomains.

- Public hosted zones - contains records that specify how to route traffic on the interner (public domain names) application1.mypublicdomain.com
- Private hosted domains - contain records that specify how you aroute trafffic within one or more VPCs iprivate domain names) application1.company.internal
- You pay $0.50 per month per hosted zone



### Route 53 - Public vs Private Hosted Zones

<img width="815" height="459" alt="image" src="https://github.com/user-attachments/assets/9e400e42-a597-4965-a612-e67a7efd36ed" />

- **Public Hosted Zone**  
  - Used for domains accessible over the **public internet**.  
  - Example: `example.com` resolves to a public IP.  
  - Common targets include:  
    - EC2 instances with public IPs  
    - Application Load Balancers  
    - Amazon CloudFront distributions  
    - Public S3 buckets  
  - Clients anywhere on the internet can resolve and connect to these resources.  

- **Private Hosted Zone**  
  - Used for internal DNS resolution within a VPC.  
  - Example: `api.example.internal` or `db.example.internal` resolve only inside the VPC.  
  - Targets include:  
    - EC2 instances with private IPs  
    - Internal databases  
    - Microservices communicating securely within the VPC  
  - Keeps internal infrastructure hidden from the public internet.  

 
Public hosted zones let users reach your applications from anywhere on the internet.

Private hosted zones enable secure communication between internal resources without exposing them externally.  


## What is DNS?

Domain Name System which translates the human friendly hostnames into the machine IP addresses
- fOR EXAMPLES: www.google.com => 172.217.18.36
- DNS is the backbone of the Internet
- DNS uses hierarchical naming structure: Starts at the top level domain so .com -> example.com -> www.example.com -> api.example .com

### DNS Terminologies  

- Domain Registrar: Service where you register domain names. Examples: Route 53, Cloudflare, GoDaddy.  

- DNS Records Instructions for your domain (e.g., A, AAAA, CNAME, NS). Map names to IP addresses or other domains.  

- Zone File: Directory that contains all DNS records for a domain. Defines how queries should be resolved.  

- Nameserver: Hosts DNS records for a domain. Resolves queries and provides authoritative answers.  

- TLD (Top Level Domain): The highest level in DNS hierarchy. Examples: `.com`, `.org`, `.gov`.  

- SLD (Second Level Domain): The main part of the domain you register. Example: `amazon` in `amazon.com`.  

- Subdomains: Extend your main domain to create sections or services. Examples: `api.example.com`, `www.example.com`.  

**Example Breakdown:**  
`http://api.www.example.com`  
- `http://` → Protocol.  
- `api` and `www` → Subdomains.  
- `example` → Second Level Domain (SLD).  
- `.com` → Top Level Domain (TLD).  

### How DNS works

<img width="814" height="457" alt="image" src="https://github.com/user-attachments/assets/f5db3cde-af19-485e-9518-90143d23415b" />

DNS (Domain Name System) translates human-friendly domain names into IP addresses that computers use to communicate.  

Step-by-step process:  

1. User Request  
   - You type `example.com` in your web browser.  
   - The browser needs the IP address to connect.  

2. Local DNS Server 
   - The request first goes to your local DNS server (usually managed by your ISP or company).  
   - If the address is cached, it returns the IP immediately. If not, it asks higher-level DNS servers.  

3. Root DNS Server 
   - If the local server doesn’t know, it queries a **Root DNS server** (managed by ICANN).  
   - Root server doesn’t have the exact IP but points to the correct **TLD DNS server**.  
   - Example: For `example.com`, it points to the `.com` DNS servers.  

4. TLD DNS Server  
   - The **Top Level Domain (TLD) DNS server** (e.g., `.com`, `.org`) is queried.  
   - This server directs the request to the correct **SLD DNS server** (Second Level Domain).  

5. SLD DNS Server 
   - The **SLD DNS server** (managed by your registrar, e.g., Route 53, GoDaddy) knows the actual IP for `example.com`.  
   - It returns the IP address, e.g., `9.10.11.12`.  

6. Response to Browser  
   - The local DNS server stores the result (caches it) and sends the IP address back to your browser.  
   - The browser now knows the IP and connects directly to the **web server** hosting `example.com`.  

### Route 53 - Records

How you want to route traffic for a domain

- Each record contains:Domain/subdomain name - e.g., example.com
  - Record type - e.g., A or AAAA
  - Value - e.g., 12.34.56.78
  - Routing Policy - how Route 53 responds to queries
  - TTL - amount of time the record cached at DNS Resolvers
- Route 53 supports the following DNS record types:
  - (basic) A / AAAA / CNAME / NS
  - (advanced) CAA / DS / MX / NAPTR / PTR / SOA / TXT / SPF / SRV


### Route 53- Record Types

- A- maps a hostname to IPv4
- AAAA - maps a hostname to IPv6
- CNAME- maps a hiostname to another hostname
  - The target is a domain name which must have an A or AAAA record
  - Cant create a CNAME record for the top node of a DNS namespace (Zone Apex)
  - Example: You cant create for example.com, but you can create for www.example.com
- NS - Name servers for the Hosted Zone
    - Control how traffic is routed for a domain 


### Route 53 - TTL 

TTL (Time To Live) is how long a DNS record is cached before its refreshed 

- High TTL - e.g. 24hrs: Less traffic on route 53, possibility of outdated records
- Low TTL - e.g. 60 seconds: More traffic on Route 53, records are outdated for less time, Esy to change records. (Cost more money)

Except for Alias records, TTL is mandatory for each DNS record

### CNAME vs ALIAS  

- CNAME (Canonical Name Record)  
  - Points one hostname to another hostname.  
  - Example: `app.mydomain.com` → `lb1234.us-east-1.elb.amazonaws.com`.  
  - Can only be used on non-root domains (e.g., `www.mydomain.com`).  
  - Cannot be used directly on the root domain (`mydomain.com`).  

- Alias  
  - Special record type in Route 53.  
  - Can point to AWS resources such as: Load Balancers, CloudFront distributions, S3 static websites  
  - Works at all domain levels, including the root domain (`mydomain.com`).  
  - Free of charge in Route 53.  
  - Supports built-in AWS health checks.  

**Key Takeaway:**  
- Use **CNAME** when mapping subdomains to another hostname (non-root only).  
- Use **ALIAS** in AWS when you need flexibility, root domain support, and direct integration with AWS resources.  


### Route 53 - Alias Records

- Alias records maps hostname to an AWS resouce 
- Automaticaly makes changes in the resources IP addresses
- Unlike CNAME, it can be used for the top node of a DNS namespace (Zone apex), e.g. Example.com
- Alias record is allways of type A/AAAA for AWS resources (IPv4/IPv6)
- You cant set the TTL


### Route 53 - Alias Records Targets

Alias records in Route 53 are designed to work with specific AWS resources. They let you map custom domain names to AWS services without needing to manage changing IPs.  


- ELB Elastic Load Balancers) - Map friendly domain names to load balancers.
- CloudFront Distributions - Serve content with a custom domain
- API Gateway - Map custom domains to your APIs.
- ELastic Beanstalk environments - Easily connect your domain to Beanstalk apps.  
- S3 Websites - Point your domain directly to static sites hosted in S3.
- VPC Interface Endpoints - Access private services in your VPC with a clean domain name.
- Global Accelerator accelerator - Improve global performance with custom domains. 
- Route 53 record in the same hosted zone - Alias records can point to records within the same hosted zone. 

You cannot set an ALIAS record for an EC2 DNS name For that, use CNAME** or A/AAAA records instead.  

## Route 53 – Routing Policies  

In Route 53, routing policies define how DNS responds to queries. Route 53 doesn’t route traffic itself—it just tells clients which IP or resource to connect to.  

**Types of Routing Policies:**  

- Simple Routing - Always returns the same IP address. Best for a single server or resource.  
- Weighted Routing - Distributes traffic based on weights (e.g., 70% to Server A, 30% to Server B). Useful for testing new versions or gradual rollouts.  
- Failover Routing - Routes traffic to a primary resource unless it fails. If the primary is unhealthy, traffic goes to a secondary (backup).  
- Latency-Based Routing - Sends users to the server that responds the fastest. Great for multi-region setups.  
- Geolocation Routing - Routes traffic based on the user’s location. Example: EU users served from Europe, US users from US.  
- Multi-Value Answer Routing - Returns multiple IP addresses in response. Provides simple load distribution without a dedicated load balancer.  
- Geoproximity Routing (with Traffic Flow) - Routes traffic based on proximity of users and resources. Allows customization and biasing traffic toward specific regions. 

### Simple Routing

The most basic routing option in Route 53. Routes traffic to a single resource (e.g., one server, one load balancer). Every DNS query gets the same response.  

- **Multiple Values**  
  - Can return multiple IP addresses in a response.  
  - The client (browser or app) randomly selects one.  
  - Provides basic traffic distribution, but not true load balancing.  

- **Limitations**  
  - Alias records can only point to a single AWS resource.  
  - No health checks—Route 53 does not know if the resource is down.  
  - Traffic may still be sent to failed resources.  

- **Best Use Case**  
  - Simple setups with one server or resource.  
  - When advanced routing (failover, latency, weighted) is not required.  

### Weighted Routing
 
Weighted Routing distributes traffic across multiple resources based on assigned weights. Useful when you don’t want traffic split evenly.  

- **How it works**  
  - Each record is assigned a weight (e.g., 70, 20, 10).  
  - Route 53 calculates the percentage of traffic for each resource as:  
    - `Weight for a specific record ÷ Sum of all the weights for all records`.  
  - Weights don’t need to add up to 100—only relative values matter.  
  - Example: Weights 7, 2, 1 = 70%, 20%, 10%.  

- **Features**  
  - Can associate health checks with weighted records.  
  - If a resource fails, Route 53 stops sending traffic to it.  
  - Setting a weight of 0 removes a resource from traffic flow without deleting the record.  

- **Use Cases**  
  - Gradually testing a new application version with a subset of users.  
  - Balancing load between regions/resources in a controlled manner.  
  - Slowly phasing out or introducing infrastructure.  


### Latency Based Routing:

Latency-Based Routing routes users to the AWS resource (e.g., EC2, Load Balancer) with the lowest latency. Optimizes performance by reducing delays for global applications.  

- **How it works**  
  - Route 53 measures latency between AWS regions and users.  
  - Directs queries to the region that responds the fastest.  
  - Sometimes, due to network conditions, the lowest latency server might not be the geographically closest.  

- **Features**  
  - Can integrate with health checks.  
  - If the lowest latency server becomes unavailable, traffic is routed to the next best option.  

- **Use Cases**  
  - Global applications where user experience and speed are top priority.  
  - Websites, APIs, or services with users spread across multiple regions. 


### Geolocation Routing 

Geolocation Routing - Routes traffic based on the user’s physical location. Supports continents, countries, and even US states.  

- **How it works**  
  - Example: Users from France can be routed to a server in Paris.  
  - If multiple rules overlap, the **most precise location** takes priority (e.g., country over continent).  
  - Requires a **default record** as a fallback for users without a matching location rule.  

- **Features**  
  - Can integrate with health checks to ensure users are sent to healthy endpoints.  

- **Use Cases**  
  - **Website localization** → Serve region-specific languages and content.  
  - **Content distribution** → Direct or restrict access based on geography (compliance, regulations).  
  - **Load balancing** → Distribute traffic geographically across servers.  


### Geoproximity Routing
  
Routes traffic based on the **geographic location** of users and resources.  Similar to Geolocation, but with **extra control using bias values**.  

- **How it works**  
  - Bias values adjust how much traffic a resource receives:  
    - Positive bias (+1 to +99) → Expands the region → Attracts more traffic.  
    - Negative bias (−1 to −99) → Shrinks the region → Sends less traffic.  
  - Can route traffic to AWS regions or even non-AWS resources (by specifying latitude/longitude).  
  - Requires Route 53 Traffic Flow to configure.  

- **Example**  
  - Resources in **US East 1** and **US West 2**.  
  - With **bias = 0**: Users are routed purely by proximity (East → US East 1, West → US West 2).  
  - With **bias = +50 on US East 1**: Route 53 expands US East 1’s region, sending more traffic there, even from users closer to US West 2.  

- **Use Cases**  
  - Shift more traffic toward a preferred region (e.g., cheaper or higher-capacity infrastructure).  
  - Balance load across regions while maintaining location awareness.  
  - Prioritize performance or failover needs globally.  


### IP-based Routing

Routes traffic based on the client’s IP address.  Uses CIDR blocks (IP ranges) to map users to specific resources.  

- **How it works**  
  - Example:  
    - User A’s IP is in CIDR Block 1 → Routed to Resource A.  
    - User B’s IP is in CIDR Block 2 → Routed to Resource B.  

- **Why use it**  
  - Provides granular control over where traffic goes.  
  - Optimize performance by directing certain IP ranges to closer or faster endpoints.  
  - Reduce network costs by routing specific ISPs or regions to cheaper infrastructure.  

- **Use Cases**  
  - Directing traffic from a specific ISP to a preferred endpoint.  
  - Routing certain customer ranges to dedicated servers.  
  - Fine-tuning network performance at the IP range level.  


### Multi-Value Routing
 
Multi-Value routing returns multiple IP addresses or resources in response to a single DNS query. Can attach **health checks** to ensure only healthy resources are returned.  

- **How it works**  
  - Route 53 can return up to 8 healthy records per query.  
  - Example: `www.example.com` has 3 records.  
    - If all 3 are healthy → all 3 IPs returned.  
    - If only 1 is healthy → only that one is returned.  
  - Client chooses which IP to use.  

- **Important Notes**  
  - Provides basic redundancy and traffic spreading.  
  - Not a replacement for a true load balancer (e.g., ALB or NLB).  
  - Less dynamic and feature-rich compared to load balancers.  

- **Use Cases**  
  - Simple load distribution without deploying a load balancer.  
  - Adding redundancy by returning multiple healthy endpoints.  


### Route 53 - Health Checks

HTTP Health Checks are only for public resources
- Health Check => Automated DNS Failover:
  - 1. Health checks that monitor an endpoint (application, server, other AWS resource)
  - 2. Health checks that monitor other health checks (Calculated Health Checks)
  - 3. Health checks that monitor Cloud Watch Alarms (full control !!) - e.g., throttles of DynamoDB, alarms on RDS, custom metrics,... (helpful for private resources)
- Health Checks are integrated with CW metrics

## Domain Registar vs DNS Service

- You buy or register your domain name with a Domain Registrar typically by paying annual charges (e.g., GoDaddy, Amazon Registrar Inc., ...)
- The Domain Registrar usually provides you with a DNS service to manage your DNS records
- But you can use another DNS service to manage your DNS records
- Example: purchase the domain from GoDaddy and use Route 53 to manage your DNS records

### GoDaddy as Register & Route 53 as DNS Service

<img width="815" height="455" alt="image" src="https://github.com/user-attachments/assets/5de0e599-365d-4b7e-8095-de40a581f9ff" />

- **Domain Registration (GoDaddy)**  
  - You purchase and register your domain name with GoDaddy.  
  - GoDaddy is your registrar but doesn’t have to manage your DNS records.  

- **DNS Management (Route 53)**  
  - You choose Amazon Route 53 to manage DNS for your domain.  
  - Route 53 provides a set of nameservers (e.g., `ns-252.awsdns-31.com`, `ns-184.awsdns-50.org`, etc.).  

- **Connecting the Two**  
  - In GoDaddy, you update the domain’s custom nameservers to point to Route 53’s nameservers.  
  - This effectively delegates DNS control from GoDaddy to Route 53.  

- **Result**  
  - GoDaddy continues as the registrar (domain ownership).  
  - Route 53 becomes the DNS service, where you configure records like A, CNAME, MX, TXT, etc.  
  - All DNS queries for your domain are now resolved through Route 53.  

### 3rd Party Register with Amazon Route 53

- If you buy byour domain on a 3rd party registrar, you can still use Route 53 as the DNS Service provider by:
   - 1- Creating a public Hoted Zone in Route 53
   -  2- Updating NS Records on a 3rd party website to use route 53 Name servers
- Note: Domain registrar and DNS Service are seperte - But every Domain Redisrar usually comes with some DNS features

---

# Chapter 11: CDN (CloudFront)

Amazon’s Content Delivery Network (CDN). Designed to deliver content faster by caching it at **edge locations** close to users.  

- **How it works**  
  - Instead of every request going back to the origin (S3, EC2, Load Balancer, etc.), CloudFront caches content at global edge locations.  
  - Users fetch data from the nearest edge, reducing latency and improving performance.  

- **Benefits**  
  - Performance: Faster load times, reduced latency.  
  - Efficiency: Reduces load on origin servers by serving cached content.  
  - Security: Integrates with AWS Shield & WAF for DDoS protection and threat mitigation.  
  - Global Reach: 216 Points of Presence (PoPs) worldwide, ensuring content availability across the globe.  

Improves user experience with quicker page loads. Provides global distribution with built-in security. Helps optimize resource usage and cost by offloading requests from origin servers.  

## CloudFront Origins

- S3 bucket:
  - For distributing files and caching them at the edge.
  - Enhanced security with CloudFront Origin Access Control (OAC)
  - OAC is replacing Origin Access Identity (OAI)
  - CloudFront can be used as an Ingress (to upload files to S3)

- Custom Origin (HTTP)
  - Application Load Balancer
  - EC2 nstance
  - S3 Websire
  - Any HTTP backend you want

## CloudFront at a High Level  

- A client (e.g., a web browser) requests content such as an image. The request is routed to the nearest **CloudFront Edge location** (global Points of Presence).  
- If the content is already cached at the Edge location → it is served immediately (fast response).
- If the content is not cached → CloudFront fetches it from the origin*(e.g., S3 bucket, EC2, or any HTTP server).  
  - Once retrieved, CloudFront caches the content at that Edge location for future requests.  

This ultimately reduces latency by serving users from the nearest Edge location. Minimizes repeated calls to the origin, saving bandwidth and lowering costs helping provide a smoother, faster user experience.  

## CloudFront - S3 as an Origin 

<img width="807" height="454" alt="image" src="https://github.com/user-attachments/assets/e7c455b0-3907-4800-89b6-e92a5bf4dade" />
 
- An S3 bucket stores static files (images, videos, etc.) and acts as the origin.  
- CloudFront uses edge locations (POPs) worldwide (e.g., Los Angeles, Mumbai, São Paulo, Melbourne).  

- **How it works**  
  - When a user requests a file: CloudFront first checks the **nearest edge location** for a cached copy.
  - If cached → it’s delivered instantly.
  - If not cached → CloudFront fetches the file from the **S3 origin**, delivers it, and caches it locally for future requests.  

- With Origin Access Control (OAC) and bucket policies, you can restrict direct S3 access. This ensures that only CloudFront can fetch files from your S3 bucket.  

This gives fast content delivery by caching files near users. Reduces repeated requests to the S3 bucket (saves bandwidth and cost) amdAdds security by limiting direct access to S3.  

## CloudFront - ALB or EC2 as an origin

<img width="818" height="456" alt="image" src="https://github.com/user-attachments/assets/f3e2c40f-3284-482a-b02f-e03bcda5ef00" />


CloudFront can use either an **Application Load Balancer (ALB)** or **EC2 instances** directly as its origin. Here’s how it works:  

Users send requests → CloudFront Edge Location (nearest POP). Edge Location forwards requests → Origin (ALB or EC2). Response is cached at the Edge for future requests.  

- **Using ALB as Origin (Top Diagram)**  
  - The ALB must be public.  
  - ALB security group must allow traffic from CloudFront edge location IP ranges.  
  - ALB then routes traffic to private EC2 instances behind it.  
  - Benefit: EC2s stay private, protected from direct exposure.  

- **Using EC2 as Origin (Bottom Diagram)**  
  - EC2 instances must be publicly accessible.  
  - Security groups on the EC2 must allow only CloudFront’s edge location IPs.  
  - Direct setup, but less secure compared to using ALB with private instances.  

- **Security Considerations**  
  - Always configure security groups to allow only CloudFront edge IP ranges.  
  - This prevents exposing ALB/EC2 to the entire internet.  
  - AWS provides the official list of CloudFront IPs:  
    [CloudFront Edge Location IP List](http://d7uri8nf7uskq.cloudfront.net/tools/list-cloudfront-ips)  

- **Summary**  
  - ALB + Private EC2 = more secure, flexible architecture.  
  - Public EC2 = simpler but less secure, must be locked down carefully.  
  - Both approaches let you leverage CloudFront for faster delivery and scalability.  









































































































































































