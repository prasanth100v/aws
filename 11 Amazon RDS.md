# 🗄️ Amazon RDS 
## 📌 What is Amazon RDS?
Amazon RDS (Relational Database Service) is a **managed database service** by AWS.

- ❌ No manual patching, ❌ No hardware management
- ✅ Fully managed database

💡 It helps you:
- Set up databases easily
- Automate backups & patching
- Scale resources effortlessly

### 🧩 RDS supports popular engines:

- 🐬 MySQL
- 🐘 PostgreSQL
- 🟠 MariaDB
- 🏢 Oracle
- 🪟 SQL Server

## 🚀 Key Features
### 🔄 Automated Management
  - Automatic provisioning
  - OS & DB patching
  - Maintenance handled by AWS

### 💾 Backups & Snapshots
  - ✅ Automated backups (default 7 days, max 35 days)
  - 📸 Manual snapshots (never expire)
  - 🔁 Point-in-Time Recovery

### 🌍 High Availability
- Multi-AZ deployment for failover
- Synchronous replication, Used for availability (NOT performance)

### 📊 Read Replicas
- Improves performance (NOT failover)
- Up to 5 read replicas
- Asynchronous replication
- Best for **read-heavy workloads**

- 🔒 Sync = Safety first (no data loss)        (Tasks are executed one after another. The next task waits until the current task finishes.)
- 🚀 Async = Speed first (better performance)  (Tasks can run independently, without waiting for others to finish.)

### 📈 Scaling
 - 🔼 Vertical scaling (instance type change)
 - 🔼 Storage scaling (increase anytime)
 - ❌ Cannot reduce storage after increasing

⚠️ Scaling instance → requires reboot (downtime)

### 🔐 Security
 - 🔒 Runs inside VPC
 - 🔐 Controlled by Security Groups (firewall)
 - 🔑 Encryption using AWS KMS
 - 🔐 SSL/TLS connections
  - 👤 IAM authentication

## 🔍 RDS Endpoint (Connection)
- 🚫 No ssh, no terminal access ❌, You don’t see the OS (Linux/Windows) running underneath, You only connect via DB clients..
- 📌 Why? Because RDS is a managed service — AWS controls the server, OS, patching, security, everything.

To connect your app:
```
Endpoint (hostname) + Username + Password + Port (e.g., 3306 for MySQL)
```
You connect using tools like: **MySQL Workbench, pgAdmin**

### 🔌 Default Ports
| Database   | Port |
| ---------- | ---- |
| MySQL      | 3306 |
| PostgreSQL | 5432 |

### Simple Analogy
 - 🖥️ EC2 → Like renting a full computer (you can SSH and control everything)
 - 🗄️ RDS → Like using a database service (you only use it, not manage the machine)

---

## ⚙️ Important Concepts
### 🔁 Multi-AZ vs Read Replica
| Feature      | Multi-AZ     | Read Replica |
| ------------ | ------------ | ------------ |
| Purpose      | Availability | Performance  |
| Replication  | Synchronous  | Asynchronous |
| Failover     | ✅ Yes        | ❌ No         |
| Read Scaling | ❌ No         | ✅ Yes        |
| Use Case     | High Availability | Read scaling |

👉 RDS supports up to **5 Read Replicas**

### 📡 Monitoring
Use **CloudWatch** to monitor:
- CPU usage
- Memory
- DB Connections
- IOPS

### 🔐 Security Best Practices
- Use IAM roles 👤
- Configure Security Groups 🔥
- Enable encryption 🔒
- Use SSL/TLS connections 🌐

### 💾 Storage Types
| Type                      | Use Case                    |
| ------------------------- | --------------------------- |
| 🟢 General Purpose (SSD)  | Balanced Cost-effective & performance |
| 🔴 Provisioned IOPS (SSD) | High performance workloads  |

## 📊 Scaling 
#### 📈 Increase Storage (Scale Up)
- 👉 You can increase storage anytime, No major downtime in most cases ✅
- AWS handles it automatically and Your database keeps running smoothly

#### 📌 Example:
   100 GB → 200 GB ✔️ (allowed)

#### 📉 Decrease Storage (Scale Down)
- 👉 You cannot reduce storage directly, AWS does not allow shrinking ❌
- To reduce size, you must: Create a new smaller DB and Migrate data (dump/restore or snapshot)

##### 📌 Example:
  200 GB → 100 GB ❌ (not allowed directly)
  
  #### ⚠️ Downtime Possibility
  Some scaling operations may cause: 🔄 Reboot and ⏳ Short downtime

👉 Especially if: Changing storage type (gp2 → gp3) (Major modifications)

### ⏳ Backup Retention (“How long your backups are stored before they are deleted.”)
  If backup retention = 7 days
   - AWS keeps backups for the last 7 days
   - You can restore the database to any point within those 7 days

 - Default: 7 days
 - Max: 35 days

### ⏸️ Instance Stop Feature
- You can stop RDS temporarily
- ⏳ Automatically starts after **7 days**

### 🧱 Storage Limits
- Max storage: **64 TB**

### 🔄 Migration
Use **AWS DMS (Database Migration Service)** to migrate databases.

### 💰 Pricing Factors
- Database engine
- Instance type
- Storage type
- Data transfer
- Multi-AZ / IOPS usage

---

## 🛠️ Steps to Create RDS

1️⃣ Go to AWS Console → RDS  
2️⃣ Click **Create Database**  
3️⃣ Choose Engine (MySQL/PostgreSQL/etc.)  
4️⃣ Set DB name, username, password  
5️⃣ Select instance type (e.g., db.t3.micro)  
6️⃣ Configure storage  (Choose size & Enable autoscaling)
7️⃣ Set VPC & security group  
8️⃣ Enable backups & monitoring  (Set retention period)
9️⃣ Click Create (⏳ Takes ~5–10 minutes)  
🔟 🔌 Connect to RDS

Use tools like:
- MySQL Workbench
- pgAdmin

Provide:
- Endpoint
- Username & Password
- Port (3306 / 5432)

---

## ✨ Summary

Amazon RDS is:
- Fully managed relational database
- Scalable 📈
- Secure 🔐
- Highly available 🌍

Perfect for modern cloud applications 🚀
