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
```yaml
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

### When to Use What?
| 🎯 **Scenario**                | 🛠 **Use**      | 📖 **What It Means**                                                     | 💡 **Best Practice**                                    |
| ------------------------------ | --------------- | ------------------------------------------------------------------------- | -------------------------------------------------------- |
| 👤 **Human login**             | 👤 IAM User    | 🧑 Individual identity for developers/admins to access AWS Console or CLI | 👉 Prefer SSO/temporary credentials over long-term users |
| 🤖 **AWS service interaction** | 🤖 IAM Role    | ⚙️ Permissions assumed by services (EC2, Lambda, EKS Pods via IRSA)       | 👉 Use roles instead of hardcoding credentials           |
| 🔑 **API/CLI access**          | 🔑 Access Keys | 💻 Programmatic access (Access Key ID + Secret Key)                       | ⚠️ Avoid long-lived keys; rotate regularly               |

## 🔄 IAM Users vs Roles
| 🧩 Feature     | 👤 IAM User                        | 🔄 IAM Role                      | 🧠 Explanation                                                  |
| -------------- | ---------------------------------- | -------------------------------- | --------------------------------------------------------------- |
| 🔑 Access      | 🔒 Permanent                       | ⏳ Temporary                      | Users have long-term access; roles are assumed for limited time |
| 🧾 Credentials | 🔑 Access Key + Secret (long-term) | 🎟️ STS tokens (short-term)      | Roles use temporary credentials issued by AWS STS             |
| 🎯 Use Case    | 👨‍💻 Humans (CLI/Console)            | 🤖 Services, apps, cross-account access | Roles are ideal for automation and cloud services                  |
| 🔒 Security    | ⚠️ Less secure                     | ✅ More secure                    | Temporary creds reduce risk of exposure                      |
| 🔄 Rotation    | 🔁 Manual                          | 🔄 Automatic                     |  Roles removes need for manual key rotation               |
| ☁️ Integration | ⚠️ Limited                         | 🔗 Native with AWS services      | Roles work seamlessly with EC2, EKS (IRSA), Lambda           |


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

1. 🔑 Login to AWS Console  
2. ⚙️ Go to **IAM Service** ` Identity & Access Management `
3. 👤 Click **Users → Add User**  
4. 🏷️ Enter username  
5. 🔐 Choose access type:
      - Console access  
      - Programmatic access  
6. 🛡️ Attach permissions:
      - AdministratorAccess  
      - ReadOnlyAccess  
7. 🔑 Enable MFA `multi-factor authentication` (🚨 Strongly recommended)  
8. ✅ Review & Create user  `🔍 Double-check permissions`

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
```hcl
IAM 👤
  ↓
Users / Roles / Groups
  ↓
Policies 📜
  ↓
Secure Access to AWS 🔐
```
## 🧩 IAM secures AWS by controlling who can access what resources and how.
