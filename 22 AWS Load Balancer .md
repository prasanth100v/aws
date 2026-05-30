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
 * 📂 Path-based routing : ➡️ Route requests to different target groups based on `URL paths` (e.g., /api → backend`, /web → frontend )
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
```hcl
🔐 Login AWS Console
          ⬇️
📂 Open Load Balancers
          ⬇️
➕ Create ALB
          ⬇️
🌐 Configure VPC & Subnets
          ⬇️
🛡️ Configure Security Groups
          ⬇️
🎯 Create Target Group
          ⬇️
🖥️ Register Targets
          ⬇️
🔗 Attach Target Group
          ⬇️
🚀 Create ALB
          ⬇️
🌍 Test ALB DNS
          ⬇️
✅ Traffic Load Balancing Ready
```

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
```hcl
🔐 Login AWS Console
          ⬇️
⚖️ Select Network Load Balancer
          ⬇️
⚙️ Configure NLB  (📡 Protocol: `TCP / UDP / TLS<br>`🔌 Port: `80 / 443`)
          ⬇️
🌐 Configure VPC & Subnets
          ⬇️
📡 Configure Listener
          ⬇️
🎯 Create Target Group
          ⬇️
❤️ Configure Health Checks
          ⬇️
📦 Register Targets
          ⬇️
🔗 Attach Target Group
          ⬇️
🚀 Click Create NLB
          ⬇️
🌍 Access NLB DNS
          ⬇️
✅ Traffic Distribution Ready (🧪 Testing  -- 🌐 Use NLB DNS (`*.elb.amazonaws.com`) )
```
---

## ⚖️ ALB vs NLB (AWS Load Balancers)
| 🧩 Feature                | 🌐 Application Load Balancer (ALB) | ⚡ Network Load Balancer (NLB)   |
| ------------------------- | ---------------------------------- | ---------------------------------- |
| 🧠 OSI Layer              | Layer 7 (Application)              | Layer 4 (Transport)             |
| 🔗 Protocols              | HTTP, HTTPS, WebSocket, gRPC       | TCP, UDP, TLS                   |
| 🔀 Routing Type           | 🎯 Content-based (URL/Host)        | 📍 Connection-based (IP/Port)   |
| ⚡ Performance             | High                               | 🔥 Ultra-high                   |
| ⏱️ Latency                | Slightly higher                    | ⚡ Very low                      |
| 🌐 Static IP              | ❌ Not supported                    | ✅ Supported (Elastic IP)        |
| 🛡️ Security Groups       | ✅ Supported                        | ❌ Not supported                 |
| 🎯 Use Case               | 🌍 Web apps, microservices         | 🎮 Real-time, gaming, streaming  |
| 🔐 SSL/TLS Termination    | ✅ Yes                              | ✅ Yes                           |
| 📂 Path-based Routing     | ✅ Yes                              | ❌ No                            |
| 🌍 Host-based Routing     | ✅ Yes                              | ❌ No                            |
| 🔌 WebSocket Support      | ✅ Yes                              | ❌ No                            |
| 📡 gRPC Support           | ✅ Yes                              | ❌ No                            |
| ❤️ Health Checks          | HTTP / HTTPS                        | TCP (basic)                       |
| 🎯 Target Types           | Instance, IP, Lambda                | Instance, IP                      |
| 🔍 Source IP Preservation | ❌ Uses X-Forwarded-For             | ✅ Preserves client IP           |
| 🔐 WAF Integration        | ✅ Supported                        | ❌ Not supported                 |

## ⚖️ When to Use ALB vs NLB (Real-World Use Cases)
| 🧩 Category         | 📱 Application Type         | 🌐 Use ALB | ⚡ Use NLB | 💡 Reason                             |
| ------------------- | --------------------------- | ---------- | --------- | ------------------------------------- |
| 🌍 Web Apps         | Static / Dynamic Websites   | ✅          | ❌         | HTTP/HTTPS + content-based routing    |
| 📱 APIs             | REST / GraphQL APIs         | ✅          | ❌         | Path-based routing (`/api`, `/users`) |
| 🧩 Microservices    | EKS / ECS apps              | ✅          | ❌         | Routes traffic to multiple services   |
| 🛒 E-commerce       | Shopping platforms          | ✅          | ❌         | Host + path routing (cart, checkout)  |
| 📊 SaaS             | Multi-tenant apps           | ✅          | ❌         | Domain-based routing                  |
| 🔐 Secure Web Apps  | Apps with WAF               | ✅          | ❌         | WAF integration supported             |
| 🔄 WebSockets       | Real-time web apps          | ✅          | ❌         | Supports WebSocket                    |
| 🎮 Gaming           | Multiplayer servers         | ❌          | ✅         | Ultra-low latency ⚡                   |
| 📡 Streaming        | Video / audio streaming     | ❌          | ✅         | High throughput                       |
| 📶 IoT              | MQTT / device communication | ❌          | ✅         | TCP/UDP protocol support              |
| 💬 Messaging        | Chat applications           | ❌          | ✅         | Persistent TCP connections            |
| 🏦 Finance          | Trading systems             | ❌          | ✅         | Low latency + high performance        |
| 🔌 Custom Protocols | Non-HTTP apps               | ❌          | ✅         | Raw TCP/UDP support                   |

🔥 ALB = Smart web routing 🌐 | NLB = Speed & performance ⚡

## 🏛️ Classic Load Balancer (CLB)
 * Classic Load Balancer is the `legacy load balancer` that supports basic `Layer 4` and `Layer 7` traffic, but it is not recommended for modern applications.
 * `Older generation` of load balancer. (Older version)
 * 📌 Suitable for applications that were built within the `EC2-Instances` without the need for advanced routing (e.g., path-based or host-based routing)

---

## ⚡ AWS Load Balancer (ELB) — Interview Q&A
| #️⃣    | ❓ Interview Question                                          | ✅ Answer                                                                                                                                     |
| ------ | ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 1️⃣    | What is a Load Balancer?                                      | ⚖️ A service that distributes incoming traffic across multiple targets (EC2, ECS, EKS, IPs, Lambda) to improve availability and scalability. |
| 2️⃣    | What is ELB?                                                  | ⚖️ Elastic Load Balancing, an `AWS-managed service for traffic distribution`.                                                                  |
| 3️⃣    | Why use a Load Balancer?                                      | 🚀 High Availability, Scalability, Fault Tolerance, Load Distribution.                                                                       |
| 4️⃣    | What problems does a Load Balancer solve?                     | 🔥 Single Point of Failure, traffic overload, and application downtime.                                                                      |
| 5️⃣    | Is ELB managed by AWS?                                        | ✅ Yes                                                                                                                                        |
| 6️⃣    | Can ELB scale automatically?                                  | ✅ Yes                                                                                                                                        |
| 7️⃣    | Can ELB distribute traffic across multiple AZs?               | ✅ Yes                                                                                                                                        |
| 8️⃣    | Where is ELB commonly used?                                   | 🌐 EC2, ECS, EKS, Lambda, Auto Scaling Groups                                                                                                |
| 9️⃣    | What are the types of AWS Load Balancers?                     | ⚖️ ALB, ⚡ NLB, 🏛️ CLB, 🌍 GWLB                                                                                                              |
| 🔟     | Which Load Balancer is most commonly used today?              | ⚖️ Application Load Balancer (ALB)                                                                                                           |
| 1️⃣1️⃣ | What is ALB?                                                  | ⚖️ Layer 7 Load Balancer for `HTTP/HTTPS traffic`.                                                                                             |
| 1️⃣2️⃣ | OSI Layer for ALB?                                            | 🌐 Layer 7 (Application Layer)                                                                                                               |
| 1️⃣3️⃣ | What protocols does ALB support?                              | 🌍 HTTP, HTTPS, WebSockets, HTTP/2                                                                                                           |
| 1️⃣4️⃣ | What is NLB?                                                  | ⚡ Layer 4 Load Balancer for TCP, UDP, TLS traffic.                                                                                           |
| 1️⃣5️⃣ | OSI Layer for NLB?                                            | 🔌 Layer 4 (Transport Layer)                                                                                                                 |
| 1️⃣6️⃣ | What protocols does NLB support?                              | 🔌 TCP, UDP, TLS                                                                                                                             |
| 1️⃣7️⃣ | What is CLB?                                                  | 🏛️ Classic Load Balancer (legacy ELB).                                                                                                      |
| 1️⃣8️⃣ | Is CLB recommended for new applications?                      | ❌ No                                                                                                                                         |
| 2️⃣0️⃣ | Which Load Balancer supports path-based routing?              | ⚖️ ALB                                                                                                                                       |
| 2️⃣1️⃣ | Which Load Balancer supports host-based routing?              | ⚖️ ALB                                                                                                                                       |
| 2️⃣2️⃣ | Which Load Balancer provides static IP?                       | ⚡ NLB                                                                                                                                        |
| 2️⃣3️⃣ | Which Load Balancer handles millions of requests/sec?         | ⚡ NLB                                                                                                                                        |
| 2️⃣4️⃣ | What is a Target Group?                                       | 🎯 A logical group of targets receiving traffic from the Load Balancer.                                                                      |
| 2️⃣5️⃣ | Supported target types?                                       | 🖥️ EC2, 🌐 IP Address, 🐳 ECS Tasks, ⚡ Lambda                                                                                               |
| 2️⃣6️⃣ | What is a Listener?                                           | 👂 Process that checks for connection requests on a specific port/protocol.                                                                  |
| 2️⃣7️⃣ | Example Listener?                                             | 🌍 HTTP:80 or 🔒 HTTPS:443                                                                                                                   |
| 2️⃣8️⃣ | What is a Listener Rule?                                      | 📜 Defines how traffic should be routed.                                                                                                     |
| 2️⃣9️⃣ | What is Path-Based Routing?                                   | 🛣️ Routes traffic based on URL path.                                                                                                        |
| 3️⃣0️⃣ | Example Path-Based Routing?                                   | `/api → backend`, `/web → frontend`                                                                                                          |
| 3️⃣1️⃣ | What is Host-Based Routing?                                   | 🌐 Routes traffic based on hostname.                                                                                                         |
| 3️⃣2️⃣ | Example Host-Based Routing?                                   | `app.company.com → App`, `api.company.com → API`                                                                                             |
| 3️⃣3️⃣ | What is a Health Check?                                       | ❤️ Mechanism used to determine whether a target is healthy.                                                                                  |
| 3️⃣4️⃣ | Why are Health Checks important?                              | 🚑 Prevent traffic from reaching unhealthy targets.                                                                                          |
| 3️⃣5️⃣ | Common Health Check protocols?                                | 🌍 HTTP, 🔒 HTTPS, ⚡ TCP                                                                                                                     |
| 3️⃣6️⃣ | What happens if Health Check fails?                           | ❌ Target marked unhealthy and removed from traffic rotation.                                                                                 |
| 3️⃣7️⃣ | What happens when target becomes healthy again?               | ✅ Automatically re-added.                                                                                                                    |
| 3️⃣8️⃣ | What is Cross-Zone Load Balancing?                            | 🔄 Distributes traffic evenly across all registered targets in all AZs.                                                                      |
| 3️⃣9️⃣ | Is Cross-Zone enabled by default on ALB?                      | ✅ Yes                                                                                                                                        |
| 4️⃣0️⃣ | Can ALB terminate SSL/TLS?                                    | ✅ Yes                                                                                                                                        |
| 4️⃣1️⃣ | What is SSL Termination?                                      | 🔒 ALB decrypts HTTPS traffic before forwarding.                                                                                             |
| 4️⃣2️⃣ | Which AWS service manages SSL certificates?                   | 🔐 AWS Certificate Manager (ACM)                                                                                                             |
| 4️⃣3️⃣ | Can ALB integrate with ACM?                                   | ✅ Yes                                                                                                                                        |
| 4️⃣4️⃣ | Why terminate SSL at ALB?                                     | 🚀 Simplifies certificate management and reduces backend load.                                                                               |
| 4️⃣5️⃣ | Can ALB redirect HTTP to HTTPS?                               | ✅ Yes                                                                                                                                        |
| 4️⃣6️⃣ | What is Sticky Session?                                       | 🍪 Routes a user to the same backend target repeatedly.                                                                                      |
| 4️⃣7️⃣ | Why use Sticky Sessions?                                      | 👤 Session persistence.                                                                                                                      |
| 4️⃣8️⃣ | Does ALB support Sticky Sessions?                             | ✅ Yes                                                                                                                                        |
| 4️⃣9️⃣ | Does NLB support Sticky Sessions?                             | ✅ Yes (source IP affinity)                                                                                                                   |
| 5️⃣0️⃣ | Can ELB work with Auto Scaling?                               | ✅ Yes                                                                                                                                        |
| 5️⃣1️⃣ | Why integrate ELB with AWS Auto Scaling Group (ASG)?           | 🚀 Automatically distribute traffic to new instances.                                                                                        |
| 5️⃣2️⃣ | What happens when new EC2 launches in ASG?                    | 🎯 Automatically registered with Target Group.                                                                                               |
| 5️⃣3️⃣ | What happens when EC2 terminates?                             | 🗑️ Automatically deregistered.                                                                                                              |
| 5️⃣4️⃣ | Can ECS services use ALB?                                     | ✅ Yes                                                                                                                                        |
| 5️⃣5️⃣ | Can EKS use ALB?                                              | ✅ Yes via AWS Load Balancer Controller                                                                                                       |
| 5️⃣6️⃣ | Which Load Balancer is commonly used with Kubernetes Ingress? | ⚖️ ALB                                                                                                                                       |
| 5️⃣7️⃣ | Can Lambda be a Target Group target?                          | ✅ Yes (ALB only)                                                                                                                             |
| 5️⃣8️⃣ | What security feature protects ALB?                           | 🛡️ AWS WAF                                                                                                                                  |
| 5️⃣9️⃣ | Can WAF attach to NLB?                                        | ❌ No                                                                                                                                         |
| 6️⃣0️⃣ | Can WAF attach to ALB?                                        | ✅ Yes                                                                                                                                        |
| 6️⃣1️⃣ | What AWS service protects ELB from DDoS attacks?              | 🛡️ AWS Shield                                                                                                                               |
| 6️⃣2️⃣ | Which Shield version is free?                                 | 🛡️ Shield Standard                                                                                                                          |
| 6️⃣3️⃣ | How monitor Load Balancer performance?                        | 📊 Amazon CloudWatch                                                                                                                         |
| 6️⃣4️⃣ | Important ELB metrics?                                        | 📈 RequestCount, HealthyHostCount, UnHealthyHostCount, Latency                                                                               |
| 6️⃣5️⃣ | What is TargetResponseTime?                                   | ⏱️ Time target takes to respond.                                                                                                             |
| 6️⃣6️⃣ | Users getting intermittent errors. First check?               | ❤️ Target Group Health Checks                                                                                                                |
| 6️⃣7️⃣ | ALB shows unhealthy targets. Checks?                          | 🔍 Security Groups, health check path, application status.                                                                                   |
| 6️⃣8️⃣ | Health Check returns 404. Result?                             | ❌ Target unhealthy.                                                                                                                          |
| 6️⃣9️⃣ | Users can access EC2 directly but not through ALB. Why?       | 🔍 Listener, Target Group, Security Group issue.                                                                                             |
| 7️⃣0️⃣ | ALB created but DNS not working. Checks?                      | 🌐 Route 53 Alias Record, DNS propagation.                                                                                                   |
| 7️⃣1️⃣ | ECS service unhealthy behind ALB. Checks?                     | 🐳 Container port mapping, health checks, SG rules.                                                                                          |
| 7️⃣2️⃣ | NLB used instead of ALB. Why?                                 | ⚡ High performance TCP/UDP workloads.                                                                                                        |
| 7️⃣3️⃣ | Which LB for REST APIs?                                       | ⚖️ ALB                                                                                                                                       |
| 7️⃣4️⃣ | Which LB for Web Applications?                                | ⚖️ ALB                                                                                                                                       |
| 7️⃣5️⃣ | Which LB for gaming or VoIP traffic?                          | ⚡ NLB                                                                                                                                        |
| 7️⃣7️⃣ | Which LB supports WebSockets?                                 | ⚖️ ALB                                                                                                                                       |
| 7️⃣8️⃣ | Which LB supports static IPs?                                 | ⚡ NLB                                                                                                                                        |
| 7️⃣9️⃣ | Can one ALB serve multiple applications?                      | ✅ Yes using host/path routing.                                                                                                               |
| 8️⃣0️⃣ | What is deregistration delay?                                 | ⏳ Time ELB waits before removing connections from a target.                                                                                  |
| 8️⃣1️⃣ | Why use deregistration delay?                                 | 🚀 Graceful shutdowns.                                                                                                                       |
| 8️⃣2️⃣ | What is connection draining?                                  | 🔄 Allowing existing requests to finish before target removal.                                                                               |
| 8️⃣3️⃣ | Common ALB production architecture?                           | 🌍 Route 53 → ALB → ECS/EKS/EC2 → RDS                                                                                                        |
| 8️⃣4️⃣ | Best practice for production ALB?                             | 🌐 Deploy across multiple AZs.                                                                                                               |
| 8️⃣5️⃣ | Best practice for security?                                   | 🛡️ WAF + Shield + HTTPS + ACM                                                                                                               |
| 8️⃣6️⃣ | Best practice for scaling?                                    | 🚀 ALB + Auto Scaling Group                                                                                                                  |
| 8️⃣7️⃣ | Most common ALB issue?                                        | 🚨 Incorrect health check path.                                                                                                              |
| 8️⃣8️⃣ | Most common NLB issue?                                        | 🚨 Wrong target port or SG configuration.                                                                                                    |
| 8️⃣9️⃣ | Interview Gold: ALB in one line?                              | ⚖️ Layer 7 Load Balancer for intelligent HTTP/HTTPS routing.                                                                                 |
| 9️⃣0️⃣ | Interview Gold: NLB in one line?                              | ⚡ High-performance Layer 4 Load Balancer for TCP/UDP traffic.                                                                                |
| 9️⃣1️⃣ | Interview Gold: Why use ELB?                                  | 🚀 To improve availability, scalability, fault tolerance, and performance by distributing traffic across multiple targets.                   |
