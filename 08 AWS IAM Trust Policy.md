# 🎯 What is a Trust Policy?
 * A trust policy defines who can assume an IAM role.
 * It specifies the trusted entity like a user, service, or OIDC provider and allows actions like :
     * `sts:AssumeRole` → Used by AWS services or IAM users
     * `sts:AssumeRoleWithWebIdentity` → Used with OIDC/JWT tokens (IRSA)
     * 👉 IRSA specifically uses `AssumeRoleWithWebIdentity` because Kubernetes provides `OIDC tokens`.

| 🧩 **Concept**      | 📖 **Description**                | 🧠 **How It Works**                                                                  | 💡 **Example**               |
| ------------------- | --------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------- |
| 🔐 **Trust Policy** | Defines **who can assume a role** | 👉 Attached to IAM Role<br>👉 Specifies trusted entities (users, services, accounts) | EC2 allowed to assume a role |

| 🎯 **Scenario**         | 🔐 **Trusted Entity (Principal)** | 🧠 **How It Works**                                             | 💡 **Real-World Insight**                       |
| ----------------------- | --------------------------------- | --------------------------------------------------------------- | ----------------------------------------------- |
| 🖥 **EC2 accessing S3** | `ec2.amazonaws.com`               | 👉 EC2 service is allowed to assume the IAM Role                | Used for instance roles (no access keys needed) |
| 📦 **EKS Pod (IRSA)**   | OIDC provider                     | 👉 Kubernetes ServiceAccount uses OIDC token to assume IAM Role | Secure Pod → AWS access without secrets         |


## ⚖️ Permission Policy vs Trust Policy
| 🧩 **Policy Type**       | 🎯 **Purpose** | 🧠 **What It Controls**            | 📍 **Attached To**  | 💡 **Example**       |
| ------------------------ | -------------- | ---------------------------------- | ------------------- | -------------------- |
| 📜 **Permission Policy** | Define actions | 👉 What actions are allowed/denied | User / Role / Group | Allow `s3:GetObject` |
| 🔐 **Trust Policy**      | Define access  | 👉 Who can assume the role         | Role only           | EC2 can assume role  |
 * Trust policies control who can assume a role, while permission policies control what actions are allowed once the role is assumed.

## 🧩 Key Components of a Trust Policy
| 🧩 **Field**     | 📖 **Meaning**          | 🧠 **How It Works**                                            | 💡 **Example**                                  |
| ---------------- | ----------------------- | -------------------------------------------------------------- | ----------------------------------------------- |
| 👤 **Principal** | Who can assume the role | 👉 Defines trusted entity (user, service, account, OIDC)       | `ec2.amazonaws.com`, AWS account, OIDC provider |
| 🎯 **Action**    | What action is allowed  | 👉 Usually `sts:AssumeRole` or `sts:AssumeRoleWithWebIdentity` | Role assumption action                          |
| ⚖️ **Effect**    | Allow or Deny           | 👉 Grants or blocks access                                     | `"Effect": "Allow"`                             |
| 🔒 **Condition** | Optional restrictions   | 👉 Adds extra security checks (IP, MFA, tags)                  | Restrict by IP or require MFA                   |

---

 ## 🔐 Trust Policy in IRSA (Core Idea)

   * 👉 Trust policy defines:
       * Which Kubernetes ServiceAccount (from which cluster & namespace) can assume this IAM role

  In Kubernetes with IRSA (IAM Roles for Service Accounts), the trust policy controls which Kubernetes ServiceAccount is allowed to assume an IAM role via OIDC.

* What is IRSA?
  * IRSA (IAM Roles for Service Accounts) lets a Pod in Kubernetes securely access AWS services without using static credentials.

 # 📦 IRSA Trust Policy Example :
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Federated": "arn:aws:iam::<ACCOUNT_ID>:oidc-provider/oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>"
      },
      "Action": "sts:AssumeRoleWithWebIdentity",
      "Condition": {
        "StringEquals": {
          "oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>:sub": "system:serviceaccount:default:my-app"         # ✅ which Kubernetes ServiceAccount is allowed to assume the IAM role
        }
      }
    }
  ]
}
```

 * 👉 "This trust policy allows a specific Kubernetes ServiceAccount (default:my-app) to assume an IAM role using OIDC via AssumeRoleWithWebIdentity.
 * 🚨 Why Condition is Mandatory
   * Without this:
       * ❌ Any pod in cluster could assume the role
       * ✅ With this → only specific ServiceAccount can use it
       * Trust Policy (THE HEART ❤️) : 👉 Which Pod is allowed to use this role..

 * ` "oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>:sub": "system:serviceaccount:default:my-app" `

| 🧩 **Part**                                       | 💡 **Meaning**                                       | 🧠 **Explanation**                                    | 🔒 **Security Insight**                      |
| ------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------ | -------------------------------------------- |
| 🌐 `oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>` | OIDC provider for your EKS cluster (“Which cluster?”) | 👉 Unique identity provider linked to your cluster    | Ensures requests come from your cluster only |
| 🔑 `:sub`                                         | “Who is requesting?”                                  | 👉 Refers to the **caller identity** in OIDC token    | Used to match exact ServiceAccount           |
| 🧬 `system:serviceaccount:default:my-app`         | Kubernetes ServiceAccount identity                    | 👉 Format: `system:serviceaccount:<namespace>:<name>` | Restricts access to a specific Pod identity  |
| 🧬 `system:serviceaccount`                        | Kubernetes identity type (“Exact Pod identity”)       | 👉 Indicates a ServiceAccount identity                | 🔑 Required for IRSA                      |
| 📂 `default`                                      | Namespace                                             | 👉 Namespace where the ServiceAccount exists           | 📦 Limits scope to namespace               |
| 📦 `my-app`                                       | ServiceAccount name                                   | 👉 Specific ServiceAccount allowed                     | 🎯 Only this Pod gets access              |

  * In IRSA
     * the trust policy uses the `OIDC provider` and
     * the `sub` claim to strictly map an `IAM role` to a `specific Kubernetes ServiceAccount`, ensuring secure and scoped access.”


---

# 🎯 Goal
  * 👉 Allow a Kubernetes Pod to access AWS (like S3)
  * 👉 WITHOUT hardcoding credentials
  * 🧩 Think of It Like This : `Pod → ServiceAccount → IAM Role → AWS Access`
  * 👉 How does AWS trust this Pod?
        * `OIDC + Trust Policy`

## 🔐 What Problem IRSA Solves
| 🧩 Scenario          | 📖 What Happens                                 | ⚠️ / ✅ Impact                                                         |
| -------------------- | ----------------------------------------------- | ------------------------------------------------------------------------ |
| ❌ **Without IRSA** | 🔑 Store AWS access keys inside Pods            | ⚠️ Security risk (key leakage, hard to rotate)                            |
| ✅ **With IRSA**    | 🔄 Pod gets temporary credentials automatically | 🔐 More Secure (no keys, auto-rotated via STS `Security Token Service` ) |

## 🧩 Step 1: Create / Verify EKS Cluster
  * You need an EKS cluster

## 🔐 Step 2: Enable OIDC Provider (VERY IMPORTANT)
  * Check if OIDC is already enabled:
```
aws eks describe-cluster \
  --name my-cluster \
  --query "cluster.identity.oidc.issuer" \
  --output text
```
### 👉 If not enabled, run:
```
eksctl utils associate-iam-oidc-provider \
  --cluster my-cluster \
  --approve
```
* 🧠 What this does:
   * Creates an OIDC identity provider in IAM
   * Allows AWS to trust Kubernetes tokens

## 🔎 Step 3: Get OIDC Provider URL
  * Example output: `https://oidc.eks.ap-south-1.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE`
  * 👉 Remove `https://` → used in trust policy

## 🔑 Step 4: Create IAM Role with Trust Policy
   * Now create IAM role in Amazon Web Services
   * ✅ Trust Policy (IRSA) :
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Federated": "arn:aws:iam::<ACCOUNT_ID>:oidc-provider/oidc.eks.ap-south-1.amazonaws.com/id/<OIDC_ID>"
      },
      "Action": "sts:AssumeRoleWithWebIdentity",                                                                                # 🔑 External identity (OIDC token)
      "Condition": {
        "StringEquals": {
          "oidc.eks.ap-south-1.amazonaws.com/id/<OIDC_ID>:sub": "system:serviceaccount:default:my-app",
          "oidc.eks.ap-south-1.amazonaws.com/id/<OIDC_ID>:aud": "sts.amazonaws.com"
        }
      }
    }
  ]
}
```
 * 🧠 What this means:
    * Only ServiceAccount `my-app` in `default namespace` can assume role
    * Only tokens meant for `STS` are accepted (🔑 AWS Security Token Service)

* 🔐 AWS STS Actions :

| 🧩 Action                              | 🎯 Purpose                                        | 🧠 How It Works                                         | 💡 Common Use Case                      |
| -------------------------------------- | ------------------------------------------------- | ------------------------------------------------------- | --------------------------------------- |
| 🔑 **`sts:AssumeRole`**                | 👤 Assume role using AWS identity                 | 👉 IAM User/Role requests temporary credentials via AWS | EC2 instance role, cross-account access |
| 🌐 **`sts:AssumeRoleWithWebIdentity`** | 🔗 Assume role using external identity (OIDC/JWT) | 👉 Uses OIDC token (no AWS credentials needed)          | EKS IRSA, social login (Google, etc.)   |











