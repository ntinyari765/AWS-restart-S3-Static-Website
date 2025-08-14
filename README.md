# AWS S3 Static Website Deployment Lab

## Overview
This project documents my experience deploying a static website to **Amazon S3** using the **AWS CLI** from an **Amazon EC2** instance.  
The lab simulates creating a website for a Café & Bakery and creating an update script for repeatable deployments.

---

## Objectives
By the end of this lab, I achieved the following:
- Ran AWS CLI commands that interact with Amazon S3.
- Created and configured an S3 bucket for website hosting.
- Uploaded static website files to the bucket.
- Enabled S3 static website hosting.
- Created a script to automate website updates.

---

## Lab Tasks

### **Task 1: Connect to an Amazon Linux EC2 instance using SSM**
Connected to the EC2 instance via AWS Systems Manager Session Manager.
```bash
sudo su -l ec2-user
pwd

