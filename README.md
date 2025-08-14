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
```
![Task 1 Screenshot](./images/ec2_ssh.png)

### ***Task 2: Configure AWS CLI**
Configured the AWS Command Line Interface (CLI) on an Amazon Linux EC2 instance for S3 operations.
```bash
aws configure
```

### **Task 3: Create S3 Bucket via AWS CLI**
Created a uniquely named S3 bucket in `us-west-2` region with proper configuration.
```bash
aws s3api create-bucket \
  --bucket ntinyari765\
  --region us-west-2 \
  --create-bucket-configuration LocationConstraint=us-west-2
```

### **Task 4: Extract Static Website Files**
Prepared the website files for deployment to S3 by extracting the lab-provided archive.
```bash
cd ~/sysops-activity-files
tar xvzf static-website-v2.tar.gz
cd static-website
ls
```
![Task 4 Screenshot](./images/Task%204.png)

### **Task 5: Deploy Static Website to S3**
Configures S3 bucket for website hosting and uploads static website files with public access.
```bash
aws s3 website s3://ntinyari765/ --index-document index.html
aws s3 cp ./static-website/ s3://ntinyari765/ \
  --recursive \
  --acl public-read
aws s3 ls s3://ntinyari765/
```
![Task 5 Screenshot](./images/task%205.png)

The static website can be accessed at: http://ntinyari765.s3-website-us-west-2.amazonaws.com
![The Static Website](./images/Website_screenshot.png)

After uploading files via AWS CLI, the bucket contents appear in the S3 Management Console as shown:
![S3 Bucket Contents](./images/s3_bucket.png)