## Chapter 1: Introduction to Networking fundamentals

### Overview of computer networks

A computer network is a group of devices connected to each other allowing them to share information and resources.

Importance in modern infrastructure:

- Foundation - Enables communication between devices
- Resource sharing - Facilitates sharing of files, printers and more
- Internet functionality - Critical for browsing, streaming and communication 
- Application support - Backbone for app connectivity and data transfer

Networking in Devops

- Server Interactions - Enables communication between servers and applications.
- Deployment - Critical for launching and updating applications 
- Management - Crucial in monitoring and managing infrastructure
- Optimisation - Enhances troubleshooting, performance and scalability

### Network basics/Types of Networks

Two core types of networks

1 - LAN (Local area Network) small area, like home or office, connects devices to share resources e.g. Home Wi-Fi, printers any devices in single location 

2 - WAN (Wide Area Network) covers large areas, like a city, country or a larger regions,connects multiple LANs over long distances e.g. Internet

### Key Networking components

Switches - Connect devices within the same network, manages data flow within a LAN

Routers - Direct traffic between networks, connect different networks

Firewalls - Protect networks from unauthorised access, monitor and control incoming and outgoing network traffic

### IP address & MAC address

### IP addresses

IP addressing refers to the system used to assign unique identifiers, known as IP addresses, to devices connected to a computer network, typically the Internet. An IP address acts like a mailing address for a device, allowing data to be routed between different devices over the network.

Two main types of IP adresses:

- IPv4 - Format: 32-bit address written in four groups of decimal numbers (each group representing 8 bits), separated by periods, like 192.168.0.5
- IPv6 - Format: 128-bit address written in eight groups of hexadecimal numbers (each group representing 16 bits), separated by colons, like 2001:0db8:85a3:0000:0000:8a2e:0370:7334

IP addresses enable devices to identify and communicate with each other on a network, without them devices wouldnt know where to send or recieve data. 

### MAC addresses 

A MAC (Media Access Control) address is a unique identifier assigned to a network interface controller (NIC) for use within a network. a MAC address is permanently assigned to the hardware by the manufacturer and is often referred to as a hardware address or physical address. MAC address help indetify eachother in a Local netowrk. They play an esential role for network communication and security.

A MAC address is a 48-bit address, usually represented as six pairs of hexadecimal digits separated by colons (:) or hyphens (-), like 00:1A:2B:3C:4D:5E.

### Ports and protocols

What are ports? A port is a logical endpoint for communication through which network connections are made. It helps differentiate between different types of traffic on a device. For example, while an IP address helps identify a device on a network, the port helps identify which service or application on that device should receive the data.

What are protocols? A protocol is a set of rules or standards that determine how data is transmitted across a network. Different protocols are used for different types of communication.

Importance of ports and protocols - Ports ensure data gets to the right application on your device while protocols ensure that the data is undertandable and properly formatted.

#### Two main types of Protocols:

1. TCP (Transmission control protocol) - TCP ensures that data sent from one device reaches another device accurately and in the correct order

Characterisitcs of TCP:

- It is connection oriented
- It requires a "handshake" where two devices agree to communicate, in networking this is a 3 step process.
- Reliable data transfer, TCP ensures that all data sent is recieved correctly on the other end, any data corruipted or incorrect TCP  will resend it.

Use cases of TCP:

- Ensures data is delivered in order
- Error checking and flow control
- Any bidirectional communication

2. UDP (User Datagram Protocol) - UDP is a simple protocol used to send and recieve data often reffered to as connectionless.

Characteristics of UDP:

- Simple protocol to send and recieve data
- Prior communication not required (Can be good and bad)
- connectionless - no form of connection established betwween sender and reciever.
- Fast but less reliable

Use cases of UDP:

- Suitable for real time applications e.g video streaming
- DNS
- VPN protocols

TCP VS UDP 

| FEATURE  | UDP  | TCP     |
|-------|------|----------|
| Connection  | Connectionless |Connection-oriented (uses a handshake)  |
| Reliability | Unreliable (no guarantees of delivery) | Reliable (ensures delivery and order) |
| Speed | Faster, no connection or handshake setup needed   | Slower due to overheaad of connection |
| Error Checking | No error checking or flow control   | Error checking and flow control |

---

## Chapter 2: OSI Model (open system interconnection model)

### Overview of OSI Model

Why do we need a communication model?

Application independence
- Without a standard model, applications must understand the underlying network.
- Imagine having different versions of your application/software for Wi-Fi, Ethernet, Fibre etc
- With a communicstion model applications can work independently of the network making development and coding much simpler and more efficient.

Simplified Network Equipment Managment
- Upgrading network mequipment is difficult without a standard model.
- Easier to upgrade and manage network gear because everything speaks the same language with the communication model
- Standardization makes maintenence and upgrading smoother and less prone to issues.

Decoupled innovation
-Innovations can happen in each layer independently, without affecting the entire system.

### 7 Layers of the OSI Model

1- Physical layer 
- Function: Transmits raw bit streams over a physical medium
- Components: Cables, switches and network interface cards

2- Data link
- Function: This layer provides node to node data transfer and detects, possibly corrects, errors that may occur in the physical layer. It ensures that data is transferred correctly between adjacent network nodes.
- Layer 2 introduces the concept of frames, which is a format for sending information over a layer 2 network.
- components: Mac addresses, switched and Bridges.
  
3- Network
- Determines how data is sent to the recipient, manages packet forwarding including routing through intermediate routers.
- IP packets are moved step by step forms source to destination via intermediate networks. Encapsulated in different frames along the way.
- Components: IP addresses, routers
  
4- Transport 
- Provides reliable data transfer services to the upper layers, segments and reassembles data.
- components: TCP and UDP

5- Session
- Function: Manages sessions between applications, Establishes, maintains and terminates connections
- components: session management protocols

6- Presentation Layer
- Function: Translates data between the application layer and the network, ensures that data is in a usable format
- component: Encryption, data formatting
  
7- Application:
- Function: Frovides network services directly to applications, End-user Layer
- components: HTTP,FTP,SMTP

### Overview of the TCP/IP Model (Layers)
![image](https://github.com/user-attachments/assets/65f1508a-3be5-4943-b85e-25772b277231)

### OSI Layers; POV of sender & reciever

#### Example 1: POV of sender - User sends a POST request to an HTTP web page

Application Layer: The user sends a POST reques with JSON data  via their browser using HTTP.

Presentation Layer: Data is encrypted (if using HTTPS) to ensure secure transmission. serialise JSON to flat byte data strings.

Session Layer: A session is created between the client and server. Request to establish TCP connection

Transport Layer: The POST request is split into segments using TCP for reliable transmission. Sends SYN request to target port 443 which is HTTPS

Network Layer: Each segment is encapsulated into IP packets and routed to the server.

Data Link Layer: The IP packets are converted into frames for transmission over the local network.

Physical Layer: The frames are transmitted as raw bits via electrical signals, radio waves, or optical signals.


#### Example 2: POV of reciever

Physical Layer: The server receives the electrical/optical signals and converts them into bits.

Data Link Layer: The bits are organized into frames, error-checked, and validated using MAC addresses.

Network Layer: The packets are checked for correct IP addresses and, if necessary, reassembled.

Transport Layer: TCP ensures the packets are delivered reliably and reassembled correctly using the port number (e.g., 80 or 443).

Session Layer: The session is managed to keep track of the HTTP request and ongoing communication. Connection session is established.

Presentation Layer: If encrypted, the POST data is decrypted and translated to the correct format. Data decompresses

Application Layer: The server processes the POST request and formulates an appropriate response (e.g., sending back a web page).

---

## Champter 3: Introduction to DNS (Domain Name System)

This section will go through:

- What is DNS and its role in networking
- DNS components
- DNS records
- How DNS works: DNS Process
- DNS tools
- using /etc/hosts on our local machine

### What is DNS and its role in networking

Definition: Translate domain names to IP addresses

Role in Networking: Simplifies navigation on the internet Essential for accessing websites and services.

### DNS components: Nameservers & Zone Files

DNS components: Name servers
- Load DNS settings and configurations
- Can be authoritative or recursive
- A recursive DNS server is responsible for querying other DNS servers to find the answer to a query.
- An authoritative DNS server is the final source of truth for a particular domain's DNS records. These servers store DNS records for specific domains

DNS components: Zone files
- Zone files are stored inside Name servers ans store information about the domain. They help name servers answer queries about how to get to the domain if the name server doesnt know the answer directly.
- Organized and readable format.

### DNS components: Records
- A zone file is compromised of multiple resource records. Each record contains specific information about hosts, name sewrvers and various nother resources.
- Components: record name, TTL, Class, Type, Data

| Resource records  | Description  
|-------|------
| Record name  | The domain name being queried |
| Time to live | Indicates how long the record is valid (before refresh required) |
| Class | Namespace of the record information |
| Type | Type of record (A or MX or AAAA etc) | 
| NS | Name of server record | 
| Data | The actual information corresponding to the record type. Like IP address for an A record |

#### DNS records

| Record  | Description  
|-------|------
| A  | Maps a domain name to an IPv4 address|
| AAAA | Maps a domain name to an IPv6 address |
| CNAME | Alias of one name to another. It allows you to point multiple domain names to the same IP address |
| MX | Specifies the mail server responsible for recieving email for the domain | 
| TXT | Allows domain admis to insert any text into DNS. Commonly used for verification purposes and to hold SPF( Sender Policy Framework) data | 

### How does DNS work:

Converts domain names to IP addressed, involves multiple steps and servers

#### DNS Hierarchy and Distribution

![image](https://github.com/user-attachments/assets/6d174d2e-00b0-426a-9aad-f075398b0f8d)

Root DNS Servers (Top Level)
- Location: At the top of the hierarchy.
- Purpose: The root servers know where to direct queries for Top-Level Domains (TLDs) (like .com, .org, .net, etc.).
- Function: When a DNS resolver queries a root DNS server, it doesn't provide the final IP address but refers the query to the appropriate TLD server.


TLD (Top-Level Domain) DNS Servers
- Location: Just below the root servers.
- Purpose: Responsible for managing top-level domains (e.g., .com, .org, .net, .uk, .fr, etc.).
- Function: These servers know where the authoritative DNS servers for a specific domain (like example.com) are located. They don’t know the IP address of the domain itself, but they know which authoritative server holds that information.

Authoritative DNS Servers (Second-Level Domains)
- Location: Below the TLD servers.
- Purpose: These servers are responsible for specific domain names and hold the actual DNS records for a domain (e.g., example.com).
- Function: When a query reaches an authoritative DNS server, it can provide the requested information (e.g., IP address) from its DNS records, including A records (for IPv4), AAAA records (for IPv6), MX records (for email servers), NS records (for name servers), etc.

Domain Name Resolvers (Recursive DNS Servers)
- Location: Not part of the hierarchical structure, but critical in the DNS resolution process.
- Purpose: These servers perform the recursive query on behalf of clients (like web browsers or applications). They traverse the hierarchy (from root to TLD to authoritative) to find the IP address associated with a domain.
- Function: A recursive DNS server queries multiple DNS servers until it gets the final answer. It also caches the results of these queries to improve performance for future requests.

#### DNS Resolution Process

![image](https://github.com/user-attachments/assets/6c4da28b-4341-446b-b455-cb8ab6752b4d)

1. Client Makes DNS Query
When a user types a domain name (www.example.com) into their browser or when an application needs to resolve a domain name, the system (typically the operating system) first checks if the domain has been resolved before by looking at its local cache (stored DNS lookups).

2. Query Sent to Recursive DNS Resolver
The recursive DNS resolver (usually provided by an ISP or a public DNS service like Google DNS 8.8.8.8 or Cloudflare 1.1.1.1) receives the query.

3. Recursive Resolver Queries Root DNS Servers
If the recursive resolver cannot answer the query from its cache, it starts the resolution process from the top of the DNS hierarchy by querying one of the root DNS servers.

4. Recursive Resolver Queries TLD DNS Servers
The recursive resolver now contacts the appropriate TLD DNS server based on the domain extension (e.g., .com, .org).

5. Recursive Resolver Queries Authoritative DNS Server
Now the recursive resolver contacts the authoritative DNS server for the domain (example.com).

6. Recursive Resolver Returns IP Address to Client
Once the recursive resolver receives the final IP address from the authoritative DNS server, it: Caches the response to speed up future queries, Returns the IP address to the original client (e.g., the web browser).

7. Client Connects to Web Server
Finally, with the IP address in hand, the client's web browser (or application) initiates a connection to the web server using the IP address provided. The browser sends an HTTP or HTTPS request to the server to retrieve the web page.

#### Domain Registar vs DNS Hosting provider;

- Registar: Purchase and register domains
- DNS Hosting: Operates DNS Nameservers

When Domain Registar and DNS Hosting rpovider are the same company, the DNS zone is automatically created and hosted.

If they are different, the name server needs to be provided with some information where the DNS zone is already hosted and is configured seperately. The process is known as DNS Query process.

![image](https://github.com/user-attachments/assets/7bad12dd-2483-4c34-8cd2-f5000fe60511)

### Netowrk Debugging Tools:

#### nslookup 

nslookup (Name Server Lookup) is a command-line utility used for querying the Domain Name System (DNS) to obtain domain name or IP address mapping information. It allows users to look up DNS records, such as A records (for IPv4 addresses), AAAA records (for IPv6 addresses), and other types like MX records (mail servers), NS records (name servers), etc.

Use the command **`nslookup`** followed bt the [domain]
Exampole:
```
nslookup www.google.com
```

#### dig

The dig (Domain Information Groper) command is a powerful network administration tool for querying the Domain Name System (DNS). It is used to perform DNS lookups, return detailed information about the DNS records for a given domain, and troubleshoot DNS problems.dig is more detailed than the nslookup command, and it is commonly used by system administrators and network engineers for debugging and investigating DNS issues.

Use the comman **`dig`** followed by [domain] 
Example:
```
dig www.google.com
```


### Using /etc/hosts on our local machine

#### What is /etc/hosts?
- A local file on your computer
- Maps domain names to IP addresses
- Takes precedence over DNS for specific entries

#### Editing the /etc/hosts File?

Step 1: Open the File in a Text Editor
To modify the /etc/hosts file, you need root or administrator privileges. Use your favorite text editor with elevated permissions.
```
sudo vim /etc/hosts

```

Step 2: Add Your Entries
Add a new line for each mapping you want to create. For example:
```
Format: IP_address domain_name  Example: 127.0.0.1 example.com

```

---

## Chapter 4: Routing

### What is routing and why it matters?

Definition: Process of determining paths for data to travel across networks.

Importance of Routing: Ensures data reaches its destination efficiently, fundamental for internet functionality.

### How routing works?

Routing process: Routers determine the best path and use routing tables to make decisions

Key components: Routers and routing tables

![image](https://github.com/user-attachments/assets/545edd05-47b6-4895-9244-b78e04ae5744)

#### Why routing matters for devops:?

- Network performance optimization
- Ensures reliable application delivery
- Crucial for managing complex infrastructures

### Static vs dynamic routing

In static routing, routes are manually configured by network administrators. Fixed paths are set by network administrators These routes do not change unless manually updated, and they define specific paths for packets to follow. They are simple to set up but not scalable.

Dynamic routing uses routing protocols to automatically discover and maintain routes. Routers communicate with each other to share information about the network topology, and routes are updated dynamically based on network conditions (e.g., link failures or congestion). Dynamic routing is also scalable and adaptable.

### Common routing protocols

Routing protocols are algorithms that enable routers to communicate with each other to determine the best path for forwarding data packets across a network. They allow routers to dynamically share information about the network’s topology, automatically adjusting to changes enhancing network efficiency.

Importance: They automate route updates and improve network reilience

#### OSPF and BGP

OSPF (open shortest path first) - OSPF is a widely used link-state routing protocol designed for use within an autonomous system. It is an interior gateway protocol, meaning it is used for routing traffic within a single organization's network, rather than between organizations

BGP ( Border Gateway protocol) - BGP is the standard protocol used for routing traffic between different autonomous systems  on the internet. It is an Exterior Gateway Protocol and is the backbone of the internet, responsible for ensuring data is routed efficiently across large, complex networks that span multiple organizations and regions.

---

## Chapter 5: Subnetting

### Introduction to subnetting

What is subnetting?

Subnetting is dividing one large network into smaller networks, this improves network management and efficiency.

#### Understanding CIDR notation

CIDR stands for classless Inter-Domain Routing

Format: IP_address/prefix_length

Example; 192.168.1.0/24

### Introduction to Binary Basics

Consider the IP address: 192.168.1.1

Step 1: Convert each octet to binary.

192 in decimal → 11000000 in binary

168 in decimal → 10101000 in binary

1 in decimal → 00000001 in binary

1 in decimal → 00000001 in binary


Step 2: Combine all the binary octets together.


192.168.1.1 → 11000000.10101000.00000001.00000001
The binary representation of the IP address 192.168.1.1 is: 11000000 10101000 00000001 00000001

#### Conversion Process
To convert from decimal to binary for each octet, follow these steps:

Divide the decimal number by 2.

Write down the remainder.

Repeat the division process with the quotient until the quotient is 0.

The binary number is the remainders written in reverse order.

Example: Convert 192 to Binary
```
192 ÷ 2 = 96, remainder = 0
96 ÷ 2 = 48, remainder = 0
48 ÷ 2 = 24, remainder = 0
24 ÷ 2 = 12, remainder = 0
12 ÷ 2 = 6, remainder = 0
6 ÷ 2 = 3, remainder = 0
3 ÷ 2 = 1, remainder = 1
1 ÷ 2 = 0, remainder = 1
```
So, 192 in decimal is 11000000 in binary.

### Calculating subnets

A subnet mask defines network and host portions.

![image](https://github.com/user-attachments/assets/12a2934d-068a-4513-8143-65f4ce0fbce9)

Example Subnet 192.168.1.0/26

IP Address: 11000000.10101000.00000001.00000000
Subnet mask: 1111111.11111111.11111111.11000000

The netowrk address: 192.168.1.0
The Broadcast address: 192.168.1.63
Usable IP ranges: 192.168.1.1 to 192.168.1.62

### NAT (Network Address Translation)

#### What is NAT

NAT (Network Address Translation) is a method used in networking to Translate private IP addresses to a public IP adress. It facilitates communication between internal network and the internet.

#### How does NAT work?

- Internal devices use private IP addresses
- Router translates private IP to public IP
- Facilitates communication with external networks


When a device on a private network (e.g., with an IP address 192.168.1.10) sends data to the internet:

The packet's source IP address (e.g., 192.168.1.10) and source port (e.g., 5000) are used in the packet's header. The packet is sent to the NAT-enabled router, typically your home or office router.
NAT translates the private IP address (e.g., 192.168.1.10) to the router's public IP address (e.g., 203.0.113.5). The router stores this mapping in a NAT table so that it knows how to translate the response back to the correct internal device later.
The modified packet, now with the public IP address and the new port number, is forwarded to the internet.

Inbound Traffic (Internet to Local):

When a response packet comes back from the external server (e.g., a web page response from 198.51.100.1): The response packet's destination IP address is the public IP address of the router (e.g., 203.0.113.5).
The router checks its NAT table to find which internal device the packet should go to by looking at the destination port (e.g., 50000). The router translates the public IP address back to the private IP address of the internal device (e.g., 192.168.1.10) and restores the original port number (e.g., 5000). The router then forwards the packet to the appropriate internal device (192.168.1.10).

#### Types of NAT

Static NAT:

-Maps a single private IP address to a single public IP address.
- It’s used for services like web servers where you want the internal device to always have the same public IP.

Dynamic NAT:

- Maps private IP addresses to a pool of public IP addresses.
- It dynamically assigns a public IP from a pool as needed.

PAT (Port Address Translation)
- It allows multiple devices on a local network to be mapped to a single public IP address by assigning different port numbers to each session.
- PAT is used for almost all home networks.

#### Benfits of NAT for Devops Engineers

- converts public IP addresses
- Enhances netowrk security
- simplifies network design and management

---

## Chapter 6: Network Troubleshooting

### Why do we troublshoot networks?

- Ensures smooth operation
- Identify and fix network problems
- Minimize downtime

### Common Network Issues

- Connectivity Loss
- Slow netowrk performance
- IP address comflicts
- DNS resolution faliures

### Identifying symtoms

Example: Connectivity Loss

Symptom: Devices cant access the network.

Steps to diagnose:

- Check physical connections
- Verify networl configuration
- Test with ping command

### Network tools to use:

1. Ping

Ping is a basic network utility used to check if a host (device) is reachable over a network. It works by sending ICMP (Internet Control Message Protocol) "echo request" packets to the target device and waiting for an "echo reply" in response.

Use Case: Test network connectivity, measure round-trip time (latency), and packet loss.

syntax: ping [IP address or domain]

Example:
```
ping 8.8.8.8
```
2. Traceroute (Windows: tracert)

Traceroute traces the path packets take to reach a destination by sending packets with increasing Time-to-Live (TTL) values. Each router along the path reduces the TTL by 1, revealing its address until the final destination is reached.

Use Case: Diagnose routing issues by seeing where packets are being delayed or dropped.

syntax: **`tracert`** [domain]

Example (Windows):
```
tracert www.example.com
```
3. nslookup
   
nslookup is a command-line tool used to query DNS (Domain Name System) servers. It can be used to obtain domain name to IP address mappings and vice versa.

Use Case: Troubleshoot DNS-related issues, check if DNS records are resolving correctly.

Syntax **`nslookup`** [domain]

Example:
```
nslookup www.example.com
```

---

## Chapter 7: Cloud Networking

What is cloud networking?

It is the pratcise of managing and configuring networks in cloud environments. This is important for devops engineers as it ensures applications and services can communicate efficiently and securely.

Key components of cloud networking:
- VPCs (Virtual private clouds)
- Subnets
- Gateways
