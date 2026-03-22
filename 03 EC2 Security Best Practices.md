# ✅ EC2 Security Best Practices

🔑 Use SSH keys only (disable password login)  
🚫 No root SSH access — use normal users + sudo  
👤 One user per person (easy auditing & revocation)  
🔒 Correct SSH permissions  
- `.ssh` → 700  
- `authorized_keys` → 600  

🌐 Restrict Security Groups  
- SSH (22) → your IP only, never `0.0.0.0/0`  

🛡 Use IAM Roles, not access keys on EC2  
🔄 Keep OS updated regularly  
📜 Enable logging & monitoring  
🔁 Rotate/remove unused SSH keys  
🧱 Run services as non-root  
☁️ Prefer SSM over SSH when possible  

👉 **Golden rule:**  
**SSH locked + SG restricted + IAM roles = secure EC2 ✅**

---

# ✅ Use IAM Roles, not Access Keys on EC2

❌ Never use `aws configure` on EC2  
❌ Never store AWS access keys on the instance  

✅ Attach an IAM Role to EC2  
✅ EC2 gets temporary, auto-rotated credentials  
✅ Permissions are controlled by IAM policies  
✅ Fully auditable via CloudTrail  
✅ AWS CLI/SDK works without any config  

👉 **Golden rule:**  
- Humans use IAM Users  
- EC2 and services use IAM Roles  

👉 **IAM Roles = secure, scalable, zero-key access for EC2**

---

# ✅ The RIGHT way: IAM Role on EC2

❌ **The WRONG way (don’t do this):** `aws configure`  

## How it works

1. Create an IAM Role  
2. Attach least-privilege policies  
3. Attach the role to EC2  
4. EC2 receives temporary credentials automatically  

👉 **Flow:**  
EC2 → IAM Role → Temporary creds → AWS APIs
