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


































