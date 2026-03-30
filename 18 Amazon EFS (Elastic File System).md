# 🌐 Amazon EFS (Elastic File System) 
## 📌 What is Amazon EFS?
Amazon Elastic File System (EFS) is a serverless, scalable, fully managed file storage service that allows multiple EC2 instances to access the same file system using the NFSv4 protocol.

✨ Designed for:
- High availability  
- High durability  
- Multi-AZ architecture  

### 🖼️ How EFS Works (Architecture)
 * 👉 Multiple EC2 instances connect to EFS using NFS protocol (v4.0 & v4.1)
 * 👉 Data is automatically stored across multiple Availability Zones (AZs)

## 📂✨ Key Features of Amazon EFS
| 🧩 Feature               | 💡 Description                                                                                                 |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| 🔧 Fully Managed         | ☁️ No infrastructure (servers) management required — AWS handles everything scaling, patching, and maintenance  |
| 📈 Elastic & Scalable    | 📊 Automatically grows (from KBs → Petabytes) and shrinks based on usage  (no manual resize)                 |
| 🌍 Multi-AZ Availability | 🛡️ Data stored (replicated) across multiple AZs → high availability & durability                            |
| 🔗 Shared File System    | 👥 Multiple EC2 instances can read/write simultaneously                                                        |
| 🔐 Security              | 🔒 Encryption at rest (KMS)<br>🔐 Encryption in transit (TLS)<br>🚦 Controlled via Security Groups (port 2049) |

 
### 🔗 NFS-Based
- Uses NFSv4 (4.0 & 4.1) protocol
- Amazon EFS (Elastic File System) uses the NFS (Network File System) protocol.
- Specifically NFSv4.0 and NFSv4.1, to allow multiple systems to access shared files over a network.

### 🔥 Why EFS uses NFSv4.1 
 Amazon EFS recommends NFSv4.1 because:
 * ⚡ Higher performance (handles more requests)
 * 🔄 Parallel connections → better throughput
 * 🔐 Stronger locking & consistency
 * 💪 Better fault tolerance

## ⚡ Performance Modes
| 🧩 Mode            | 💡 Description                                                           |
| ------------------ | ------------------------------------------------------------------------ |
| 🚀 General Purpose | ⚡ Low latency, best for most applications (web apps, CMS, dev workloads) |
| 📊 Max I/O         | 🔄 High throughput for parallel workloads (big data, analytics)          |

## 💾 Storage Classes
| 🧩 Storage Class          | 💡 Use Case                                                 |
| ------------------------- | ----------------------------------------------------------- |
| 🚀 Standard               | 📊 Frequently accessed data (low latency, high performance) |
| 💰 Infrequent Access (IA) | 🗂️ Rarely used data (lower cost, slightly higher latency)  |

## 🚄 Throughput Modes
| 🧩 Mode        | 💡 Description                                                             |
| -------------- | -------------------------------------------------------------------------- |
| ⚡ Bursting     | 📈 Default mode, automatically scales throughput based on file system size |
| 🎯 Provisioned | 📊 Fixed throughput for consistent performance (independent of size)       |

## 🔐 Security & Encryption
 * 🔒 Encryption at rest → AWS KMS
 * 🔐 Encryption in transit → Use -o tls while mounting

💡 Encryption = converting data into a secret code accessible only with a key.

## 💰 Pricing (Billing)
- Pay for:
  - Storage used (GB)
  - Throughput (if provisioned)
  - Requests (for IA class)

---

## 🧠 Common Use Cases
  * 📁 Shared storage across EC2 instances
  * 🌐 Web hosting (e.g., WordPress multi-server)
  * 📊 Data analytics & Machine Learning
  * 💾 Backup & Disaster Recovery
  * ☸️ Kubernetes (EKS) stateful apps
  * 🐳 Containers (ECS, EKS)

---

## 🔍 Important Points
 * ✅ Supports multiple EC2 instances simultaneously
 * ✅ Works only with Linux systems
 * ❌ For Windows → Use FSx for Windows
 * ✅ Max file size: 52.7 TB
 * ✅ No minimum storage (pay-as-you-use)
 * ✅ Supports 10+ GB/s throughput
 * ✅ Can be mounted on:
     * EC2
     * Lambda
     * ECS / EKS / Kubernetes
 * ✅ Accessible from on-prem via:
     * AWS VPN
     * Direct Connect
 * ✅ Limit: 125 file systems per region

---

## ⚖️ Amazon EFS vs Amazon EBS
| 🧩 Feature  | 📂 EFS (File Storage)          | 💽 EBS (Block Storage)         |
| ----------- | ------------------------------ | ------------------------------ |
| 📦 Type     | 📁 File Storage                | 💾 Block Storage               |
| 🔗 Access   | 👥 Multiple instances (shared) | 🖥️ Single instance (attached) |
| 📈 Scaling  | ⚡ Automatic                    | 🔧 Manual resizing             |
| 🎯 Use Case | 🔗 Shared storage (apps, NFS)  | 🖥️ OS disks, databases        |

---

## 🏗️ How to Create EFS File System

### 1️⃣ Create File System
  * 🌐 Go to AWS Console → EFS
  *  Click Create File System
  * 🌍 Select VPC
  * 🏗️ Choose Type :
     * 🌍 Regional (recommended)
     * 🟡 One Zone (cheaper)
  * Click Next

### 2️⃣ Configure Settings
  * 🏷️ Set name
  * Choose:
    * ⚡ Performance Mode → General Purpose / Max I/O
    * 📈 Throughput Mode → Bursting / Provisioned
  * 🔄 Enable Lifecycle Management (optional)

### 3️⃣ Network & Security
  * 📍 Attach subnets in VPC
  * 🛡️ Configure Security Group:
     * 🔓 Allow NFS (port 2049)
  * 🔒 Enable encryption (optional)
  * 🎉 Click Create File System               🚀 EFS ready to use      

---

## 🔗 Mount EFS to EC2
### Install NFS Utilities
```bash

sudo yum install -y amazon-efs-utils                      # Amazon Linux
sudo apt install -y nfs-common                            # Ubuntu/Debian

sudo mkdir -p /mnt/efs                                # 📁 Create Mount Directory       

sudo mount -t efs fs-xxxxxxxx:/ /mnt/efs            # 🔌 Mount EFS
              OR
sudo mount -t efs -o tls fs-xxxxxxxx:/ /mnt/efs     # 🔐 Mount with Encryption

df -h | grep efs   # ✅ Verify Mount

```

---

## 📌 Final Summary

- EFS = Shared, scalable file storage  
- Best for multi-instance and Kubernetes workloads  
- Fully managed, highly available, secure  

