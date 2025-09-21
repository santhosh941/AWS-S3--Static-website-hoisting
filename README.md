# AWS-S3--Static-website-hoisting

This project demonstrates how to host a static website on AWS using S3, EC2, IAM Roles, Auto Scaling, and Load Balancer. The goal is to set up a scalable, secure, and highly available web application environment.

Project Architecture

VPC with public and private subnets across multiple availability zones.

Internet Gateway for public subnet access.

EC2 Instances launched in private subnets using a Launch Template with a custom AMI (Nginx + index.html).

Application Load Balancer (ALB) in the public subnet to distribute traffic across EC2 instances.

Auto Scaling Group (ASG) to automatically scale instances based on demand.

CloudWatch Alarm with SNS notifications to monitor scaling activities.

S3 Bucket configured to host a static website, serving the index.html page.

Steps Implemented

VPC Setup

Created a VPC with CIDR block supporting 65,536 IPs.

Added public and private subnets in different availability zones.

Internet Gateway & Routing

Attached Internet Gateway to VPC.

Updated public route table for internet access.

Custom AMI Creation

Installed Nginx and placed a custom index.html page stating:
“This webpage is launched using custom AMI in an Auto Scaling group.”

Saved it as a custom AMI.

Launch Template & Auto Scaling

Created a Launch Template with the custom AMI.

Configured Auto Scaling Group with:

Min: 2

Max: 5

Desired: 2

Attached Application Load Balancer to distribute traffic.

EC2 Access

Deployed EC2 instances in private subnets.

Accessed them via bastion host (EC2 in public subnet) using SSH.

Monitoring & Alerts

Configured CloudWatch Alarm for instance launch/terminate events.

Integrated with SNS topic for email notifications.

S3 Static Website Hosting

Created an S3 bucket and enabled Static Website Hosting.

Uploaded index.html.

Assigned IAM role to EC2 for S3 access.

Tools & Services Used

AWS VPC

EC2 with Custom AMI

Auto Scaling Group (ASG)

Application Load Balancer (ALB)

CloudWatch & SNS

IAM Roles

S3 Bucket (Static Website Hosting)

Outcome

A scalable and highly available static website hosted on AWS.

Auto Scaling + Load Balancer ensures performance under traffic load.

S3 static hosting provides an alternative lightweight hosting solution.

CloudWatch Alerts notify scaling activities for monitoring.
