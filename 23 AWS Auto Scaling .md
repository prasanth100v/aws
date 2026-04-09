# ⚙️ AWS Auto Scaling
## 🚀 What is Auto Scaling?

 * ✨ AWS Auto Scaling helps automatically adjust the number of EC2 instances based on traffic demand.
 * It uses `Auto Scaling Groups`, `launch templates`, and `scaling policies` to maintain performance and availability while optimizing cost.
 * It ensures your application runs efficiently by `scaling out` (adding instances) during `high traffic` and `scaling in` (removing instances) during `low traffic`.
 * Ensures `high availability` and `fault tolerance`.
 * 🔗 AWS Auto Scaling can integrate with `Elastic Load Balancing` (ELB) to distribute incoming traffic across instances in the Auto Scaling Group.
 * When new instances are added, they are automatically registered with the `load balancer`, and when instances are terminated, they are `deregistered`.
 * Simple Understanding : `High Traffic 📈 → Add Instances (Scale Out), Low Traffic 📉 → Remove Instances (Scale In)`
 * 🎯 Auto Scaling benefits :
     * ⚡ Handle traffic spikes automatically
     * 💰 Save `cost` during low usage
     * 🛡️ Improve availability & fault tolerance

---

## 🧩 Key Components:

- 📦 Auto Scaling Group (ASG) – A `group of EC2 instances` managed together.  
- 📄 Launch Template / Configuration – Defines the `instance type`, `AMI`, and other settings.  
- 📊 Scaling Policies – Rules that determine when to scale (e.g., `CPU usage > 70%`).  
- 💚 Health Checks – Ensures only healthy instances remain active.  
- ⚖️ Load Balancer (optional) – Distributes traffic among instances.  

---

## 🚀 Create Auto Scaling group
| 🎯 Step | 🧩 Section          | 📌 Action           | 💡 Details                                                     |
| ------- | ------------------- | --------------------- | ---------------------------------------------------------------- |
| 1️⃣     | 🌐 AWS Console      | Open EC2 Dashboard    | 🔍 AWS → EC2 → Auto Scaling Groups                             |
| 2️⃣     | 📄 Launch Template  | Create Launch Template| 🖥️ Define `AMI`, `instance type`, `key pair`, `security group`  |
| 3️⃣     | ⚙️ Template Config  | Add Instance Details  | 💾 Storage, 🔐 IAM role, 🧾 user data (optional)               |
| 4️⃣     | 📈 Create ASG       | Start Creation        | 🚀 Click **Create Auto Scaling Group**                          |
| 5️⃣     | 📌 Choose Template  | Select Template       | 📄 Use created launch template                                  |
| 6️⃣     | 🌐 Network Settings | Select VPC & Subnets  | 📍 Choose VPC + at least 2 AZs                                  |
| 7️⃣     | ⚖️ Load Balancer    | Attach (Optional)     | 🔗 Add ALB/NLB target group                                     |
| 8️⃣     | 📊 Group Size       | Set Capacity          | 🔢 Set Minimum, Desired=2, and Maximum (4) instances.         |
| 9️⃣     | 🔄 Scaling Policies | Add Rules             | 🎯 CPU target (e.g., 50%), step/scheduled scaling           |
| 🔟      | ❤️ Health Checks   | Configure             | 🔍 EC2 or ELB health checks to replace unhealthy instances  |
| 1️⃣1️⃣  | 🔔 Notifications    | Add Alerts (Optional) | 📩 SNS alerts for scaling events                            |
| 1️⃣2️⃣  | 🔍 Review           | Verify Config         | 👀 Check all settings                                       |
| 1️⃣3️⃣  | 🚀 Create           | Launch ASG            | ⚡ Click Create Auto Scaling Group                           |

#### 👉 ASG = Auto scale 📈 + High availability 🛡️ + Cost optimization 💰


---

# 🚢 AWS OpenShift ROSA (Red Hat OpenShift Service on AWS)

 * AWS OpenShift (`ROSA`) stands for `Red Hat OpenShift Service` on AWS.
 * It’s a fully managed OpenShift (`Kubernetes-based`) service and 🤝 Joint Enterprise Support from `Red Hat` and `AWS`.  
 * ☁️ ROSA helps you to run OpenShift clusters directly on AWS without managing the infrastructure.  

## 💰 Pricing:

- 💡 EKS: You pay for EC2 + EKS control plane ($0.10/hour per cluster)  
- 💸 ROSA: Slightly more expensive — includes OpenShift licensing & support  

### ⚖️ Amazon EKS vs Red Hat OpenShift on AWS
| 🧩 Feature           | ☸️ Amazon EKS                     | 🟥 Red Hat OpenShift on AWS           |
| -------------------- | --------------------------------- | ------------------------------------- |
| 📛 Full Name         | Amazon Elastic Kubernetes Service | Red Hat OpenShift Service on AWS      |
| 🧠 Kubernetes Type   | 🌐 Upstream Kubernetes            | 🧩 OpenShift (K8s + Red Hat platform) |
| ⚙️ Management Level  | AWS manages control plane         | AWS + Red Hat manage platform         |
| 😊 Ease of Use       | ⚖️ Moderate (manual setup needed) | ✅ Easier (more automated)             |
| 🛠️ CLI Tools        | `kubectl`, `eksctl`, AWS CLI       | `oc` (OpenShift CLI), `kubectl`        |
| 🖥️ UI (Console)     | 📊 Basic dashboard                | 🎨 Rich OpenShift web console         |
| 🔄 Built-in CI/CD    | ❌ Not included                  | ✅ OpenShift Pipelines                 |
| 🌐 Networking        | AWS VPC CNI                       | OpenShift SDN / OVN-Kubernetes        |
| 🔐 Security          | IAM, Security Groups, IRSA        | 🛡️ Advanced (RBAC + SCC + integrated policies)  |
| 📦 Image Registry    | External (ECR)                    | ✅ Built-in image registry                     |
| 📊 Monitoring & Logs | CloudWatch (manual setup)         | 📈 Built-in monitoring stack                  |
| 🔄 Upgrades          | ⚠️ Manual / semi-automated        | ✅ Automated & managed                       |
| 💰 Cost              | 💲 Lower (pay for infra + control plane fee)  | 💸 Higher (includes license)       |
| 🧑‍💼 Vendor Support    | AWS Support                        | AWS + Red Hat support                           |
| 🎛️ Customization     | 🔓 High flexibility               | ⚠️ Opinionated (less flexible, guided approach)  |


---

# 🔍 AWS CloudTrail

 * ✨ AWS CloudTrail is a service that `logs` and `monitors API activity` in your AWS account.
 * ✨ It helps track `user actions`, detect `security issues`, and `audit compliance`.
 * ✨ Simple Understanding `CloudTrail = Who did WHAT, WHEN, and WHERE`

## ⭐ Key Features:

1. 📜 Event Logging – Records `API calls` and `actions taken` in AWS.  
2. 📦 S3 Integration – Stores `logs` securely in Amazon S3.  
3. 📊 CloudWatch Integration – Enables real-time `monitoring` and `alerts`.  
4. 🌍 Multi-Region Support – Captures activities across `multiple AWS regions`.  
5. 🕒 Event History – Provides `past event logs` for analysis.  

## 🎯 Use Cases:

- 🔐 Security Auditing – Detects unauthorized access.  
- 📋 Compliance Monitoring – Ensures compliance with industry regulations.  
- 🛠️ Troubleshooting – Helps diagnose operational issues.  
- 👤 User Activity Tracking – Monitors actions taken by AWS users.  

### 📜 AWS CloudTrail Setup (Step-by-Step)
| 🎯 Step | 🧩 Section           | 📌 Action        | 💡 Details                                           |
| ------- | --------------------- | ---------------- | ----------------------------------------------------- |
| 1️⃣     | 🌐 AWS Console        | Open CloudTrail  | 🔍 AWS → Search **CloudTrail**                       |
| 2️⃣     | ➕ Create Trail       | Start Creation   | 🚀 Click **Create trail**                             |
| 3️⃣     | 🏷️ Trail Name        | Enter Name        | 📝 Example: `my-cloudtrail`                           |
| 4️⃣     | 🌍 Scope             | Choose Regions    | 🌐 All regions (recommended) or single region       |
| 5️⃣     | 📦 Storage (S3)      | Configure Bucket  | 🗂️ Create/select S3 bucket for logs                 |
| 6️⃣     | 🔍 Log Validation    | Enable Validation | 🛡️ Ensures logs are not tampered                     |
| 7️⃣     | 🔐 Encryption        | Configure         | 🔑 SSE-S3 (default) or SSE-KMS for advanced security |
| 8️⃣     | 📊 Management Events | Enable Logging    | 🔍 Track API calls (Read/Write)                      |
| 9️⃣     | 📂 Data Events       | Optional          | 📦 Track S3 object / Lambda activity                 |
| 🔟      | 🧠 Insights         | Optional          | 🚨 Detect unusual API activity                       |
| 1️⃣1️⃣  | 🔍 Review            | Verify Settings    | 👀 Check all configuration                           |
| 1️⃣2️⃣  | 🚀 Create Trail      | Launch CloudTrail  | ⚡ Click **Create trail**                            |

