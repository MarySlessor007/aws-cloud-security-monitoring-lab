# AWS Cloud Security Monitoring Lab

## Overview

This project demonstrates the deployment, configuration, and monitoring of a secure web server in Amazon Web Services (AWS).

The objective of this lab was to build a production-style cloud environment while applying cloud security best practices, Linux administration, and centralized logging using Amazon CloudWatch.

The project simulates tasks commonly performed by Cloud Engineers, Cloud Security Engineers, and SOC Analysts.

---

# Technologies Used

- Amazon EC2
- Ubuntu 24.04 LTS
- Amazon VPC
- Security Groups
- IAM Roles
- Apache HTTP Server
- AWS CloudWatch
- CloudWatch Agent
- Linux
- SSH
- Systemd

---

# Project Architecture

Internet
↓

AWS Security Group
- Port 22 (SSH)
- Port 80 (HTTP)

↓

Amazon EC2
Ubuntu Server

↓

Apache Web Server

↓

Linux Logs

- /var/log/auth.log
- /var/log/apache2/access.log
- /var/log/apache2/error.log

↓

CloudWatch Agent

↓

Amazon CloudWatch

- Metrics
- Log Groups
- Monitoring
- Alarms

---

# Objectives

- Launch an EC2 instance
- Configure secure networking
- Deploy Apache
- Create a custom web page
- Monitor authentication logs
- Monitor Apache logs
- Configure CloudWatch Agent
- Send Linux logs to CloudWatch
- Create CloudWatch metrics
- Create CloudWatch alarms
- Analyze web traffic
- Apply security best practices

---

# Phase 1 — Launch EC2

Created an Ubuntu EC2 instance using Amazon EC2.

Configured:

- VPC
- Public subnet
- Internet Gateway
- Elastic IP
- Security Groups

SSH access was restricted to the administrator IP.

HTTP was opened for public web access.

---

# Phase 2 — Linux Administration

Connected using SSH.

Performed:

- System updates
- Package installation
- Service verification
- Authentication log review

Useful commands:

sudo apt update

sudo tail -20 /var/log/auth.log

systemctl status apache2

---

# Phase 3 — Apache Deployment

Installed Apache.

sudo apt install apache2 -y

Verified:

systemctl status apache2

Created a custom security-themed homepage.

Verified browser access using the EC2 public IP.

---

# Phase 4 — Log Analysis

Reviewed:

Authentication logs

/var/log/auth.log

Apache access logs

/var/log/apache2/access.log

Apache error logs

/var/log/apache2/error.log

Observed:

- Successful SSH logins
- Scheduled cron jobs
- HTTP requests
- Browser favicon requests
- Internet scanners
- 404 responses
- 408 timeouts

---

# Phase 5 — IAM Role

Created an IAM Role:

CloudWatchAgentRole

Attached:

CloudWatchAgentServerPolicy

Assigned the role to the EC2 instance.

Verified using Instance Metadata Service (IMDSv2).

---

# Phase 6 — CloudWatch Agent

Downloaded and installed the official CloudWatch Agent.

Configured monitoring for:

- CPU
- Memory
- Disk
- Authentication logs
- Apache Access Logs
- Apache Error Logs

---

# Phase 7 — CloudWatch Logs

Created Log Groups:

/aws/ec2/CyberLab/auth

/aws/ec2/CyberLab/apache/access

/aws/ec2/CyberLab/apache/error

Verified log ingestion from the EC2 instance.

---

# Phase 8 — Monitoring & Alerts

Configured:

- Memory monitoring
- CPU monitoring
- CloudWatch metrics
- CloudWatch alarms

Validated successful metric collection.

---

# Troubleshooting

Resolved multiple issues during deployment including:

- IMDSv2 metadata access
- CloudWatch Agent installation
- Invalid JSON configuration
- CollectD configuration errors
- Permission denied for auth.log
- cwagent group membership
- Agent restart failures

---

# Security Best Practices

✔ Least privilege IAM

✔ SSH restricted by IP

✔ Security Groups

✔ Centralized logging

✔ Cloud monitoring

✔ IAM Roles instead of Access Keys

✔ Linux authentication monitoring

✔ Web server monitoring

✔ CloudWatch alarms

---

# Skills Demonstrated

- AWS EC2
- Linux Administration
- Apache Administration
- IAM
- Cloud Security
- CloudWatch
- Incident Monitoring
- Log Analysis
- Security Operations
- Networking
- Troubleshooting

---

# Learning Outcomes

This project demonstrates how to deploy and secure a cloud-hosted web server while implementing centralized monitoring and security logging using AWS CloudWatch.

The environment follows cloud engineering and security best practices commonly used in production environments.
