## 💻 What is a Computer Network?
A **computer network** is a group of computers and devices connected together so they can **share data, resources, and communicate**.

- Examples: sharing files, printers, or sending emails  
- Types: LAN (local), WAN (wide), etc.  
- Devices are connected using cables, Wi-Fi, or other technologies  

👉 Simple idea: *Computers talking to each other*

---

## 🌐 How Does the Internet Work?
The **internet** is basically a **global network of networks**.

Here’s a short, simple flow:

1. **You request something**  
   (e.g., open a website in your browser)

2. **Your device sends data**  
   through your internet service provider (ISP)

3. **Data travels in small packets**  
   across many networks using routers

4. **Server responds**  
   The website’s server sends data back

5. **Your device assembles it**  
   and shows the webpage

---

## 🚀 Why Networking is Useful for DevOps (in short)

Networking is essential in **DevOps** because everything runs on **connected systems**.

- **Communication between services**  
  Apps, databases, APIs, and microservices need networking to talk to each other.

- **Cloud & infrastructure access**  
  Platforms like Amazon Web Services, Microsoft Azure, and Google Cloud Platform rely heavily on networking.

- **Deployment & CI/CD**  
  Tools send code across servers and environments over networks.

- **Security**  
  Firewalls, VPNs, and network rules protect systems.

- **Monitoring & troubleshooting**  
  DevOps engineers use networking to detect issues (latency, downtime, etc.)

---

## 🌐 Overview of the OSI Model (in short)

The **OSI (Open Systems Interconnection) Model** is a framework that explains **how data travels across a network in 7 layers**.

### 📊 7 Layers (Top → Bottom)

1. **Application** – User-facing services (browser, email)  
2. **Presentation** – Data format, encryption, compression  
3. **Session** – Manages connections between devices  
4. **Transport** – Reliable delivery (e.g., TCP)  
5. **Network** – Routing using IP addresses  
6. **Data Link** – Physical addressing (MAC), error detection  
7. **Physical** – Cables, signals, hardware  

---

## 🌐 Overview of the TCP/IP Model (in short)

The **TCP/IP model** is a simpler, practical model that explains **how data moves on the internet**. It has **4 layers**.

### 📊 4 Layers (Top → Bottom)

1. **Application Layer**  
   Handles user-level protocols like HTTP, FTP, DNS  

2. **Transport Layer**  
   Ensures data delivery (TCP = reliable, UDP = fast)

3. **Internet Layer**  
   Handles addressing and routing using IP  

4. **Network Access Layer**  
   Deals with physical transmission (hardware, cables, Wi-Fi)

---

## 🌐 IP & Subnets — Quick Overview

### 📌 What is an IP Address?
An **IP (Internet Protocol) address** is a unique number assigned to each device on a network.

- Example: `192.168.1.1`  
- Works like a **home address** for your device  
- Helps data find the correct destination  

### 📌 What is Subnetting?
**Subnetting** means dividing a large network into **smaller networks (subnets)**.

- Improves **performance** (less traffic)  
- Enhances **security**  
- Makes networks easier to manage  

### 📊 Example
- IP: `192.168.1.0/24`  
  - `/24` = subnet mask (first 24 bits are network part)  
  - Allows ~256 devices in that subnet  

---

## 🌐 DNS, NAT & Firewalls — Quick Overview

### 📌 DNS (Domain Name System)
DNS converts **human-friendly names into IP addresses**.

- Example: `google.com` → `142.250.x.x`  
- Like a **phonebook of the internet**  
- Without DNS, you'd have to remember IPs  

### 📌 NAT (Network Address Translation)
NAT allows multiple devices to share **one public IP address**.

- Used in home/office networks  
- Your router assigns **private IPs** internally  
- Saves IP addresses and adds a layer of privacy  

### 📌 Firewalls
A firewall is a **security system** that controls network traffic.

- Blocks unauthorized access  
- Allows safe data to pass  
- Can be hardware or software  

---

## 🌐 `ping`, `traceroute`, `nslookup` — Quick Overview

### 📌 `ping`
Checks if a device/server is reachable and how fast it responds.

- Sends small packets and waits for reply  
- Shows **latency (time)** and packet loss  
- Useful to test connectivity  

👉 Example: `ping google.com`

### 📌 `traceroute` (or `tracert` in Windows)
Shows the **path data takes** to reach a destination.

- Lists all routers (hops) along the way  
- Helps find where delays or failures happen  

👉 Example: `traceroute google.com`

### 📌 `nslookup`
Finds the **IP address of a domain** (DNS query tool).

- Checks DNS records  
- Useful for debugging domain issues  

👉 Example: `nslookup google.com`

---

## ⚖️ Load Balancers — Quick Overview

A **load balancer** distributes incoming network traffic across multiple servers so no single server gets overloaded.

### 📌 Why it’s used
- Improves **performance** (faster response)  
- Ensures **high availability** (if one server fails, others handle traffic)  
- Enables **scalability** (add more servers easily)

### 📊 How it works (simple)
1. User sends request  
2. Load balancer receives it  
3. Forwards to one of many servers  
4. Returns response to user  

### 🔁 Types of Load Balancing
- **Round Robin** – sends requests one by one to each server  
- **Least Connections** – sends to server with least load  
- **IP Hash** – based on user’s IP  

### 🌐 Types by Layer
- **Layer 4 (Transport)** – based on IP & port (fast)  
- **Layer 7 (Application)** – based on content like URL (smart)

---

## 🌐 VPC & VPC Peering — Quick Overview

### 📌 What is a VPC (Virtual Private Cloud)?
A **VPC** is a **private network inside a cloud provider** where you can run your resources securely.

- You control **IP ranges, subnets, routing, and security**  
- Isolated from other users in the cloud  
- Used in platforms like Amazon Web Services, Microsoft Azure, and Google Cloud Platform  

👉 Think of it as your **own private data center in the cloud**

### 📌 What is VPC Peering?
**VPC Peering** connects two VPCs so they can **communicate privately**.

- Traffic stays within the cloud (no public internet)  
- Used to connect different environments (e.g., dev ↔ prod)  
- Works across regions (in many cases)

### 📊 Simple Idea
- VPC = your private network  
- VPC Peering = a **direct private link between two networks**
