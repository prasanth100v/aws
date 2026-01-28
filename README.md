## 🔹 AWS Glossary
| **Term**                    | **Full Form**                  | **Clear Explanation**                                                      | **Example / Use Case**     |
| --------------------------- | ------------------------------ | -------------------------------------------------------------------------- | -------------------------- |
| AWS                         | Amazon Web Services            | Cloud platform that provides servers, storage, databases, networking, etc. | Hosting a website or app   |
| Region                      | —                              | A geographical area where AWS data centers are located                     | Mumbai (`ap-south-1`)      |
| Availability Zone (AZ)      | —                              | Isolated data centers inside a Region for high availability  and fault tolerance | ap-south-1a      |
| VPC                         | Virtual Private Cloud          | Your own private network inside AWS                                        | Private cloud for your app |
| Subnet                      | —                              | A smaller network inside a VPC                                             | Public & Private subnets   |
| Internet Gateway            | —                              | Allows internet access to VPC resources                                    | EC2 public access          |
| NAT Gateway                 | —                              | Allows private subnet servers to access the internet                       | Private EC2 updates        |
| Route Table                 | —                              | Controls traffic routing inside VPC                                        | Internet routing           |
| Security Group              | —                              | Virtual firewall for EC2 (instance-level)                                  | Allow port 22, 80          |
| NACL                        | Network Access Control List    | Firewall at subnet level                                                   | Block specific IPs         |
| EC2                         | Elastic Compute Cloud          | Virtual server in AWS                                                      | Run applications           |
| AMI                         | Amazon Machine Image           | Template for creating EC2 instances                                        | OS + software              |
| Instance Type               | —                              | Defines CPU, RAM, network capacity                                         | t2.micro                   |
| Auto Scaling                | —                              | Automatically adds/removes EC2 instances                                   | Handle traffic spikes      |
| ELB                         | Elastic Load Balancer          | Distributes traffic across servers                                         | High availability          |
| ALB                         | Application Load Balancer      | Load balances HTTP/HTTPS traffic                                           | Web applications           |
| NLB                         | Network Load Balancer          | Handles high-speed TCP traffic                                             | Gaming, real-time apps     |
| S3                          | Simple Storage Service         | Object storage for files                                                   | Store images, backups      |
| Bucket                      | —                              | Container for storing objects in S3                                        | my-app-data                |
| Object                      | —                              | File stored in S3                                                          | image.jpg                  |
| EBS                         | Elastic Block Store            | Disk storage for EC2                                                       | Root volume                |
| EFS                         | Elastic File System            | Shared file system                                                         | Multiple EC2 access        |
| RDS                         | Relational Database Service    | Managed relational databases                                               | MySQL, PostgreSQL          |
| DynamoDB                    | —                              | NoSQL key-value database                                                   | High-speed apps            |
| IAM                         | Identity and Access Management | Manages users, roles & permissions                                         | Secure access              |
| IAM User                    | —                              | A person using AWS                                                         | Developer login            |
| IAM Role                    | —                              | Permission set for AWS services                                            | EC2 access to S3           |
| Policy                      | —                              | Rules defining permissions                                                 | Allow S3 read              |
| CloudWatch                  | —                              | Monitoring and logging service                                             | CPU usage alert            |
| CloudTrail                  | —                              | Tracks AWS API activity                                                    | Security auditing          |
| SNS                         | Simple Notification Service    | Sends notifications                                                        | SMS, email alerts          |
| SQS                         | Simple Queue Service           | Message queue service                                                      | Decouple services          |
| Lambda                      | —                              | Serverless function service                                                | Run code without servers   |
| API Gateway                 | —                              | Create and manage APIs                                                     | Backend for apps           |
| Elastic Beanstalk           | —                              | Easy app deployment service                                                | Deploy Java/Python apps    |
| CloudFormation              | —                              | Infrastructure as Code (IaC) using templates                             | Create infrastructure stacks |
| CDK                         | Cloud Development Kit          | Infrastructure as Code using programming languages                         | Python/TypeScript          |
| Route 53                    | —                              | DNS service                                                                | Domain routing             |
| KMS                         | Key Management Service         |  Encryption key management service                                         | Secure data                |
| WAF                         | Web Application Firewall       | Protects web apps                                                          | Block SQL injection        |
| Shield                      | —                              | DDoS protection service                                                    | Attack prevention          |

