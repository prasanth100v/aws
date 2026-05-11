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


## ⚡ Subnets in AWS VPC — Rapid Fire Q&A

| 🔢 Q#   | ❓ Question                                        | 💡 Answer                                                                                                                                                                                           |
| ------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔹 Q1   | What is a subnet in AWS?                           | 👉 A logical subdivision of a Amazon Web Services VPC IP range.                                                                                                                                     |
| 🔹 Q2   | Why do we use subnets?                             | 👉 To organize, isolate, and secure resources within a VPC.                                                                                                                                         |
| 🔹 Q3   | Are subnets region-specific?                       | 👉 ❌ No — they are Availability Zone–specific.                                                                                                                                                      |
| 🌐 Q4   | Types of subnets?                                  | 👉 Public and Private                                                                                                                                                                               |
| 🌐 Q5   | What is a public subnet?                           | 👉 Subnet with route to Internet Gateway (IGW).                                                                                                                                                     |
| 🌐 Q6   | What is a private subnet?                          | 👉 No direct route to internet.                                                                                                                                                                     |
| 🌍 Q7   | How do instances in public subnet access internet? | 👉 Via Internet Gateway + public IP.                                                                                                                                                                |
| 🌍 Q8   | How do private subnet instances access internet?   | 👉 Via NAT Gateway (outbound only).                                                                                                                                                                 |
| 🌍 Q9   | Can private subnet have inbound internet access?   | 👉 ❌ No (by design).                                                                                                                                                                                |
| 📐 Q10  | How is subnet CIDR defined?                        | 👉 Subset of VPC CIDR block.                                                                                                                                                                        |
| 📐 Q11  | Example?                                           | 👉 VPC: 10.0.0.0/16 → Subnet: 10.0.1.0/24                                                                                                                                                           |
| 📐 Q12  | Reserved IPs in subnet?                            | 👉 5 IPs reserved by AWS.                                                                                                                                                                           |
| 🧭 Q13  | What determines subnet behavior?                   | 👉 Route table association.                                                                                                                                                                         |
| 🧭 Q14  | Can multiple subnets share a route table?          | 👉 ✅ Yes                                                                                                                                                                                            |
| 🔐 Q15  | Subnet-level security?                             | 👉 Network ACL (NACL)                                                                                                                                                                               |
| 🔐 Q16  | Instance-level security?                           | 👉 Security Groups                                                                                                                                                                                  |
| 🏢 Q17  | Can a subnet span multiple AZs?                    | 👉 ❌ No                                                                                                                                                                                             |
| 🏢 Q18  | Why create subnets in multiple AZs?                | 👉 High availability.                                                                                                                                                                               |
| ☸️ Q19  | Why multiple subnets in EKS?                       | 👉 For high availability across AZs.                                                                                                                                                                |
| ☸️ Q20  | Public vs private subnets in EKS?                  | 👉 Public = Load Balancers <br> 👉 Private = Worker nodes                                                                                                                                           |
| ⚙️ Q21  | What is subnet auto-assign public IP?              | 👉 Automatically assigns public IP to instances.                                                                                                                                                    |
| ⚙️ Q22  | What is route propagation?                         | 👉 Dynamic routing updates (VPN/Direct Connect).                                                                                                                                                    |
| 🛠️ Q23 | Instance not reachable?                             | 👉 Check: Route table, IGW/NAT, Security Group, NACL                                                                                                                                                |
| 🛠️ Q24 | No internet from private subnet?                    | 👉 Check NAT Gateway + route.                                                                                                                                                                       |
| 🏗️ Q25 | Typical 3-tier architecture subnets?                | 👉 Public → Load Balancer <br> Private → App servers <br> Private → Database                                                                                                                        |
| 🎯 Q26  | How to make subnet public?                         | 👉 Attach route table with IGW route.                                                                                                                                                               |
| 🎯 Q27  | Why not place DB in public subnet?                 | 👉 Security risk.                                                                                                                                                                                   |
| 🎯 Q28  | Can a subnet be both public & private?             | 👉 ❌ No — depends on route table.                                                                                                                                                                   |
| 🔥 Q29  | Pro Tips (Interview Gold)                          | ✔ Always use private subnets for backend & DB <br> ✔ Use NAT Gateway for outbound internet <br> ✔ Design across multiple AZs <br> ✔ Keep public exposure minimal <br> ✔ Use proper CIDR planning |


