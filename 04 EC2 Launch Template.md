# 🚀 AWS EC2 Launch Template
## 🧩 What is an EC2 Launch Template?

An **EC2 Launch Template** is a **pre-configured blueprint** used to launch EC2 instances.

👉 It defines all required configuration settings in one place.

## 📦 What Does It Include?
A Launch Template contains:

- 🖥️ AMI (Amazon Machine Image)
- ⚙️ Instance Type (t2.micro, m5, etc.)
- 🔑 Key Pair (SSH access)
- 🔐 Security Groups (firewall rules)
- 🌐 Network Settings (VPC, Subnet)
- 💾 Storage (EBS volumes)
- 🧠 IAM Roles (permissions)
- 📜 User Data (startup scripts)

## ✨ Key Features

- 🔢 **Versioning Support** → Maintain multiple template versions
- 🔁 **Reusable Configuration** → Launch multiple identical instances
- ⚡ **Automation Ready** → Used in Auto Scaling Groups
- 🔄 **Flexible Updates** → Modify without affecting running instances

---

## ⚠️ Important Note

> Deleting a Launch Template ❌ does NOT terminate running instances created from it.

## 🏗️ Why Use Launch Templates?

- ⚡ Faster deployments
- 🔁 Consistency across environments
- 🤖 Perfect for automation (Auto Scaling)
- 🛠️ Easy to manage configurations

---

## 🛠️ Steps to Create a Launch Template

### 1️⃣ Open EC2 Dashboard
- Login to AWS Console
- Navigate to EC2 Service

### 2️⃣ Go to Launch Templates
- Left menu → Click **Launch Templates**

### 3️⃣ Create Template
- Click **Create launch template**
- Enter:
  - Name
  - Description

---

### 4️⃣ Configure Settings

#### 🖥️ AMI ID
- Select OS (Amazon Linux, Ubuntu, etc.)

#### ⚙️ Instance Type
- Example: t2.micro (Free Tier)

#### 🔑 Key Pair
- Select or create key pair for SSH

#### 🌐 Network Settings
- Choose:
  - VPC
  - Subnet
  - Security Groups

#### 💾 Storage
- Configure:
  - Root volume
  - Additional EBS volumes

#### 🧠 Advanced Settings
- IAM Role
- User Data (startup scripts)
- Monitoring & shutdown behavior

### 5️⃣ Create Template
- Click **Create launch template**

---

## 🚀 Launch EC2 Instance Using Launch Template

### Step-by-Step
```
1. Go to **EC2 Console**
2. Click **Launch Templates**
3. Select your template
4. Click **Launch instance from template**
5. Choose:
   - Default version OR specific version
6. Review settings
7. Click **Launch**
```
---

## 🔄 Launch Template vs Launch Configuration

| Feature | Launch Template | Launch Configuration |
|--------|----------------|---------------------|
| Versioning | ✅ Yes | ❌ No |
| Flexibility | High | Limited |
| Recommended | ✅ Yes | ❌ Deprecated |

---

## 🎯 Real-World Use Case

- Auto Scaling Group uses Launch Template
- Automatically launches instances during:
  - High traffic 📈
  - Failures 🔁

## 🔥 Pro Tips

- Always use **latest version** in Auto Scaling
- Use **User Data** to automate app setup
- Combine with **Load Balancer** for high availability

## 🎯 Summary

- Launch Template = Blueprint for EC2
- Saves time & ensures consistency
- Supports versioning & automation
- Essential for Auto Scaling

---

🚀 **Master Launch Templates → Build scalable & automated AWS systems!**

