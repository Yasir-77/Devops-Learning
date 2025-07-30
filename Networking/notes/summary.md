# 🧠 Networking Fundamentals Cheat Sheet

A quick reference guide for DevOps, sysadmins, and anyone learning computer networking.

---

## 📡 Chapter 1: Networking Fundamentals

### 🌐 What is a Computer Network?
A group of connected devices that share resources and information.

### 🔍 Why Networking Matters

- **Communication:** Device-to-device interaction  
- **Resource Sharing:** Printers, files, storage  
- **Internet Access:** Web, streaming, emails  
- **DevOps:** App deployment, monitoring, server communication

---

### 📍 Types of Networks

| Type | Description | Example |
|------|-------------|---------|
| **LAN** | Local Area Network – limited area | Home Wi-Fi, office setup |
| **WAN** | Wide Area Network – large/geographical area | Internet, multiple branches |

---

### 🧩 Key Networking Components

- **Switch:** Connects devices within a LAN  
- **Router:** Connects different networks, routes packets  
- **Firewall:** Controls and protects traffic  
- **IP Address:** Logical address of a device  
- **MAC Address:** Unique hardware identifier

---

## 🔌 Ports & Protocols

### ⚙️ What Are They?

- **Ports:** Identify services/apps on a device  
- **Protocols:** Define communication rules

### 🔁 TCP vs UDP

| Feature        | UDP                        | TCP                                |
|----------------|----------------------------|-------------------------------------|
| **Connection** | Connectionless              | Connection-oriented (3-way handshake) |
| **Reliability**| Unreliable (no delivery guarantee) | Reliable (ensures delivery & order) |
| **Speed**      | Faster                     | Slower due to overhead             |
| **Error Checking** | No                      | Yes                                |
| **Use Cases**  | Video streaming, DNS, games | Web, file transfer, email          |

---

## 🧱 Chapter 2: OSI Model

### 📦 Why OSI Model?

- Standardization  
- Independent upgrades per layer  
- Easier troubleshooting  
- Enables protocol compatibility

### 📊 7 Layers of OSI

| Layer | Name           | Function |
|-------|----------------|----------|
| 7     | Application    | Interface to user (HTTP, FTP) |
| 6     | Presentation   | Encoding, encryption, formatting |
| 5     | Session        | Manage sessions/connections |
| 4     | Transport      | Reliable data transfer (TCP/UDP) |
| 3     | Network        | Routing, IP addressing |
| 2     | Data Link      | MAC addresses, framing |
| 1     | Physical       | Raw bits over cable/media |

---

## 🌐 TCP/IP Model

| Layer         | Equivalent OSI Layers         | Protocols/Examples       |
|---------------|-------------------------------|--------------------------|
| Application   | 5, 6, 7                        | HTTP, FTP, SMTP          |
| Transport     | 4                              | TCP, UDP                 |
| Internet      | 3                              | IP, ICMP                 |
| Network Access| 1, 2                           | Ethernet, Wi-Fi          |

---

## 🌍 Chapter 3: DNS

### 🔄 What is DNS?

Translates human-readable domains into IP addresses.

### 📌 Key DNS Components

| Component     | Description |
|---------------|-------------|
| **Name Server** | Stores and resolves DNS records |
| **Zone File**   | Stores domain-specific DNS data |
| **Resolver**    | Performs recursive queries |
| **Authoritative Server** | Final source of truth for domain info |

### 📄 DNS Record Types

| Type  | Description |
|-------|-------------|
| **A**     | Maps domain to IPv4 |
| **AAAA**  | Maps domain to IPv6 |
| **CNAME** | Alias of one domain to another |
| **MX**    | Mail server for domain |
| **TXT**   | Text data, often for verification (SPF, DKIM) |
| **NS**    | Name server record |

---

## 🚦 Chapter 4: Routing

### 🛣️ What is Routing?

Determines how data travels between devices across networks.

### 📘 Static vs Dynamic Routing

| Type     | Description |
|----------|-------------|
| **Static** | Manually configured routes |
| **Dynamic** | Auto-discovered via protocols |

### 🔁 Common Routing Protocols

| Protocol | Description |
|----------|-------------|
| **OSPF** | Internal routing within organizations |
| **BGP**  | Internet-wide routing across ASNs |

---

## 🔢 Chapter 5: Subnetting

### 📐 CIDR Notation

Format: `IP/prefix_length`  
Example: `192.168.1.0/24`

### 🔢 Binary Conversion Example

| Decimal | Binary     |
|---------|------------|
| 192     | 11000000   |
| 168     | 10101000   |
| 1       | 00000001   |
| 1       | 00000001   |

### 🧮 Subnet Example

- **CIDR:** 192.168.1.0/26  
- **Range:** 192.168.1.1 → 192.168.1.62  
- **Broadcast:** 192.168.1.63  
- **Usable Hosts:** 62

---

## 🔄 NAT (Network Address Translation)

### 🧭 Purpose of NAT

Translates private IPs to public IPs so devices can access the internet.

### 📋 Types of NAT

| Type         | Description |
|--------------|-------------|
| **Static NAT** | One-to-one IP mapping |
| **Dynamic NAT** | Many-to-pool IP mapping |
| **PAT** (Port Address Translation) | Many-to-one with different ports (used in homes) |

---

## 🧪 Chapter 6: Troubleshooting Tools

### 🧰 Common Tools & Commands

| Tool      | Use Case |
|-----------|----------|
| **ping**      | Check host availability |
| **traceroute** / `tracert` | See path packets take |
| **nslookup**  | DNS resolution |
| **dig**       | Detailed DNS query |
| **/etc/hosts**| Manual domain–IP override |

---

## ☁️ Chapter 7: Cloud Networking

### ☁️ Key Components

| Component | Description |
|----------|-------------|
| **VPC**  | Isolated virtual network in cloud |
| **Subnets** | Divide a VPC into smaller sections |
| **Gateways** | Connect cloud network to internet/VPN |

---

## 📘 Glossary

| Term           | Description |
|----------------|-------------|
| **IP Address** | Logical network address |
| **MAC Address**| Hardware address |
| **Router**     | Directs packets across networks |
| **Switch**     | Connects devices in LAN |
| **Firewall**   | Controls traffic access |
| **DNS**        | Resolves domain names to IPs |
| **NAT**        | Allows private IP to access public networks |

---

> ✅ Use this as a handy reference for networking essentials in DevOps, system admin, and cloud engineering
