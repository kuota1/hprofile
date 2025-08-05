# Prerequisites
#
- JDK 11
- Maven 3
- MySQL 8 

# Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- MySQL
# Database
Here,we used MySQL DB 
MSQL DB Installation Steps for Linux ubuntu 14.04:
- $ sudo apt-get update
- $ sudo apt-get install mysql-server

Then look for the file :
- /src/main/resources/db_backup.sql
The `db_backup.sql` file is a MySQL dump. You need to import it into your MySQL server using:
- > mysql -u <user_name> -p accounts < db_backup.sql

# CI/CD Pipeline with Amazon ECS Fargate

This project demonstrates a complete CI/CD workflow using GitHub Actions to deploy a Dockerized web application to **Amazon ECS (Fargate)** behind an **Application Load Balancer (ALB)**. It also integrates **CloudWatch Logs**, **Amazon RDS (MySQL)**, and **SonarQube** for static code analysis.

---

## 🛠️ Technologies Used

- **AWS ECS Fargate**
- **Amazon RDS (MySQL)**
- **Amazon ECR**
- **Application Load Balancer (ALB)**
- **CloudWatch Logs**
- **GitHub Actions**
- **SonarQube (Cloud version)**
- **Docker**

---

## 📦 Infrastructure Overview

- **Fargate Task Definition** with 1024 CPU units and 2048 MiB memory
- **ECS Service** running behind an **Internet-facing ALB**
- **Target Group** configured to forward traffic on port 8080
- **MySQL RDS instance** connected within the same VPC
- **CloudWatch Logs** enabled for container-level logs
- **ECR** stores Docker image with auto-versioning

---

## ⚙️ CI/CD Pipeline (GitHub Actions)

1. **Testing job** – Run unit/static code checks
2. **Build and Push** – Build Docker image and push to Amazon ECR
3. **Deploy** – Register new task definition and update ECS service

> ✅ The deployment completes successfully in ~2.5 minutes.

---

## 🧪 Code Quality - SonarQube

SonarQube Cloud was used to scan the source code:
- 0% test coverage
- 3.7% duplication
- 866 maintainability issues
- 39 reliability issues

(These results are expected for demo code.)

---

## 🌐 Application Endpoint

> 📍 ALB DNS:  
`http://vproapp-act-elb-1850646019.us-east-1.elb.amazonaws.com/login`

![Login Screen](./screenshots/login.png)

---

## 📸 Screenshots

| Service | Screenshot |
|--------|------------|
| GitHub Actions Workflow | ![Workflow](./screenshots/workflow.png) |
| ECS Deployment | ![ECS](./screenshots/ecs_deploy.png) |
| ALB + CloudWatch Logs | ![ALB + Logs](./screenshots/alb_logs.png) |
| RDS MySQL | ![RDS](./screenshots/rds.png) |
| SonarQube Summary | ![SonarQube](./screenshots/sonarqube.png) |

---

## 🧹 Clean-up

All AWS resources and GitHub actions were destroyed after testing.  
No persistent data or services remain.

---

## 👨‍💻 Author

**Roberto Rodriguez**  
DevOps & Cloud Engineer (AWS Certified)  
GitHub: [kuota1](https://github.com/kuota1)