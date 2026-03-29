# 📦 Amazon ECR (Elastic Container Registry) – Complete Guide
## 🌟 What is Amazon ECR?

**Amazon Elastic Container Registry (ECR)** is a fully managed Docker container registry that allows you to **store, manage, and deploy container images** securely on AWS.

👉 It integrates seamlessly with services like:
- 🚀 ECS (Elastic Container Service)
- ☸️ EKS (Elastic Kubernetes Service)
- ⚡ Fargate

This makes deploying containerized applications simple and efficient.

---

## 🔐 Public vs Private Repositories

Amazon ECR supports two types of repositories:

### 🌍 Public Repositories
- Anyone can **pull images**
- No authentication required
- Ideal for open-source images

---

### 🔒 Private Repositories
- Access controlled using **IAM policies**
- Secure storage for internal applications
- Only authorized users can access

---

## 🎯 Key Benefits of Amazon ECR
| 🧩 Feature                 | 💡 Description                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------ |
| ✨ Fully Managed & Scalable | ☁️ No infrastructure to manage — AWS handles scaling automatically (AWS handles everything) |
| 🔐 Secure by Default       | 🛡️ IAM-based access control + Image vulnerability scanning             |
| 🔗 AWS Integration         | ⚙️ Works seamlessly with ECS, EKS, and Fargate            |
| 📦 Flexible Repositories   | 🌐 Supports both public & private container registries         |
| 🧹 Lifecycle Policies      | 🗑️ Auto-delete old/unused images → reduces cost            |
| 🛡️ Image Scanning         | 🔍 Detects vulnerabilities in container images for better security           |


---

## 💾 Storage & Pricing

- Uses **Amazon S3** for storing container images  
- Ensures **high durability and availability**

💰 Pricing is based on:
- Storage usage  
- Data transfer  
- Optional image scanning  

---

## 🏷️ Image Tagging

Tags help:
- Version images (e.g., `v1`, `latest`)
- Identify specific builds
- Manage deployments easily

---

# 🛠️ Step-by-Step: Create ECR Repository

---

## 🏗️ 1. Create a Repository

1. Open **Amazon ECR Dashboard**
2. Click **"Create repository"**
3. Enter repository name  
   👉 Example: `my-app-repo`

---

### ⚙️ Optional Settings

- 🔒 **Tag Immutability**
  - Mutable → tags can be overwritten  
  - Immutable → prevents overwriting  

- 🛡️ **Scan on Push**
  - Automatically scans images for vulnerabilities  

- 🔐 **KMS Encryption**
  - Encrypt repository using AWS KMS  

---

👉 Click **Create Repository**

🎉 Your repository is ready!

---

# 🔑 Authenticate Docker with ECR
### How ECR Works (Flow)
🔄 Workflow:

1️⃣ Build Docker image locally
2️⃣ Tag the image
3️⃣ Push → ECR
4️⃣ ECS/EKS pulls image
5️⃣ Container runs 🚀

Use the following command:

```bash
aws ecr get-login-password --region <region> | docker login \
--username AWS \
--password-stdin <aws_account_id>.dkr.ecr.<region>.amazonaws.com
```
### 🐳 3. Build and Tag Docker Image

```
docker build -t my-app-image .                                           # 🔨 Build Image

docker tag my-app-image:latest \                                         # 🏷️ Tag Image
<aws_account_id>.dkr.ecr.<region>.amazonaws.com/my-app-repo:latest
```
### 🚀 4. Push Image to ECR
```
docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:<tag>
```
### 📥 5. Pull Image from ECR
```
docker pull <aws_account_id>.dkr.ecr.<region>.amazonaws.com/my-app:latest
```
## 🎯 Summary
 * 📦 ECR = Secure Docker image registry on AWS
 * 🔐 Supports IAM-based access
 * 🌍 Public & Private repositories
 * 🧹 Lifecycle policies reduce storage cost
 * 🛡️ Image scanning improves security
 * ⚡ Seamless integration with ECS, EKS, Fargate

### 💡 Amazon ECR is the backbone of container image management in AWS, making deployments faster, safer, and scalable.

