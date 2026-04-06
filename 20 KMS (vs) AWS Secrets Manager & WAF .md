# 🔐 AWS KMS (Key Management Service) vs AWS Secrets Manager
## 🧠 What is KMS?
  * 👉 AWS KMS is used to create and manage cryptographic keys for `encrypting` 🔒 and `decrypting` 🔓 data.
  * ✨ It integrates with AWS services like `S3, RDS, and EBS` to protect sensitive data by handling encryption automatically.
  * 📌 Example: You upload sensitive files to an `S3 bucket` and want to encrypt them using a KMS key.
  * 🔑 Key Concept : A `cryptographic key` = secret string used for `encryption/decryption`

## 🔐 Create AWS KMS Key (Step-by-Step)
| 🧩 Step | 📌 Action           | 💡 Details                                                      |
| ------- | -------------------- | ---------------------------------------------------------------- |
| 1️⃣     | 🖥️ Open Console      | 🌐 Go to AWS Console → Search **KMS (Key Management Service)**   |
| 2️⃣     | ➕ Create Key        | 🆕 Click **“Create key”**                                       |
| 3️⃣     | 🔑 Key Type          | ⚙️ Choose **Symmetric** (common) or Asymmetric                  |
| 4️⃣     | 🎯 Key Usage         | 🔐 Select **Encrypt and Decrypt**                               |
| 5️⃣     | 🏷️ Add Alias         | 📝 Example: `my-kms-key`                                        |
| 6️⃣     | 👤 Define Admins     | 🛡️ Choose IAM users/roles to manage key                         |
| 7️⃣     | 🔐 Usage Permissions | 🔑 Select who can use the key (encrypt/decrypt)                 |
| 8️⃣     | 🔍 Review            | 👀 Verify all configurations                                    |
| 9️⃣     | ✅ Create            | 🚀 Click **Create key**                                         |


## 🔒 What is AWS Secrets Manager?
  * ✨ Use AWS Secrets Manager to store and manages sensitive data (secrets) like passwords🗄️, API keys🔑, Tokens🎫 and database credentials with automatic rotation.
  *  Select the rotation interval (e.g., 30, 60, 90 days).
  * 📌 Example : 👉 Store RDS password securely
      * App fetches secret dynamically
      * No hardcoding ❌

## 🔐 Create Secret in AWS Secrets Manager (Step-by-Step)
| 🧩 Step | 📌 Action              | 💡 Details                                                  |
| ------- | ---------------------- | ----------------------------------------------------------- |
| 1️⃣     | 🌐 Open Console        | 🔍 Go to AWS Console → Search **Secrets Manager**           |
| 2️⃣     | ➕ Store Secret         | 🆕 Click **“Store a new secret”**                           |
| 3️⃣     | 🧩 Select Type         | 📦 Choose: RDS / Database / **Other (API keys, passwords)** |
| 4️⃣     | ✍️ Enter Values        | 🔑 Add key-value or JSON (username, password, API key)      |
| 5️⃣     | 🔐 Encryption          | 🛡️ Use default (**aws/secretsmanager**) or custom KMS key  |
| 6️⃣     | 🏷️ Name Secret         | 📝 Example: `prod/db-credentials` + tags/description        |
| 7️⃣     | 🔄 Rotation (Optional) | ⚙️ Enable auto-rotation using Lambda (e.g., 30 days)        |
| 8️⃣     | ✅ Create               | 🚀 Review and click **Store**                               |

### 🔐 Access Secrets from AWS Secrets Manager
| 🧩 Method        | 📌 What it Means               | 💡 Example                                                            |
| ---------------- | ------------------------------- | --------------------------------------------------------------------- |
| 🌐 AWS Console   | 👀 View secret manually in UI  | Open AWS → Secrets Manager → Select secret → **Retrieve value**       |
| 💻 AWS CLI       | ⚡ Fetch via command line      | `aws secretsmanager get-secret-value --secret-id prod/db-credentials` |
| 🧑‍💻 SDK (Code)    | 🔗 Access inside applications  | Python / Java / Node.js fetch secrets dynamically                     |

 * 👉 Access Methods = Ways to read or use your stored secret
 * 🔍 Real Example
     * Instead of hardcoding password in code ❌
     * Your app fetches it from Secrets Manager using SDK ✅

---

## ⚖️ AWS KMS vs AWS Secrets Manager
| 🧩 Feature      | 🔐 AWS KMS                      | 🔒 AWS Secrets Manager       |
| --------------- | -------------------------------- | ---------------------------- |
| 🎯 Purpose      | 🔑 Encryption & key management  | 🗝️ Store & manage secrets   |
| 💾 Stores Data? | ❌ No (stores keys only)        | ✅ Yes (stores secrets)     |
| 🎯 Use Case     | 🔐 Encrypt/decrypt data         | 🔑 Store Passwords, API keys |
| 🔄 Rotation     | ⚠️ Manual / limited             | ✅ Automatic rotation        |

---

# 🛡️ AWS WAF (Web Application Firewall)
## 🚀 What is AWS WAF?
* ✨ AWS WAF (Web Application Firewall) is a security service that helps protect web applications from common threats like `SQL injection`, `cross-site scripting (XSS)`, and `bot attacks` by filtering HTTP/HTTPS traffic.
* 💥 SQL injection is a `code injection` technique that might destroy your database. SQL injection is one of the most common web hacking techniques.
* ⚠️ `XSS attack` happens when a hacker Injecting harmful scripts into web pages.
* When someone visits the site, the code runs in their browser and can steal information or do bad things. 

## 🤖 Bot Attacks
 * 🤖 A bot attack happens when hackers use automated programs (`bots`) to perform harmful actions on websites or applications.
 * These bots can:
    * Steal data
    * Overload servers (`Distributed Denial-of-Service (DDoS) attack`)
    * Spread spam
 * 📌 Example: If a bot sends `more than 1000 requests` in `5` minutes, AWS WAF temporarily blocks it to prevent a `DDoS attack`.


## 🔑 Key Features of AWS WAF (Web Application Firewall):
 
  * 🛡️ Protects Web Applications — Blocks threats like `SQL injection`, `XSS`, and `bot attacks`.
  * 🔗 Works with AWS Services — Supports `ALB`, `API Gateway`, `CloudFront`
  * 📊 Rate-Based Rules — Limits requests to `prevent DDoS` (Distributed Denial of Service) and `brute force attacks`.
  * 🌍 Geo Restriction — `Blocks/Allows` traffic from specific countries.
  * 🚫 IP Blocking — Allows or denies access based on `IP addresses` or `CIDR blocks`.
  * 💰 Cost-Effective — `Pay-as-you-go` pricing based on rules and requests inspected.  

---

## ⚙️ AWS WAF Setup:
| 🧩 Step | 📌 Action          | 💡 Description                                                                               |
| ------- | ------------------ | --------------------------------------------------------------------------------------------- |
| 1️⃣     | 🖥️ Open Console   | 🌐 Go to AWS Console → **AWS WAF**                                                             |
| 2️⃣     | 🏗️ Create Web ACL | 📝 Define name & choose region or CloudFront                                                   |
| 3️⃣     | 🔗 Choose Resource | ⚖️ Attach AWS WAF to `ALB`, `API Gateway`, or `CloudFront`                                    |
| 4️⃣     | 🧩 Add Rules       | 🛡️ Use Managed Rules (`AWS-provided`) or Custom Rules (IP block, rate limit, geo restriction) |
| 5️⃣     | 🎯 Default Action  | ⚙️ Choose `Allow` / `Block` or `Count` for unmatched requests                                 |
| 6️⃣     | 📄 Enable Logging  | 📊 Send `logs` to CloudWatch / S3                                                             |
| 7️⃣     | ✅ Review & Create  | 🚀 Finalize and deploy `Web ACL `                                                            |


### 🏁 Final Summary

 * ✨ KMS → Encryption keys 🔐
 * ✨ Secrets Manager → Store secrets 🔒
 * ✨ WAF → Protect web apps 🛡️
