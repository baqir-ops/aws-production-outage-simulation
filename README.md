# 🚨 AWS Production Outage Simulation & Root Cause Analysis

## Overview
This project simulates a real-world AWS production outage scenario where
EC2 instances running in private subnets were unreachable through an
Application Load Balancer (ALB).

The issue was identified using CloudWatch alarms and ALB health checks,
and resolved by fixing private subnet routing using a NAT Gateway.

---

## Architecture
- VPC with public and private subnets
- EC2 instances in private subnets
- Apache HTTP server installed
- Application Load Balancer (internet-facing)
- Target Groups with health checks
- CloudWatch alarms
- NAT Gateway and Route Tables
- VPC Interface Endpoints

---

## 📸 Screenshots (Proof of Work)

### VPC Setup
![VPC Created](screenshots/vpc-created.png)


### EC2 & Apache
![Webserver Created](screenshots/webserver-created.png)
![Apache Running](screenshots/apache-running.png)


### Load Balancer & Target Group Issue
![Load Balancer Created](screenshots/created-loadbalancer.png)
![Target Group Unhealthy](screenshots/target-group-unhealthy.png)
![ALB Alarm](screenshots/alb-unhealthyhost-count.png)


### Monitoring & Access Issue
![Session Manager Issue](screenshots/session-manager-issue.png)


### Networking Fix
![Private Route Table Before Fix](screenshots/private-route-table-before-fix.png)
![Private Route Table After Fix](screenshots/private-route-table-after-fix.png)
![VPC Endpoints](screenshots/endpoints-created.png)

### Final Result
![Target Group Healthy](screenshots/target-group-healthy.png)


---

## Root Cause Analysis
- EC2 instances were deployed in private subnets
- No proper outbound routing initially
- ALB health checks failed
- CloudWatch alarm triggered for unhealthy hosts

---

## Resolution
- Verified Apache service running on EC2
- Fixed private subnet route table
- Enabled required networking components
- ALB target group became healthy

---

## Key Learnings
- Troubleshooting ALB health checks
- Importance of private subnet routing
- Using CloudWatch alarms for outage detection
- Real-world AWS production issue simulation

---

## Author
Muhammad Baqir Nawaz
