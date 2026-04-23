# 🎯 What is a Trust Policy?
 * A trust policy defines who can assume an IAM role.
 * It specifies the trusted entity like a user, service, or OIDC provider and allows actions like :
     * `sts:AssumeRole` → Used by AWS services or IAM users
     * `sts:AssumeRoleWithWebIdentity` → Used with OIDC/JWT tokens (IRSA)
     * 👉 IRSA specifically uses `AssumeRoleWithWebIdentity` because Kubernetes provides `OIDC tokens`.

| 🧩 **Concept**      | 📖 **Description**                | 🧠 **How It Works**                                                                  | 💡 **Example**               |
| ------------------- | --------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------- |
| 🔐 **Trust Policy** | Defines **who can assume a role** | 👉 Attached to IAM Role<br>👉 Specifies trusted entities (users, services, accounts) | EC2 allowed to assume a role |

| 🎯 **Scenario**         | 🔐 **Trusted Entity (Principal)** | 🧠 **How It Works**                                              | 💡 **Real-World Insight**                       |
| ----------------------- | --------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------- |
| 🖥 **EC2 accessing S3** | `ec2.amazonaws.com`               | 👉 EC2 service is allowed to assume the IAM Role                   | Used for instance roles (`no access keys` needed) |
| 📦 **EKS Pod (IRSA)**   | OIDC provider                     | 👉 Kubernetes ServiceAccount uses `OIDC token` to assume IAM Role | Secure Pod → AWS access without secrets         |

## ⚖️ Permission Policy vs Trust Policy
| 🧩 **Policy Type**       | 🎯 **Purpose** | 🧠 **What It Controls**            | 📍 **Attached To**  | 💡 **Example**       |
| ------------------------ | -------------- | ---------------------------------- | ------------------- | -------------------- |
| 📜 **Permission Policy** | Define actions | 👉 What actions are allowed/denied | User / Role / Group | Allow `s3:GetObject` |
| 🔐 **Trust Policy**      | Define access  | 👉 Who can assume the role         | Role only           | EC2 can assume role  |
 * Trust policies control `who can assume a role`, while permission policies control `what actions are allowed` once the role is assumed.

## 🧩 Key Components of a Trust Policy
| 🧩 **Field**     | 📖 **Meaning**          | 🧠 **How It Works**                                            | 💡 **Example**                                  |
| ---------------- | ----------------------- | -------------------------------------------------------------- | ----------------------------------------------- |
| 👤 **Principal** | Who can assume the role | 👉 Defines trusted entity (user, service, account, OIDC)       | `ec2.amazonaws.com`, AWS account, OIDC provider |
| 🎯 **Action**    | What action is allowed  | 👉 Usually `sts:AssumeRole` or `sts:AssumeRoleWithWebIdentity` | Role assumption action                          |
| ⚖️ **Effect**    | Allow or Deny           | 👉 Grants or blocks access                                     | `"Effect": "Allow"`                             |
| 🔒 **Condition** | Optional restrictions   | 👉 Adds extra security checks (IP, MFA, tags)                  | Restrict by IP or require MFA                   |

 * 🎯 Why is Condition Important in Trust Policy?
   * 👉 Condition restricts who exactly can assume the role, adding security.
   * 👉 Without condition, any entity in the trusted provider could assume the role.
   * OIDC is used to verify the `identity` of Kubernetes Pods. AWS trusts the `OIDC provider` configured for the EKS cluster to validate tokens

---

 ## 🔐 Trust Policy in IRSA 
 
  * In Kubernetes with IRSA (IAM Roles for Service Accounts), the trust policy allows a specific Kubernetes ServiceAccount (from which `cluster & namespace`) to assume an IAM role using an OIDC provider.
  * It uses `sts:AssumeRoleWithWebIdentity` and `restricts` access using the `sub` condition.
  * Pod in Kubernetes securely access `AWS services` without using `static credentials`.
  * 🎯 What happens if you remove the Condition?
      * 👉 “Any Pod in the cluster could assume the IAM role, which is a `major security risk`.”
  * 🎯 Can multiple ServiceAccounts use same role?
      * 👉 “Yes, by adding multiple sub values

---

# 🎯 Goal
  * ✅ IRSA setup using `AWS CLI + kubectl`
  * 👉 Allow a Kubernetes Pod to access AWS service (like S3)
  * 👉 WITHOUT hardcoding credentials
  * 🧩 Think of It Like This : `Pod → ServiceAccount → IAM Role → AWS Access`
  * 👉 How does AWS trust this Pod?
        * `OIDC + Trust Policy`

## 🔐 What Problem IRSA Solves
| 🧩 Scenario          | 📖 What Happens                                 | ⚠️ / ✅ Impact                                                         |
| -------------------- | ----------------------------------------------- | ------------------------------------------------------------------------ |
| ❌ **Without IRSA** | 🔑 Store AWS access keys inside Pods            | ⚠️ Security risk (key leakage, hard to rotate)                            |
| ✅ **With IRSA**    | 🔄 Pod gets temporary credentials automatically | 🔐 More Secure (no keys, auto-rotated via STS `Security Token Service` ) |

## IRSA (IAM Roles for Service Accounts) in Amazon EKS, including OIDC provider + Trust Policy + Pod usage
| 🔢 Step | 📖 Action                              | 🧠 How It Works                                                      | 💡 Why It Matters                |
| ------- | -------------------------------------- | -------------------------------------------------------------------- | -------------------------------- |
| 1️⃣     | 🔗 Enable OIDC Provider                | 👉 Connects EKS cluster with AWS IAM                                 | Required for identity federation |
| 2️⃣     | 📜 Create IAM Policy                   | 👉 Define permissions (e.g., S3 access)                              | Least privilege access           |
| 3️⃣     | 🤖 Create IAM Role (Trust Policy)      | 👉 Allows specific ServiceAccount to assume role                     | Secure role assumption           |
| 4️⃣     | 👤 Create ServiceAccount               | 👉 Kubernetes identity for Pod                                       | Pod identity                     |
| 5️⃣     | 🏷 Attach IAM Role to ServiceAccount   | 👉 Add annotation `eks.amazonaws.com/role-arn`                       | Link AWS + K8s                   |
| 6️⃣     | 📦 Run Pod with ServiceAccount         | 👉 Pod uses that ServiceAccount                                      | Identity applied                 |
| 7️⃣     | 🌐 Pod assumes IAM Role via OIDC token | 👉 Uses `sts:AssumeRoleWithWebIdentity` → gets temporary credentials | No secrets needed 🔐             |

## 🧩 Step 1: Create / Verify EKS Cluster
  * You need an EKS cluster

## 🔐 Step 2: Enable OIDC Provider (VERY IMPORTANT)
  * Check if OIDC is already enabled:
```json
aws eks describe-cluster \
  --name my-cluster \
  --query "cluster.identity.oidc.issuer" \
  --output text
```
### 👉 If not enabled, run:
```json
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

## 🔑 Step 4: Create IAM Policy
  * 👉 Example: Allow S3 access
       * policy.json
```json
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
```Bash
aws iam create-policy \
  --policy-name $POLICY_NAME \
  --policy-document file://policy.json
```
## 🧩 Step 5: Create Trust Policy (CRITICAL 🔥)

 * 👉 This defines which Kubernetes ServiceAccount can assume the role
 * 🔐 Trust Policy Example :
       * trust-policy.json
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Federated": "arn:aws:iam::<ACCOUNT_ID>:oidc-provider/oidc.eks.ap-south-1.amazonaws.com/id/EXAMPLE"
      },
      "Action": "sts:AssumeRoleWithWebIdentity",
      "Condition": {
        "StringEquals": {
          "oidc.eks.ap-south-1.amazonaws.com/id/EXAMPLE:sub": "system:serviceaccount:default:my-app",            # ✅ which Kubernetes ServiceAccount is allowed to assume the IAM role
          "oidc.eks.ap-south-1.amazonaws.com/id/EXAMPLE:aud": "sts.amazonaws.com"
        }
      }
    }
  ]
}
```

 * 👉 "This trust policy allows a specific Kubernetes ServiceAccount (`default:my-app`) to assume an IAM role using OIDC via `AssumeRoleWithWebIdentity`.
 * 🚨 Why Condition is Mandatory
   * Without this:
       * ❌ Any pod in cluster could assume the role
       * ✅ With this → only specific ServiceAccount can use it
       * Trust Policy (THE HEART ❤️) : 👉 Which Pod is allowed to use this role..

### ` "oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>:sub": "system:serviceaccount:default:my-app" `
| 🧩 **Part**                                       | 💡 **Meaning**                                       | 🧠 **Explanation**                                    | 🔒 **Security Insight**                      |
| ------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------ | -------------------------------------------- |
| 🌐 `oidc.eks.<region>.amazonaws.com/id/<OIDC_ID>` | OIDC provider for your EKS cluster (“Which cluster?”) | 👉 Unique identity provider linked to your cluster    | Ensures requests come from your cluster only |
| 🔑 `:sub`                                         | “Who is requesting?”                                  | 👉 Refers to the **caller identity** in OIDC token    | Used to match exact ServiceAccount           |
| 🧬 `system:serviceaccount:default:my-app`         | Kubernetes ServiceAccount identity                    | 👉 Format: `system:serviceaccount:<namespace>:<name>` | Restricts access to a specific Pod identity  |
| 🧬 `system:serviceaccount`                        | Kubernetes identity type (“Exact Pod identity”)       | 👉 Indicates a ServiceAccount identity                | 🔑 Required for IRSA                      |
| 📂 `default`                                      | Namespace                                             | 👉 Namespace where the ServiceAccount exists           | 📦 Limits scope to namespace               |
| 📦 `my-app`                                       | ServiceAccount name                                   | 👉 Specific ServiceAccount allowed                     | 🎯 Only this Pod gets access              |
| 🌐 **`Federated`**                                | OIDC provider (EKS identity source)                   | 👉 Points to your cluster’s OIDC provider ARN          | Ensures only your cluster can request access |
| 🎯 **`aud`**                                      | Token audience                                     | 👉 Must be `sts.amazonaws.com`  (🔑 AWS Security Token Service)    | Ensures token is intended for AWS STS  |
| 🔐 **`sts:AssumeRoleWithWebIdentity`**            | Action for role assumption                           | 👉 Allows OIDC-based role assumption                     | Enables secure, token-based access           |

  * In IRSA
     * the trust policy uses the `OIDC provider` and
     * the `sub` claim to strictly map an `IAM role` to a `specific Kubernetes ServiceAccount`, ensuring secure and scoped access.”

#### 🔐 AWS STS Actions :

| 🧩 Action                              | 🎯 Purpose                                         | 🧠 How It Works                                          | 💡 Common Use Case                      |
| -------------------------------------- | --------------------------------------------------- | --------------------------------------------------------- | --------------------------------------- |
| 🔑 **`sts:AssumeRole`**                | 👤 Assume role using AWS identity                  | 👉 `IAM User/Role` requests temporary credentials via AWS | EC2 instance role, cross-account access |
| 🌐 **`sts:AssumeRoleWithWebIdentity`** | 🔗 Assume role using external identity (`OIDC/JWT`) | 👉 Uses OIDC token (no AWS credentials needed)           | EKS IRSA, social login (Google, etc.)   |

## 🧩 Step 6: Create IAM Role
```json
aws iam create-role \
  --role-name my-irsa-role \
  --assume-role-policy-document file://trust-policy.json
```
#### 🔗 Attach Policy to Role
```json
aws iam attach-role-policy \
  --role-name my-irsa-role \
  --policy-arn arn:aws:iam::<ACCOUNT_ID>:policy/my-irsa-policy
```

## 🧩 Step 7: Create Kubernetes ServiceAccount with annotations
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: my-app
  namespace: default
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::<ACCOUNT_ID>:role/my-irsa-role
```
```Bash
kubectl apply -f sa.yaml
```

## 🧩 Step 8: Create Pod using ServiceAccount
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: aws-test
spec:
  serviceAccountName: my-app
  containers:
  - name: aws-cli
    image: amazon/aws-cli
    command: ["sleep", "3600"]
```
```Bash
kubectl apply -f pod.yaml
```

## 🧩 Step 7: Verify Inside Pod
  * Command : `kubectl exec -it aws-test -- sh`
  * Check identity `aws sts get-caller-identity`  Output should show `IAM Role ARN`


## 🔐 IRSA Internal Flow

| 🔢 Step | 📖 What Happens                   | 🧠 How It Works                                                    | 💡 Key Insight       |
| ------- | --------------------------------- | ------------------------------------------------------------------ | -------------------- |
| 1️⃣     | 📦 Pod starts with ServiceAccount | 👉 Pod is associated with a specific ServiceAccount                | Identity defined     |
| 2️⃣     | 🔗 OIDC token injected            | 👉 Kubernetes mounts JWT token inside Pod (`/var/run/secrets/...`) | Used for auth        |
| 3️⃣     | 🌐 Pod calls AWS STS              | 👉 Uses `AssumeRoleWithWebIdentity` API                            | No AWS keys needed   |
| 4️⃣     | 🔍 STS validates token            | 👉 Verifies token with OIDC provider                               | Ensures authenticity |
| 5️⃣     | 🔐 Trust policy checked           | 👉 Matches `sub` (SA identity) and `aud` (`sts.amazonaws.com`)     | Authorization step   |
| 6️⃣     | ⏳ Temporary credentials returned  | 👉 STS issues short-lived credentials (AccessKey, Secret, Token)   | Secure access        |
| 7️⃣     | ☁️ Pod accesses AWS services      | 👉 Uses credentials to access S3, DynamoDB, etc.                   | Fully secure         |


## ⚠️ IRSA Common Mistakes (VERY IMPORTANT)

| ❌ Mistake                    | 📖 What Goes Wrong               | 💡 Fix                                   |
| ---------------------------- | -------------------------------- | ---------------------------------------- |
| 🔗 OIDC not created          | IRSA won’t work at all           | 👉 Enable OIDC provider for EKS          |
| 🧬 Wrong `sub` format        | Role assumption fails            | 👉 Use `system:serviceaccount:<ns>:<sa>` |
| 📂 Namespace mismatch        | Token doesn’t match trust policy | 👉 Ensure correct namespace              |
| 🎯 Missing `aud`             | Token validation fails           | 👉 Set `sts.amazonaws.com`               |
| 🏷 Wrong Role ARN annotation | Pod not linked to IAM Role       | 👉 Check `eks.amazonaws.com/role-arn`    |
| 📦 Wrong ServiceAccount      | Pod uses default SA → no access  | 👉 Assign correct SA in Pod spec         |

## 🔐 IRSA Security Best Practices

| ✅ Practice                | 💡 Why It Matters                         |
| ------------------------- | ----------------------------------------- |
| 🎯 Least privilege        | Limit access to only required AWS actions |
| 🧩 Separate roles per app | Avoid shared blast radius                 |
| 🚫 Avoid `*`              | Prevent over-permission                   |
| 📂 Restrict namespace     | Limit role usage to specific namespace    |
| 🔍 Audit regularly        | Detect misuse & improve security          |

---

# 🔐 Pod getting AccessDenied (IRSA) – What to Check

| 🧩 Check Item                | 📖 What to Verify                              | 💡 Why It Matters             |
| ---------------------------- | ---------------------------------------------- | ----------------------------- |
| 🔗 **OIDC Provider**         | OIDC is enabled for EKS cluster                | Required for IRSA to work     |
| 🔐 **Trust Policy (`sub`)**  | Matches `system:serviceaccount:<ns>:<sa>`      | Ensures correct Pod identity  |
| 📂 **Namespace**             | ServiceAccount is in correct namespace         | Mismatch = access denied      |
| 🏷 **Role ARN Annotation**   | `eks.amazonaws.com/role-arn` on ServiceAccount | Links IAM Role to Pod         |
| 🎯 **`aud` Condition**       | Usually `sts.amazonaws.com`                    | Required for token validation |
| 📦 **ServiceAccount in Pod** | Pod uses correct ServiceAccount                | Default SA won’t have access  |
 * 👉 “Most common issue is mismatch in namespace or ServiceAccount name.”

# 🚀 Multiple ServiceAccounts to use one IAM role
   * 👉 Use StringLike in trust policy:
```json
"Condition": {
  "StringLike": {
    "oidc.eks.region.amazonaws.com/id/xxx:sub": [
      "system:serviceaccount:default:app1",
      "system:serviceaccount:default:app2"
    ]
  }
}
```
 * 👉 OR allow `namespace-wide` (careful ⚠️): `system:serviceaccount:default:*`
 * 👉 “But I prefer `least privilege` — restrict to specific ServiceAccounts.”

## Same ServiceAccount name but different namespace — will it work?”

 * 👉 No, it will fail. : `system:serviceaccount:dev:my-app ≠ system:serviceaccount:prod:my-app` 👉 Namespace is part of identity

## You recreated EKS cluster, IRSA stopped working. Why?

  * 👉 “OIDC provider ID changes when cluster is recreated.”
  * Fix: `Update trust policy` with `new OIDC ID`

## 🚀 What happens when OIDC token expires?

 * 👉 “Kubernetes automatically refreshes token, and AWS SDK fetches new credentials.”
 * 👉 No manual rotation needed ✅

## 🚀 Why do we add `aud: sts.amazonaws.com`?

  * 👉 “It ensures the token is intended for `AWS STS` and prevents misuse of token elsewhere.”

## 🚀 🔟 Someone Used Wildcard * : Trust policy has `system:serviceaccount:*:* ` — what’s wrong?”

  * 👉 “It allows all ServiceAccounts in all namespaces — very risky.”
  * 👉 Fix: Restrict to specific namespace or SA

## 🚀 Why IRSA not working when Pod uses default ServiceAccount?

  * 👉 Default ServiceAccount usually `doesn't have role annotation`.
  * Fix: `Add annotation` OR use `custom ServiceAccount`.


# 🎯 One-Line Summary
   * Trust policy defines `who can assume the role`, while permission policy defines `what they can do`.
   * 👉 CLI IRSA flow: OIDC → Trust Policy → IAM Role → ServiceAccount annotation → Pod → STS temporary credentials


