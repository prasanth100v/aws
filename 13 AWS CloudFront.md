# 🌐 AWS CloudFront
![InShot_20260327_214504681 jpg](https://github.com/user-attachments/assets/25c157bc-e491-4f89-b74a-cf87c73eb057)
## What is AWS CloudFront?
 * AWS CloudFront is a content delivery network (CDN) that speeds up the delivery of your `website`, `videos`, `APIs`, and other web content to users across the world.
 * It caches content at edge locations (`data centers worldwide`), reducing latency and improving performance..

## 🚀 Key Features
 * **Global Edge Network** – Distributes content closer to users.
 * **Low Latency & High Speed** – Delivers data quickly by serving it from the `nearest edge location`.
 * **Security** – Supports `AWS Shield`,` WAF`, and `SSL/TLS` encryption to protect content.
 * **Integration with AWS Services** – Works with `S3`, `EC2`, `Load Balancers`, and `API Gateway` for seamless content delivery.
 * **Caching** – CloudFront caches content at edge locations, `reducing the load on origin servers `and improving content delivery speed.
 * **Pay-as-you-go Pricing** – No upfront costs; you pay for data transfer and requests.

---

## ⚡ How CloudFront Works
 * CloudFront caches content at edge locations, reducing the load on origin servers and speeding up content delivery.
   * **Web Distributions** – Deliver `HTTP/HTTPS` content.
   * **RTMP Distributions** – Stream media content. (Real-Time Messaging Protocol)

## 📍 Edge Location
 * An Edge Location is a data center where CloudFront stores cached content for fast delivery to users.

## 🔗 Supported Origins
 * CloudFront supports multiple origin types:
   * Amazon S3 buckets
   * HTTP/HTTPS servers
   * AWS Elastic Load Balancers

---

## 🛠️ Steps to Create CloudFront Distribution
| 🔢 Step    | 🛠️ Action                  | 📘 Details                                                                                                       |
| ---------- | --------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| ☁️ **1️⃣** | 🌐 **Go to AWS CloudFront** | Open [AWS Management Console] and navigate to CloudFront                                                       |
| ➕ **2️⃣**  | 🚀 **Create Distribution**  | Click **Create Distribution**                                                                                    |
| 📦 **3️⃣** | 🔗 **Choose an Origin**     | Select content source                                                                                            |
|            | 🪣 🖥️ ⚖️                  | Amazon S3 Bucket, EC2 Instance and Load Balancer (ALB/ELB)                                                   |
| ⚙️ **4️⃣** | 🔒 **Set Cache & Security** | Configure caching behavior                                                                                       |
|            | 🌍                          | Enable HTTPS                                                                                                     |
|            | 📡                          | Configure allowed HTTP methods                                                                                   |
|            | ⚡                           | Set cache policies                                                                                               |
| ✅ **5️⃣**  | 🚀 **Deploy Distribution**  | Click **Create** and wait for deployment                                                                         |
| 🌐 **6️⃣** | 🔗 **Use CloudFront URL**   | Access content faster using generated URL                                                                         |
|            | 📌                          | Example: `abc123.cloudfront.net`                                                                                 |

---

## 🎯 Summary
 * AWS CloudFront improves application performance by caching content at global edge locations, reducing latency, enhancing security, and enabling fast and reliable content delivery across the world.

---

## ⚡ AWS CloudFront — Rapid Fire Q&A
| #️⃣    | ❓ Question                                             | ✅ Answer                                                           |
| ------ | ------------------------------------------------------ | ------------------------------------------------------------------ |
| 1️⃣    | 🌍 What is Amazon CloudFront?                          | 👉 CDN (Content Delivery Network) service from Amazon Web Services |
| 2️⃣    | 🚀 Main purpose of CloudFront?                         | 👉 Deliver content globally with low latency                       |
| 3️⃣    | 📦 What type of content can CloudFront deliver?        | 👉 Static, dynamic, video, APIs                                    |
| 4️⃣    | 🌐 What is a CDN?                                      | 👉 Network of edge locations caching content near users            |
| 5️⃣    | ⚡ Main advantage of CloudFront?                        | 👉 Faster content delivery                                         |
| 6️⃣    | 📍 What are Edge Locations?                            | 👉 Global AWS locations serving cached content                     |
| 7️⃣    | 🧠 How does CloudFront reduce latency?                 | 👉 Serves content from nearest edge location                       |
| 9️⃣    | ☁️ Common CloudFront origins?                          | 👉 S3, ALB, EC2, API Gateway                                       |
| 🔟     | 🪣 Can S3 be used as CloudFront origin?                | 👉 ✅ Yes                                                           |
| 1️⃣1️⃣ | ⚖️ Can ALB be used as origin?                          | 👉 ✅ Yes                                                           |
| 1️⃣2️⃣ | 📡 What happens on cache miss?                         | 👉 CloudFront fetches content from origin                          |
| 1️⃣3️⃣ | ⚡ What happens on cache hit?                           | 👉 Content served directly from edge cache                         |
| 1️⃣4️⃣ | 🧾 What is cache behavior?                             | 👉 Rules controlling caching and routing                           |
| 1️⃣5️⃣ | ⏳ What is TTL in CloudFront?                           | 👉 Cache duration before refresh                                   |
| 1️⃣6️⃣ | 🔄 Lower TTL advantage?                                | 👉 Faster updates                                                  |
| 1️⃣7️⃣ | 💰 Higher TTL advantage?                               | 👉 Better performance and lower origin load                        |
| 1️⃣8️⃣ | 🔐 Can CloudFront enforce HTTPS?                       | 👉 ✅ Yes                                                           |
| 1️⃣9️⃣ | 🛡️ What SSL/TLS certificates are commonly used?       | 👉 ACM certificates                                                |
| 2️⃣0️⃣ | 🌍 Can CloudFront use custom domains?                  | 👉 ✅ Yes                                                           |
| 2️⃣1️⃣ | 📛 Example custom domain setup?                        | 👉 Route 53 Alias → CloudFront                                     |
| 2️⃣8️⃣ | 🎥 Can CloudFront stream video?                        | 👉 ✅ Yes                                                           |
| 2️⃣9️⃣ | 🌎 Is CloudFront globally distributed?                 | 👉 ✅ Yes                                                           |
| 3️⃣0️⃣ | 🔐 Can CloudFront restrict geographic access?          | 👉 ✅ Yes                                                           |
| 3️⃣1️⃣ | 🌍 What is Geo Restriction?                            | 👉 Block/allow specific countries                                  |
| 3️⃣2️⃣ | 🛡️ Can CloudFront integrate with WAF?                 | 👉 ✅ Yes                                                           |
| 3️⃣3️⃣ | 🔥 Purpose of AWS WAF with CloudFront?                 | 👉 Protect against web attacks                                     |
| 3️⃣4️⃣ | 🚨 Example attacks blocked by WAF?                     | 👉 SQL injection, XSS                                              |
| 3️⃣5️⃣ | ⚡ Can CloudFront improve DDoS protection?              | 👉 ✅ With AWS Shield                                               |
| 3️⃣6️⃣ | 📊 What monitoring service integrates with CloudFront? | 👉 CloudWatch                                                      |
| 3️⃣7️⃣ | 📜 Can CloudFront logs be stored?                      | 👉 ✅ In S3                                                         |
| 3️⃣8️⃣ | 📈 What metrics can CloudFront monitor?                | 👉 Requests, errors, cache hit ratio                               |
| 3️⃣9️⃣ | 📡 What is cache hit ratio?                            | 👉 Percentage served from cache                                    |
| 4️⃣0️⃣ | ⚠️ Low cache hit ratio means?                          | 👉 More origin requests                                            |
| 4️⃣1️⃣ | 🔄 Can CloudFront serve dynamic APIs?                  | 👉 ✅ Yes                                                           |
| 4️⃣2️⃣ | 🚀 Why use CloudFront with APIs?                       | 👉 Lower latency and protection                                    |
| 4️⃣3️⃣ | ☸️ Can CloudFront work with EKS apps?                  | 👉 ✅ Yes                                                           |
| 4️⃣4️⃣ | 🌐 Typical Kubernetes integration?                     | 👉 CloudFront → ALB → Ingress                                      |
| 4️⃣5️⃣ | 📂 Can multiple origins exist in one distribution?     | 👉 ✅ Yes                                                           |
| 4️⃣6️⃣ | 🎯 Example multiple-origin use case?                   | 👉 Static files from S3 + APIs from ALB                            |
| 4️⃣7️⃣ | 🔄 What is origin failover?                            | 👉 Backup origin if primary fails                                  |
| 4️⃣8️⃣ | ⚠️ Website updated but old content shown — why?        | 👉 Cached content not expired                                      |
| 5️⃣1️⃣ | 🐢 Website slow globally — solution?                   | 👉 Use CloudFront CDN                                              |
| 5️⃣2️⃣ | 🔐 Why use HTTPS-only viewer policy?                   | 👉 Encrypt client communication                                    |
| 5️⃣3️⃣ | 📦 Best origin for static website files?               | 👉 S3                                                              |
| 5️⃣4️⃣ | 🌍 Best AWS service for global low-latency delivery?   | 👉 CloudFront                                                      |
| 5️⃣5️⃣ | 💰 CloudFront pricing based on?                        | 👉 Data transfer and requests                                      |
| 5️⃣6️⃣ | ⚡ Why reduce origin load with CloudFront?              | 👉 Edge caching serves repeated requests                           |
| 5️⃣7️⃣ | 📛 Can Route 53 integrate with CloudFront?             | 👉 ✅ Yes                                                           |
| 5️⃣8️⃣ | 🔗 Common Route 53 record type for CloudFront?         | 👉 Alias record                                                    |
| 5️⃣9️⃣ | 💻 AWS CLI command to list distributions?              | 👉 `aws cloudfront list-distributions`                             |
| 6️⃣0️⃣ | 🚀 One-line interview definition of CloudFront?        | 👉 Global CDN service for secure, low-latency content delivery     |
