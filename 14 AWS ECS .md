# 🚀 AWS ECS (Elastic Container Service)
## What is AWS ECS?

Amazon Elastic Container Service (ECS) is a fully managed container orchestration service that helps deploy, manage, and scale containerized applications on AWS. ECS is designed specifically for Docker containers.

## ⚙️ Launch Types

ECS supports two launch types:

* **EC2 Launch Type** – Runs containers on EC2 instances.
* **Fargate Launch Type** – A serverless compute engine for running containers without managing EC2 instances.

---

## 📄 Task Definition

A Task Definition is a blueprint for running a container in ECS. It includes details like:

* Container image
* CPU & memory
* Networking
* Logging
* IAM roles

👉 Defined in JSON format.


## 🧩 Task vs Service

### 🔹 Task

A Task is one running container or a group of containers.

* Runs based on a Task Definition
* Example: Running an Nginx web server once
* Runs once and stops (no auto-restart)

### 🔹 Service

A Service ensures that tasks keep running.

* Automatically restarts failed tasks
* Can scale number of tasks
* Example: Run 3 Nginx containers continuously


## 💾 Storage Support

ECS supports Amazon EFS for persistent storage, enabling stateful applications.


# 🛠️ Steps to Create AWS ECS Setup
## 1️⃣ Set Up Prerequisites

* AWS Account
* IAM Role (e.g., AmazonECSTaskExecutionRolePolicy)
* Docker Image (push to Amazon ECR or Docker Hub)

## 2️⃣ Create an ECS Cluster

1. Go to ECS Dashboard
2. Click **Create Cluster**
3. Choose cluster template:

   * Networking Only → Fargate
   * EC2 Linux + Networking → EC2
   * Custom → Advanced
4. Configure:

   * Cluster name
   * EC2 (if applicable): instance type, VPC, subnets, security groups
5. Click **Create**

👉 Cluster is ready!

---

## 3️⃣ Create Task Definition

Example: Nginx container

* Go to Task Definitions → Create new
* Select launch type (Fargate/EC2)
* Name: `nginx-task`
* CPU: 256
* Memory: 512

### Add Container:

* Name: `nginx-container`
* Image: `nginx:latest`
* Port: 80

(Optional): Add env variables, storage, logging

👉 Click **Create**


## 4️⃣ Create ECS Service

Example: Deploy Nginx

1. Go to ECS Cluster → Create Service
2. Select:

   * Launch Type: Fargate/EC2
   * Task Definition: nginx-task
   * Tasks: 1
3. Configure networking:

   * VPC
   * Subnets
   * Security Group (allow port 80)
4. (Optional) Attach Load Balancer (ALB/NLB)
5. Click **Create Service**

👉 Service is running!

## 5️⃣ Verify and Test

* Check tasks & services status
* Use ALB/NLB DNS (if enabled)
* Monitor logs in CloudWatch

## 6️⃣ (Optional) Clean Up

* Delete ECS service
* Stop tasks
* Delete cluster

👉 Avoid unnecessary charges

---

## 🎯 Summary

AWS ECS simplifies container deployment by managing infrastructure, scaling, and availability. With support for EC2 and Fargate, it provides flexible options for running containerized workloads efficiently.
