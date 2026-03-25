# 🌐 AWS Route 53 – Complete Guide
## 📌 What is AWS Route 53?
AWS Route 53 is a **scalable and highly available DNS (Domain Name System)** web service.

💡 It helps:
- Register domains
- Route internet traffic
- Perform health checks
- Enable failover for high availability

🔢 **Why "53"?**
 Route 53 refers to **Port 53**, used for DNS queries.

👉 Example:
- If a user types **amazon.com**, Route 53 converts it into an **IP address**.
- 👉 It helps users connect to applications by translating domain names → IP addresses. This process is called DNS Resolution..

---

## 🚀 Key Features

### 🏷️ Domain Registration
- Buy and manage domains directly in AWS

### 🌍 DNS Routing
- Converts domain names → IP addresses, Uses DNS records (A, CNAME, etc.)

### 🎯 Traffic Management
- Supports multiple routing policies (Controls how users reach your application)

### ❤️ Health Checks & Failover
- Monitors application health
- Automatically redirects traffic if failure happens

### 🔒 Private DNS
- Internal DNS inside a VPC

### 🛡️ Security
- Supports **DNSSEC** (prevents spoofing attacks)

# 🗂️ Hosted Zones
## 📌 Types of Hosted Zones:

### 🌐 Public Hosted Zone
- For internet-facing domains

### 🔐 Private Hosted Zone
- For internal VPC communication

## 🔗 CNAME vs Alias
| Type   | Description |
|--------|------------|
| CNAME  | Maps to another domain |
| Alias  | Maps to AWS resources (S3, ELB, CloudFront) |

## DNS Record Types (Must Know)
| Record Type | Purpose                 |
| ----------- | ----------------------- |
| 🟢 A Record | Domain → IPv4           |
| 🔵 AAAA     | Domain → IPv6           |
| 🔁 CNAME    | Domain → Domain         |
| ☁️ Alias    | Domain → AWS resource   |
| 📧 MX       | Email servers           |
| 📝 TXT      | Verification / security |
| 🧭 NS       | Name servers            |


---

## 🎯 Routing Policies
### 🔹 Simple Routing
- 👉 One resource only,  No load balancing 
  👉 Example:  Single EC2 website

### ⚖️ Weighted Routing
- ➡️ Split traffic by percentage  (Used in A/B testing)
  👉 70% → Server1, 30% → Server2

### ⚡ Latency-Based Routing
- Routes to lowest latency region (Sends users to nearest region) 
  Example: 👉 India → Mumbai, US → Virginia  

### 🔁 Failover Routing
- Switch to backup if primary fails 
  Example: Server1 → Server2 (High availability) 

### 🌍 Geolocation Routing
- Based on user location  
  Example: Japan users → Tokyo server
  
### 📍 Geoproximity Routing (Advanced traffic shifting)
- Based on distance location + bias  

### 🔀 Multi-Value Routing
- ➡️ Returns multiple healthy IPs

---

## 🌳 Root Domain vs Subdomain
| Type           | Example          |
| -------------- | ---------------- |
| 🌳 Root Domain | example.com      |
| 🌿 Subdomain   | blog.example.com |


## 🔐 DNSSEC (Security Feature)
👉 Full Form: Domain Name System Security Extensions

Protects Against:
- ❌ DNS Spoofing
- ❌ Cache Poisoning
- ✔️ Ensures authentic DNS responses

## 💰 Pricing
| Component       | Cost |
|----------------|------|
| Hosted Zone    | $0.50/month |
| DNS Queries    | $0.40 per million |
| Health Check   | $0.50/month |

### 👉 Example:
   10 million queries = **$4/month**

## 🛠️ Steps to Create Hosted Zone

1️⃣ Open AWS Console → Route 53  
2️⃣ Click **Create Hosted Zone**  
3️⃣ Enter domain name  
4️⃣ Choose Public or Private  
5️⃣ Add DNS Records  
    1. Click **Create Record**
    2. Select type (A, CNAME, etc.)
    3. Enter value
    4. Save 
6️⃣ Update NS in registrar ( Domain Registrar) (GoDaddy, etc.)  
7️⃣ Test using nslookup  

🎉 Done! Route 53 is managing your domain.

---

## ✨ Summary

AWS Route 53 is:
- Highly available 🌍
- Scalable 📈
- Secure 🔐
- Cost-effective 💰

Perfect for:
- Websites
- Applications
- Global traffic routing

## Why Route 53 over traditional DNS?
  - Global infrastructure
  - High availability
  - Built-in health checks
  - Advanced routing policies
  - Tight integration with AWS services
