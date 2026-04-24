 ## What are AWS Support Plans?
  * AWS provides four support plans through Amazon Web Services:
    * Basic
    * Developer
    * Business
    * Enterprise
    * Each plan offers different levels of technical support, response time SLAs, and guidance.
    * SLA → Agreement with customer (e.g., `response time`)

## What is included in Basic Support?

 * Free for all AWS users
 * Access to documentation, whitepapers, forums
 * Billing & account support only
  * ❌ No technical support
  * ❌ No SLA
  * 👉 Used for learning or non-critical workloads

## Which AWS support plan is recommended for production workloads?

 * 👉 Business Support Plan
 * Because:
    * `24×7` support
    * Fast response times
    * Full access to Trusted Advisor
    * Supports production systems

## What is SLA in AWS Support?

 * SLA (`Service Level Agreement`) defines expected response time for `support cases` based on severity.
 * ⚠️ Important:
      * AWS provides `response time SLA`, `not resolution SLA`
      * AWS guarantees response time only, `Resolution` depends on `complexity`

## What is the response time for a critical issue in Business and Enterprise plans?

  * Business → `< 30` minutes
  * Enterprise → `< 15` minutes

## What is a Technical Account Manager (TAM)?

 * A TAM is a dedicated AWS expert available in the Enterprise Support Plan who:
    * Provides architecture guidance
    * Helps with cost optimization
    * Assists in incident management
    * Offers proactive recommendations

## What is AWS Trusted Advisor?

 * A tool in Amazon Web Services that provides recommendations for:
    * Cost optimization
    * Security
    * Performance
    * Fault tolerance
    * 👉 Full access available in `Business` & `Enterprise` plans

## What are the severity levels in AWS Support?

| Severity | Meaning             |
| -------- | ------------------- |
| Critical | System down         |
| Urgent   | Production down     |
| High     | Production impaired |
| Normal   | System impaired     |
| Low      | General guidance    |

## Difference between Business and Enterprise Support?

| Feature             | Business | Enterprise |
| ------------------- | -------- | ---------- |
| Response (critical) | < 30 min | < 15 min   |
| TAM                 | ❌        | ✅          |
| Proactive support   | Limited  | Advanced   |
| Cost                | Lower    | Higher     |

## Is AWS SLA same for all services?

 * ❌ No
 * Each AWS service (EC2, S3, etc.) has its own SLA
 * Support plan SLA is different from service SLA

## What happens if AWS violates SLA?

 * Customers may receive `service credits`
 * Not direct financial compensation
 * ❌ Not direct refund

## Which plan gives 24/7 support?

 * Business & Enterprise
 * 👉 Developer → `Business hours only`

## Your production website is down. Which support plan is required?

 * 👉 At least Business Support Plan
 * Because:
     * 24×7 support
     * Fast response (`<30 min`)

## Why not use Enterprise for all workloads?

 * `High cost` & Not required for `small` or `non-critical systems`
 * Business plan is sufficient for `most production use cases`

## Startup runs production workloads but uses Basic plan to save cost. Is it okay?

 * ❌ Risky decision
 * Because:
    * No technical support, No SLA & No urgent help
    * Recommendation : `At least Business Support Plan`

## Support vs Service SLA Confusion
| 🧩 **Type**        | 📖 **Meaning**          | 🧠 **What It Covers**               | 💡 **Example**                   |
| ------------------ | ----------------------- | ----------------------------------- | -------------------------------- |
| ☁️ **Service SLA** | Uptime guarantee        | 👉 Availability of AWS services     | EC2 = 99.99% uptime              |
| 🛠 **Support SLA** | Response time guarantee | 👉 How quickly AWS support responds | Critical issue → 15 min response |

## You are doing a one-time high-risk production migration. Which plan is best temporarily?

 * 👉 Enterprise (short-term upgrade)
 * Because:
    * Fastest response
    * TAM support
    * Migration guidance

## ⚡ AWS Support Plans – Rapid Fire Q&A

| 🔢     | ❓ Question                        | 💡 Answer                                  |
| ------ | --------------------------------- | ------------------------------------------ |
| 1️⃣    | How many support plans?           | 4 → Basic, Developer, Business, Enterprise |
| 2️⃣    | Which plan is free?               | Basic                                      |
| 3️⃣    | Basic has technical support?      | ❌ No                                       |
| 4️⃣    | Minimum for production?           | 👉 Business                                |
| 5️⃣    | Which has TAM?                    | 👉 Enterprise                              |
| 6️⃣    | Business critical response?       | ⏱️ < 30 mins                               |
| 7️⃣    | Enterprise critical response?     | ⚡ < 15 mins                                |
| 8️⃣    | Resolution time guaranteed?       | ❌ No (only response SLA)                   |
| 9️⃣    | Developer support hours?          | 🕒 Business hours only                     |
| 🔟     | 24/7 support plans?               | 👉 Business & Enterprise                   |
| 1️⃣1️⃣ | Developer for production outages? | ❌ No                                       |
| 1️⃣2️⃣ | SLA meaning?                      | ⏱️ Response time commitment                |
| 1️⃣3️⃣ | TAM?                              | 👤 Technical Account Manager               |
| 1️⃣4️⃣ | Full Trusted Advisor?             | 👉 Business & Enterprise                   |
| 1️⃣5️⃣ | SLA missed → result?              | 💰 Service credits                         |
| 1️⃣6️⃣ | “Production down” severity?       | 🔥 Critical                                |
| 1️⃣7️⃣ | “Slow system” severity?           | ⚠️ High                                    |
| 1️⃣8️⃣ | Misuse severity allowed?          | ❌ No                                       |
| 1️⃣9️⃣ | Support vs Service SLA?           | 🎯 Response vs Uptime                      |
| 2️⃣0️⃣ | Best plan for scaling startup?    | 👉 Business                                |
| 2️⃣1️⃣ | Proactive guidance plan?          | 👉 Enterprise                              |
| 2️⃣2️⃣ | Email support in all plans?       | ❌ No                                       |
| 2️⃣3️⃣ | Phone support available?          | 👉 Business & Enterprise                   |
| 2️⃣4️⃣ | Change plans anytime?             | ✔ Yes (billing applies)                    |
| 2️⃣5️⃣ | Biggest mistake?                  | ❌ Using Basic/Developer for prod           |
| 2️⃣6️⃣ | App down + Developer plan?        | ❌ No immediate support                     |
| 2️⃣7️⃣ | Responded but not fixed → SLA?    | ✔ SLA met                                  |
| 2️⃣8️⃣ | Need architecture reviews?        | 👉 Enterprise                              |
| 2️⃣9️⃣ | Cheapest prod-ready plan?         | 👉 Business                                |
| 3️⃣0️⃣ | Who provides support plans?       | ☁️ Amazon Web Services                     |
