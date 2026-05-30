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

---

## ⚡ AWS Auto Scaling — Rapid Fire Interview Q&A
| #️⃣    | ❓ Interview Question                                           | ✅ Answer                                                                                                           |
| ------ | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| 1️⃣    | 🚀 What is AWS Auto Scaling?                                   | 📈 AWS service that automatically adds or removes resources based on demand.                                       |
| 2️⃣    | 🎯 Why use Auto Scaling?                                       | 🚀 High Availability, Scalability, Performance, Cost Optimization.                                                 |
| 3️⃣    | 🖥️ Which AWS service is most commonly used with Auto Scaling? | 💻 EC2                                                                                                             |
| 4️⃣    | 🏗️ What is an Auto Scaling Group (ASG)?                       | 👥 Logical group of EC2 instances managed automatically.                                                           |
| 5️⃣    | 🔄 Main purpose of ASG?                                        | 🎯 Maintain desired number of healthy instances.                                                                   |
| 6️⃣    | 📊 What metrics can trigger scaling?                           | 💻 CPU, 🧠 Memory (custom), 🌐 Network, 📈 CloudWatch Metrics                                                      |
| 7️⃣    | 🌟 Key benefits of Auto Scaling?                               | 🚀 Scalability, 💰 Cost Savings, 🛡️ Fault Tolerance                                                               |
| 8️⃣    | 🔢 What is Desired Capacity?                                   | 🎯 Number of instances ASG tries to maintain.                                                                      |
| 9️⃣    | ⬇️ What is Minimum Capacity?                                   | 📉 Minimum number of running instances.                                                                            |
| 🔟     | ⬆️ What is Maximum Capacity?                                   | 📈 Maximum number of instances allowed.                                                                            |
| 1️⃣1️⃣ | 🔧 What is a Launch Template?                                  | 📋 Blueprint defining EC2 configuration.                                                                           |
| 1️⃣2️⃣ | 📦 What does a Launch Template contain?                        | 🖼️ AMI, 💻 Instance Type, 🔑 Key Pair, 🛡️ Security Group, 🎭 IAM Role                                            |
| 1️⃣3️⃣ | 🚀 Can ASG work without a Launch Template?                     | ❌ No (Launch Template or Launch Configuration required).                                                           |
| 1️⃣4️⃣ | 📜 What is Launch Configuration?                               | 🏛️ Legacy method for EC2 launch settings.                                                                         |
| 1️⃣5️⃣ | ✅ Recommended today?                                           | 🚀 Launch Template                                                                                                 |
| 1️⃣6️⃣ | 📈 What is Scale-Out?                                          | ➕ Adding instances when demand increases.                                                                          |
| 1️⃣7️⃣ | 📉 What is Scale-In?                                           | ➖ Removing instances when demand decreases.                                                                        |
| 1️⃣8️⃣ | 🔥 Example Scale-Out Policy?                                   | CPU > 70% ➜ Add 2 instances                                                                                        |
| 1️⃣9️⃣ | ❄️ Example Scale-In Policy?                                    | CPU < 30% ➜ Remove 1 instance                                                                                      |
| 2️⃣0️⃣ | 📡 Which service monitors scaling metrics?                     | 📊 Amazon CloudWatch                                                                                               |
| 2️⃣1️⃣ | 🎯 What is Target Tracking Scaling?                            | 📈 Keeps metric near target value automatically.                                                                   |
| 2️⃣2️⃣ | 📌 Example Target Tracking?                                    | CPU utilization = 50%                                                                                              |
| 2️⃣3️⃣ | ⚡ What is Simple Scaling?                                      | 📉 Scale based on a single CloudWatch alarm.                                                                       |
| 2️⃣4️⃣ | 🚀 What is Step Scaling?                                       | 📊 Different scaling actions based on threshold ranges.                                                            |
| 2️⃣5️⃣ | ⏰ What is Scheduled Scaling?                                   | 📅 Scale at predefined times.                                                                                      |
| 2️⃣6️⃣ | 🎄 Scheduled Scaling use case?                                 | 🛍️ Black Friday traffic spike                                                                                     |
| 2️⃣7️⃣ | ❤️ What is an EC2 Health Check?                                | 🔍 Verifies EC2 instance health.                                                                                   |
| 2️⃣8️⃣ | ⚖️ What is ELB Health Check?                                   | 🌐 Verifies application health through Load Balancer.                                                              |
| 2️⃣9️⃣ | 🚨 What happens if instance becomes unhealthy?                 | 🔄 ASG terminates and replaces it.                                                                                 |
| 3️⃣0️⃣ | 🛡️ What is Self-Healing?                                      | 🤖 Automatic replacement of failed instances.                                                                      |
| 3️⃣1️⃣ | 🌍 Can ASG span multiple AZs?                                  | ✅ Yes                                                                                                              |
| 3️⃣2️⃣ | 🎯 Why use multiple AZs?                                       | 🛡️ High Availability                                                                                              |
| 3️⃣3️⃣ | ⚖️ Which AWS service is commonly paired with ASG?              | 🌐 Application Load Balancer (ALB)                                                                                 |
| 3️⃣4️⃣ | 🔗 Why integrate ALB with ASG?                                 | 🚀 Distribute traffic across instances.                                                                            |
| 3️⃣5️⃣ | 🆕 New instance launched by ASG. What happens?                 | 🎯 Automatically registered with Target Group.                                                                     |
| 3️⃣6️⃣ | 🗑️ Instance terminated by ASG. What happens?                  | ❌ Automatically deregistered from Target Group.                                                                    |
| 3️⃣7️⃣ | 💰 How does Auto Scaling reduce cost?                          | 📉 Removes unused instances during low traffic.                                                                    |
| 3️⃣8️⃣ | ⚡ What is Instance Refresh?                                    | 🔄 Gradually replace EC2 instances with updated configuration.                                                     |
| 3️⃣9️⃣ | 🎯 Why use Instance Refresh?                                   | 🚀 Rolling updates with minimal downtime.                                                                          |
| 4️⃣0️⃣ | 📦 What is Warm Pool?                                          | 🔥 Pre-initialized EC2 instances ready for fast scaling.                                                           |
| 4️⃣1️⃣ | 🚀 Benefit of Warm Pool?                                       | ⚡ Faster scale-out events.                                                                                         |
| 4️⃣2️⃣ | 🛡️ What is Scale-In Protection?                               | 🔒 Prevents selected instances from termination.                                                                   |
| 4️⃣3️⃣ | 🎯 Use case for Scale-In Protection?                           | 🗄️ Long-running critical workloads.                                                                               |
| 4️⃣4️⃣ | 🌐 What is Predictive Scaling?                                 | 🤖 Uses ML to forecast traffic and scale proactively.                                                              |
| 4️⃣5️⃣ | 🎄 Predictive Scaling use case?                                | 🛒 E-commerce seasonal traffic.                                                                                    |
| 4️⃣6️⃣ | 🔄 What happens if an AZ fails?                                | 🚀 ASG launches instances in healthy AZs.                                                                          |
| 4️⃣7️⃣ | 📉 ASG not scaling out. What to check?                         | 🔍 CloudWatch alarms, scaling policies, limits.                                                                    |
| 4️⃣8️⃣ | 🚨 Instances terminating repeatedly. Why?                      | ❤️ Failed health checks.                                                                                           |
| 4️⃣9️⃣ | 🌍 Website slow during traffic spike. Solution?                | 📈 Auto Scaling + ALB                                                                                              |
| 5️⃣0️⃣ | 📊 How monitor Auto Scaling activities?                        | 📈 CloudWatch + ASG Activity History                                                                               |
| 5️⃣1️⃣ | 💻 CLI command to list ASGs?                                   | `aws autoscaling describe-auto-scaling-groups`                                                                     |
| 5️⃣2️⃣ | 🔍 CLI command to view scaling activities?                     | `aws autoscaling describe-scaling-activities`                                                                      |
| 5️⃣3️⃣ | 🐳 Can ECS use Auto Scaling?                                   | ✅ Yes                                                                                                              |
| 5️⃣4️⃣ | ☸️ Can EKS use Auto Scaling?                                   | ✅ Yes (Cluster Autoscaler/Karpenter)                                                                               |
| 5️⃣5️⃣ | 🛒 E-commerce traffic suddenly increases. Solution?            | 🚀 Dynamic Scaling                                                                                                 |
| 5️⃣6️⃣ | 🌙 Traffic drops overnight. Solution?                          | 📉 Scale-In                                                                                                        |
| 5️⃣7️⃣ | 🚨 Single EC2 instance for production. Good practice?          | ❌ No, single point of failure.                                                                                     |
| 5️⃣8️⃣ | 🏆 Best production architecture?                               | 🌍 Route 53 → ALB → ASG → EC2 → RDS                                                                                |
| 5️⃣9️⃣ | 💡 Most common Auto Scaling metric?                            | 💻 CPU Utilization                                                                                                 |
| 6️⃣0️⃣ | 🔥 Most common production issue?                               | 🚨 Misconfigured health checks                                                                                     |
| 6️⃣1️⃣ | 🎯 Interview Gold: Auto Scaling in one line?                   | 🚀 Automatically adjusts resources to match application demand while maintaining availability and optimizing cost. |
| 6️⃣2️⃣ | 🎯 Interview Gold: Why Auto Scaling with ALB?                  | ⚖️ ALB distributes traffic, while ASG ensures enough healthy instances are available.                              |
| 6️⃣3️⃣ | 🎯 Interview Gold: Main advantages?                            | 🚀 Scalability + 🛡️ High Availability + 💰 Cost Optimization + 🤖 Self-Healing                                    |
| 6️⃣4️⃣ | 🎯 Interview Gold: Real-world setup?                           | 🌍 Route 53 → ALB → Auto Scaling Group → EC2 → RDS + CloudWatch Monitoring                                         |

---

## ⚡ AWS CloudTrail — Rapid Fire Interview Q&A 
| #️⃣    | ❓ Interview Question                                        | ✅ Answer                                                                                                                |
| ------ | ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 1️⃣    | 🔍 What is AWS CloudTrail?                                  | 📜 AWS service that records and tracks API activity and account actions across AWS.                                     |
| 2️⃣    | 🎯 Main purpose of CloudTrail?                              | 🛡️ Auditing, Governance, Compliance, and Security Monitoring.                                                          |
| 3️⃣    | 🌍 Is CloudTrail a Regional or Global service?              | 🌎 Service operates across AWS Regions and can capture global service events.                                           |
| 4️⃣    | 👤 What activities does CloudTrail record?                  | 🔑 User actions, API calls, Console logins, SDK and CLI operations.                                                     |
| 5️⃣    | 📋 What is a CloudTrail Event?                              | 📝 A record of an AWS API activity.                                                                                     |
| 6️⃣    | 🚀 Why is CloudTrail important?                             | 🔍 Helps track who did what, when, and from where.                                                                      |
| 7️⃣    | 📦 Where are CloudTrail logs stored?                        | 🪣 Amazon S3 Bucket.                                                                                                    |
| 8️⃣    | 🔄 Does CloudTrail log API calls automatically?             | ✅ Yes                                                                                                                   |
| 9️⃣    | 🏢 What is a Trail?                                         | 📜 Configuration that delivers events to S3 and other destinations.                                                     |
| 🔟     | 🌎 What is a Multi-Region Trail?                            | 📡 Captures events from all AWS Regions.                                                                                |
| 1️⃣1️⃣ | 📍 What is a Single-Region Trail?                           | 🗺️ Captures events from one Region only.                                                                               |
| 1️⃣2️⃣ | 👨‍💻 Does CloudTrail record Console actions?               | ✅ Yes                                                                                                                   |
| 1️⃣3️⃣ | 💻 Does CloudTrail record AWS CLI actions?                  | ✅ Yes                                                                                                                   |
| 1️⃣4️⃣ | 🔗 Does CloudTrail record SDK actions?                      | ✅ Yes                                                                                                                   |
| 1️⃣5️⃣ | 🔐 Can CloudTrail track IAM changes?                        | ✅ Yes                                                                                                                   |
| 1️⃣6️⃣ | 🗑️ Can CloudTrail track resource deletions?                | ✅ Yes                                                                                                                   |
| 1️⃣7️⃣ | 📊 What are Management Events?                              | ⚙️ Events related to AWS resource management operations.                                                                |
| 1️⃣8️⃣ | 🪣 Example of Management Event?                             | 👤 Creating IAM user, launching EC2 instance.                                                                           |
| 1️⃣9️⃣ | 📂 What are Data Events?                                    | 📁 Events related to resource-level operations.                                                                         |
| 2️⃣0️⃣ | 📦 Example of Data Event?                                   | 🪣 S3 GetObject, PutObject operations.                                                                                  |
| 2️⃣1️⃣ | ⚡ What are Insights Events?                                 | 🔎 Detect unusual API activity patterns.                                                                                |
| 2️⃣2️⃣ | 🚨 Example CloudTrail Insight?                              | 📈 Sudden spike in EC2 API calls.                                                                                       |
| 2️⃣3️⃣ | 🔑 Does CloudTrail record failed API calls?                 | ✅ Yes                                                                                                                   |
| 2️⃣4️⃣ | 🌐 Can CloudTrail track login attempts?                     | ✅ Yes                                                                                                                   |
| 2️⃣5️⃣ | ❌ Failed Console Login visible in CloudTrail?               | ✅ Yes                                                                                                                   |
| 2️⃣6️⃣ | 🛡️ Which AWS service commonly analyzes CloudTrail logs?    | 🔍 Amazon GuardDuty                                                                                                     |
| 2️⃣7️⃣ | 📊 Can CloudTrail integrate with CloudWatch?                | ✅ Yes                                                                                                                   |
| 2️⃣8️⃣ | 🔔 Why integrate CloudTrail with CloudWatch?                | 🚨 Create alerts on specific events.                                                                                    |
| 2️⃣9️⃣ | 📧 Example alert use case?                                  | 🔑 Root account login notification.                                                                                     |
| 3️⃣0️⃣ | 🪣 Can CloudTrail logs be encrypted?                        | ✅ Yes using AWS KMS                                                                                                     |
| 3️⃣1️⃣ | 🔐 Recommended encryption method?                           | 🔑 SSE-KMS                                                                                                              |
| 3️⃣2️⃣ | 📜 Can CloudTrail validate log integrity?                   | ✅ Yes                                                                                                                   |
| 3️⃣3️⃣ | 🛡️ Why enable Log File Validation?                         | 🔍 Detect log tampering.                                                                                                |
| 3️⃣4️⃣ | ⏳ Default CloudTrail Event History retention?               | 📅 90 days                                                                                                              |
| 3️⃣5️⃣ | 🗄️ How retain logs longer than 90 days?                    | 🪣 Store logs in S3.                                                                                                    |
| 3️⃣6️⃣ | 🌍 Which global service events are logged?                  | 👤 IAM, Route 53, CloudFront, STS                                                                                       |
| 3️⃣7️⃣ | 👑 Can CloudTrail monitor Root Account activity?            | ✅ Yes                                                                                                                   |
| 3️⃣8️⃣ | 🚨 Why monitor Root Account usage?                          | 🔒 Security best practice.                                                                                              |
| 3️⃣9️⃣ | 🏢 Can CloudTrail work across AWS Organizations?            | ✅ Yes                                                                                                                   |
| 4️⃣0️⃣ | 📋 What is Organization Trail?                              | 🌎 Trail applied across all AWS accounts in an Organization.                                                            |
| 4️⃣1️⃣ | 🔍 Need to know who deleted an EC2 instance. Which service? | 📜 CloudTrail                                                                                                           |
| 4️⃣2️⃣ | 🪣 Need to know who deleted an S3 bucket. Which service?    | 📜 CloudTrail                                                                                                           |
| 4️⃣3️⃣ | 🔑 Need to know who changed IAM policy. Which service?      | 📜 CloudTrail                                                                                                           |
| 4️⃣4️⃣ | 🚀 EC2 instance terminated unexpectedly. How investigate?   | 🔍 Search CloudTrail events.                                                                                            |
| 4️⃣5️⃣ | 🔒 Unauthorized API calls detected. What should you check?  | 📜 CloudTrail logs.                                                                                                     |
| 4️⃣6️⃣ | 📡 Which service can query CloudTrail logs in S3?           | 🔎 Amazon Athena                                                                                                        |
| 4️⃣7️⃣ | 📈 Can CloudTrail logs be visualized?                       | ✅ Using CloudWatch, Athena, QuickSight.                                                                                 |
| 4️⃣8️⃣ | 🛡️ Compliance frameworks commonly requiring CloudTrail?    | 📋 PCI-DSS, HIPAA, SOC2, ISO 27001                                                                                      |
| 4️⃣9️⃣ | 🔄 Can CloudTrail capture cross-account role assumptions?   | ✅ Yes                                                                                                                   |
| 5️⃣0️⃣ | 🔑 What API is logged during role assumption?               | `sts:AssumeRole`                                                                                                        |
| 5️⃣1️⃣ | ☸️ Can CloudTrail audit EKS activities?                     | ✅ Yes                                                                                                                   |
| 5️⃣2️⃣ | 🐳 Can CloudTrail audit ECS activities?                     | ✅ Yes                                                                                                                   |
| 5️⃣3️⃣ | 🏗️ Can CloudTrail audit Terraform changes?                 | ✅ Yes, through AWS API calls.                                                                                           |
| 5️⃣4️⃣ | 📜 CLI command to describe trails?                          | `aws cloudtrail describe-trails`                                                                                        |
| 5️⃣5️⃣ | 🔍 CLI command to lookup events?                            | `aws cloudtrail lookup-events`                                                                                          |
| 5️⃣6️⃣ | 🚨 Most common CloudTrail use case?                         | 🔍 Security auditing and troubleshooting.                                                                               |
| 5️⃣7️⃣ | ⚠️ Most common production investigation?                    | 👤 "Who deleted or modified this resource?"                                                                             |
| 5️⃣8️⃣ | 🏆 Best practice for CloudTrail?                            | 🌎 Enable Multi-Region Trail and log to encrypted S3 bucket.                                                            |
| 5️⃣9️⃣ | 🏆 Best security setup?                                     | 🔒 CloudTrail + KMS + CloudWatch Alarms + GuardDuty                                                                     |
| 6️⃣0️⃣ | 🎯 Interview Gold: CloudTrail in one line?                  | 📜 AWS CloudTrail records all AWS API activity, enabling auditing, monitoring, compliance, and security investigations. |
| 6️⃣1️⃣ | 🎯 Interview Gold: CloudTrail vs CloudWatch?                | 📜 CloudTrail = Who did what; 📊 CloudWatch = Resource performance and monitoring.                                      |
| 6️⃣2️⃣ | 🎯 Interview Gold: Real-world use case?                     | 🔍 Investigating security incidents, tracking changes, and maintaining compliance.                                      |
| 6️⃣3️⃣ | 🎯 Interview Gold: Most important feature?                  | 🛡️ Complete audit trail of AWS account activities.                                                                     |
| 6️⃣4️⃣ | 🎯 Interview Gold: Production architecture?                 | 👤 User/API → AWS Service → 📜 CloudTrail → 🪣 S3 → 🔎 Athena / 📊 CloudWatch / 🛡️ GuardDuty                           |
