# ⚖️ AWS EKS vs Self-Managed Kubernetes
| 🧩 Feature           | ☁️ AWS EKS                      | 🛠️ Self-Managed Kubernetes   |
| -------------------- | ------------------------------- | ----------------------------- |
| 🧠 Control Plane     | ✅ Managed by AWS                | ❌ You manage it               |
| 🌍 High Availability | ✅ Built-in multi-AZ             | ⚠️ You must configure         |
| 🔧 Maintenance       | ✅ AWS handles patching          | ❌ Manual updates              |
| 📈 Scaling           | 🔄 Automatic (with autoscaling) | ⚠️ Manual setup required      |
| 🔗 Integration       | 🔐 IAM, VPC, CloudWatch ready   | ⚙️ Custom integrations needed |
| 🛡️ Security         | ✅ Built-in features             | ⚠️ Depends on your setup      |

---

## 🌐💾 AWS EKS Summary (All-in-One Table)
| 🧩 Category        | 📌 Component / Feature   | 💡 Description                             |
| ------------------ | ------------------------ | ------------------------------------------ |
| 🧠 Key Features    | ⚙️ Managed Control Plane | ☁️ AWS manages API server, etcd, scheduler |
|                    | 🔗 AWS Integration       | 🔐 IAM, 🌐 VPC, 📊 CloudWatch              |
|                    | 🛡️ Built-in Security    | 🔒 KMS encryption, network policies        |
|                    | ⚡ Reduced Overhead       | 🧑‍💻 Less operational effort              |
| 🌐 Networking      | 🔌 VPC CNI Plugin        | 🌍 Assigns real IPs to pods                |
|                    | 🌐 VPC Integration       | 🖥️ Works inside AWS network               |
| 💾 Storage         | 💽 EBS                   | 📦 Block storage                           |
|                    | 📂 EFS                   | 🔗 Shared storage                          |
| 💰 Pricing         | 🧠 Control Plane         | 💵 ~$0.10/hour (~$72/month)                |
|                    | 🖥️ Worker Nodes         | 💰 EC2 or Fargate pricing                  |
| 🖥️ Compute        | 🖥️ EC2 Nodes            | 🔧 Full control                            |
|                    | ⚡ Fargate                | ☁️ Serverless                              |
| 🧱 Core Components | 📦 Node Groups           | 🔄 Auto scaling nodes                      |
|                    | 🌐 LoadBalancer          | 🔀 External traffic                        |
|                    | 🔗 NodePort              | 🌍 Node-level exposure                     |
|                    | 🌐 Ingress               | ⚖️ HTTP/HTTPS routing                      |
| 🛠️ Tools          | 🧑‍💻 kubectl            | 🔧 Manage workloads                        |
|                    | ⚙️ eksctl                | 🚀 Create/manage clusters                  |


---

## 🪜 Create Amazon EKS Cluster (Console Steps)
| 🧩 Step                  | 📌 Action                                                           | 💡 Description                     |
| ------------------------ | ------------------------------------------------------------------- | ---------------------------------- |
| 🔹 1️⃣ Open Console      | 🌐 Go to AWS → EKS → Create Cluster                                 | 🚀 Start cluster creation          |
| 🔹 2️⃣ Configure Cluster | 🏷️ Name: `my-eks-cluster`<br>📦 Version: Latest<br>🔐 IAM Role     | ⚙️ Set basic cluster configuration |
| 🔹 3️⃣ Networking        | 🌐 Select VPC<br>📍 Choose subnets<br>🛡️ Configure security groups | 🔗 Define network setup            |
| ⏳ Wait                   | ⏱️ 10–15 mins                                                       | 🟢 Cluster becomes Active          |
| 🔹 4️⃣ Add Node Group    | 🖥️ Instance: `t3.medium`<br>🔢 Nodes: 2                            | 📦 Add worker nodes                |
| ⏳ Wait                   | ⏱️ 5–10 mins                                                        | 🟢 Nodes ready                     |
| 🔹 5️⃣ Connect Cluster   | 🧑‍💻 Install AWS CLI<br>⚙️ Install kubectl                         | 🔗 Access and manage cluster       |

### 🧹 Delete Cluster
```
eksctl delete cluster --name <cluster-name>
```
---

## 🎯 Summary

- Fully managed Kubernetes
- Highly available & scalable
- Deep AWS integration
