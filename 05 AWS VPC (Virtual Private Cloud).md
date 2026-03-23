# 🌐 AWS VPC (Virtual Private Cloud) – Complete Guide

---

## 🧠 What is AWS VPC?

Amazon VPC (Virtual Private Cloud) is a **logically isolated network** in AWS.

👉 It allows you to:
- Define IP ranges
- Create subnets
- Configure routing
- Apply security controls

---

## 🧩 Key Components of VPC

### 🌍 VPC
- Your private network in AWS

### 🏠 Subnets
- Divide VPC into smaller networks
- Types:
  - 🌐 Public Subnet
  - 🔒 Private Subnet
- Limit: Up to 200 subnets per VPC

---

### 🛣️ Route Tables
- Control how traffic flows inside VPC

---

### 🌐 Internet Gateway (IGW)
- Enables internet access
- Only **one IGW per VPC**

---

### 🔄 NAT Gateway
- Allows **private subnet → internet (outbound only)**
- Deployed in **public subnet**

---

### 🔥 Security Groups
- Instance-level firewall
- Controls inbound & outbound traffic

---

### 🧱 Network ACLs (NACLs)
- Subnet-level firewall
- Stateless (rules apply both ways)

---

### 🔗 VPC Peering
- Connect two VPCs privately

---

### 🌉 Transit Gateway
- Central hub for connecting multiple VPCs

---

### 🚪 VPC Endpoints
- Private access to AWS services (S3, DynamoDB)
- No internet required

---

### 🌐 IP Support
- Supports both IPv4 & IPv6

---

## 🏗️ Public vs Private Subnet

| Feature | Public Subnet | Private Subnet |
|--------|---------------|----------------|
| Internet Access | ✅ Yes (via IGW) | ❌ No |
| Use Case | Web servers | Databases, backend |

---

## 📏 CIDR Block

- Defines IP range of VPC  
- Example: `10.0.0.0/16` → 65,536 IPs

---

## 🔢 VPC Limits

- Default: 5 VPCs per region per account
- Can request increase via AWS Support

---

## 🌍 Region Scope

- VPC is **region-specific**
- Cannot span multiple regions

---

## 💰 VPC Pricing

- VPC itself → FREE ✅
- Paid services:
  - NAT Gateway 💸
  - Transit Gateway 💸
  - Cross-region peering 💸

---

## 🌐 Elastic IP (EIP)

- Static public IPv4 address
- Used for EC2 / NAT Gateway
- Charged if unused

---

## 🏢 Availability Zones (AZs)

- Separate data centers in a region
- Improves:
  - High availability
  - Fault tolerance

👉 Example (Mumbai):
- ap-south-1a
- ap-south-1b
- ap-south-1c

---

## ⚖️ IGW vs NAT Gateway

| Feature | IGW | NAT Gateway |
|--------|-----|-------------|
| Inbound | ✅ Yes | ❌ No |
| Outbound | ✅ Yes | ✅ Yes |

---

## 🔐 VPN Connection

- Secure connection between:
  - On-premises ↔ AWS VPC

---

## 🚀 AWS Direct Connect

- Private dedicated connection to AWS
- Benefits:
  - Better performance
  - More secure
  - Reliable

---

## 🚪 VPC Endpoint

- Private access to AWS services
- No need for:
  - Internet Gateway
  - NAT Gateway
  - VPN

---

## 🌉 Virtual Private Gateway (VGW)

- Connects VPC to:
  - VPN
  - Direct Connect

---

## 🛠️ Steps to Create VPC

1. Login to AWS Console  
2. Open VPC Service  
3. Click **Create VPC**  
4. Enter:
   - Name
   - CIDR (e.g., 10.0.0.0/16)
5. Enable DNS (optional)  
6. Click Create  

---

## 🔧 Next Steps

- Create Subnets  
- Attach Internet Gateway  
- Configure Route Tables  
- Setup Security Groups & NACLs  

---

## 🎯 Summary

- VPC = Private AWS network
- Subnets = Divide network
- IGW/NAT = Internet access control
- SG/NACL = Security layers
- Multi-AZ = High availability

---

🔥 **Master VPC = Strong Networking Foundation for AWS & DevOps!**
