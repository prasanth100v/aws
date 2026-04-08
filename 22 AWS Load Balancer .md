# ⚖️ Load Balancer (Elastic Load Balancing - ELB)
## 🚀 What is ELB?

 * ✨ Load Balancer distributes `incoming traffic` across multiple `Servers` to ensure high availability and fault tolerance.
 * It helps to ensure that no single instance or server is `overwhelmed` with too much traffic.
 * 🔐 ELB Integration with `AWS IAM` for secure access, and support for `SSL/TLS` termination (secure communication)
 * 🔄 ELB automatically distributes `incoming traffic` across multiple targets.
 * 💚 Health checks monitor the status of `targets` and route traffic only to `healthy targets`.
 * 🌐 Internet-facing ELB has a `public IP`, while `internal ELB` routes traffic within a private VPC.
 * 🚢 AWS ELB helps make `Kubernetes services` scalable and accessible externally.
     * 📌 Use `Service type` LoadBalancer to create an ELB automatically.
     * 📌 Use `AWS ALB Ingress Controller` for advanced routing (e.g.,` path-based, host-based`)
     * 📌 `Annotations` allow customization of `ELB behavior` (e.g., internal/external, `SSL/TLS`, `health checks`)

---

# ☁️ AWS offers different types of Load Balancers:
## 🌐 Application Load Balancer (ALB)

 * Application Load Balancer works at `Layer 7` (application layer) and supports advanced routing like `path-based` and `host-based` routing.
 * 💡 It is ideal for `microservices` and `container-based applications`
 * Supports `HTTP/HTTPS` traffic.
 * 📂 Path-based routing : ➡️ Route requests to different target groups based on `URL paths` (e.g., /`api` vs. /`images`).
 * 🌐 Host-based routing : ➡️ Route traffic based on the `requested hostname` (e.g., `api.example.com` vs. `app.example.com`).  


### 🎯 ALB Target Types (Where ALB Routes Traffic)

 * `Target groups` receive traffic from the load balancer.
 * Each target group is associated with a `specific protocol` and `port`, and the `load balancer` routes traffic to the targets based on the rules defined in the listener.


- 🖥️ EC2 Instances — `Traditional` virtual machines.  
- 📦 Containers (`ECS`, `EKS`, `Fargate`) — Routes traffic to containerized applications.  
- ⚡ Lambda Functions — Directly invokes AWS Lambda functions for `serverless` architectures.  
- 🌍 IP Addresses — Routes to `on-premises` servers or `external` services.  

---

## 🚀 Create an Application Load Balancer (ALB) in AWS
| 🎯 Step | 🧩 Section             | 📌 Action           | 💡 Details                                            |
| ------- | ---------------------- | ------------------- | ----------------------------------------------------- |
| 1️⃣     | 🌐 Open AWS Console    | EC2 Dashboard       | 🔍 Login → Search **EC2** → Open Dashboard            |
| 2️⃣     | ⚖️ Load Balancer Menu  | Open Load Balancers | 📂 Left sidebar → **Load Balancing → Load Balancers** |
| 3️⃣     | ➕ Create Load Balancer | Click Create        | 🚀 Click **Create Load Balancer**                     |
| 4️⃣     | 🧩 Choose Type         | Select ALB          | 🌐 Application Load Balancer (Layer 7 - HTTP/HTTPS)   |
| 5️⃣     | ⚙️ Basic Config        | Name                | 📝 Example: `my-alb`                                  |
|         |                        | Scheme              | 🌍 Internet-facing / 🔒 Internal                      |
|         |                        | IP Type             | 🌐 IPv4 / Dual-stack                                  |
| 6️⃣     | 🌐 Network Mapping     | Select VPC          | 🔗 Choose VPC                                         |
|         |                        | Subnets             | 📍 Select **2+ AZs** (mandatory)                      |
| 7️⃣     | 🛡️ Security Groups    | Assign SG           | 🔓 Allow HTTP (80), HTTPS (443)                       |
| 8️⃣     | 🔗 Listeners & Routing | Add Listener        | 📡 Default: HTTP : 80                                 |
| 9️⃣     | 🎯 Target Group        | Create Target Group | ➕ Click **Create Target Group**                       |
| 🔟      | ⚙️ Target Config       | Target Type         | 🖥️ Instance / IP / Lambda                            |
|         |                        | Protocol & Port     | 🌐 HTTP : 80                                          |
|         |                        | Health Check        | ❤️ Default `/`                                        |
| 1️⃣1️⃣  | 📦 Register Targets    | Add EC2 Instances   | ➕ Select → Include as pending                         |
| 1️⃣2️⃣  | ✅ Review TG            | Create              | 🚀 Click **Create Target Group**                      |
| 1️⃣3️⃣  | 🔗 Attach TG           | Select Target Group | 🔄 Attach to ALB                                      |
| 1️⃣4️⃣  | 🔍 Review              | Verify Config       | 👀 Check all settings                                 |
| 1️⃣5️⃣  | 🚀 Create ALB          | Launch              | ⚡ Click **Create Load Balancer**                      |
| 1️⃣6️⃣  | ⏳ Provisioning         | Wait                | 🔄 Status: Provisioning → Active                      |
| 1️⃣7️⃣  | 🌐 Test ALB            | Access DNS          | 🔗 Copy DNS → Open in browser                         |
| 1️⃣8️⃣  | ✅ Output               | Verify Traffic      | 🔄 Traffic distributed across EC2                     |

### 🛡️ Security Group Rules (ALB / EC2)
| 🧩 Rule Type     | 🔌 Port | 🌐 Source | 💡 Purpose                  |
| ----------------- | ------- | --------- | ----------------------------- |
| 🌐 HTTP          | 80      | 0.0.0.0/0 | 🌍 Public web access          |
| 🔐 HTTPS         | 443     | 0.0.0.0/0 | 🛡️ Secure (encrypted) access |
| 🖥️ Custom (SSH)  | 22      | Your IP   | 🔑 Admin access (optional)    |
  

---

## ⚡ Network Load Balancer (NLB)

 * Network Load Balancer operates at `Layer 4` (transport layer) and is used for `high-performance`, `low-latency` applications.
 * It supports `TCP and UDP traffic` and provides `static IP` addresses.
 * 🌐 Supports `static IP` addresses and `Elastic IPs`.
 * Use Case Real-time apps:
     * Gaming 🎮
     * Streaming 📺
     * Financial systems 💰 

## ⚖️ Create Network Load Balancer (NLB) – AWS
| 🎯 Step | 🧩 Section             | 📌 Action            | 💡 Details                                                           |
| ------- | ---------------------- | -------------------- | -------------------------------------------------------------------- |
| 1️⃣     | 🌐 AWS Console         | Open EC2 Dashboard   | 🔍 AWS → EC2 → Load Balancers                                        |
| 2️⃣     | ⚖️ Load Balancer Type  | Select NLB           | 🚀 Click **Create Load Balancer** → Choose **Network Load Balancer** |
| 3️⃣     | ⚙️ Basic Config        | Name & Scheme        | 📝 `my-nlb`<br>🌍 Internet-facing / 🔒 Internal                      |
| 4️⃣     | 🌐 IP Settings         | Select IP Type       | IPv4 or 🌍 Dualstack (IPv6)                                          |
| 5️⃣     | 🔗 Listener Config     | Add Listener         | 📡 Protocol: `TCP / UDP / TLS<br>`🔌 Port: `80 / 443`                  |
| 6️⃣     | 🌐 Network Mapping     | Select VPC & Subnets | 📍 Choose VPC + at least 2 AZs                                       |
| 7️⃣     | 🎯 Target Group        | Create Target Group  | 🖥️ Instance / 📦 IP<br>Protocol: TCP<br>Port: 80                    |
| 8️⃣     | ❤️ Health Check        | Configure            | 🔍 TCP, Traffic Port, Interval: 30s                                  |
| 9️⃣     | 📦 Register Targets    | Add EC2 Instances    | ➕ Select instances → Register                                        |
| 🔟      | 🔗 Attach Target Group | Link to NLB          | 🔄 Attach TG to listener                                             |
| 1️⃣1️⃣  | 🔍 Review              | Verify Config        | 👀 Check all settings                                                |
| 1️⃣2️⃣  | 🚀 Create              | Launch NLB           | ⚡ Click **Create Load Balancer**                                     |
| 1️⃣3️⃣  | 🧪 Testing             | Access via DNS       | 🌐 Use NLB DNS (`*.elb.amazonaws.com`)                               |

---

# 🏛️ Classic Load Balancer (CLB)

The previous generation of load balancer. (Older version)  

⚙️ It operates at both Layer 4 (TCP/SSL) and Layer 7 (HTTP/HTTPS).  

📌 Suitable for applications that were built within the EC2-Instances without the need for advanced routing (e.g., path-based or host-based routing)
