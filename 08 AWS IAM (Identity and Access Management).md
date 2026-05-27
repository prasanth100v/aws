# 🔐 AWS IAM (Identity and Access Management)
## 🧠 What is IAM?
 * IAM (Identity and Access Management) is a service that helps you securely control access to AWS resources by defining:
    * Who can access (`users`, `roles`)
    * What actions they can perform (`policies`)  → Under what conditions (`Permissions`)
    * IAM is a **FREE service**, 💰 You only pay for AWS resources used
    * 🧩 IAM secures AWS by controlling who can access what resources..

### 🎯 IAM = Control access to AWS resources securely
```yaml
🔄 IAM Flow :  User 👤 → Authenticated 🔑 → Policy Check 📜 → Access Granted ✅
```
## ☁️ AWS IAM Core Components
| 🧩 **Component** | 📖 **Description**                      | 🧠 **How It Works**                                    | 💡 **Real-World Example**    |
| ---------------- | --------------------------------------- | ------------------------------------------------------- | ---------------------------- |
| 👤 **Users**     | Individual identity (person/app)        | 👉 Has login credentials (password, access keys)       | `john-admin`, CI/CD user     |
| 👥 **Groups**    | Collection of users                     | 👉 Permissions assigned to group → apply to all members | `Developers`, `Admins`       |
| 🔄 **Roles**     | Temporary identity (no permanent creds) | 👉 Assumed by services/users → gets temporary access    | EC2 accessing S3, EKS IRSA   |
| 📜 **Policies**  | JSON permission documents               | 👉 Define what actions `resources` are allowed or denied  | Control S3, EC2, etc. access |

### 🔍 IAM Policy Structure
  * Policies are JSON documents that define permissions:

| 🔑 **Field** | 📖 **Meaning**         | 💡 **Example**              |
| ------------ | ---------------------- | --------------------------- |
| Effect       | Allow or Deny access   | `"Effect": "Allow"`         |
| Action       | What action is allowed | `"Action": "s3:ListBucket"` |
| Resource     | Target resource        | `"Resource": "*"`           |

---

## 🔐 Core Concepts
### 🛡️ Secure Access Control
  - Ensures only authorized users can access AWS resources

### 🧾 Authentication & Authorization
| Concept           | Meaning          |
| ----------------- | ---------------- |
| Authentication 🔑 | Who you are     |
| Authorization 🛡️  | What you can do? |


## 👥 IAM Components
### 👤 Users
  - Individual identities
  - Have Long-term (`permanent`) credentials (`password` / `access keys`)

### 👨‍👩‍👧 Groups
 - Collection of users  (`Dev team`, `Admin team`)
 - Share common permissions

### 🤖 Roles
 - Temporary access
 - Used by `AWS services` or `external users`
 - Credentials are temporary and `auto-rotated`, typically valid for `1 hour` (3600 seconds) (default).
 - Max session duration: **12 hours**
   * 🎯 If AWS service talks to another → `Use IAM Role`

### 📜 Policies
 - JSON-based permission rules
 - Define `allowed/denied` actions
#### 📌 Example Policy
```yaml
{
  "Effect": "Allow",                     # JSON document defining permissions
  "Action": "s3:ListBucket",
  "Resource": "*"
}
```
## 📜 Types of IAM Policies
| 🧩 **Policy Type**               | 📖 **Description**              | 🧠 **How It Works**                                  | 💡 **Real-World Use Case**            |
| -------------------------------- | ------------------------------- | ------------------------------------------------------ | ------------------------------------- |
| 📦 **AWS-Managed Policies**      | Predefined by AWS               | 👉 Ready-to-use policies maintained by `AWS`          | `AmazonS3ReadOnlyAccess`, quick setup |
| 🛠 **Customer-Managed Policies** | Created by you                  | 👉 Custom `JSON policies` reusable across `users/roles` | Fine-grained access for apps          |
| 📌 **Inline Policies**           | Attached directly to one entity | 👉 Exists only for that specific `user/group/role`     | One-off permissions for specific user |

### 📦 Managed Policies
 - Reusable
 - Created by: AWS (predefined) or Users

### 📌 Inline Policies
 - Attached to one entity
 - ❌ Not reusable

 * 🎯 Managed policies are reusable; inline policies are specific to one entity.
 * 🎯 Interview Tip
     * “Managed policies are reusable and recommended, while inline policies are tightly coupled to a single identity and used for specific cases.

## What is the difference between Managed and Inline Policies?
| 🧩 Type               | 💡 Description                                               |
| --------------------- | ------------------------------------------------------------ |
| 📦 **Managed Policy** | ♻️ Reusable → can attach to multiple users, groups, or roles |
| 📄 **Inline Policy**  | 🔒 One-to-one → attached to a single user/role only          |

## What happens when multiple policies are attached?
  * IAM evaluate policies
| 🧩 Rule             | 💡 Meaning                                     |
| -------------------- | ---------------------------------------------- |
| ❌ **Explicit Deny** | 🚫 Highest priority, overrides `any Allow`    |
| ✅ **Allow**         | ✔️ Grants permission (only if no deny exists) |
| ⚠️ **Default Deny**  | ❌ If no policy allows it, access is denied   |

### What is MFA in IAM?
 * Multi-Factor Authentication adds extra security:
    * Password + OTP (phone/app/device)

---

## 🔑 IAM Features

### 🔐 Multi-Factor Authentication (MFA)
📘 What is MFA?

 * Adds extra security layer:
    - Password 🔑
    - OTP / Code 📱
    - 🎯 Benefit :  Protects against `unauthorized access`

### ⚖️ Least Privilege
  - Grant minimum permissions needed

### 🔑 IAM Access Keys
 - Used for `CLI` / `SDK` access
 - Includes:
   - Access Key ID
   - Secret Access Key

---
## ⚠️ Root User
  - Default AWS account owner
  - Full access to everything

#### ❗ Best Practices
 * ❌ Don’t use root user daily
 * ✅ Create IAM users instead

### 🔑 IAM Access Keys
   - Used for: Used for programmatic access `CLI`, `SDK` and `API`
   - 🔐 Components : Access Key ID and Secret Access Key  (⚠️ Should be `rotated regularly`)

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
| 🎯 Use Case    | 👨‍💻 Humans (CLI/Console)            | 🤖 Services, apps, cross-account access | Roles are ideal for automation and cloud services      |
| 🔒 Security    | ⚠️ Less secure                     | ✅ More secure  (temporary tokens)  | Temporary creds reduce risk of exposure                      |
| 🔄 Rotation    | 🔁 Manual                          | 🔄 Automatic                     |  Roles removes need for manual key rotation               |
| ☁️ Integration | ⚠️ Limited                         | 🔗 Native with AWS services      | Roles work seamlessly with EC2, EKS (IRSA), Lambda           |


## What is an IAM Role?
  * 👉 A role provides temporary access to AWS resources without sharing credentials.
     * ✔ No long-term credentials
     * ✔ Uses temporary security tokens

## ⚖️ IAM Role Assumption Types
| 🔐 **Type**                | 👤 **Who Assumes Role**      | 🧠 **How It Works**                                                   | 🌍 **Real Use Case**              |
| -------------------------- | ---------------------------- | ----------------------------------------------------------------------- | --------------------------------- |
| ☁️ **AWS Service**         | EC2, Lambda, ECS, EKS        | 👉 AWS service assumes role via service principal (`ec2.amazonaws.com`) | App accessing S3 without keys     |
| 🏢 **AWS Account**         | IAM Users / Roles            | 👉 Another account/user assumes role using `sts:AssumeRole`             | Cross-account access (Dev → Prod) |
| 🌐 **Web Identity (OIDC)** | External IdP / Kubernetes    | 👉 Uses OIDC token with `sts:AssumeRoleWithWebIdentity`                 | IRSA in EKS, Google login         |
| 🏛 **SAML**                 | Corporate Identity Providers | 👉 Uses SAML assertion for authentication                               | Enterprise SSO (Okta, Azure AD)   |

---

### 🔗 When to Use What?
  - 👤 Humans → `IAM Users  `
  - 🤖 EC2 / Lambda → `IAM Roles ` 

### 🧩 How IAM Works
```hcl
IAM 👤
  ↓
Users / Roles / Groups
  ↓
Policies / Permissions 📜
  ↓
Secure Access to AWS Resource 🔐
```

### 🎯 Principle of Least Privilege
   - Grant only minimum permissions required (`Dev user → Only EC2 access`)
   - Principle of Least Privilege : Give only the `minimum permissions` required to perform a task—nothing more.

### What is Policy Simulation?
  * A tool to test whether a policy `allows or denies` an action.

### What is STS (Security Token Service)?
  * Provides `temporary credentials` for accessing AWS resources.

### How to restrict access to a specific IP?
  * Use condition in policy:
```json
"Condition": {
  "IpAddress": {
    "aws:SourceIp": "192.168.1.1/32"
  }
}
```
## How do you audit IAM permissions?

 * IAM Access Analyzer
 * CloudTrail logs
 * Credential reports

## ⚠️ I attached full S3 access, but still getting Access Denied. Why?

 * Even if IAM allows, access can still be denied due to:
    * ❌ `Explicit Deny` in any policy
    * ❌ `S3 Bucket Policy` blocking access
    * ❌ SCP (Service Control Policy) restriction
    * ❌ Incorrect `ARN` / `resource` mismatch
    * 👉 Key line to say: `Explicit Deny` always overrides Allow across all policy types.

## 🔐 User can access AWS Console but not CLI. Why?

 * Console uses password (authentication)
 * CLI requires access keys
 * 👉 Possible issue: Access keys `not created` or `inactive`

## 🔥 Two policies: one allows, one denies. What happens?
   * 👉 `Explicit Deny` wins ALWAYS

## User should access S3 only during office hours. How?”
   * Use `time-based` condition:
```json
"Condition": {
  "DateGreaterThan": {"aws:CurrentTime": "09:00Z"},
  "DateLessThan": {"aws:CurrentTime": "18:00Z"}
}
```

## Developer accidentally exposed access keys on GitHub. What do you do?

 * ❌ Immediately disable/delete keys
 * 🔄 Rotate credentials
 * 🔍 Check logs using CloudTrail
 * 🔐 Apply least privilege
 * 🚫 Use roles instead of keys going forward

## You have 100 developers. How do you manage permissions efficiently?

 * Use Groups
 * Attach managed policies to groups
 * Avoid individual user policies

## User says they didn’t delete resource, but it’s gone. How do you investigate?

 * Check AWS CloudTrail logs
 * Identify:
   * Who performed action
   * When
   * From which IP

## How to allow access to only one specific S3 bucket?”

  * Define resource ARN : `Resource": "arn:aws:s3:::my-bucket/*`

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
- Enable `MFA` for all users
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
