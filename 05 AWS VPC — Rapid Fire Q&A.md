## ⚡ AWS VPC — Rapid Fire Q&A

| 🔢 Q#   | ❓ Question                       | 💡 Answer                                                                        |
| ------- | ----------------------------------- | -------------------------------------------------------------------------------- |
| 🔹 Q1   | What is a VPC?                     | 👉 Amazon Web Services Virtual Private Cloud — an isolated network in the cloud. |
| 🔹 Q2   | Default CIDR block example?        | 👉 10.0.0.0/16                                                                   |
| 🔹 Q3   | What is CIDR?                      | 👉 Classless Inter-Domain Routing — defines IP range.                            |
| 🌐 Q4   | What is a subnet?                  | 👉 A segment of VPC IP range.                                                    |
| 🌐 Q5   | Types of subnets?                  | 👉 Public and Private                                                            |
| 🌐 Q6   | What makes a subnet public?        | 👉 Route to Internet Gateway.                                                    |
| 🌐 Q7   | What makes a subnet private?       | 👉 No direct internet route.                                                     |
| 🌍 Q8   | What is an Internet Gateway (IGW)? | 👉 Enables internet access for VPC.                                              |
| 🌍 Q9   | What is a NAT Gateway?             | 👉 Allows private subnet instances to access internet (outbound only).           |
| 🌍 Q10  | NAT Gateway vs NAT Instance?       | 👉 Gateway = managed, Instance = EC2-based.                                      |
| 🧭 Q11  | What is a Route Table?             | 👉 Defines traffic routes.                                                       |
| 🧭 Q12  | Default route for internet?        | 👉 0.0.0.0/0                                                                     |
| 🔐 Q13  | What is Security Group?            | 👉 Stateful firewall at instance level.                                          |
| 🔐 Q14  | What is NACL?                      | 👉 Network ACL — stateless firewall at subnet level.                             |
| 🔐 Q15  | Difference?                        | 👉 SG = stateful, NACL = stateless.                                              |
| 🔗 Q16  | What is VPC Peering?               | 👉 Connect two VPCs privately.                                                   |
| 🔗 Q17  | What is AWS Transit Gateway?       | 👉 Hub to connect multiple VPCs.                                                 |
| 🔗 Q18  | What is VPN?                       | 👉 Secure connection from on-prem to VPC.                                        |
| 🔗 Q19  | What is Direct Connect?            | 👉 Dedicated private link to AWS.                                                |
| 🌐 Q20  | Does VPC support DNS?              | 👉 ✅ Yes                                                                       |
| 🌐 Q21  | What is Route 53?                  | 👉 Amazon Route 53 AWS DNS service.                                              |
| 🏢 Q22  | What is an Availability Zone?      | 👉 Separate data center within a region.                                         |
| 🏢 Q23  | Best practice for HA?              | 👉 Use multiple AZs.                                                             |
| 📌 Q24  | What is Elastic IP?                | 👉 Static public IP.                                                             |
| 📌 Q25  | What is ENI?                       | 👉 Elastic Network Interface.                                                    |
| 📊 Q26  | What is VPC Flow Logs?             | 👉 Captures network traffic logs.                                                |
| ☸️ Q27  | How does EKS use VPC?              | 👉 Pods and nodes run inside VPC.                                                |
| ☸️ Q28  | What is AWS CNI?                   | 👉 Assigns VPC IPs to pods.                                                      |
| 🛠️ Q29 | Instance not reachable?             | 👉 Check: Security Group, NACL, Route Table, IGW                                 |
| 🛠️ Q30 | No internet from private subnet?    | 👉 Check NAT Gateway.                                                            |
| 🎯 Q31  | Why use private subnet?            | 👉 Security for backend services.                                                |
| 🎯 Q32  | How to design secure architecture? | 👉 Public (ALB) + Private (App + DB).                                            |
| 🎯 Q33  | Why multi-AZ deployment?           | 👉 Fault tolerance.                                                              |
