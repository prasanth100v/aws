# 🌈 AWS Lambda 
## 🚀 What is AWS Lambda?
 * AWS Lambda is a **serverless compute service** that runs your code **without managing servers**.
 * 👉 Focus on writing code, AWS handles infrastructure.
 * 🎯 AWS Lambda = Run code `without servers`, pay only for `execution`..
 * 💡 Ideal for:
    * Microservices
    * Automation
    * Cost-efficient workloads

## ⚡ Why Use AWS Lambda?
  * 🚫 No server management
  * 💰 Cost-efficient (`pay only when used`)
  * 🚀 Auto scaling
  * ⚡ Fast deployment

### 🎉 Simple Analogy
  * Traditional servers = Owning a restaurant 🍽️
  * AWS Lambda = Ordering food only when hungry 🍱
     * ✔ No infrastructure management
     * ✔ Pay only when used

## ✨ Key Features
### ⚡ Automatic Scaling
 * Scales automatically based on demand
 * Handles thousands of requests automatically
 * No manual scaling needed

## 💰 Pay-per-Use
 * Charged only for execution time ⏱️ (`milliseconds`)
 * Number of requests 📊

## 🌍 Multi-Language Support
 * Supports :
    * Python 🐍
    * Node.js 🟢
    * Java ☕
    * Go 🐹
    * Ruby 💎
    * .NET ⚙️

## 🔗 AWS Integrations with :
  * 📦 S3
  * 🗄️ DynamoDB
  * 🌐 API Gateway
  * 📬 SNS
  * 📥 SQS
  * 📊 CloudWatch

## 🔄 Cold Start vs Warm Start
| 🧩 **Type**       | 📖 **Description**           | 🧠 **What Happens**                            | ⏱️ **Performance** | 💡 **Common Scenario**         |
| ----------------- | ---------------------------- | ----------------------------------------------- | ------------------ | ------------------------------ |
| ❄️ **Cold Start** | First execution of Lambda    | AWS creates new execution environment/container | 🐢 Slower          | First request after inactivity |
| 🔥 **Warm Start** | Reused execution environment | Existing Lambda container reused                | ⚡ Faster          | Frequent/continuous requests   |

---

# 💵 Pricing Model
## 🧮 Compute Time
 * Based on **GB-seconds**
 * (Memory × Execution time)
```hcl
Cost = Memory (GB) × Execution Time (seconds)
```

## 📩 Requests
 * 🆓 First 1 million requests/month Free
 * After that:💲 `$0.20 per 1 million requests `
 * 💸 Additional Costs
     * Storage 📦
     * Data transfer 🌐
     * Other AWS services

### ⚠️ Limits of AWS Lambda
| 🧩 **Resource**                 | 📏 **Limit**        | 🧠 **Detailed Explanation**                                 | 💡 **Why It Matters**              |
| ------------------------------- | -------------------- | ----------------------------------------------------------- | ---------------------------------- |
| 🧠 **Memory**                   | `128 MB → 10 GB`     | Controls RAM allocated to function (CPU scales with memory) | More memory = better performance   |
| ⏱️ **Timeout**                  | `Maximum 15 minutes` | Lambda execution stops after timeout                        | Not suitable for long-running jobs |
| 📦 **Deployment Package Size**  | `250 MB (unzipped)`  | Includes code + dependencies + layers                       | Large frameworks may exceed limit  |
| 💾 **Ephemeral Storage (/tmp)** | `512 MB → 10 GB`     | Temporary storage available during execution                | Useful for file processing         |

### 🔔 Lambda Triggers
  * 📁 S3 (file `upload/delete`)
  * 🌐 API Gateway (`HTTP requests`)
  * 🗄 DynamoDB Streams (DB updates trigger function)
  * 📬 SNS / SQS

## 🌐 Lambda in VPC
  * Can run inside a **VPC**
  * Access private resources:
    * RDS
    * EC2

### 📦 Lambda with Containers
 * Supports container images
 * Max size: **10 GB**
 * Stored in **Amazon ECR**

## 💡 Real-World Example
* 👉 When a user makes a purchase:

```hcl
User buys product 🛒
        ↓
Trigger Lambda 🔔
        ↓
Send "Thank You" Email 📧
```
### 📚 Lambda Layers
 * Share code/dependencies across functions
 * Reduce duplication

# 🛠️ Steps to Create AWS Lambda
| 🔢 Step       | 🛠️ Action                       | 📘 Details                                                                            |
| ------------- | -------------------------------- | ------------------------------------------------------------------------------------- |
| 🔐 **1️⃣**    | ☁️ **Login to AWS Console**      | Open [AWS Management Console](https://aws.amazon.com/console/?utm_source=chatgpt.com) |
|               | 🔑                               | Sign in to your AWS account                                                           |
| ⚡ **2️⃣**     | 📂 **Open Lambda Service**       | Search for **Lambda**                                                                 |
|               | 🌐                               | Open the **AWS Lambda Dashboard**                                                     |
| ➕ **3️⃣**     | 🚀 **Create Function**           | Click **Create function**                                                             |
| ⚙️ **4️⃣**    | 📝 **Choose Creation Method**    | Select **Author from scratch**                                                        |
| 🏷️ **5️⃣**   | 🛠️ **Configure Basic Settings** | Enter Lambda function details                                                         |
|               | 📛                               | **Function Name:** `MyLambdaFunction`                                                 |
|               | 💻                               | **Runtime:** Python / Node.js / Java etc.                                             |
|               | 🐍                               | Example: `Python 3.12`                                                                |
| 🔐 **6️⃣**    | 🛡️ **Configure Permissions**    | Choose existing IAM Role                                                              |
|               | ✅                                | Or select **Create a new role with basic Lambda permissions**                         |
| ✅ **7️⃣**     | 🎯 **Create Function**           | Click **Create function**                                                             |
| 💻 **8️⃣**    | ✍️ **Add Function Code**         | Write your Lambda code in the Code section / upload ZIP  &  Add trigger (optional)    |
| 🚀 **9️⃣**    | 📦 **Deploy Function**           | Click **Deploy**                                                                      |
| 🧪 **🔟**     | ⚡ **Test Lambda Function**       | Click **Test**                                                                        |
|               | 📝                               | Create test event                                                                     |
|               | ▶️                               | Click **Test** again                                                                  |
| 📊 **1️⃣1️⃣** | 📜 **View Execution Result**     | Check response and CloudWatch logs                                                    |


## 🔄 Lambda Execution Flow
  ```hcl
Event Trigger 🔔
      ↓
Lambda Function ⚙️
      ↓
Processing Logic 🧠
      ↓
Response / Action 🚀
```

---

# 🎯 Best Practices
 * ✅ Keep functions small & single-purpose
 * ✅ Use environment variables
 * ✅ Monitor with CloudWatch
 * ✅ Optimize memory for performance
 * ✅ Use IAM roles securely

## 🧠 Final Summary
 * ✔ Serverless compute
 * ✔ Auto scaling + cost efficient
 * ✔ Deep AWS integration  

---

## ⚡ AWS Lambda — Rapid Fire Q&A
| ❓ Question                                   | ✅ Answer                                                              |
| -------------------------------------------- | --------------------------------------------------------------------- |
| 🚀 What is AWS Lambda?                       | 👉 Serverless compute service that runs code without managing servers |
| ☁️ What is serverless computing?             | 👉 Running applications without provisioning/managing infrastructure  |
| ⭐ Main advantage of Lambda?                  | 👉 Auto scaling + pay only for execution time                         |
| ⚙️ How does Lambda execute code?             | 👉 In response to events/triggers                                     |
| 🔔 What is an event source?                  | 👉 Service triggering Lambda execution                                |
| 🔗 Common Lambda triggers?                   | 👉 S3, API Gateway, CloudWatch, DynamoDB, SQS                         |
| 💻 Supported runtimes?                       | 👉 Python, Node.js, Java, Go, .NET, Ruby, custom runtime              |
| 📦 Can Lambda run containers?                | 👉 ✅ Yes                                                              |
| 📈 Does Lambda auto scale?                   | 👉 ✅ Yes                                                              |
| 🔄 What is concurrency?                      | 👉 Number of simultaneous executions                                  |
| ⏳ Maximum Lambda timeout?                    | 👉 15 minutes                                                         |
| 🧠 Maximum memory allocation?                | 👉 10 GB                                                              |
| 📂 Temporary storage limit (/tmp)?           | 👉 Up to 10 GB                                                        |
| 💰 How is Lambda priced?                     | 👉 Requests + execution duration + memory                             |
| ❄️ What is a cold start?                     | 👉 Delay during first initialization                                  |
| 🥶 Why do cold starts happen?                | 👉 New execution environment creation                                 |
| 🚚 Deployment methods?                       | 👉 ZIP package or container image                                     |
| 🏗️ IaC tools for Lambda?                    | 👉 Terraform, SAM, CloudFormation                                     |
| 🔐 How Lambda gets AWS permissions?          | 👉 IAM Execution Role                                                 |
| 🚫 Why avoid hardcoded credentials?          | 👉 Security risk                                                      |
| 🌐 Can Lambda run inside VPC?                | 👉 ✅ Yes                                                              |
| 🏢 Why attach Lambda to VPC?                 | 👉 Access private resources like RDS                                  |
| 📊 Which service monitors Lambda?            | 👉 Amazon CloudWatch                                                  |
| 📝 Where are Lambda logs stored?             | 👉 CloudWatch Logs                                                    |
| 🌍 Which service exposes Lambda as REST API? | 👉 API Gateway                                                        |
| 🪣 Can Lambda process S3 uploads?            | 👉 ✅ Yes                                                              |
| 🖼️ Example Lambda use case?                 | 👉 Image resizing after upload                                        |
| ⚡ Why Lambda ideal for event-driven systems? | 👉 Executes automatically on events                                   |
| ❌ What happens if Lambda fails?              | 👉 Retry or send to DLQ                                               |
| 📥 What is DLQ?                              | 👉 Dead Letter Queue for failed events                                |
| 🏷️ What is Lambda versioning?               | 👉 Immutable function snapshots                                       |
| 🎯 What is an alias?                         | 👉 Pointer to Lambda version                                          |
| 🚀 How reduce cold starts?                   | 👉 Provisioned Concurrency, smaller packages                          |
| 📚 What are Lambda Layers?                   | 👉 Shared libraries/dependencies                                      |
| ⚙️ Why use environment variables?            | 👉 Store config separately from code                                  |
| 🛡️ Lambda security best practices?          | 👉 Least privilege IAM, encryption, avoid public exposure             |
| ☸️ Lambda vs Kubernetes?                     | 👉 Lambda = serverless, Kubernetes = container orchestration          |
| 🐢 Why Lambda times out?                     | 👉 Slow APIs, heavy processing, low memory                            |
| 💸 Why Lambda becomes expensive?             | 👉 Infinite loops, high invocations, long execution                   |
| 🔥 What is Provisioned Concurrency?          | 👉 Pre-warmed Lambda environments                                     |
| 📡 What is Lambda destination?               | 👉 Routing results to another service                                 |
| 🖥️ CLI command to invoke Lambda?            | 👉 `aws lambda invoke --function-name myfunc output.txt`              |
| 📃 CLI command to list functions?            | 👉 `aws lambda list-functions`                                        |
| 🚫 When NOT to use Lambda?                   | 👉 Long-running/stateful/GPU workloads                                |
| ⚔️ Lambda vs EC2?                            | 👉 Lambda = serverless, EC2 = full server control                     |
| 🛠️ Common Lambda use cases?                 | 👉 APIs, automation, ETL, notifications                               |
| 🔄 CI/CD tools for Lambda?                   | 👉 GitHub Actions, Jenkins, CodePipeline                              |
| 🚨 Lambda cannot access S3 — why?            | 👉 Missing IAM permissions                                            |
| 🌍 Lambda inside VPC has no internet — why?  | 👉 Missing NAT Gateway                                                |
-
🎉 Happy Learning AWS Lambda!
