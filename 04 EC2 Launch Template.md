# 🚀 AWS EC2 Launch Template
## 🧩 What is an EC2 Launch Template?
 * An **EC2 Launch Template** is a **pre-configured blueprint** used to launch EC2 instances.
 * 👉 It defines all required configuration settings in one place.

## 📦 What Does It Include?
 * A Launch Template contains:
    - 🖥️ AMI (Amazon Machine Image)
    - ⚙️ Instance Type (t2.micro, m5, etc.)
    - 🔑 Key Pair (SSH access)
    - 🔐 Security Groups (firewall rules)
    - 🌐 Network Settings (VPC, Subnet)
    - 💾 Storage (EBS volumes)
    - 🧠 IAM Roles (permissions)
    - 📜 User Data (startup scripts)

## ✨ Key Features
  - 🔢 **Versioning Support** → Maintain multiple template versions
  - 🔁 **Reusable Configuration** → Launch multiple identical instances
  - ⚡ **Automation Ready** → Used in Auto Scaling Groups
  - 🔄 **Flexible Updates** → Modify without affecting running instances

## ⚠️ Important Note
> Deleting a Launch Template ❌ does NOT terminate running instances created from it.

## 🏗️ Why Use Launch Templates?
 - ⚡ Faster deployments
 - 🔁 Consistency across environments
 - 🤖 Perfect for automation (`Auto Scaling`)
 - 🛠️ Easy to manage configurations

---

## 🛠️ Steps to Create a Launch Template
| 🔢 Step  | 🛠️ Action                     | 📘 Description                                               |
| -------- | ------------------------------ | ------------------------------------------------------------ |
| 🔐 1️⃣   | ☁️ **Open EC2 Dashboard**      | Login to AWS Console and navigate to EC2 Service             |
| 📂 2️⃣   | 📑 **Go to Launch Templates**  | From the left menu, click **Launch Templates**               |
| 🚀 3️⃣   | 🆕 **Create Template**         | Click **Create launch template**                             |
| 📝 4️⃣   | 🏷️ **Enter Template Details** | Provide Template Name & Description                          |
| 🖥️ 5️⃣  | 📀 **Choose AMI ID**           | Select operating system like Amazon Linux 🟡 or Ubuntu 🟠    |
| ⚙️ 6️⃣   | 💻 **Select Instance Type**    | Choose instance type such as `t2.micro`                      |
| 🔑 7️⃣   | 🛡️ **Choose Key Pair**        | Select or create SSH key pair                                |
| 🌐 8️⃣   | 🔒 **Configure Network**       | Select VPC, Subnet, and Security Groups                      |
| 💾 9️⃣   | 📦 **Configure Storage**       | Add Root Volume and optional EBS volumes                     |
| 🧠 🔟    | ⚡ **Advanced Settings**        | Configure IAM Role, User Data, Monitoring, Shutdown behavior |
| ✅ 1️⃣1️⃣ | 🎯 **Create Launch Template**  | Review settings and click **Create launch template** 🚀      |

---

## 🚀 Launch EC2 Instance Using Launch Template
| 🔢 Step | 🛠️ Action                           | 📘 Description                                               |
| ------- | ------------------------------------ | ------------------------------------------------------------ |
| 🔐 1️⃣  | ☁️ **Go to EC2 Console**             | Login to AWS Console and open EC2 Dashboard                  |
| 📂 2️⃣  | 📑 **Open Launch Templates**         | Click **Launch Templates** from the left-side menu           |
| 🎯 3️⃣  | 🗂️ **Select Launch Template**       | Choose the required launch template from the list            |
| 🚀 4️⃣  | ▶️ **Launch Instance from Template** | Click **Launch instance from template**                      |
| 🔄 5️⃣  | 📌 **Choose Template Version**       | Select Default Version ⭐ or Specific Version 🔢              |
| 👀 6️⃣  | 📝 **Review Configuration**          | Verify AMI, Instance Type, Network, Storage, Security Groups |
| ✅ 7️⃣   | 🎉 **Click Launch**                  | Launch the EC2 instance using the selected template 🚀       |

---

## 🔄 Launch Template vs Launch Configuration
| 🧩 **Feature**              | 🚀 **Launch Template**                   | 📦 **Launch Configuration** | 🧠 **Explanation**                       | 🎯 **Recommendation**     |
| --------------------------- | ---------------------------------------- | --------------------------- | ---------------------------------------- | ------------------------- |
| 🔢 **Versioning**           | ✅ Supported                              | ❌ Not supported             | Templates can maintain multiple versions | Easier updates & rollback |
| ⚙️ **Flexibility**          | ✅ High                                   | ❌ Limited                   | Supports more EC2 features               | Modern deployments        |
| 🆕 **Latest Features**      | ✅ Supported                              | ❌ Limited support           | Supports new AWS capabilities            | Future-proof              |
| 💻 **Instance Types**       | ✅ Multiple instance types                | ❌ Single instance type      | Better Auto Scaling flexibility          | Cost optimization         |
| 📈 **Auto Scaling Support** | ✅ Full support                           | ⚠️ Legacy support           | Preferred by AWS                         | Production standard       |

## 🎯 Real-World Use Case
 - Auto Scaling Group uses Launch Template
 - Automatically launches instances during:
   - High traffic 📈
   - Failures 🔁

## 🔥 Pro Tips
  - Always use **latest version** in Auto Scaling
  - Use **User Data** to automate app setup
  - Combine with **Load Balancer** for high availability

## 🎯 Summary
  - Launch Template = Blueprint for EC2
  - Saves time & ensures consistency
  - Supports versioning & automation
  - Essential for Auto Scaling

🚀 **Master Launch Templates → Build scalable & automated AWS systems!**

---

## ⚡ Scenario-Based AWS EC2 — Rapid Fire Q&A
| 🔢 Q#   | ❓ Scenario Question                                      | 💡 Answer                                                                                     |
| ------- | ---------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| 🔐 Q1   | Unable to SSH into EC2 instance — what do you check first? |  Security Group (`port 22`) <br> Key pair <br> Public IP <br> Route table <br> Instance state |
| 🔐 Q2   | SSH timeout error — possible reasons?                      |  Port 22 blocked <br> No Internet Gateway <br> Wrong subnet route <br> Instance unreachable |
| 🔐 Q3   | Permission denied (publickey) during SSH — why?            |  Wrong SSH key or incorrect permissions on `.pem` file.                                     |
| 🔐 Q4   | Correct permission for `.pem` file?                        | 👉 `chmod 400 key.pem`                                                                        |
| 🌐 Q5   | EC2 running but website inaccessible — checks?             |  Web service status <br> Security Group <br> Load Balancer <br> Port listening              |
| 🌐 Q6   | Website accessible locally but not externally — reason?    | 👉 Port `80/443` blocked in Security Group or firewall.                                         |
| 🌐 Q7   | Application service crashed after reboot — fix?            | 👉 Enable service using: `systemctl enable <service>`                                         |
| 💾 Q8   | EC2 disk full — what do you do?                            |  Find large files/logs <br> Extend EBS volume <br> Resize filesystem                        |
| 💾 Q9   | Deleted logs but disk still full — why?                    | 👉 Process still holding deleted file.                                                        |
| 💾 Q10  | Command to check disk usage?                               | 👉 `df -h`                                                                                    |
| ⚡ Q11   | EC2 instance very slow — checks?                           | CPU usage <br> Memory <br> Disk I/O (Input/Output) <br> Network                            |
| ⚡ Q12   | Command to identify high CPU process?                      | 👉 `top`                                                                                      |
| ⚡ Q13   | High memory usage issue — action?                          | 👉 Restart leaking app or scale instance.                                                     |
| 📈 Q14  | Traffic suddenly increased — solution?                     | 👉 Use Auto Scaling + Load Balancer.                                                          |
| 📈 Q15  | One EC2 instance overloaded while others idle — reason?    | 👉 `Load balancer misconfiguration.`                                                            |
| 🌍 Q16  | EC2 in private subnet cannot access internet — checks?     | 👉 `NAT Gateway + route table.  `                                                               |
| 🌍 Q17  | Public EC2 instance has no internet — reason?              | 👉 `Missing IGW route `or `public IP`.                                                            |
| 🌍 Q18  | Application port not reachable — checks?                   |  Security Group <br> NACL <br> Service listening                                            |
| 🔒 Q19  | Developer stored AWS keys on EC2 — problem?                | 👉 Security risk.                                                                             |
| 🔒 Q20  | Better alternative to AWS keys?                            | 👉 IAM Roles.                                                                                 |
| 🔒 Q21  | SSH open to entire internet (`0.0.0.0/0`) — concern?       | 👉 Major security risk.                                                                       |
| ⚖️ Q22  | Load Balancer health check failing — reasons?              |  Wrong port/path <br> App not responding <br> Firewall issues                               |
| ⚖️ Q23  | Users intermittently getting errors — possible issue?      | 👉 Unhealthy EC2 instances behind Load Balancer.                                              |
| 💽 Q24  | How backup EC2 data?                                       | 👉 EBS snapshots.                                                                             |
| 💽 Q25  | EC2 accidentally terminated — recovery possible?           | 👉 Restore from AMI/snapshot backup.                                                          |
| 📊 Q26  | Auto Scaling not launching new instances — checks?         |  Launch Template <br> Limits <br> Health checks                                             |
| 📊 Q27  | Instances terminate repeatedly in ASG — why?               | 👉 Failed health checks.                                                                      |
| 🔑 Q28  | EC2 cannot access S3 bucket — checks?                      | 👉 IAM role permissions.                                                                      |
| 🔑 Q29  | AWS CLI works locally but fails on EC2 — reason?           | 👉 Missing IAM role or credentials.                                                           |
| ☸️ Q30  | EKS worker node NotReady — checks?                         |  EC2 status <br> kubelet <br> IAM permissions <br> Networking                               |
| 📊 Q31  | CPU spikes observed — how monitor?                         | 👉 Amazon CloudWatch alarms.                                                                  |
| 📊 Q32  | No CloudWatch metrics visible — reason?                    | 👉 Monitoring disabled or IAM issue.                                                          |
| 🚀 Q33  | New deployment broke application — action?                 | 👉 Rollback to previous stable version.                                                       |
| 🚀 Q34  | Deployment works in staging but fails in production — why? | 👉 Environment/configuration differences.                                                     |
| ⚡ Q35   | Spot instance suddenly terminated — why?                   | 👉 AWS reclaimed capacity.                                                                    |
| ⚡ Q36   | Best workloads for Spot Instances?                         | 👉 Fault-tolerant/stateless workloads.                                                        |
| 🏗️ Q37 | One Availability Zone fails — how ensure uptime?           | 👉 Multi-AZ deployment.                                                                       |
| 🏗️ Q38 | Single EC2 instance for production — good practice?        | 👉 ❌ No — single point of failure.                                                            |
| 🧪 Q39  | Check listening ports?                                     | 👉 `ss -tulnp`                                                                                |
| 🧪 Q40  | Check running services?                                    | 👉 `systemctl status nginx`                                                                   |
| 🛠️ Q41 | EC2 rebooted automatically — possible reasons?             |  AWS maintenance <br> Crash <br> Auto recovery                                              |
| 💰 Q42  | High billing from EC2 — causes?                            | 👉 Overprovisioned instances <br> Idle resources <br> Data transfer                           |
| 🛡️ Q43 | How secure EC2 in production?                              | 👉 Private subnets <br> IAM roles <br> Minimal SG rules <br> Patch regularly                  |
| 🚀 Q44  | Why use Launch Templates?                                  | 👉 Standardized instance configuration.                                                       |
| 🚀 Q45  | Why use Auto Scaling with Load Balancer?                   | 👉 High availability + scalability.                                                           |
