
# Assignment 3 – Deploying AWS EC2 and RDS using CloudFormation

**Name:** Keerthana Garimella  
**Student ID:** 8985513  
**Course:** PROG8870 – Cloud Architectures and Infrastructure as Code

---

## 📚 Assignment Overview

This assignment involves deploying the following infrastructure using AWS CloudFormation:

- VPC, Subnets, Route Table, and Internet Gateway  
- EC2 instance with SSH access  
- MySQL RDS instance with public access  

---

## 🧾 Files Included

- `networking.yml` – CloudFormation template for networking resources (VPC, subnets, IGW, route table)  
- `ec2.yml` – Template to deploy EC2 instance along with security group  
- `rds.yml` – Template for deploying a publicly accessible MySQL-compatible Amazon Aurora RDS instance  

---

## 🖼️ Screenshots

- ✅ VPC, Subnets, and Internet Gateway – Captured from AWS VPC Dashboard  
- ✅ Route Table creation and associations  
- ✅ Security Group for EC2 and RDS allowing necessary access (SSH and MySQL)  
- ✅ Deployed EC2 instance with public IP  
- ✅ Amazon Aurora DB cluster with writer and two reader nodes  
- ✅ CloudFormation stack outputs and events confirming successful deployment  

---

## 🚀 Deployment Commands Used

### Deploy Networking Stack
```bash
aws cloudformation create-stack   --stack-name assignment3-networking   --template-body file://networking.yml   --capabilities CAPABILITY_NAMED_IAM
```

### Deploy EC2 Stack
```bash
aws cloudformation create-stack   --stack-name assignment3-ec2   --template-body file://ec2.yml   --capabilities CAPABILITY_NAMED_IAM   --parameters     ParameterKey=AMI,ParameterValue=ami-0cbbe2c6a1bb2ad63     ParameterKey=InstanceType,ParameterValue=t2.micro
```

### Deploy RDS Stack
```bash
aws cloudformation create-stack   --stack-name assignment3-rds   --template-body file://rds.yml   --capabilities CAPABILITY_NAMED_IAM   --parameters     ParameterKey=DBUsername,ParameterValue=admin     ParameterKey=DBPassword,ParameterValue=Password123!
```

---

## ✅ Summary

All stacks were successfully created. Each resource was verified using the AWS Console:  
- VPC CIDR: 10.0.0.0/23  
- EC2: Amazon Linux 2, publicly accessible  
- RDS: Aurora MySQL-compatible DB cluster, secure with DB subnet group and SG rules  


