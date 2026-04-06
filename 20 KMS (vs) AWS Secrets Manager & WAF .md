# 🔐 AWS KMS (Key Management Service) vs AWS Secrets Manager
## 🧠 What is KMS?
  * ✨ KMS is used to create and manage encryption keys (`encrypt🔒` and `decrypt🔓` data and manage cryptographic keys securely).
  * It integrates with AWS services like `S3, RDS, and EBS` to protect sensitive data by handling encryption automatically.
  * 📌 Example: You upload sensitive files to an `S3 bucket` and want to encrypt them using a KMS key.
  * 🔑 Key Concept : A `cryptographic key` = secret string used for `encryption/decryption`

## 🔒 What is AWS Secrets Manager?
  * ✨ Use AWS Secrets Manager to store and manages sensitive data (secrets) like passwords🗄️, API keys🔑, Tokens🎫 and database credentials with automatic rotation.
  *  Select the rotation interval (e.g., 30, 60, 90 days).
  * 📌 Example : 👉 Store RDS password securely
      * App fetches secret dynamically
      * No hardcoding ❌


| 🧩 Feature      | 🔐 AWS KMS                     | 🔒 AWS Secrets Manager     |
| --------------- | ------------------------------ | -------------------------- |
| 🎯 Purpose      | 🔑 Encryption & key management | 🗝️ Store & manage secrets |
| 💾 Stores Data? | ❌ No (stores keys only)        | ✅ Yes (stores secrets)     |
| 🎯 Use Case     | 🔐 Encrypt/decrypt data        | 🔑 Passwords, API keys     |
| 🔄 Rotation     | ⚠️ Manual / limited            | ✅ Automatic rotation       |


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

1. 🖥️ Open AWS WAF Console — Navigate to `AWS WAF` in the AWS Management Console.  
2. 🏗️ Create Web ACL — Define a name and select a region or CloudFront.  
3. 🔗 Choose Resource — Attach AWS WAF to `ALB`, `API Gateway`, `CloudFront`  
4. 🧩 Add Rules — Use Managed Rules (`AWS-provided`) or create Custom Rules (`IP blocking`, `rate limits`, `geo-restriction`).  
5. 🎯 Set Default Action — Choose `Allow`, `Block`, or `Count` for unmatched requests.  
6. 📄 Enable Logging — Send `logs` to CloudWatch S3  
7. ✅ Review & Create — Finalize and deploy the `Web ACL`.


