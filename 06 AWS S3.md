# 🪣 AWS S3 (Simple Storage Service) 
## ☁️ What is Amazon S3?

Amazon S3 is a **scalable, durable, and highly available object storage service**.

👉 Store and retrieve any amount of data from anywhere on the internet.

### 📦 Use Cases
- Backup & Restore
- Big Data & Analytics
- Static Website Hosting
- Disaster Recovery

## ✨ Key Features of S3
### 🛡️ Durability & Availability
- 99.999999999% (11 9’s) durability  
- 99.99% availability  
- Data replicated across multiple AZs  

### 🧊 Storage Classes

| Class | Use Case |
|------|---------|
| Standard | Frequent access |
| Intelligent-Tiering | Auto cost optimization |
| Standard-IA | Infrequent access |
| One Zone-IA | Single AZ storage |
| Glacier | Archival (minutes–hours retrieval) |
| Glacier Deep Archive | Long-term (12 hours retrieval) |

### 🔄 Versioning
- Keeps multiple versions of objects  
- Protects from accidental deletion  
- Easy rollback  

### 🔁 Lifecycle Management
- Automates data transitions & deletion  

**Examples:**
- Move to Glacier after 30 days  
- Delete after 365 days  

### 📈 Scalability
- Automatically scales storage

---

### 🌐 Static Website Hosting
- Host HTML, CSS, JS directly from S3

### 🔐 Encryption

- SSE-S3 → AES-256 encryption (automatic)
- Supports server-side & client-side encryption

### 🔑 Access Control

- IAM Policies → Internal access  
- Bucket Policies → External access  
- ACLs → Legacy control  

✅ Block Public Access (recommended)  
✅ Use Pre-Signed URLs for temporary access  

---

## 🌍 Static Website Hosting (Steps)

1. Enable static hosting in bucket properties  
2. Upload website files  
3. Set bucket policy (public read)  
4. Access via S3 endpoint  

## 📊 Monitoring

Use **CloudWatch** to track:
- Bucket size  
- Object count  
- Requests  

## 📦 Object Limits

- Max object size: **5 TB**

## 🔁 Replication

- CRR → Cross-region (disaster recovery)  
- SRR → Same-region  

---

## 🔐 Access Strategy

👉 IAM Roles → AWS services (EC2, Lambda)  
👉 Bucket Policies → External/public access  

---

## ⚡ Transfer Acceleration

- Uses CloudFront edge locations  
- Faster uploads/downloads  

---

## 💰 Pricing

- Pay-as-you-go  
- Based on:
  - Storage class  
  - Data transfer  
  - Requests  

## 🔔 Event Notifications

- Trigger Lambda on upload  
- Automate processing  

---

## 💸 Cost Optimization Tips

- Use correct storage class  
- Enable lifecycle policies  
- Delete unused data  
- Reduce API requests  
- Use CloudFront caching  
- Monitor via Cost Explorer  

---

## 🛠️ Steps to Create S3 Bucket

1. Login to AWS Console  
2. Open S3  
3. Click **Create bucket**  
4. Enter name & region  
5. Configure settings  
6. Click Create  

---

## 🎯 Summary

- S3 = Object storage in AWS  
- Highly durable & scalable  
- Multiple storage classes  
- Secure & cost-effective  
