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
| 🛠️ Tools          | 🧑‍💻 kubectl                | 🔧 Manage workloads                        |
|                    | ⚙️ eksctl                | 🚀 Create/manage clusters                  |

## 🚀 Production-Grade Kubernetes on AWS (EKS Stack)
| 🧩 Component            | 📌 Service                                                | 💡 Purpose                             |
| ----------------------- | --------------------------------------------------------- | -------------------------------------- |
| ☸️ Kubernetes           | Amazon EKS                                                | 🧠 Managed Kubernetes control plane    |
| 🖥️ Compute              | Amazon EC2 / AWS Fargate                                  | ⚙️ Run worker nodes or serverless pods |
| 🔐 Secrets & Encryption | AWS Secrets Manager / AWS Key Management Service          | 🔒 Secure secrets & encryption         |
| 👤 Identity & Access    | AWS Identity and Access Management                        | 🛡️ RBAC integration & access control  |
| 🗄️ Database             | Amazon RDS / Amazon Aurora                                | 📊 Managed databases for apps          |
| 📦 Object Storage       | Amazon S3                                                 | 💾 Store logs, backups, Helm charts    |
| 📈 Auto Scaling         | AWS Auto Scaling                                          | 🔄 Scale worker nodes automatically    |
| 🔐 TLS Certificates     | AWS Certificate Manager                                   | 🌐 Manage HTTPS certificates           |
| 🌐 Networking           | VPC + IAM                                                 | 🔗 Secure networking & access control  |
| 📦 Container Registry   | Amazon ECR                                                | 🐳 Store Docker images                 |
| ⚖️ Load Balancing       | AWS Application Load Balancer / AWS Network Load Balancer | 🔀 Distribute traffic to services      |
| 📊 Monitoring & Logs    | Amazon CloudWatch                                         | 📈 Logging, metrics, alerts            |

---

# AWS EKS
 * “Kubernetes follows a master-worker architecture where the Control Plane makes all cluster decisions, and Worker Nodes execute those decisions by running containerized applications.”

## 🪜 Create Amazon EKS Cluster (Console Steps)
| 🔢 Step       | 🛠️ Action                     | 📘 Details                                                   |
| ------------- | ------------------------------ | ------------------------------------------------------------ |
| 🔐 **1️⃣**    | ☁️ Login to AWS Console        | Sign in to AWS Management Console                            |
| 📋 **2️⃣**    | ✅ Verify Prerequisites         | AWS Account, IAM Permissions, VPC, Subnets, AWS CLI, kubectl |
| ☸️ **3️⃣**    | 📂 Open EKS Dashboard          | Search for **EKS** in AWS Console                            |
| ➕ **4️⃣**     | 🚀 Create EKS Cluster          | Click **Add Cluster → Create**                               |
| 📝 **5️⃣**    | ⚙️ Configure Cluster           | Enter `Cluster Name`, `Kubernetes Version`, `IAM Role `      |
| 🌐 **6️⃣**    | 🔗 Configure Networking        | Select `VPC`, `Public/Private Subnets`, `Security Groups`     |
| 📊 **7️⃣**    | 📜 Enable Logging *(Optional)* | Enable Control Plane Logs                                    |
| ✅ **8️⃣**     | 🎯 Create Cluster              | Click **Create Cluster** *(⏳ Takes `10–20 mins`)*           |
| 🖥️ **9️⃣**   | ➕ Create Node Group            | Open Cluster → Compute → Add Node Group                      |
| ⚙️ **🔟**     | 📝 Configure Node Group        | Enter `Node Group Name` and `IAM Role`                    |
| 💻 **1️⃣1️⃣** | 📦 Select Instance Type        | Example: `t3.medium`                                         |
| 📈 **1️⃣2️⃣** | 🔢 Configure Scaling           | Set Desired, Minimum, and Maximum Nodes                      |
| 🌍 **1️⃣3️⃣** | 📂 Select Subnets              | Choose Worker Node Subnets                                   |
| ✅ **1️⃣4️⃣**  | 🚀 Create Node Group           | Click **Create Node Group**                                  |
| 🔗 **1️⃣5️⃣** | 💻 Configure kubectl           | Update kubeconfig using AWS CLI                              |
| 🧪 **1️⃣6️⃣** | 📊 Verify Cluster              | Run `kubectl get nodes`                                      |


### 🧹 Delete Cluster
```hcl
eksctl delete cluster --name <cluster-name>
```
---

## 🎯 Summary
  - Fully managed Kubernetes
  - Highly available & scalable
  - Deep AWS integration

---

## ⚡ AWS EKS (Elastic Kubernetes Service) — Full Detailed Interview Q&A
| #️⃣ | ❓ Question                            | ✅ Answer                                                                                                                                                    |
| --- | ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1️⃣ | ☁️ What is Amazon EKS?                | 👉 Amazon EKS (Elastic Kubernetes Service) is a fully managed Kubernetes service provided by Amazon Web Services that simplifies running Kubernetes on AWS. |
| 2️⃣ | 🎯 Why use EKS?                       | 👉 To run Kubernetes without managing the control plane infrastructure.                                                                                     |
| 3️⃣ | 🧠 What does AWS manage in EKS?       | 👉 Kubernetes Control Plane, API Server, etcd, Scheduler, Controller Manager, upgrades, and availability.                                                   |
| 4️⃣ | 🏗️ What are the main EKS components? | 👉 Control Plane, Worker Nodes, Pods, Services, IAM, VPC Networking.                                                                                        |
| 5️⃣ | 🌍 Is EKS regional or zonal?          | 👉 Regional service with Multi-AZ control plane.                                                                                                            |
| 6️⃣ | 🔄 What is Kubernetes in EKS?         | 👉 Open-source container orchestration platform managed by AWS.                                                                                             |
| 7️⃣ | 📦 What workloads run on EKS?         | 👉 Containerized applications, microservices, APIs, batch jobs, and AI workloads.                                                                           |
| 8️⃣ | 🏢 Who manages worker nodes?          | 👉 Customer (EC2 nodes) or AWS (Fargate).                                                                                                                   |
| 9️⃣ | ⚡ What is EKS Fargate?                | 👉 Serverless Kubernetes Pods without managing worker nodes.                                                                                                |
| 🔟  | 🎯 EKS control plane availability?    | 👉 Highly available across multiple Availability Zones.                                                                                                     |
| 1️⃣1️⃣ | 🏗️ What are EKS architecture components?       | 👉 Control Plane, Worker Nodes, VPC, IAM, Load Balancers, Storage. |
| 1️⃣2️⃣ | 🎮 What runs in Control Plane?                  | 👉 API Server, Scheduler, Controller Manager, etcd.                |
| 1️⃣3️⃣ | 🖥️ What are Worker Nodes?                      | 👉 EC2 instances or Fargate running Pods.                          |
| 1️⃣4️⃣ | 📡 How do nodes communicate with Control Plane? | 👉 Through Kubernetes API Server.                                  |
| 1️⃣5️⃣ | 🔐 How is control plane secured?                | 👉 IAM, Security Groups, TLS, RBAC.                                |
| 1️⃣6️⃣ | 🌐 Where does EKS run?                          | 👉 Inside an AWS VPC.                                              |
| 1️⃣7️⃣ | 📦 What is a Node Group?                        | 👉 Collection of worker nodes managed together.                    |
| 1️⃣8️⃣ | ⚙️ Types of Node Groups?                        | 👉 Managed Node Groups and Self-Managed Node Groups.               |
| 1️⃣9️⃣ | 🚀 What are Managed Node Groups?                | 👉 AWS-managed EC2 worker nodes.                                   |
| 2️⃣0️⃣ | 🛠️ What are Self-Managed Node Groups?          | 👉 EC2 nodes fully managed by users.                               |
| 2️⃣1️⃣ | 🌐 Which networking plugin does EKS use?     | 👉 Amazon VPC CNI Plugin.                        |
| 2️⃣2️⃣ | 📡 What is Amazon VPC CNI?                   | 👉 Assigns VPC IPs directly to Pods.             |
| 2️⃣3️⃣ | 🎯 Benefit of VPC CNI?                       | 👉 Native AWS networking and security groups.    |
| 2️⃣4️⃣ | 🔐 Can Pods have security groups?            | 👉 Yes, using Security Groups for Pods.          |
| 2️⃣5️⃣ | 🌍 How expose applications externally?       | 👉 LoadBalancer Service or Ingress.              |
| 2️⃣6️⃣ | ⚖️ Which AWS Load Balancer is commonly used? | 👉 Application Load Balancer (ALB).              |
| 2️⃣7️⃣ | 🌐 What is AWS Load Balancer Controller?     | 👉 Creates and manages ALBs/NLBs for Kubernetes. |
| 2️⃣8️⃣ | 🔄 Service types in EKS?                     | 👉 ClusterIP, NodePort, LoadBalancer.            |
| 2️⃣9️⃣ | 📡 What handles DNS inside EKS?              | 👉 CoreDNS.                                      |
| 3️⃣0️⃣ | ❌ DNS resolution failing in Pods?            | 👉 Check CoreDNS pods and configuration.         |
| 3️⃣1️⃣ | 🔐 How does EKS integrate with IAM?      | 👉 IAM authenticates users and services.                      |
| 3️⃣2️⃣ | 🛡️ What is RBAC?                        | 👉 Role-Based Access Control inside Kubernetes.               |
| 3️⃣3️⃣ | 🔑 Difference between IAM and RBAC?      | 👉 IAM = AWS Authentication, RBAC = Kubernetes Authorization. |
| 3️⃣4️⃣ | 🚀 What is IRSA?                         | 👉 IAM Roles for Service Accounts.                            |
| 3️⃣5️⃣ | 🎯 Purpose of IRSA?                      | 👉 Pod-level AWS permissions.                                 |
| 3️⃣6️⃣ | 🌍 What identity provider does IRSA use? | 👉 OIDC Provider.                                             |
| 3️⃣7️⃣ | 🔄 Which STS API is used by IRSA?        | 👉 AssumeRoleWithWebIdentity.                                 |
| 3️⃣8️⃣ | 🔐 Why use IRSA instead of AWS keys?     | 👉 No static credentials stored in Pods.                      |
| 3️⃣9️⃣ | 📜 What is a Trust Policy?               | 👉 Defines who can assume an IAM role.                        |
| 4️⃣0️⃣ | ⚠️ Most common IRSA issue?               | 👉 ServiceAccount annotation mismatch.                        |
| 4️⃣1️⃣ | 💾 How provide storage in EKS?            | 👉 EBS, EFS, FSx.                          |
| 4️⃣2️⃣ | 📦 What is Persistent Volume (PV)?        | 👉 Cluster-level storage resource.         |
| 4️⃣3️⃣ | 📄 What is Persistent Volume Claim (PVC)? | 👉 Request for storage by a Pod.           |
| 4️⃣4️⃣ | 💿 Most common storage for databases?     | 👉 EBS.                                    |
| 4️⃣5️⃣ | 📂 Shared storage across Pods?            | 👉 EFS.                                    |
| 4️⃣6️⃣ | 🔄 PVC Pending issue?                     | 👉 StorageClass or provisioner problem.    |
| 4️⃣7️⃣ | 📦 Why use StatefulSets?                  | 👉 Stable identity and persistent storage. |
| 4️⃣8️⃣ | ❌ Database data lost after restart?       | 👉 No persistent volume attached.          |
| 4️⃣9️⃣ | 📈 What is HPA?                 | 👉 Horizontal Pod Autoscaler.                      |
| 5️⃣0️⃣ | 🎯 HPA scales based on?         | 👉 CPU, Memory, Custom Metrics.                    |
| 5️⃣1️⃣ | 🖥️ What is Cluster Autoscaler? | 👉 Adds/removes worker nodes automatically.        |
| 5️⃣2️⃣ | ⚡ What is Karpenter?            | 👉 AWS-native Kubernetes node autoscaler.          |
| 5️⃣3️⃣ | 🔄 Why use Cluster Autoscaler?  | 👉 Automatically adjust node count.                |
| 5️⃣4️⃣ | 🌍 Multi-AZ EKS benefit?        | 👉 High Availability.                              |
| 5️⃣5️⃣ | ❌ One node fails. What happens? | 👉 Pods are rescheduled to healthy nodes.          |
| 5️⃣6️⃣ | ⚠️ HPA not scaling?             | 👉 Metrics Server missing or requests not defined. |
| 5️⃣7️⃣ | 🚀 What is Deployment?           | 👉 Manages Pod lifecycle and rolling updates.     |
| 5️⃣8️⃣ | 🔄 What is Rolling Update?       | 👉 Gradual replacement of old Pods with new Pods. |
| 5️⃣9️⃣ | ↩️ Rollback deployment command?  | 👉 `kubectl rollout undo deployment app`          |
| 6️⃣0️⃣ | 🎯 Zero-downtime deployment?     | 👉 Rolling updates + readiness probes.            |
| 6️⃣1️⃣ | 🟢🔵 Blue-Green deployment?      | 👉 Two environments with traffic switching.       |
| 6️⃣2️⃣ | 🐤 Canary deployment?            | 👉 Gradual traffic shifting to new version.       |
| 6️⃣3️⃣ | 🔄 Upgrade worker node process?  | 👉 Drain → Upgrade → Restart → Uncordon.          |
| 6️⃣4️⃣ | 💾 Best practice before upgrade? | 👉 Take etcd backup.                              |
| 6️⃣5️⃣ | 📊 Common monitoring stack?       | 👉 Prometheus + Grafana                          |
| 6️⃣6️⃣ | 📜 Common logging stack?          | 👉 EFK (Elasticsearch, Fluentd, Kibana) or Loki. |
| 6️⃣7️⃣ | 🔔 Alerting tool?                 | 👉 Prometheus Alertmanager.                      |
| 6️⃣8️⃣ | 📈 What metrics are monitored?    | 👉 CPU, Memory, Network, Pod Health.             |
| 6️⃣9️⃣ | ☁️ AWS-native monitoring service? | 👉 Amazon CloudWatch                             |
| 7️⃣0️⃣ | 📜 View Pod logs?                 | 👉 `kubectl logs <pod>`                          |

---
## ⚡ Scenario-Based EKS Interview Q&A
| #️⃣    | 🚨 Scenario                  | ✅ Answer                                            |
| ------ | ---------------------------- | --------------------------------------------------- |
| 7️⃣1️⃣ | Pod stuck in Pending         | 👉 Check resources, taints, PVCs, scheduler events. |
| 7️⃣2️⃣ | Pod CrashLoopBackOff         | 👉 Check logs, env vars, configs, DB connectivity.  |
| 7️⃣3️⃣ | ImagePullBackOff             | 👉 Wrong image, tag, registry credentials.          |
| 7️⃣4️⃣ | Node NotReady                | 👉 Check kubelet, container runtime, networking.    |
| 7️⃣5️⃣ | Service not reachable        | 👉 Check selectors, endpoints, labels.              |
| 7️⃣6️⃣ | Ingress returning 404        | 👉 Verify host/path rules and backend service.      |
| 7️⃣7️⃣ | DNS failing in Pods          | 👉 Check CoreDNS.                                   |
| 7️⃣8️⃣ | PVC Pending                  | 👉 Verify StorageClass and CSI driver.              |
| 7️⃣9️⃣ | Pod OOMKilled                | 👉 Increase memory limit or optimize application.   |
| 8️⃣0️⃣ | HPA not scaling              | 👉 Metrics server issue or missing requests.        |
| 8️⃣1️⃣ | User gets Forbidden error    | 👉 Check RBAC roles and bindings.                   |
| 8️⃣2️⃣ | EKS node not joining cluster | 👉 Check IAM role, SGs, bootstrap process.          |
| 8️⃣3️⃣ | Argo CD OutOfSync            | 👉 Git state differs from cluster state.            |
| 8️⃣4️⃣ | Cluster suddenly slow        | 👉 Check node resources, API latency, etcd health.  |
| 8️⃣5️⃣ | Pods restarting randomly     | 👉 OOMKilled, probe failures, node instability.     |

---

## 🏆 Interview Gold Answers
| ❓ Question                                | ✅ Strong Interview Answer                                                                                                  |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| 🚀 What is EKS?                           | 👉 "EKS is AWS's managed Kubernetes service that removes the operational burden of managing the Kubernetes control plane." |
| 🔐 Why use IRSA?                          | 👉 "IRSA securely provides AWS permissions to Pods without storing static credentials."                                    |
| ⚡ EKS vs ECS?                             | 👉 "EKS provides Kubernetes flexibility and ecosystem support, while ECS is simpler and AWS-native."                       |
| 🌐 How do Pods get networking?            | 👉 "Through the Amazon VPC CNI plugin, which assigns VPC IP addresses directly to Pods."                                   |
| 🎯 Real-world deployment flow?            | 👉 "Developer → GitHub → CI/CD → ECR → EKS Deployment → ALB → Users."                                                      |
| 🛡️ Most important EKS security practice? | 👉 "Use IRSA, RBAC, private networking, and least-privilege IAM permissions."                                              |

