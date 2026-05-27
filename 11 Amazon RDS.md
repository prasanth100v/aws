# 🗄️ Amazon RDS 
## 📌 What is Amazon RDS?
 * Amazon RDS (`Relational Database Service`) is a **managed database service** by AWS.
 * ❌ No manual patching, ❌ No hardware management
 * ✅ Fully managed database
 * 💡 It helps you:
     * Set up databases easily
     * Automate `backups` & `patching`
     * Scale resources effortlessly

### 🧩 RDS supports popular engines:
 - 🐬 MySQL
 - 🐘 PostgreSQL
 - 🟠 MariaDB
 - 🏢 Oracle
 - 🪟 SQL Server

## 🚀 Key Features
 * 🔄 Automated Management
    * Automatic provisioning and OS & DB patching
    * Maintenance handled by AWS
 * 💾 Backups & Snapshots
    * ✅ Automated backups (default `7 days`, max `35 days`)
    * 📸 Manual snapshots (`never expire`)
    * 🔁 Point-in-Time Recovery
 * 🌍 High Availability
    * Multi-AZ deployment for failover
    * Synchronous replication, Used for availability (`NOT performance`)
 * 📊 Read Replicas
    * Improves performance (NOT failover)
    * Up to 5 read replicas
    * Asynchronous replication
    * Best for **read-heavy workloads**

  - 🔒 Sync = Safety first (`no data loss`)        (Tasks are executed one after another. The next task waits until the current task finishes.)
  - 🚀 Async = Speed first (`better performance`)  (Tasks can run independently, without waiting for others to finish.)

 * 📈 Scaling
    * 🔼 Vertical scaling (instance type change)
    * 🔼 Storage scaling (`increase anytime`)
    * ❌ Cannot reduce storage after increasing
    * ⚠️ Scaling instance → requires reboot (downtime)

 * 🔐 Security
   * 🔒 Runs inside VPC
   * 🔐 Controlled by Security Groups (`firewall`)
   * 🔑 Encryption using AWS KMS
   * 🔐 SSL/TLS connections
   * 👤 IAM authentication

## 🔍 RDS Endpoint (Connection)
  * 🚫 No ssh, no terminal access ❌, You don’t see the OS (`Linux/Windows`) running underneath, You only connect via `DB clients`..
  * 📌 Why? Because RDS is a managed service — AWS controls the `server`, `OS`, `patching`, `security`, everything...

#### To connect your app:
```hcl
Endpoint (hostname) + Username + Password + Port (e.g., 3306 for MySQL)
```
 * You connect using tools like: **MySQL Workbench, pgAdmin**

### 🔌 Default Ports
| Database   | Port |
| ---------- | ---- |
| MySQL      | 3306 |
| PostgreSQL | 5432 |

### Simple Analogy
 * 🖥️ EC2 → Like renting a full computer (you can SSH and control everything)
 * 🗄️ RDS → Like using a database service (you only use it, `not manage the machine`)

---

## ⚙️ Important Concepts
### 🔁 Multi-AZ vs Read Replica
| 🧩 **Feature**            | 🛡️ **Multi-AZ**  | 📖 **Read Replica**         | 🧠 **Explanation**                      | 🎯 **Best Use Case**     |
| ------------------------- | ----------------- | --------------------------- | --------------------------------------- | ------------------------ |
| 🎯 **Purpose**            | High Availability | Read Scaling                | Different goals                         | HA vs performance        |
| 🔄 **Replication Type**   | Synchronous       | Asynchronous                | Sync = zero/minimal data loss           | Performance optimization |
| 🚨 **Automatic Failover** | ✅ Yes             | ❌ No                        | Multi-AZ promotes standby automatically | Disaster recovery        |
| 📈 **Read Scaling**       | ❌ No              | ✅ Yes                       | Read replicas handle read traffic       | Analytics/reporting      |
| 🌍 **Availability Zone**  | Different AZ      | Same or different AZ/Region | Improves resiliency                     | Flexible scaling         |

👉 RDS supports up to **5 Read Replicas**

### 📡 Monitoring
 * Use **CloudWatch** to monitor:
    * CPU usage
    * Memory
    * DB Connections
    * IOPS

### 🔐 Security Best Practices
  - Use IAM roles 👤
  - Configure Security Groups 🔥
  - Enable encryption 🔒
  - Use `SSL/TLS` connections 🌐

### 💾 Storage Types
| 🧩 **Storage Type**           | 📖 **Purpose**           | 🧠 **Detailed Explanation**                         | ⚡ **Performance** | 💡 **Best Use Case**            |
| ----------------------------- | ------------------------ | ----------------------------------------------------- | ----------------- | --------------------------------- |
| 🟢 **General Purpose (SSD)**  | Balanced storage         | Cost-effective SSD storage with good performance      | Medium to High    | Web apps, small/medium databases  |
| 🔴 **Provisioned IOPS (SSD)** | High-performance storage | Dedicated IOPS for consistent low-latency performance | 🚀 Very High      | high-traffic DBs                |

## 📊 Scaling 
### 📈 Increase Storage (Scale Up)
  - 👉 You can increase storage anytime, No major downtime in most cases ✅
  - AWS handles it `automatically` and Your database keeps running smoothly
  -  📌 Example: `100 GB → 200 GB` ✔️ (allowed)

### 📉 Decrease Storage (Scale Down)
  - 👉 You cannot reduce storage directly, AWS does not allow shrinking ❌
  - To reduce size, you must: Create a new smaller DB and Migrate data (`dump/restore` or `snapshot`)
  - 📌 Example : `200 GB → 100 GB` ❌ (not allowed directly)
  
### ⚠️ Downtime Possibility
  * Some scaling operations may cause: 🔄 `Reboot` and ⏳ `Short downtime`
  * 👉 Especially if: Changing storage type (`gp2 → gp3`) (Major modifications)

### ⏳ Backup Retention (“How long your backups are stored before they are deleted.”)
   * If backup retention (holding) = `7 days`
   * AWS keeps backups for the last 7 days
   * You can restore the database to any point within those 7 days
     * Default: `7 days`
     * Max: `35 days`

### ⏸️ Instance Stop Feature
  - You can stop RDS temporarily
  - ⏳ Automatically starts after **7 days**

### 🧱 Storage Limits
  - Max storage: **64 TB**

### 🔄 Migration
  * Use **AWS DMS (`Database Migration Service`)** to migrate databases.

### 💰 Pricing Factors
  - Database engine
  - Instance type
  - Storage type
  - Data transfer
  - Multi-AZ / IOPS usage

---

| 🔢 Step     | 🛠️ Action                          | 📘 Details                                       |
| ----------- | ----------------------------------- | ------------------------------------------------ |
| 🔐 **1️⃣**  | ☁️ **Open AWS Console → RDS**       | Login to AWS Console and open the RDS Dashboard  |
| ➕ **2️⃣**   | 🚀 **Create Database**              | Click **Create Database**                        |
| 🛢️ **3️⃣** | 📦 **Choose Database Engine**       | Select MySQL / PostgreSQL / MariaDB / SQL Server & Choose Version |
| 📝 **4️⃣**  | 🔑 **Set DB Credentials**           | Configure DB name, username, and password        |
| 💻 **5️⃣**  | ⚙️ **Select Instance Type**         | Example: `db.t3.micro`                           |
| 💾 **6️⃣**  | 📂 **Configure Storage**            | Choose storage type & size and enable autoscaling       |
| 🌐 **7️⃣**  | 🔗 **Set VPC & Security Group**     | Select VPC, subnet group, and security group & Configure Public Access *(Yes/No)*      |
| 📊 **8️⃣**  | 🛡️ **Enable Backups & Monitoring** | Configure backup `retention period` and `monitoring` |
| ✅ **9️⃣**   | 🎯 **Create Database**              | Click **Create** *(⏳ Takes ~5–10 minutes)*       |
| 🔌 **🔟**   | 🌍 **Connect to RDS**               | Use RDS endpoint with DB client                  |

* To connect Use tools like:
  * MySQL Workbench
  * pgAdmin
  * Provide:
    * Endpoint
    * Username & Password
    * Port (`3306` / `5432`)

---

## ✨ Summary

Amazon RDS is:
 - Fully managed relational database
 - Scalable 📈
 - Secure 🔐
 - Highly available 🌍

Perfect for modern cloud applications 🚀

---

## ⚡ AWS RDS — Rapid Fire Q&A
| #️⃣    | ❓ Question                                           | ✅ Answer                                                        |
| ------ | ---------------------------------------------------- | --------------------------------------------------------------- |
| 1️⃣    | 🗄️ What is Amazon RDS?                              | 👉 Managed relational database service in Amazon Web Services   |
| 2️⃣    | 🎯 Main purpose of RDS?                              | 👉 Simplify database setup, operation, scaling, and maintenance |
| 3️⃣    | 🧩 What does RDS stand for?                          | 👉 Relational Database Service                                  |
| 4️⃣    | 📚 What type of databases does RDS support?          | 👉 Relational databases                                         |
| 5️⃣    | 🛠️ Common database engines in RDS?                  | 👉 MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora       |
| 6️⃣    | ⚡ What is Amazon Aurora?                             | 👉 AWS-managed high-performance relational database             |
| 7️⃣    | 🚀 Aurora compatible with which databases?           | 👉 MySQL and PostgreSQL                                         |
| 8️⃣    | ☁️ Is RDS managed or self-managed?                   | 👉 Managed service                                              |
| 9️⃣    | 🔄 What management tasks does AWS handle in RDS?     | 👉 Backups, patching, monitoring, failover                      |
| 🔟     | 💾 What storage does RDS use?                        | 👉 EBS storage                                                  |
| 1️⃣1️⃣ | 📦 RDS storage types?                                | 👉 General Purpose SSD, Provisioned IOPS SSD, Magnetic          |
| 1️⃣2️⃣ | ⚡ Best storage for high-performance workloads?       | 👉 Provisioned IOPS SSD                                         |
| 1️⃣3️⃣ | 🧠 What is Multi-AZ in RDS?                          | 👉 High availability deployment with standby instance           |
| 1️⃣4️⃣ | 🔄 Purpose of Multi-AZ?                              | 👉 Automatic failover and high availability                     |
| 1️⃣5️⃣ | 👀 What is Read Replica?                             | 👉 Read-only copy of database for scaling reads                 |
| 1️⃣6️⃣ | ⚖️ Multi-AZ vs Read Replica?                         | 👉 Multi-AZ = HA, Read Replica = Read scaling                   |
| 1️⃣7️⃣ | 🌍 Can Read Replicas be cross-region?                | 👉 ✅ Yes                                                        |
| 1️⃣8️⃣ | 💾 What are automated backups in RDS?                | 👉 Scheduled database backups managed by AWS                    |
| 1️⃣9️⃣ | 📸 What is DB Snapshot?                              | 👉 Manual backup of RDS database                                |
| 2️⃣0️⃣ | 🔄 Difference between snapshot and automated backup? | 👉 Snapshot = manual, Automated backup = scheduled              |
| 2️⃣1️⃣ | ⏳ Backup retention period range?                     | 👉 0–35 days                                                    |
| 2️⃣2️⃣ | 🔐 How secure RDS?                                   | 👉 IAM, Security Groups, Encryption, SSL/TLS                    |
| 2️⃣3️⃣ | 🔑 Encryption options in RDS?                        | 👉 KMS encryption at rest and SSL in transit                    |
| 2️⃣4️⃣ | 🛡️ What controls network access to RDS?             | 👉 Security Groups                                              |
| 2️⃣5️⃣ | 🌐 Can RDS have public access?                       | 👉 ✅ Yes, but not recommended for production                    |
| 2️⃣6️⃣ | 🔒 Best practice for production RDS?                 | 👉 Deploy in private subnet                                     |
| 2️⃣7️⃣ | 🏢 Which AWS service isolates RDS network?           | 👉 VPC                                                          |
| 2️⃣8️⃣ | 📍 What is DB Subnet Group?                          | 👉 Group of subnets for RDS deployment                          |
| 2️⃣9️⃣ | ⚡ What is failover in RDS?                           | 👉 Automatic switch to standby DB during failure                |
| 3️⃣0️⃣ | 📈 How scale RDS vertically?                         | 👉 Increase DB instance size                                    |
| 3️⃣1️⃣ | 📊 How scale RDS horizontally?                       | 👉 Use Read Replicas                                            |
| 3️⃣2️⃣ | 🔍 Which service monitors RDS?                       | 👉 Amazon Web Services CloudWatch                               |
| 3️⃣3️⃣ | 📊 Common RDS monitoring metrics?                    | 👉 CPU, Memory, Storage, Connections, IOPS                      |
| 3️⃣4️⃣ | 📜 Where are RDS logs stored/viewed?                 | 👉 CloudWatch Logs / RDS console                                |
| 3️⃣5️⃣ | ⚙️ What is Parameter Group?                          | 👉 Database engine configuration settings                       |
| 3️⃣6️⃣ | 🧩 What is Option Group?                             | 👉 Additional database features/configurations                  |
| 3️⃣7️⃣ | 🔄 Can RDS upgrades be automated?                    | 👉 ✅ Yes                                                        |
| 3️⃣8️⃣ | ⏱️ What is maintenance window?                       | 👉 Scheduled time for updates/patching                          |
| 3️⃣9️⃣ | 🛠️ What is minor version upgrade?                   | 👉 Small DB engine patch/update                                 |
| 4️⃣0️⃣ | 🚀 What is major version upgrade?                    | 👉 Large DB engine version change                               |
| 4️⃣1️⃣ | ⚠️ Why test major upgrades first?                    | 👉 Prevent compatibility issues                                 |
| 4️⃣2️⃣ | ☸️ How EKS apps securely access RDS?                 | 👉 IAM roles, Secrets Manager, private networking               |
| 4️⃣3️⃣ | 🔑 Best place to store DB passwords?                 | 👉 Amazon Web Services Secrets Manager                          |
| 4️⃣4️⃣ | 📦 Can RDS be used with Terraform?                   | 👉 ✅ Yes                                                        |
| 4️⃣5️⃣ | 🔄 Common RDS backup strategy?                       | 👉 Automated backups + manual snapshots                         |
| 4️⃣6️⃣ | 🌍 How improve disaster recovery for RDS?            | 👉 Cross-region snapshots/replicas                              |
| 4️⃣7️⃣ | ⚡ What causes high RDS CPU usage?                    | 👉 Heavy queries or insufficient instance size                  |
| 4️⃣8️⃣ | 🐢 Database performance slow — checks?               | 👉 Queries, indexes, CPU, storage, connections                  |
| 4️⃣9️⃣ | 🔥 RDS storage full — solution?                      | 👉 Increase allocated storage                                   |
| 5️⃣0️⃣ | 💻 AWS CLI command to list RDS instances?            | 👉 `aws rds describe-db-instances`                              |

