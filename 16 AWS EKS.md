# ☸️ AWS EKS (Elastic Kubernetes Service) 
## 🌟 What is AWS EKS?
**Amazon Elastic Kubernetes Service (EKS)** is a fully managed Kubernetes service from AWS 

👉 It allows you to:
  * Deploy containerized apps
  * Manage Kubernetes clusters ☸️
  * Scale applications automatically 📈

#### 💡 Think: EKS = Kubernetes without managing control plane
👉 It offers a **highly available, secure, and scalable Kubernetes environment** without the need to manage the control plane.

---

## 🧩 Components of an EKS Cluster
### 🧠 Control Plane
- Managed by AWS
- Includes:
| 🧩 Component          | 💡 Description                           |
| --------------------- | ---------------------------------------- |
| 🌐 API Server         | 🔗 Entry point for cluster management & Handles requests(kubectl/API calls)   |
| 💾 etcd               | 📦 Stores cluster state & data           |
| 🧠 Scheduler          | 📍 Assigns pods to nodes                 |
| ⚙️ Controller Manager | 🔄 Maintains desired state               |

### ✅ Key Benefits
   * 🌍 Runs across multiple AZs
   * 🛡️ Highly available
   * ⚡ No maintenance needed
   * ☁️ Managed entirely by AWS

### 🖥️ Worker Nodes
- Run your applications (pods)  
- Can be:
| 🧩 Option              | 💡 Description                    |
| ---------------------- | --------------------------------- |
| 🖥️ 🛠️ Self-managed Nodes | EC2 Instances 🔧 You manage nodes manually    |
| ⚙️ Managed Node Groups | 🤖 AWS manages lifecycle (scaling, updates) |
| ☁️ Fargate             | ⚡ Serverless (no nodes to manage) |

 ### 🔧 Components on Each Node
| 🧩 Component  | 💡 Role                                                       |
| ------------- | -------------------------------------------------------------- |
| 🤖 kubelet    | 🖥️ Node agent (🔗 Communicates with control plane -- talks to API server) |
| 🌐 kube-proxy | 🔀 Handles networking rules              |
| 🔌 VPC CNI    | 🌍 Assigns IP addresses to pods          |


### 📦 Node Groups
- Collection of worker nodes  
- Same configuration  
- Can be managed or self-managed
| 🧩 Type               | 💡 Description                   |
| --------------------- | -------------------------------- |
| ⚙️ Managed Node Group | 🤖 AWS manages scaling & updates |
| 🛠️ Self-managed      | 🔧 You manage everything         |

### 🔌 Add-ons (Extra features 🔌)
Pre-configured Kubernetes components: 
| 🧩 Add-on     | 💡 Purpose           |
| ------------- | -------------------- |
| 🌐 CoreDNS    | 🔍 Service discovery |
| 🔀 kube-proxy | 🌍 Networking        |
| 🔌 VPC CNI    | 📡 Pod networking    |

---

## ⚖️ EKS vs Self-Managed Kubernetes

### 🚀 Managed Control Plane
AWS manages:
- API Server  
- etcd  
- Scheduler  

### 🔗 AWS Integration
Seamlessly integrates with:
- IAM  
- VPC  
- CloudWatch  
- ALB / NLB  

### ⚙️ Reduced Operational Overhead
- No patching  
- No control plane maintenance  
- Automatic scaling  

### 🔐 Security
- IAM integration  
- Encryption with KMS  
- Compliance & certifications  

---

## 🌐 Networking in EKS
 🔑 Key Concepts
 | 🧩 Component       | 📌 Description                         | 💡 Why it Matters                                          |
| ------------------ | -------------------------------------- | ---------------------------------------------------------- |
| 🔌 VPC CNI Plugin  | 🌍 Assigns real VPC IPs to pods        | 🖥️ Pods behave like EC2 instances (direct networking)     |
| 🔐 Security Groups | 🛡️ Act like firewalls                 | 🚦 Control inbound & outbound traffic (can attach to pods) |
| ⚖️ Load Balancing  | 🌐 ALB (HTTP/HTTPS)<br>⚡ NLB (TCP/UDP) | 🔀 Distributes traffic to applications                     |

---

### 📈 Scaling in Amazon EKS
🔑 Key Scaling Components
| 🧩 Component                       | 📌 What it Does                             | 💡 Why it Matters                           |
| ---------------------------------- | ------------------------------------------- | ------------------------------------------- |
| 🔄 Cluster Autoscaler              | 🖥️ Adds/removes worker nodes automatically | 📈 Handles cluster capacity based on demand |
| 📦 Horizontal Pod Autoscaler (HPA) | 🔁 Scales number of pods                    | ⚡ Based on CPU, memory, or custom metrics   |
| 📊 Vertical Pod Autoscaler (VPA)   | 📏 Adjusts CPU/memory of pods               | 🎯 Optimizes resource usage                 |

---

### ⚡ Fargate in EKS
- Run pods without managing EC2  
- Fully serverless, No EC2 management (✔️ Pay per usage)

---

## 📊 Monitoring & Observability

- 📈 CloudWatch → Logs & metrics  
- 📊 Prometheus → Metrics collection  
- 📉 Grafana → Visualization dashboards  

## 📜 Deployment Tools
### 🧾 Kubernetes Manifests
- YAML files to define:
  - Deployments  
  - Services  
  - Configurations  

### 📦 Helm Charts
- Package Kubernetes apps  
- Reusable templates for deployments  

## 🔍 CoreDNS
- DNS server inside Kubernetes  
- Resolves service names → IP addresses  
- Enables communication between pods  

## 🔌 Add-ons
- 🌐 CoreDNS → Service discovery  
- 🔁 kube-proxy → Networking  
- ⚖️ AWS Load Balancer Controller  
- 📈 Cluster Autoscaler  

## 🔐 Security
### 🔑 IAM Integration
- Control user and service access  

### 🪪 IRSA (IAM Roles for Service Accounts)
- Secure AWS access from pods  

### 🔐 Encryption
- Uses AWS KMS  

### 🛡️ Network Policies
- Control pod-to-pod communication  
- Tools like Calico  

---

# 🎯 Summary

- ☸️ EKS = Managed Kubernetes on AWS  
- 🧠 Control Plane → AWS managed  
- 🖥️ Worker Nodes → EC2 or Fargate  
- 🌐 Deep AWS integration  
- 🔐 Strong security & IAM control  
- 📈 Built-in autoscaling & monitoring  

---

💡 *EKS simplifies Kubernetes operations while providing enterprise-grade scalability, security, and reliability.*
