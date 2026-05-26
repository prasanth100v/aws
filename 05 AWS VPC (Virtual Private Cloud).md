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

## 🏗️ Public vs Private Subnet
| 🧩 **Feature**            | 🌍 **Public Subnet**             | 🔒 **Private Subnet**       | 🧠 **Explanation**                   | 🎯 **Common Use Case**         |
| ------------------------- | -------------------------------- | --------------------------- | ------------------------------------ | ------------------------------ |
| 🌐 **Internet Access**    | ✅ Yes (via Internet Gateway)     | ❌ No direct internet access | Public subnet routes traffic to IGW  | External vs internal workloads |
| 🛣️ **Route Table**       | Route to IGW (`0.0.0.0/0 → IGW`) | No direct IGW route         | Determines internet connectivity     | Network isolation              |
| 🖥️ **Typical Resources** | Web servers, Load Balancers      | Databases, backend apps     | Public-facing vs internal services   | Layered architecture           |
| 🔐 **Security Level**     | Less isolated                    | More secure                 | Private subnets reduce exposure      | Sensitive workloads            |
| 🌍 **Public IP**          | Usually assigned                 | Usually not assigned        | Public IP needed for internet access | External communication         |

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
 | 🧩 **Traffic Type**     | 📖 **Meaning**                   | 🧠 **Detailed Explanation**                      | 💡 **Example**                          | 🎯 **Common Use Case**      |
| ----------------------- | -------------------------------- | --------------------------------------------------- | --------------------------------------- | --------------------------- |
| ⬇️ **Inbound Traffic**  | Incoming traffic to a resource   | Requests coming *into* a server, instance,         | User accessing website on port `80/443` | Web server access           |
| ⬆️ **Outbound Traffic** | Outgoing traffic from a resource | Requests leaving a server, instance                | Internet access, DB communication   | App → Database, software updates |

#### 🔒 Steps to Create a Security Group in AWS VPC
| 🔢 Step     | 🛠️ Action                      | 📘 Details                                                                            |
| ----------- | ------------------------------- | ------------------------------------------------------------------------------------- |
| 🔐 **1️⃣**  | ☁️ **Login to AWS Console**     | Open [AWS Management Console]                                                      |
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

## 🌐 Elastic IP (EIP)
 * Elastic IP is a `fixed Static public IPv4 address` used for `stable internet connectivity` in AWS.
 * Unlike normal public IPs, an Elastic IP `does not change` when the instance is stopped and started.
 * Used for EC2 / NAT Gateway
 * 💰 Pricing :
    * ✅ One attached Elastic IP is usually free. ✅ Elastic IP works only with `IPv4`.
    * ❌ Unused Elastic IPs are chargeable.

 * 🎯 Interview Answer 
  * To create an `Elastic IP` in AWS, go to the EC2 dashboard, allocate a new Elastic IP, and associate it with an EC2 instance to provide a `static public IP` address.


### 🧱 Network ACLs (NACLs)
 * A Network ACL (`Network Access Control List`) is a security layer in a VPC that controls inbound and outbound traffic at the `subnet level`
 * Subnet-level firewall
 * Stateless (rules apply both ways)

#### 📦 Example NACL Rules
* Inbound Rules

| Rule # | Type        | Port | Source    | Allow/Deny |
| ------ | ----------- | ---- | --------- | ---------- |
| 100    | HTTP        | 80   | 0.0.0.0/0 | ALLOW      |
| 110    | SSH         | 22   | Your IP   | ALLOW      |
| 120    | All Traffic | All  | 0.0.0.0/0 | DENY       |

* Outbound Rules

| Rule # | Type        | Port | Destination | Allow/Deny |
| ------ | ----------- | ---- | ----------- | ---------- |
| 100    | All Traffic | All  | 0.0.0.0/0   | ALLOW      |

* 🎯 Interview Answer 
  * To create a Network ACL in AWS, go to the VPC dashboard, create a `Network ACL`, configure `inbound` and `outbound rules`, and associate it with the `required subnet`.

### 🛡️ Security Group vs NACL
| 🧩 **Feature**          | 🛡️ **Security Group (SG)**  | 🚧 **Network ACL (NACL)** | 🧠 **Explanation**                      | 
| ----------------------- | ---------------------------- | ------------------------- | --------------------------------------- |
| 🔄 **Stateful**         | ✅ Yes                      | ❌ No                      | SG remembers connections; NACL does not | 
| 🚦 **Allow / Deny**     | Allow only                   | Allow & Deny              | NACL supports explicit deny rules       | 
| 📋 **Rule Processing**  | All rules evaluated          | Rules processed in order  | NACL stops at first matching rule       | 
| 🔐 **Default Behavior** | Deny inbound, allow outbound | Depends on rules          | SG safer by default                     | 
| 🔗 **Association**      | Attached to instances        | Attached to subnets       | Different protection scope              |

