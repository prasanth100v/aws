# 🌐 AWS CloudFront
![InShot_20260327_214504681 jpg](https://github.com/user-attachments/assets/25c157bc-e491-4f89-b74a-cf87c73eb057)

![IMG_20260327_215740 jpg](https://github.com/user-attachments/assets/ddbcc1c7-d4e1-4983-8853-f216c80a6b38)

## What is AWS CloudFront?

AWS CloudFront is a content delivery network (CDN) that speeds up the delivery of your website, videos, APIs, and other web content to users across the world. It caches content at edge locations (data centers worldwide), reducing latency and improving performance.

## 🚀 Key Features

* **Global Edge Network** – Distributes content closer to users.
* **Low Latency & High Speed** – Delivers data quickly by serving it from the nearest edge location.
* **Security** – Supports AWS Shield, WAF, and SSL/TLS encryption to protect content.
* **Integration with AWS Services** – Works with S3, EC2, Load Balancers, and API Gateway for seamless content delivery.
* **Caching** – CloudFront caches content at edge locations, reducing the load on origin servers and improving content delivery speed.
* **Pay-as-you-go Pricing** – No upfront costs; you pay for data transfer and requests.

---

## ⚡ How CloudFront Works

CloudFront caches content at edge locations, reducing the load on origin servers and speeding up content delivery.

* **Web Distributions** – Deliver HTTP/HTTPS content.
* **RTMP Distributions** – Stream media content.

## 📍 Edge Location

An Edge Location is a data center where CloudFront stores cached content for fast delivery to users.


## 🔗 Supported Origins

CloudFront supports multiple origin types:

* Amazon S3 buckets
* HTTP/HTTPS servers
* AWS Elastic Load Balancers

---

## 🛠️ Steps to Create CloudFront Distribution

1. **Go to AWS CloudFront**
   Open the AWS Console and navigate to CloudFront.

2. **Create a Distribution**
   Click on "Create Distribution."

3. **Choose an Origin**
   Select where your content is stored (S3, EC2, or Load Balancer).

4. **Set Cache & Security**
   Configure caching behavior and security settings (HTTPS, allowed methods).

5. **Deploy the Distribution**
   Click "Create" and wait for CloudFront to deploy.

6. **Use CloudFront URL**
   AWS provides a URL like `abc123.cloudfront.net`. Use it to access your content faster.

---

## 🎯 Summary

AWS CloudFront improves application performance by caching content at global edge locations, reducing latency, enhancing security, and enabling fast and reliable content delivery across the world.
