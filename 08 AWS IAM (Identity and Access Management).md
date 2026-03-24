# 🔐 AWS IAM (Identity and Access Management)
## 🧠 What is IAM?
AWS IAM (Identity and Access Management) enables you to control:

👉 **Who (Users) → Can access → What (Resources) → Under what conditions (Permissions)**

- IAM is a **FREE service**
- 💰 You only pay for AWS resources used

### 🎯 IAM = Control access to AWS resources securely
```
🔄 IAM Flow :  User 👤 → Authenticated 🔑 → Policy Check 📜 → Access Granted ✅
```
---

## 🔐 Core Concepts
### 🛡️ Secure Access Control
- Ensures only authorized users can access AWS resources

### 🧾 Authentication & Authorization
| Concept           | Meaning          |
| ----------------- | ---------------- |
| Authentication 🔑 | Who you are     |
| Authorization 🛡️ | What you can do? |


## 👥 IAM Components
### 👤 Users
- Individual identities
- Have Long-term (permanent) credentials (password / access keys)

### 👨‍👩‍👧 Groups
- Collection of users  (Dev team, Admin team)
- Share common permissions

### 🤖 Roles
- Temporary access
- Used by AWS services or external users
- Max session duration: **12 hours**
🎯 If AWS service talks to another → Use IAM Role

### 📜 Policies
- JSON-based permission rules
- Define allowed/denied actions
#### 📌 Example Policy
```
{
  "Effect": "Allow",                     # JSON document defining permissions
  "Action": "s3:ListBucket",
  "Resource": "*"
}
```
## 🔐 Types of Policies
### 📦 Managed Policies
- Reusable
- Created by: AWS (predefined) or Users

### 📌 Inline Policies
- Attached to one entity
- ❌ Not reusable

🎯 Managed policies are reusable; inline policies are specific to one entity.

---

## 🔑 IAM Features

### 🔐 Multi-Factor Authentication (MFA)
📘 What is MFA?

Adds extra security layer:
- Password 🔑
  - OTP / Code 📱
- 🎯 Benefit :  Protects against unauthorized access

### ⚖️ Least Privilege
- Grant minimum permissions needed

### 🔑 IAM Access Keys
- Used for CLI / SDK access
- Includes:
  - Access Key ID
  - Secret Access Key

---
## ⚠️ Root User
- Default AWS account owner
- Full access to everything

#### ❗ Best Practices
❌ Don’t use root user daily
✅ Create IAM users instead

### ✅ Best Practices:
- Enable MFA
- Create IAM users instead
- Avoid using root credentials

### 🔑 IAM Access Keys
  - Used for: CLI, SDK and API
  - 🔐 Components : Access Key ID and Secret Access Key

#### When to Use What?
| Scenario                | Use         |
| ----------------------- | ----------- |
| Human login             | IAM User    |
| AWS service interaction | IAM Role    |
| API/CLI access          | Access Keys |


## 🔄 IAM Users vs Roles
| Feature | IAM User 👤 |  IAM Role 🔄 |
|--------|----------|----------|
| Access  | Permanent | Temporary |
| Credentials | Long-term   | Short-term        |
| Use Case | Humans | Services/Apps / cross-account  |
| Security | Less secure | More secure |

---

### 🔗 When to Use What?
- 👤 Humans → IAM Users  
- 🤖 EC2 / Lambda → IAM Roles  

### 🧩 How IAM Works
👉 Flow: User/Service → IAM Policy → Permissions → AWS Resource

### 🎯 Principle of Least Privilege
   - Grant only minimum permissions required (Dev user → Only EC2 access)

---

## 🛠️ Steps to Create IAM User

1. Login to AWS Console  
2. Go to **IAM Service**  
3. Click **Users → Add User**  
4. Enter username  
5. Choose access type:
   - Console access  
   - Programmatic access  
6. Attach permissions:
   - AdministratorAccess  
   - ReadOnlyAccess  
7. Enable MFA (recommended)  
8. Review & Create user  

---

### 🔐 🔐 Best Practices
- Save Access Key & Secret Key securely
- Enable MFA for all users
- Use roles instead of access keys
- Never share credentials  
- Rotate keys regularly
- Follow least privilege

### ⚠️ Common Mistakes
- ❌ Using root account daily
- ❌ Giving full admin access
- ❌ Hardcoding access keys
- ❌ Not enabling MFA

## 🎯 Summary

- IAM = Access control system in AWS  
- Users, Roles, Policies are core 
- Always follow least privilege  
- Use MFA for security  
```
IAM 👤
  ↓
Users / Roles / Groups
  ↓
Policies 📜
  ↓
Secure Access to AWS 🔐
```
## 🧩 IAM secures AWS by controlling who can access what resources and how.
