# 🧑‍💻 AWS CLI 
## 📌 What is AWS CLI?
 * AWS CLI (`Command Line Interface`) is a tool that allows you to interact with AWS services using **commands instead of the AWS Console**.
 * 💡 It helps you:
   * Automate tasks ⚙️
   * Manage AWS resources quickly 🚀
   * Script cloud operations 📜

## 🚀 Why Use AWS CLI?
  - ✅ Faster than Console
  - ✅ Automation & scripting
  - ✅ Easy bulk operations
  - ✅ Works well with DevOps workflows  

---

## 🐧 Install AWS CLI on Linux
```hcl
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

## ⚙️ Configuration
Run the following command:
```bash
aws configure
```

### 🔑 You will be prompted to enter:
 - AWS Access Key ID
 - AWS Secret Access Key
 - Region (e.g., `us-east-1`)
 - Output format (json | table | text)

## 🧪 Verify Installation
```hcl
aws --version
```
### 📁 Where Config is Stored?
```hcl
~/.aws/credentials
~/.aws/config
```
### 🔑 Authentication (Important)
 * AWS CLI uses IAM credentials:
    * Access Key ID
    * Secret Access Key
    * 👉 These are created in IAM (Identity and Access Management)

## 📦 Basic AWS CLI Commands 
```hcl
aws s3 ls                                 # List S3 Buckets
aws s3 cp myfile.txt s3://my-bucket/        # Upload File to S3
aws s3 rb s3://my-bucket --force             # Delete S3 Bucket
aws ec2 describe-security-groups       # List Security Groups
```
### ☸️ EKS Commands

🔹 Create EKS Cluster
```hcl
aws eks create-cluster \
  --name my-eks-cluster \
  --role-arn arn:aws:iam::123456789012:role/EKSRole \
  --resources-vpc-config subnetIds=subnet-abc123,securityGroupIds=sg-abc123
```

```hcl
aws eks list-clusters          #  List EKS Clusters
```
### 🔄 CLI vs Console
| Feature    | CLI    | Console |
| ---------- | ------ | ------- |
| Speed      | ⚡ Fast | 🐢 Slow |
| Automation | ✅ Yes  | ❌ No    |
| UI         | ❌ No   | ✅ Yes   |
| Bulk tasks | ✅ Easy | ❌ Hard  |


## 🎯 Real Use Cases
 - Deploy infrastructure using scripts 🏗️
 - Automate backups 💾
 - CI/CD pipeline integration 🔄
 - Manage cloud resources at scale 📈

## 🔐 Security Tips
 - Never share access keys on servers  ❌
 - Use `IAM roles` instead of root user 👤
 - Rotate credentials regularly 🔄
 - Store credentials securely 🔒
 - 🔒 Use least privilege permissions 

---

## ✨ Summary
AWS CLI is:
 - Powerful 💪
 - Fast ⚡
 - Automation-friendly 🤖
 - Essential for DevOps 🚀

