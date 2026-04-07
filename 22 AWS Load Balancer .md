# ⚖️ Load Balancer (Elastic Load Balancing - ELB)

A Load Balancer distributes incoming traffic across multiple EC2 instances to ensure high availability and fault tolerance. It helps to ensure that no single instance is overwhelmed with too much traffic.

🔐 ELB Integration with AWS IAM for secure access, and support for SSL/TLS termination (secure communication)

🔄 ELB automatically distributes incoming traffic across multiple targets.

💚 Health checks monitor the status of targets and route traffic only to healthy targets.

🌐 Internet-facing ELB has a public IP, while internal ELB routes traffic within a private VPC.

🚢 AWS ELB helps make Kubernetes services scalable and accessible externally.

📌 Use Service type LoadBalancer to create an ELB automatically.  
📌 Use AWS ALB Ingress Controller for advanced routing (e.g., path-based, host-based)  
📌 Annotations allow customization of ELB behavior (e.g., internal/external, SSL/TLS, health checks)

---

# ☁️ AWS offers different types of Load Balancers:

## 🌐 Application Load Balancer (ALB)

Operates at Layer 7 (application layer). Supports HTTP/HTTPS traffic.  

➡️ Route requests to different target groups based on URL paths (e.g., /api vs. /images).  
➡️ Route traffic based on the requested hostname (e.g., api.example.com vs. app.example.com).  

💡 Ideal for microservices and container-based application  

---

# 🎯 ALB Target Types (Where ALB Routes Traffic)

Target groups receive traffic from the load balancer. Each target group is associated with a specific protocol and port, and the load balancer routes traffic to the targets based on the rules defined in the listener.

- 🖥️ EC2 Instances — Traditional virtual machines.  
- 📦 Containers (ECS, EKS, Fargate) — Routes traffic to containerized applications.  
- ⚡ Lambda Functions — Directly invokes AWS Lambda functions for serverless architectures.  
- 🌍 IP Addresses — Routes to on-premises servers or external services.  

---

# 🚀 Create an Application Load Balancer (ALB) in AWS

🖥️ Go to the EC2 Dashboard.  
➡️ Create an Application Load Balancer.  

⚙️ Configure the load balancer (name, scheme, VPC, Availability Zones, subnets, security groups).  

🎧 Set up listeners (e.g., HTTP or HTTPS (choose a Security Group)) and Select Target Type and groups.  

📌 Register targets and configure health checks.  

✅ Review and create the ALB.  

🔍 Verify the ALB and configure additional features as needed.  

---

# ⚡ Network Load Balancer (NLB)

Operates at Layer 4 (transport layer).  

🚀 Ideal for load balancing TCP, UDP, and TLS traffic.  
⚡ Handles extreme performance with low latency.  

🌐 Supports static IP addresses and Elastic IPs  

---

# 🚀 Create a Network Load Balancer (NLB) in AWS

🖥️ Go to the EC2 Dashboard.  
➡️ Create a Network Load Balancer.  

⚙️ Configure the load balancer (name, scheme, VPC, subnets).  

🎧 Set up listeners and target groups.  

📌 Register targets and configure health checks.  

✅ Review and create the NLB.  

🔍 Verify the NLB and configure additional features as needed.  

---

# 🏛️ Classic Load Balancer (CLB)

The previous generation of load balancer. (Older version)  

⚙️ It operates at both Layer 4 (TCP/SSL) and Layer 7 (HTTP/HTTPS).  

📌 Suitable for applications that were built within the EC2-Instances without the need for advanced routing (e.g., path-based or host-based routing)
