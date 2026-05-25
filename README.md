## 🔹 AWS Glossary
| 🌟 **Term**                   | 📝 **Full Form**               | 📘 **Clear Explanation**                                                      | 💡 **Example / Use Case**    |
| ----------------------------- | ------------------------------ | ----------------------------------------------------------------------------- | ---------------------------- |
| ☁️ **AWS**                    | Amazon Web Services            | Cloud platform providing servers, storage, databases, networking, etc.        | Hosting a website or app     |
| 🌍 **Region**                 | —                              | Geographical area where AWS data centers are located                          | Mumbai (`ap-south-1`)        |
| 🏢 **Availability Zone (AZ)** | —                              | Isolated data centers inside a Region for high availability & fault tolerance | `ap-south-1a`                |
| 🔐 **VPC**                    | Virtual Private Cloud          | Your own private network inside AWS                                           | Private cloud for your app   |
| 🧩 **Subnet**                 | —                              | Smaller network inside a VPC                                                  | Public & Private subnets     |
| 🌐 **Internet Gateway**       | —                              | Allows internet access to VPC resources                                       | EC2 public access            |
| 🚪 **NAT Gateway**            | —                              | Allows private subnet servers to access the internet                          | Private EC2 updates          |
| 🛣️ **Route Table**           | —                              | Controls traffic routing inside VPC                                           | Internet routing             |
| 🛡️ **Security Group**        | —                              | Virtual firewall for EC2 (instance-level)                                     | Allow port 22, 80            |
| 🚫 **NACL**                   | Network Access Control List    | Firewall at subnet level                                                      | Block specific IPs           |
| 🖥️ **EC2**                   | Elastic Compute Cloud          | Virtual server in AWS                                                         | Run applications             |
| 📀 **AMI**                    | Amazon Machine Image           | Template for creating EC2 instances                                           | OS + software                |
| ⚙️ **Instance Type**          | —                              | Defines CPU, RAM, and network capacity                                        | `t2.micro`                   |
| 📈 **Auto Scaling**           | —                              | Automatically adds/removes EC2 instances                                      | Handle traffic spikes        |
| ⚖️ **ELB**                    | Elastic Load Balancer          | Distributes traffic across servers                                            | High availability            |
| 🌐 **ALB**                    | Application Load Balancer      | Load balances HTTP/HTTPS traffic                                              | Web applications             |
| 🚀 **NLB**                    | Network Load Balancer          | Handles high-speed TCP traffic                                                | Gaming, real-time apps       |
| 🪣 **S3**                     | Simple Storage Service         | Object storage for files                                                      | Store images, backups        |
| 📦 **Bucket**                 | —                              | Container for storing objects in S3                                           | `my-app-data`                |
| 📄 **Object**                 | —                              | File stored in S3                                                             | `image.jpg`                  |
| 💽 **EBS**                    | Elastic Block Store            | Disk storage for EC2                                                          | Root volume                  |
| 📂 **EFS**                    | Elastic File System            | Shared file system                                                            | Multiple EC2 access          |
| 🗄️ **RDS**                   | Relational Database Service    | Managed relational databases                                                  | MySQL, PostgreSQL            |
| ⚡ **DynamoDB**                | —                              | NoSQL key-value database                                                      | High-speed apps              |
| 👤 **IAM**                    | Identity and Access Management | Manages users, roles & permissions                                            | Secure access                |
| 👨‍💻 **IAM User**            | —                              | A person using AWS                                                            | Developer login              |
| 🎭 **IAM Role**               | —                              | Permission set for AWS services                                               | EC2 access to S3             |
| 📜 **Policy**                 | —                              | Rules defining permissions                                                    | Allow S3 read                |
| 📊 **CloudWatch**             | —                              | Monitoring and logging service                                                | CPU usage alert              |
| 🕵️ **CloudTrail**            | —                              | Tracks AWS API activity                                                       | Security auditing            |
| 📢 **SNS**                    | Simple Notification Service    | Sends notifications                                                           | SMS, email alerts            |
| 📨 **SQS**                    | Simple Queue Service           | Message queue service                                                         | Decouple services            |
| ⚡ **Lambda**                  | —                              | Serverless function service                                                   | Run code without servers     |
| 🔌 **API Gateway**            | —                              | Create and manage APIs                                                        | Backend for apps             |
| 🌱 **Elastic Beanstalk**      | —                              | Easy application deployment service                                           | Deploy Java/Python apps      |
| 📜 **CloudFormation**         | —                              | Infrastructure as Code (IaC) using templates                                  | Create infrastructure stacks |
| 💻 **CDK**                    | Cloud Development Kit          | Infrastructure as Code using programming languages                            | Python/TypeScript            |
| 🌍 **Route 53**               | —                              | DNS service                                                                   | Domain routing               |
| 🔑 **KMS**                    | Key Management Service         | Encryption key management service                                             | Secure data                  |
| 🛡️ **WAF**                   | Web Application Firewall       | Protects web applications                                                     | Block SQL injection          |
| 🛑 **Shield**                 | —                              | DDoS protection service                                                       | Attack prevention            |


## ⭐ AWS Glossary for Interviews
| 🌟 **Term**                        | 📘 **Interview-Ready Explanation**                                                      |
| ---------------------------------- | --------------------------------------------------------------------------------------- |
| ☁️ **AWS**                         | A cloud platform providing on-demand compute, storage, networking, and managed services |
| 🌍 **Region**                      | A physical geographic location where AWS data centers are hosted                        |
| 🏢 **Availability Zone (AZ)**      | An isolated data center within a Region for high availability and fault tolerance       |
| 🔐 **VPC**                         | A logically isolated virtual network in AWS                                             |
| 🧩 **Subnet**                      | A range of IP addresses inside a VPC                                                    |
| 🌐 **Public Subnet**               | Subnet with internet access via Internet Gateway                                        |
| 🔒 **Private Subnet**              | Subnet without direct internet access                                                   |
| 🚪 **Internet Gateway**            | Allows resources in a VPC to connect to the internet                                    |
| 🔄 **NAT Gateway**                 | Enables private subnet instances to access the internet securely                        |
| 🛣️ **Route Table**                | Controls traffic routing in a VPC                                                       |
| 🛡️ **Security Group**             | Instance-level firewall that controls inbound and outbound traffic                      |
| 🚫 **NACL**                        | Subnet-level firewall that allows or denies traffic                                     |
| 🖥️ **EC2**                        | Virtual server in AWS                                                                   |
| 📀 **AMI**                         | Template used to launch EC2 instances                                                   |
| ⚙️ **Instance Type**               | Defines CPU, memory, and network capacity of EC2                                        |
| 📈 **Auto Scaling**                | Automatically adjusts EC2 count based on demand                                         |
| ⚖️ **Elastic Load Balancer (ELB)** | Distributes traffic across multiple instances                                           |
| 🌐 **ALB**                         | Layer 7 load balancer for HTTP/HTTPS traffic                                            |
| 🚀 **NLB**                         | Layer 4 load balancer for high-performance TCP/UDP traffic                              |
| 🪣 **S3**                          | Object storage service with high durability                                             |
| 📦 **S3 Bucket**                   | Container for storing objects in S3                                                     |
| 📄 **S3 Object**                   | File stored inside a bucket                                                             |
| 💽 **EBS**                         | Block storage for EC2                                                                   |
| 📂 **EFS**                         | Shared file storage for multiple EC2 instances                                          |
| 🗄️ **RDS**                        | Managed relational database service                                                     |
| ⚡ **DynamoDB**                     | Fully managed NoSQL key-value database                                                 |
| 👤 **IAM**                         | Manages users, roles, and permissions                                                   |
| 👨‍💻 **IAM User**                 | Individual AWS identity                                                                   |
| 🎭 **IAM Role**                    | Temporary permission set for AWS services                                               |
| 📜 **IAM Policy**                  | JSON document defining permissions                                                      |
| 📊 **CloudWatch**                  | Monitoring and logging service                                                          |
| 🕵️ **CloudTrail**                 | Records AWS API activity for auditing                                                   |
| 📢 **SNS**                         | Push notification service                                                               |
| 📨 **SQS**                         | Message queue for decoupling applications                                               |
| ⚡ **Lambda**                       | Serverless compute service                                                              |
| 🔌 **API Gateway**                 | Manages and exposes APIs                                                                |
| 🌱 **Elastic Beanstalk**           | Platform to deploy applications easily                                                  |
| 📜 **CloudFormation**              | Infrastructure as Code using templates                                                  |
| 💻 **CDK**                         | Infrastructure as Code using programming languages                                      |
| 🌍 **Route 53**                    | Scalable DNS and domain management service                                              |
| 🔑 **KMS**                         | Encryption key management service                                                       |
| 🛡️ **WAF**                        | Web application firewall                                                                |
| 🛑 **Shield**                      | DDoS protection service                                                                 |
| 🤝 **Shared Responsibility Model** | AWS secures the cloud; customer secures what’s in the cloud                             |
| 🎓 **Free Tier**                   | Limited free usage for learning AWS                                                     |
