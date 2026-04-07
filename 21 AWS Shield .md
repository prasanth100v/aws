# 🛡️ AWS Shield
## 🚀 What is AWS Shield?
 * ✨ AWS Shield is a managed service from Amazon Web Services that protects applications from `DDoS` (Distributed Denial of Service) attacks.
 * 👉 DDoS = flooding servers with `huge traffic` to crash them 💥
 * ⚙️ Types of AWS Shield:
      * 🟢 AWS Shield Standard – Free, 🔄 `automatic protection` against common DDoS attacks.
      * 🔵 AWS Shield Advanced – Paid service with 🚀 `Advanced protection`, real-time monitoring, and 📞 `AWS support` during attacks

### ❓ Why Use AWS Shield?

- 🛡️ Protects websites and applications from DDoS attacks.  
- 🔗 Works with CloudFront, ALB, Route 53, and AWS Global Accelerator ⚡ Maintains availability & performance.  
- ⚡ Reduces downtime and latency during attacks.  

---

# 🔥 What is AWS Firewall Manager?

 * AWS Firewall Manager allows centralized management of security policies like `WAF and Shield` across multiple AWS accounts, ensuring consistent security configurations.
 * Helps to manage:
     * WAF rules 🛡️
     * Shield protection ⚡
     * Security policies 🔐
 * 📌 `Use Case Example`:
     * A company with `multiple AWS accounts` wants to apply the `same WAF rules` to `all ALBs` and `API Gateways`.
     * 💡 Instead of configuring each account manually, `AWS Firewall Manager` automatically enforces the rules.

---

# 💰 AWS Cost Explorer and Budgets:

 * 📊 Cost Explorer is for analyzing past and current costs.
 * It provides `reports`, `trends`, and `cost forecasts` to understand where money is being spent.
 * 🎯 while Budgets is for `setting limits` and `getting alerts`, ensuring better `cost management`.
 * 👉 Cost Explorer = `Analyze` 📊 | Budgets = `Control` 🎯

### 💰 Cost Explorer vs Budgets (AWS)
| 🧩 Feature | 📊 Cost Explorer        | 🎯 Budgets                  |
| ---------- | ----------------------- | --------------------------- |
| 🎯 Purpose | 🔍 Cost analysis        | 🎯 Cost control             |
| ⏳ Time     | 📊 Past & current usage | 🔮 Future tracking & alerts |
| 🚨 Alerts  | ❌ No                    | ✅ Yes (email/SNS alerts)    |

---

# 🌐 What is Route Table?

 * ✨ A route table in a VPC defines how network traffic is directed.
 * It contains routes that specify the `destination` and `target`, such as `internet gateways` or `NAT gateways`.
 * `Route Table` = `Traffic rules for network`
 * route table = `set of rules` (routes)

 ### 📌 Important Points
   * 📌 Every VPC has a default route table, And you can create `custom route tables`.
   * 📌 Each subnet in a VPC must be associated with `one route table`, which controls the `traffic` for that subnet.
   * 📌 If a subnet is not associated with a `custom route table`, it uses the `VPC’s main route table`.
   * 🧩 Each route consists of:
        * 🎯 Destination : The `IP address range` (`CIDR block 0.0.0.0/0`) where traffic is intended to go.
        * 🔗 Target      : The destination for the traffic (e.g., an `internet gateway`, `NAT gateway`, `VPC peering` connection) (`Where traffic goes`).
        * 🌍 Allow internet access :  Destination: `0.0.0.0/0` : Target: `Internet Gateway`

---

# 🚀 NAT Gateway (Private Subnet Internet Access)
## 🚀 What is NAT Gateway?
  * ✨ A NAT Gateway allows instances in a `private subnet` to access the internet without exposing them publicly.
  * It is placed in a public subnet and associated with a `route table` for `private subnets`.
  * 🎯 Real-Life Example :
      * You have a `backend server` (`DB/API`) in private subnet. It needs to : `Install packages`, Call `external APIs`
      * 👉 NAT Gateway access internet securely without exposing it.
      * 🌍 One NAT Gateway per `AZ` (best practice)

| 🧩 Component      | 💡 Description                                                     |
| ----------------- | ------------------------------------------------------------------- |
| 🔒 Private Subnet | 🖥️ Secure instances (no direct internet access)                    |
| 🌍 Public Subnet  | 🚪 Where `NAT Gateway` is placed                                   |
| 🌐 Elastic IP     | 🔑 Public IP used by `NAT Gateway` for internet access             |
| 🧭 Route Table    | 🔀 Sends traffic (`0.0.0.0/0`) from `private subnet → NAT Gateway` |

## 🔄 Step-by-Step Working
| 🔢 Step | 💡 What Happens                                         |
| ------- | -------------------------------------------------------- |
| 1️⃣     | 🖥️ Private EC2 sends request (e.g., `install software`)  |
| 2️⃣     | 🧭 Route table sends traffic to `NAT Gateway `           |
| 3️⃣     | 🔄 NAT Gateway converts **`Private IP → Public IP`**     |
| 4️⃣     | 🌍 Request goes to `internet `                           |
| 5️⃣     | 📥 Internet sends response back                          |
| 6️⃣     | 🔄 NAT Gateway converts **`Public IP → Private IP`**     |
| 7️⃣     | ✅ Private EC2 receives the response                     |

## ⚠️ Important Points :
  * 💰 `NAT Gateway is paid service`, 🌍 `Must be placed in a public subnet`, 🔁 `Works only for outbound traffic`, 📍 `Requires Elastic IP`

## 🚀 How to create NAT Gateway?
| 🎯 Step | 🧭 Action                 | 📝 Details                                                                                |
| ------- | -------------------------- | ------------------------------------------------------------------------------------------ |
| 1️⃣     | 🏗️ Create VPC              | 🌐 Go to **Amazon Web Services Console → VPC → Create VPC<br>Example CIDR: `10.0.0.0/16`   |
| 2️⃣     | 🧩 Create Subnet           | 🔓 Public Subnet: `10.0.0.0/24` (for NAT)<br>🔐 Private Subnet: `10.0.1.0/24` (for EC2)    |
| 3️⃣     | 🌍 Create Internet Gateway | 🔗 Create IGW and **attach to VPC**<br>👉 Enables internet for public subnet               |
| 4️⃣     | 🧭 Public Route Table      | ➡️ Add route:<br>`0.0.0.0/0 → Internet Gateway`<br>👉 Public subnet gets internet          |
| 5️⃣     | 🌐 Allocate Elastic IP     | 🔑 Go to Elastic IPs → Allocate new IP<br>👉 Used by NAT Gateway                           |
| 6️⃣     | 🚪 Create NAT Gateway      | 📍 Select:<br>• Public Subnet<br>• Elastic IP<br>👉 NAT must be in public subnet           |
| 7️⃣     | 🔒 Private Route Table     | ➡️ Add route:<br>`0.0.0.0/0 → NAT Gateway`<br>👉 Private subnet gets internet via NAT      |
| 8️⃣     | 🖥️ Launch EC2 (Private)    | 🚫 Launch EC2 in private subnet<br>🚫 No public IP                                         |
| 9️⃣     | ✅ Test Connectivity       | 🌐 Ensure the instance can access the internet (e.g., by running `ping or curl` commands)   |

----

### 🌐 NAT Gateway vs Internet Gateway (AWS)
| 🧩 Feature          | 🚪 NAT Gateway     | 🌍 Internet Gateway      |
| ------------------- | ------------------ | ------------------------ |
| 🎯 Used for         | 🔒 Private subnet  | 🌐 Public subnet         |
| 📥 Incoming Traffic | ❌ Not allowed      | ✅ Allowed                |
| 📤 Outgoing Traffic | ✅ Allowed          | ✅ Allowed                |
| 🌐 Public IP Needed | ❌ Instance no need | ✅ Required for instances |

## 🌐 Inbound vs Outbound Traffic (AWS Networking)
| 🧩 Type         | 💡 Meaning                                  | 🔄 Direction          | 📌 Example                      |
| --------------- | ------------------------------------------- | --------------------- | ------------------------------- |
| 🔽 **Inbound**  | 📥 Traffic **coming into** your resource    | 🌍 Internet ➝ Server  | 🌐 User accessing your website  |
| 🔼 **Outbound** | 📤 Traffic **going out from** your resource | 🖥️ Server ➝ Internet | 📡 Server calling API / Downloading updates |

### 📊 Real-World Scenarios
| 🧩 Scenario                              | 🔄 Type     |
| ---------------------------------------- | ----------- |
| 🌐 Open website in browser → reaches EC2 | 🔽 Inbound  |
| 🔐 SSH from laptop to EC2                | 🔽 Inbound  |
| 📦 EC2 downloads updates (`yum update`)  | 🔼 Outbound |
| 🔗 EC2 calls external API                | 🔼 Outbound |

---

### 🏁 Final Summary

 * ✨ Shield → DDoS protection 🛡️
 * ✨ Firewall Manager → Central security control 🔥
 * ✨ Cost Explorer → Analyze costs 📊
 * ✨ Budgets → Control spending 🎯
 * ✨ Route Table → Traffic rules 🌐
 * ✨ NAT Gateway → Private internet access 🚀
