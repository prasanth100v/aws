# IRSA setup using the AWS Console (GUI) step-by-step. No CLI required. 

 * 🚀 What you’ll do in GUI
     * Enable OIDC provider (`EKS`)
     * Create IAM Policy
     * Create IAM Role (with `Trust Policy`)
     * 🚀 Create Kubernetes ServiceAccount (with `annotation`)
     * ♻️ Deploy Pod and verify

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

## 🧩 Step 2: Create IAM Policy (GUI)
  * 👉 Example: Allow S3 access
  * 👉 Steps : Go to AWS IAM
      * Click Policies → Create policy
      * Choose `JSON tab`
      * Paste example:
```JSON
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

## 🧩 Step 3: Create IAM Role (GUI)

| 🔢 Step | 📖 Action                                        | 🧠 How It Works                                                        | 💡 Important Note              |
| ------- | ------------------------------------------------ | ---------------------------------------------------------------------- | ------------------------------ |
| 1️⃣     | 🧭 Go to IAM → Click Roles → Create role         | 👉 Start role creation                                                 | Core IRSA step                 |
| 2️⃣     | 🌐 Select **Trusted entity type = `Web identity`** | 👉 Enables OIDC-based authentication                                   | Required for IRSA              |
| 3️⃣     | 🔗  Identity provider → Select your EKS OIDC provider| 👉 Select EKS OIDC (e.g., `oidc.eks.ap-south-1.amazonaws.com/id/XXXX`) | Links cluster to IAM           |
| 4️⃣     | 🎯 Set Audience                                  | 👉 `sts.amazonaws.com`                                                 | Mandatory for token validation |
| 5️⃣     | 🔐 Add Condition (`sub`)                         | 👉 This binds  specific `ServiceAccount / Namespace `                | Most important security step   |
| 6️⃣     | 📜 Attach Policy                                 | 👉 Select `my-irsa-policy`                                             | Defines AWS permissions        |
| 7️⃣     | 🏷 Add Role Name                                  | 👉 Example: `my-irsa-role`                                             | Use meaningful naming          |
| 8️⃣     | ✅ Create Role                                   | 👉 Finalize                                                            | Ready for use                  |

## 🧩 Step 4: Verify Trust Policy (GUI)

 * After creation:
    * Open the role
    * Go to Trust relationships → `Edit`
 * You should see something like:
```json
{
  "Effect": "Allow",
  "Principal": {
    "Federated": "arn:aws:iam::<ACCOUNT_ID>:oidc-provider/oidc.eks.ap-south-1.amazonaws.com/id/XXXX"
  },
  "Action": "sts:AssumeRoleWithWebIdentity",
  "Condition": {
    "StringEquals": {
      "oidc.eks.ap-south-1.amazonaws.com/id/XXXX:sub": "system:serviceaccount:default:my-app",
      "oidc.eks.ap-south-1.amazonaws.com/id/XXXX:aud": "sts.amazonaws.com"
    }
  }
}
```
 * ✔ If missing → manually fix

## 🧩 Step 5: Create Kubernetes ServiceAccount

  * 👉 This part is NOT in AWS Console
  * 👉 You must use Kubernetes

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: my-app
  namespace: default
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::<ACCOUNT_ID>:role/my-irsa-role
```
```bash
kubectl apply -f sa.yaml
```

## 🧩 Step 6: Deploy Pod
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

---

## ⚠️ IRSA Common GUI Mistakes

| ❌ Mistake                    | 📖 What Goes Wrong                     | 💡 Fix                              |
| ---------------------------- | -------------------------------------- | ----------------------------------- |
| 🔐 Missing `sub` condition   | Anyone with OIDC could assume role     | 👉 Add strict `sub` condition       |
| 📦 Wrong ServiceAccount name | Token won’t match trust policy         | 👉 Verify exact SA name             |
| 📂 Namespace mismatch        | Access denied due to identity mismatch | 👉 Match namespace correctly        |
| 🔗 Wrong OIDC provider       | Token validation fails                 | 👉 Select correct EKS OIDC          |
| 🏷 Missing SA annotation     | Role not linked to Pod                 | 👉 Add `eks.amazonaws.com/role-arn` |
| 🤖 Pod not using SA          | Default SA used → no access            | 👉 Specify SA in Pod spec           |

## 🔐 IRSA Best Practices (Real-World)

| ✅ Practice                     | 💡 Why It Matters            |
| ------------------------------ | ---------------------------- |
| 🧩 One IAM role per app        | Isolates permissions         |
| 📂 Separate namespace per team | Better multi-tenancy         |
| 🔒 Strict `sub` condition      | Prevents unauthorized access |
| 🚫 Avoid `"Resource": "*"`     | Enforces least privilege     |


## 🎯 One-Line Summary

 * 👉 In GUI: EKS OIDC → IAM Role (Web Identity + sub condition) → ServiceAccount annotation → Pod → STS credentials

