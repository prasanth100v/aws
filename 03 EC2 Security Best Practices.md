
# 🔐 AWS EC2 Security Best Practices 
## 🛡️ EC2 Security Best Practices

### 🔑 SSH Security

- ✅ Use SSH keys only (disable password login)
- 🚫 Disable root SSH access
- 👤 Create one user per person (better auditing)
- 🔒 Set correct permissions:
  - `.ssh` → 700
  - `authorized_keys` → 600

---

### 🌐 Security Groups (Firewall)

- Restrict SSH (Port 22) to **your IP only**
- ❌ Never allow `0.0.0.0/0` for SSH

### 🧠 IAM Best Practices

- 🛡️ Use IAM Roles instead of access keys
- 🔁 Rotate/remove unused SSH keys
- 📜 Enable logging (CloudTrail, CloudWatch)

---

### ⚙️ System Hardening

- 🔄 Keep OS updated regularly
- 🧱 Run services as non-root user
- ☁️ Prefer SSM over SSH for secure access

## 🏆 Golden Rule

> 🔐 SSH Locked + SG Restricted + IAM Roles = Secure EC2 ✅

---

# 🔑 IAM Roles vs Access Keys on EC2
## ❌ What NOT to Do

- ❌ Never run `aws configure` on EC2
- ❌ Never store AWS access keys on instance

---

## ✅ Best Practice

- ✅ Attach IAM Role to EC2
- ✅ Use temporary credentials (auto-rotated)
- ✅ Control permissions using IAM policies
- ✅ Fully auditable with CloudTrail
- ✅ AWS CLI/SDK works automatically

## 🏆 Golden Rule

- 👤 Humans → IAM Users  
- 🤖 EC2/Services → IAM Roles  

---

## 🚀 Why IAM Roles?

| Feature | Benefit |
|--------|--------|
| 🔐 Security | No hardcoded credentials |
| 🔄 Auto Rotation | Credentials rotate automatically |
| 📊 Audit | Full visibility via CloudTrail |
| ⚡ Simplicity | No need for manual config |

---

# 🧩 The RIGHT Way: IAM Role on EC2

### ❌ WRONG Way : 
- aws configure
## ✅ RIGHT Way (Step-by-Step)

1. 🛠️ Create an IAM Role  
2. 🔐 Attach least-privilege policies  
3. 🖥️ Attach role to EC2 instance  
4. 🔄 EC2 automatically receives temporary credentials  

## 🔄 How It Works
```
👉 Flow: EC2 Instance → IAM Role → Temporary Credentials → AWS APIs
```
---

## 🎯 Real-World Example

- EC2 needs access to S3  
- Attach IAM Role with S3 permissions  
- EC2 can securely access S3 without keys  

## 🔥 Pro Tips

- Always follow **least privilege principle**
- Avoid long-lived credentials
- Use **SSM Session Manager** instead of SSH
- Monitor using CloudWatch + CloudTrail

---

## 🎯 Summary

- Never store AWS keys on EC2 ❌
- Always use IAM Roles ✅
- Restrict SSH and Security Groups 🔐
- Enable monitoring and logging 📊

