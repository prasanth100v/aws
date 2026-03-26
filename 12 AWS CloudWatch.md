# 📊 AWS CloudWatch
## 📌 What is AWS CloudWatch?
AWS CloudWatch is a **monitoring and observability service** from Amazon Web Services.
  
  👀 “Eyes of AWS” — constantly watching your infrastructure

💡 It helps you:
- Monitor AWS resources 📡
- Analyze logs 📜
- Set alarms 🚨
- Automate responses 🤖

🎯 Simple Example :
```
👉 Monitor an EC2 instance:
    CPU usage > 80%
   ⏰ For 5 minutes
   🚨 Trigger alarm → Send notification
```

## 🚀 Key Components
### 📈 Metrics
- 👉 Numerical data about performance (CPU, memory, network)
- Automatically collected from services like EC2, RDS, Lambda

### 📜 Logs
- Collect and store logs from applications & AWS services
- Useful for: Debugging and Troubleshooting

### 🚨 Alarms
- Trigger actions when thresholds are crossed
-  (e.g., 📩 Send SNS notification, ⚙️ Trigger Lambda and 🔄 Auto Scaling etc...)
-  Example: CPU > 80% → Send alert
   
### 📊 Dashboards
- Visualize metrics in one place
- Create custom dashboards: Graphs, Charts

### ☸️ Container Insights
- Monitor EKS, ECS, Kubernetes workloads
- Tracks: CPU, Memory and Network

### ⚡ Events (EventBridge)
- Detect changes and trigger automated actions
- Example: EC2 instance stopped → Trigger action

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
Monitors:
- Clusters
- Nodes
- Pods
- Containers
- Helps in: Kubernetes troubleshooting and Performance tuning

📊 Tracks:
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
Logs help:
- Identify errors ❌  
- Trace issues 🔍  
- Improve performance ⚡  

---

## 🛠️ Create CloudWatch Alarm

1️⃣ Go to AWS Console → CloudWatch  
2️⃣ Click **Alarms → Create Alarm**  
3️⃣ Choose metric (e.g., CPUUtilization)  
4️⃣ Set threshold (CPU > 80% for 5 minutes)  
5️⃣ Select action (Send SNS notification / Trigger Auto Scaling)  
6️⃣ Click **Create Alarm**  

## 🔐 Security & Integration
- Works with IAM roles 👤  
- Integrates with SNS 📩  
- Works with Lambda ⚡  
- Supports Auto Scaling 📈  

---

## ✨ Summary

AWS CloudWatch is:
- Real-time monitoring 📡  
- Intelligent alerting & automation 🚨  
- Powerful logging 📜  
- Automation-ready 🤖
- Integrates with SNS, Lambda, Auto Scaling 🎯

Perfect for maintaining healthy and scalable cloud systems 🚀
