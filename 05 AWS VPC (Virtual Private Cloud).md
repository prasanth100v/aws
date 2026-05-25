# 🌐 AWS VPC (Virtual Private Cloud) 
## 🧠 What is AWS VPC?
 * Amazon VPC (Virtual Private Cloud) is a **logically isolated network** in AWS.
 * 👉 It allows you to:
    - Define IP ranges
    - Create subnets
    - Configure routing
    - internet connectivity
    - Apply security controls for cloud resources.

### 🌍 Steps to create VPC
 * To create a VPC in AWS, go to the VPC dashboard, click Create VPC, provide a CIDR block (10.0.0.0/16), create public/private subnets, attach an Internet Gateway, configure route tables
 * and then launch resources like EC2 instances inside the VPC.

# 🧩 Key Components of VPC
| 🧩 **Feature**             | 📖 **Purpose**        | 🧠 **Explanation**                      | 💡 **Example**                |
| -------------------------- | --------------------- | --------------------------------------- | ----------------------------- |
| 🌐 **CIDR Block**          | IP address range      | Defines network size for VPC            | `10.0.0.0/16`                 |
| 🏘️ **Subnets**            | Network segmentation  | Divide VPC into `public/private` sections | Public subnet, Private subnet |
| 🛣️ **Route Tables**       | Traffic routing       | Controls where `network traffic goes`     | Route internet traffic to `IGW` |
| 🌍 **Internet Access**     | External connectivity | Enables internet communication          | Internet Gateway              |
| 🛡️ **Security Rules**     | Traffic protection    | Control `inbound/outbound traffic `       | Security Groups & NACLs       |
| 🔗 **Hybrid Connectivity** | Connect on-premises   | Integrate AWS with data centers         | `VPN / Direct Connect  `        |

## 🏠 Subnets
 - It divides the VPC into smaller networks for better Security.
 - A subnet is a `range of IP addresses inside a VPC` where AWS resources like EC2 instances are launched.
 -  Limit: Up to `200 subnets` per VPC
 - Types:
   - 🌐 Public Subnet   :
       - subnet connected to the internet using an Internet Gateway., Used for : Web servers and Load balancers
   - 🔒 Private Subnet
       - subnet without direct internet access., Used for : Databases and Backend applications

 * 🎯 Interview Answer
   * To create a subnet in AWS, go to the VPC dashboard, select Subnets, click Create subnet, choose the `VPC`, provide` subnet name`, Availability Zone,
   * and CIDR block, then configure routing depending on whether it is `public` or `private`.

## 🛣️ Route Tables
  * Route Table controls the path of network traffic for `subnets` inside a VPC.
  * 🎯 Interview Answer 
    * To create a Route Table in AWS, go to the VPC dashboard, create a Route Table, add routes like `Internet Gateway` or `NAT Gateway`, and associate the Route Table with the required `subnet`.

## 🌐 Internet Gateway (IGW)
- An Internet Gateway enables internet access for resources in `public subnets`.
- Only **one IGW per VPC**

#### 🌐 Steps to Create and Configure an Internet Gateway (IGW) in AWS
| 🔢 Step     | 🛠️ Action                                 | 📘 Details                                                                            |
| ----------- | ------------------------------------------ | ------------------------------------------------------------------------------------- |
| 🔐 **1️⃣**  | ☁️ **Login to AWS Console**                | Open [AWS Management Console](https://aws.amazon.com/console/?utm_source=chatgpt.com) |
|             |                                         | Sign in to your AWS account                                                           |
|             |                                          | Select your AWS Region                                                                |
| 🌐 **2️⃣**  | 📂 **Open VPC Dashboard**                  | Search for **VPC** in AWS search bar                                                  |
|             |                                         | Open the **VPC Dashboard**                                                            |
| 🚪 **3️⃣**  | 🌍 **Go to Internet Gateways**             | From the left-side menu click **Internet Gateways**                                   |
|             |                                           | Click **Create internet gateway**                                                     |
| ⚙️ **4️⃣**  | 🏷️ **Configure Internet Gateway**         | Enter a Name tag                                                                      |
|             |                                          | Example: **My-IGW**                                                                   |
|             |                                           | Click **Create internet gateway**                                                     |
| 🔗 **5️⃣**  | 🌐 **Attach IGW to VPC**                   | Select the created IGW                                                                |
|             |                                           | Click **Actions → Attach to VPC**                                                     |
|             |                                          | Select your VPC                                                                       |
|             |                                          | Example: **My-VPC**                                                                   |
|             |                                           | Click **Attach internet gateway**                                                     |
| 🛣️ **6️⃣** | 📡 **Update Route Table**                  | Go to **Route Tables**                                                                |
|             |                                          | Select **Public Route Table**                                                         |
|             |                                          | Open **Routes** tab                                                                   |
|             |                                           | Click **Edit routes → Add route**                                                     |
|             |                                          | **Destination:** `0.0.0.0/0`                                                          |
|             |                                          | **Target:** Internet Gateway                                                          |
|             |                                          | Click **Save changes**                                                                |
| 🌐 **7️⃣**  | 📌 **Associate Public Subnet**             | Open **Subnet Associations**                                                          |
|             |                                          | Click **Edit associations**                                                           |
|             |                                          | Select your **Public Subnet**                                                         |
|             |                                          | Click **Save**                                                                        |
| 🖥️ **8️⃣** | 🌍 **Enable Public IP for EC2 (Optional)** | Go to **Subnets**                                                                     |
|             |                                          | Select subnet                                                                         |
|             |                                          | Click **Actions → Edit subnet settings**                                              |
|             |                                           | Enable **Auto-assign public IPv4 address**                                            |

## 🔄 NAT Gateway (Network Address Translation Gateway)
 * NAT Gateway allows private subnet instances to access the internet without allowing incoming internet traffic directly to them.
 * 👉 It is mainly used for:
    * Software updates
    * Downloading packages
    * Allows **private subnet → internet (outbound only)**, Deployed in **public subnet**

#### 📋 Steps to Create a NAT Gateway in AWS
| 🔢 Step     | 🛠️ Action                        | 📘 Details                                                                            |
| ----------- | --------------------------------- | ------------------------------------------------------------------------------------- |
| 🔐 **1️⃣**  | ☁️ **Login to AWS Console**       | Open [AWS Management Console](https://aws.amazon.com/console/?utm_source=chatgpt.com) |
| 🌐 **2️⃣**  | 📂 **Open VPC Dashboard**         | Search for **VPC** and open the VPC Dashboard                                         |
| 🌍 **3️⃣**  | 📌 **Create Elastic IP**          | Go to **Elastic IPs**                                                                 |
|             | ➕                                 | Click **Allocate Elastic IP address**                                                 |
|             | ✅                                 | Click **Allocate**                                                                    |
| 🚪 **4️⃣**  | 📡 **Go to NAT Gateways**         | From the left-side menu click **NAT Gateways**                                        |
| 🚀 **5️⃣**  | ➕ **Create NAT Gateway**          | Click **Create NAT Gateway**                                                          |
| ⚙️ **6️⃣**  | 📝 **Configure NAT Gateway**      | Select **Public Subnet**                                                              |
|             | 🌍                                | Attach the **Elastic IP**                                                             |
|             | 🏷️                               | Example Name: `My-NAT-Gateway`                                                        |
| ✅ **7️⃣**   | 🎯 **Create NAT Gateway**         | Click **Create NAT Gateway**                                                          |
| 🛣️ **8️⃣** | 🔒 **Update Private Route Table** | Go to **Route Tables**                                                                |
|             | 📂                                | Select **Private Route Table**                                                        |
|             | 🧭                                | Open **Routes** tab                                                                   |
|             | ➕                                 | Click **Edit routes → Add route**                                                     |
|             | 🌍                                | **Destination:** `0.0.0.0/0`                                                          |
|             | 🎯                                | **Target:** NAT Gateway                                                               |
|             | 💾                                | Click **Save changes**                                                                |

## 🔥 Security Groups
 * A Security Group is a Instance-level virtual firewall that controls `inbound` and `outbound traffic` for resources like EC2 instances inside a VPC
 * A Security Group controls which traffic is allowed to enter or leave 
 * 🚀 Security Groups are commonly attached to:
    * EC2 Instances
    * RDS Databases
    * Load Balancers
    * ECS/EKS services

 #### 🛡️ Types of Security Group Rules
| 🧩 **Rule Type**      | 📖 **Purpose**   | 🧠 **What It Controls**                  | 💡 **Common Examples**                 | 🎯 **Use Case**           |
| --------------------- | ---------------- | ------------------------------------------ | -------------------------------------- | ------------------------- |
| ⬇️ **Inbound Rules**  | Incoming traffic | Controls traffic entering the EC2 instance | SSH (`22`), HTTP (`80`), HTTPS (`443`) | Web server access         |
| ⬆️ **Outbound Rules** | Outgoing traffic | Controls traffic leaving the EC2 instance  | Internet access, DB communication      | App → Database/API access |

#### 🔒 Steps to Create a Security Group in AWS VPC
| 🔢 Step     | 🛠️ Action                      | 📘 Details                                                                            |
| ----------- | ------------------------------- | ------------------------------------------------------------------------------------- |
| 🔐 **1️⃣**  | ☁️ **Login to AWS Console**     | Open [AWS Management Console](https://aws.amazon.com/console/?utm_source=chatgpt.com) |
|             | 🔑                              | Sign in to your AWS account                                                           |
|             | 🌍                              | Select your AWS Region                                                                |
| 🌐 **2️⃣**  | 📂 **Open VPC Dashboard**       | Search for **VPC** and open the VPC Dashboard                                         |
| 🛡️ **3️⃣** | 🔒 **Go to Security Groups**    | From the left-side menu click **Security Groups**                                     |
|             | ➕                               | Click **Create security group**                                                       |
| ⚙️ **4️⃣**  | 📝 **Configure Security Group** | Enter Security Group details                                                          |
|             | 🏷️                             | **Security Group Name:** `Web-SG`                                                     |
|             | 📄                              | **Description:** Security group for web server                                        |
|             | 🌐                              | **VPC:** `My-VPC`                                                                     |
| 📥 **5️⃣**  | 🚪 **Add Inbound Rules**        | Configure incoming traffic rules                                                      |
|             | 🔑                              | **SSH** → TCP → Port `22` → Source `Your IP`                                          |
|             | 🌍                              | **HTTP** → TCP → Port `80` → Source `0.0.0.0/0`                                       |
|             | 🔐                              | **HTTPS** → TCP → Port `443` → Source `0.0.0.0/0`                                     |
| 📤 **6️⃣**  | 🌐 **Add Outbound Rules**       | Configure outgoing traffic rules                                                      |
|             | ✅                               | Default: **All Traffic → 0.0.0.0/0**                                                  |
|             | 💡                              | Usually default outbound rule is enough                                               |
| ✅ **7️⃣**   | 🎯 **Create Security Group**    | Click **Create security group**                                                       |
| 🖥️ **8️⃣** | 🔗 **Attach SG to EC2**         | Go to EC2 → Select Instance                                                           |
|             | ⚡                               | Actions → Security → Change security groups                                           |
|             | 📌                              | Attach the created Security Group                                                     |

### 🧱 Network ACLs (NACLs)
- Subnet-level firewall
- Stateless (rules apply both ways)

---

### 🔗 VPC Peering
- Connect two VPCs privately

### 🌉 Transit Gateway
- Central hub for connecting multiple VPCs

### 🚪 VPC Endpoints
- Private access to AWS services (S3, DynamoDB)
- No internet required

### 🌐 IP Support
- Supports both IPv4 & IPv6

## 🏗️ Public vs Private Subnet

| Feature | Public Subnet | Private Subnet |
|--------|---------------|----------------|
| Internet Access | ✅ Yes (via IGW) | ❌ No |
| Use Case | Web servers | Databases, backend |

---

## 📏 CIDR Block

- Defines IP range of VPC  
- Example: `10.0.0.0/16` → 65,536 IPs

## 🔢 VPC Limits

- Default: 5 VPCs per region per account
- Can request increase via AWS Support

## 🌍 Region Scope

- VPC is **region-specific**
- Cannot span multiple regions

## 💰 VPC Pricing

- VPC itself → FREE ✅
- Paid services:
  - NAT Gateway 💸
  - Transit Gateway 💸
  - Cross-region peering 💸

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

## ⚖️ IGW vs NAT Gateway

| Feature | IGW | NAT Gateway |
|--------|-----|-------------|
| Inbound | ✅ Yes | ❌ No |
| Outbound | ✅ Yes | ✅ Yes |

---

## 🔐 VPN Connection

- Secure connection between:
  - On-premises ↔ AWS VPC

## 🚀 AWS Direct Connect

- Private dedicated connection to AWS
- Benefits:
  - Better performance
  - More secure
  - Reliable

## 🚪 VPC Endpoint

- Private access to AWS services
- No need for:
  - Internet Gateway
  - NAT Gateway
  - VPN

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

#### 🔧 Next Steps

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
