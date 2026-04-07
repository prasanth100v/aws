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


## 🧭 Create Route Table (IN AWS VPC)
| 🎯 Step | 🧭 Action            | 💡 Details                                                             |
| ------- | -------------------- | ----------------------------------------------------------------------- |
| 1️⃣     | 🌐 Open VPC          | 🔍 AWS Console → Search **VPC**                                         |
| 2️⃣     | 📂 Route Tables       | 📌 Left panel → Click **Route Tables**                                  |
| 3️⃣     | ➕ Create Route Table | 🆕 Click **Create route table**                                         |
| 4️⃣     | 🏷️ Enter Details     | 📝 Name: `my-route-table`<br>🌐 Select your VPC                         |
| 5️⃣     | ✅ Create            | 🚀 Click **Create route table**                                         |
| 6️⃣     | 🔀 Add Routes        | ➡️ `0.0.0.0/0 → IGW` (public)<br>➡️ `0.0.0.0/0 → NAT Gateway` (private) |
| 7️⃣     | 💾 Save Routes       | 💾 Click **Save changes**                                               |
| 8️⃣     | 🔗 Associate Subnet  | 📂 Go to **Subnet associations**                                        |
| 9️⃣     | 📍 Select Subnet     | 🔓 Public subnet → IGW<br>🔐 Private subnet → NAT                       |
| 🔟     | ✅ Save Association   | 🚀 Click **Save**                                                      |

#### 👉 Route table = Traffic controller 🧭 : `Public subnet → Internet Gateway ➡️ 🌍 Private subnet → NAT Gateway 🔒`

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

 * ✨ Route Table → Traffic rules 🌐
 * ✨ NAT Gateway → Private internet access 🚀
