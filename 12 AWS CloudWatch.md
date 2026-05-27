# 📊 AWS CloudWatch
## 📌 What is AWS CloudWatch?
 * AWS CloudWatch is a **monitoring and observability service** from Amazon Web Services.
 * 👀 “Eyes of AWS” — constantly watching your infrastructure
 * 💡 It helps you:
    * Monitor AWS resources 📡
    * Analyze logs 📜
    * Set alarms 🚨
  
### 🎯 Simple Example :
```hcl
👉 Monitor an EC2 instance:
    CPU usage > 80%
   ⏰ For 5 minutes
   🚨 Trigger alarm → Send notification
```

## 🚀 Key Components
 * 📈 Metrics
   * 👉 Numerical data about performance (`CPU, memory, network`)
   * Automatically collected from services like` EC2`, `RDS`, `Lambda`
 * 📜 Logs
   * Collect and store logs from applications & AWS services
   * Useful for: `Debugging` and `Troubleshooting`
 * 🚨 Alarms
   * Trigger actions when thresholds are crossed
   * e.g., 📩 Send `SNS notification`, ⚙️ Trigger Lambda and 🔄 Auto Scaling etc...
   * Example: CPU > 80% → Send alert
 * 📊 Dashboards
   * Visualize metrics in one place
   * Create custom dashboards: `Graphs`, `Charts`
 * ☸️ Container Insights
   * Monitor `EKS`, `ECS`, Kubernetes workloads
   * Tracks: CPU, Memory and Network
 * ⚡ Events (`EventBridge`)
   * Detect changes and trigger automated actions
   * Example: EC2 instance stopped → `Trigger action`

---

## ⚙️ How CloudWatch Works
1️⃣ Collects data from AWS services (EC2, RDS, Lambda)  
2️⃣ Stores metrics, logs, events  
3️⃣ Evaluates thresholds  
4️⃣ Triggers alarms  
5️⃣ Visualizes data in dashboards  
6️⃣ CloudWatch integrates with: 📩 SNS (notifications), ⚙️ Lambda (automation), 📈 Auto Scaling, 🗄️ RDS, 🖥️ EC2 etc....

## 💰 Pricing
### 🆓 Free Tier
 - 10 custom metrics  
 - 5 GB logs  
 - 3 dashboards  
 - 1M events/month  

### 💵 Paid
| Feature      | Cost                   |
| ------------ | ---------------------- |
| 🆓 Free Tier | 10 metrics, 5GB logs   |
| 📊 Metrics   | $0.30 per metric/month |
| 📜 Logs      | $0.50 per GB           |
| 🚨 Alarms    | $0.10 per alarm/month  |

### ☸️ Container Insights
* Monitors:
  - Clusters
  - Nodes
  - Pods
  - Containers
  - Helps in: `Kubernetes troubleshooting` and `Performance tuning`
* 📊 Tracks:
  - CPU
  - Memory
  - Disk
  - Network

## 🔍 Use Cases
### 🔥 Real Use Cases of DevOps Scenarios:
  - 🚨 Alert if server is down
  - 📊 Monitor application performance
  - 🔄 Auto-scale EC2 instances
  - 🐞 Debug logs in real-time

### Debugging & Troubleshooting
* Logs help:
  - Identify errors ❌  
  - Trace issues 🔍  
  - Improve performance ⚡  

---

## 🛠️ Create CloudWatch Alarm
| 🔢 Step    | 🛠️ Action                           | 📘 Details                                         |
| ---------- | ------------------------------------ | -------------------------------------------------- |
| 🔐 **1️⃣** | ☁️ **Open AWS Console → CloudWatch** | Login to AWS Console and open CloudWatch Dashboard |
| 🚨 **2️⃣** | 📊 **Create Alarm**                  | Click **Alarms → Create Alarm**                    |
| 📈 **3️⃣** | ⚙️ **Choose Metric**                 | Select metric like `CPUUtilization`                |
| 🎯 **4️⃣** | 🔥 **Set Threshold**                 | Example: CPU > `80%` for `5 minutes`               |
| 🔔 **5️⃣** | 📩 **Select Action**                 | Choose action                                      |
|            | 📧                                   | Send SNS notification                              |
|            | 📈                                   | Trigger Auto Scaling                               |
| ✅ **6️⃣**  | 🚀 **Create Alarm**                  | Click **Create Alarm**                             |

## 🔐 Security & Integration
 - Works with IAM roles 👤  
 - Integrates with SNS 📩  
 - Works with Lambda ⚡  
 - Supports Auto Scaling 📈  

---

## ✨ Summary

* AWS CloudWatch is:
  - Real-time monitoring 📡  
  - Intelligent alerting & automation 🚨  
  - Powerful logging 📜  
  - Automation-ready 🤖
  - Integrates with SNS, Lambda, Auto Scaling 🎯
  - Perfect for maintaining healthy and scalable cloud systems 🚀

---

## ⚡ AWS CloudWatch — Rapid Fire Q&A
| #️⃣    | ❓ Question                                            | ✅ Answer                                                       |
| ------ | ----------------------------------------------------- | -------------------------------------------------------------- |
| 1️⃣    | ☁️ What is Amazon CloudWatch?                         | 👉 Monitoring and observability service in Amazon Web Services |
| 2️⃣    | 🎯 Main purpose of CloudWatch?                        | 👉 Monitor AWS resources, applications, and logs               |
| 3️⃣    | 📊 What can CloudWatch monitor?                       | 👉 EC2, RDS, Lambda, EKS, ALB, custom applications             |
| 4️⃣    | 📈 What are CloudWatch Metrics?                       | 👉 `Time-series performance data `                               |
| 5️⃣    | 🖥️ Example EC2 metrics?                              | 👉 CPUUtilization, NetworkIn, DiskReadOps                      |
| 8️⃣    | 🚨 Example alarm use case?                            | 👉 CPU > 80% for 5 minutes                                     |
| 9️⃣    | 📩 What service commonly used with CloudWatch alarms? | 👉 SNS (Simple Notification Service)                           |
| 🔟     | 📜 What are CloudWatch Logs?                          | 👉 Centralized log storage and monitoring                      |
| 1️⃣1️⃣ | 📂 What is a Log Group?                               | 👉 Collection of related log streams                           |
| 1️⃣2️⃣ | 📄 What is a Log Stream?                              | 👉 Sequence of log events from one source                      |
| 1️⃣3️⃣ | 🔍 What is CloudWatch Logs Insights?                  | 👉 Query tool for analyzing logs                               |
| 1️⃣4️⃣ | ⚡ Why use Logs Insights?                              | 👉 Faster troubleshooting and log analysis                     |
| 1️⃣5️⃣ | 📊 What is a CloudWatch Dashboard?                    | 👉 Visual monitoring dashboard for metrics/logs                |
| 1️⃣6️⃣ | 🛠️ Can custom metrics be pushed to CloudWatch?       | 👉 ✅ Yes                                                       |
| 1️⃣8️⃣ | ⏱️ Default EC2 monitoring interval?                   | 👉 5 minutes                                                   |
| 1️⃣9️⃣ | 🔄 What is CloudWatch Events/EventBridge?             | 👉 Event-driven automation service                             |
| 2️⃣0️⃣ | ⚙️ Example EventBridge use case?                      | 👉 Trigger Lambda on EC2 state change                          |
| 2️⃣1️⃣ | 🧪 Can CloudWatch monitor application logs?           | 👉 ✅ Yes                                                       |
| 2️⃣2️⃣ | 📡 How EC2 sends logs to CloudWatch?                  | 👉 CloudWatch Agent                                            |
| 2️⃣3️⃣ | 🔑 IAM requirement for CloudWatch Agent?              | 👉 IAM role with CloudWatch permissions                        |
| 2️⃣4️⃣ | ☸️ Can Kubernetes logs go to CloudWatch?              | 👉 ✅ Yes                                                       |
| 2️⃣5️⃣ | 🚀 Common EKS logging solution?                       | 👉 Fluent Bit / CloudWatch Container Insights                  |
| 2️⃣7️⃣ | 🔔 Alarm states in CloudWatch?                        | 👉 OK, ALARM, INSUFFICIENT_DATA                                |
| 2️⃣8️⃣ | 📤 What actions can alarms trigger?                   | 👉 SNS, Auto Scaling, Lambda                                   |
| 2️⃣9️⃣ | 🔄 What is Auto Scaling integration?                  | 👉 Automatically scale resources from alarms                   |
| 3️⃣0️⃣ | 📜 What is CloudWatch Agent?                          | 👉 Agent collecting OS/app metrics and logs                    |
| 3️⃣1️⃣ | 💾 Can CloudWatch monitor memory usage by default?    | 👉 ❌ No, requires agent                                        |
| 3️⃣2️⃣ | 🖥️ Can disk usage be monitored?                      | 👉 ✅ Using CloudWatch Agent                                    |
| 3️⃣3️⃣ | 🧾 What is metric retention in CloudWatch?            | 👉 Metrics stored for different durations based on granularity |
| 3️⃣4️⃣ | 🔍 What is CloudTrail vs CloudWatch?                  | 👉 CloudTrail = API auditing, CloudWatch = monitoring/logging  |
| 3️⃣5️⃣ | 📦 Can Lambda logs go to CloudWatch?                  | 👉 ✅ Automatically                                             |
| 3️⃣6️⃣ | ⏳ How long are CloudWatch logs stored?                | 👉 Configurable retention period                               |
| 3️⃣7️⃣ | 🔐 How secure CloudWatch logs?                        | 👉 IAM policies + encryption                                   |
| 3️⃣8️⃣ | 📈 What is Container Insights?                        | 👉 Monitoring for containers/EKS/ECS                           |
| 3️⃣9️⃣ | 🛡️ Why monitor CloudWatch alarms?                    | 👉 Detect outages/performance issues early                     |
| 4️⃣0️⃣ | ⚠️ EC2 CPU suddenly high — what to check?             | 👉 CloudWatch metrics and processes                            |
| 4️⃣1️⃣ | 🐢 Application slow but EC2 healthy — next step?      | 👉 Check application logs in CloudWatch                        |

