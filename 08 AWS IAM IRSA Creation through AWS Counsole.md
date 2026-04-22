
# IRSA setup using the AWS Console (GUI) step-by-step. No CLI required. 

 * 🚀 What you’ll do in GUI
     * Enable OIDC provider (EKS)
     * Create IAM Policy
     * Create IAM Role (with Trust Policy)
     * Create Kubernetes ServiceAccount (with annotation)
     * Deploy Pod and verify

## 🧩 Step 1: Enable OIDC Provider (Console)
   
  * 👉 Go to: Amazon EKS
  * Steps:
      * Open your cluster
      * Go to Configuration → Details
      * Scroll to `OpenID Connect provider URL`
      * 👉 If you see a URL → already enabled
      * 👉 If not:
         * Click “Associate OIDC provider”
         * Click Confirm
         * ✔ Done

Create IAM Policy
  * 👉 Example: Allow S3 access
  * 👉 Steps : Go to AWS IAM
      * Click Policies → Create policy
      * Choose `JSON tab`
      * Paste example:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket", "s3:GetObject"],
      "Resource": "*"
    }
  ]
}
```
 * Click Next
  * Name: `my-irsa-policy`
  * Create





# Create IAM Role (GUI) (OPTINAL)
| 🔢 Step | 📖 Action                                        | 🧠 How It Works                                                        | 💡 Important Note              |
| ------- | ------------------------------------------------ | ---------------------------------------------------------------------- | ------------------------------ |
| 1️⃣     | 🧭 Go to IAM → Click Roles → Create role         | 👉 Start role creation                                                 | Core IRSA step                 |
| 2️⃣     | 🌐 Select **Trusted entity type = Web identity** | 👉 Enables OIDC-based authentication                                   | Required for IRSA              |
| 3️⃣     | 🔗  Identity provider → Select your EKS OIDC provider| 👉 Select EKS OIDC (e.g., `oidc.eks.ap-south-1.amazonaws.com/id/XXXX`) | Links cluster to IAM           |
| 4️⃣     | 🎯 Set Audience                                  | 👉 `sts.amazonaws.com`                                                 | Mandatory for token validation |
| 5️⃣     | 🔐 Add Condition (`sub`)                         | 👉 This binds  specific `ServiceAccount / Namespace `                | Most important security step   |
| 6️⃣     | 📜 Attach Policy                                 | 👉 Select `my-irsa-policy`                                             | Defines AWS permissions        |
| 7️⃣     | 🏷 Add Role Name                                  | 👉 Example: `my-irsa-role`                                             | Use meaningful naming          |
| 8️⃣     | ✅ Create Role                                   | 👉 Finalize                                                            | Ready for use                  |





🎯 One-Line Summary

👉 In GUI:

EKS OIDC → IAM Role (Web Identity + sub condition) → ServiceAccount annotation → Pod → STS credentials
