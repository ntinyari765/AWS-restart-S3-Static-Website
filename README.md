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

 ### ***Task 2: Configure AWS CLI**
Configured the AWS Command Line Interface (CLI) on an Amazon Linux EC2 instance for S3 operations.

### **Task 3: Create S3 Bucket via AWS CLI**
Created a uniquely named S3 bucket in `us-west-2` region with proper configuration.
```bash
aws s3api create-bucket \
  --bucket ntinyari765\
  --region us-west-2 \
  --create-bucket-configuration LocationConstraint=us-west-2

### **Task 3: Extract Static Website Files**
Prepared the website files for deployment to S3 by extracting the lab-provided archive.
```bash
cd ~/sysops-activity-files
tar xvzf static-website-v2.tar.gz
cd static-website
ls

### **Task 7: Deploy Static Website to S3**
Configures S3 bucket for website hosting and uploads static website files with public access.
```bash
aws s3 website s3://ntinyari765/ --index-document index.html
