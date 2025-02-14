# AWS CLI in Kali Linux

## Introduction
AWS CLI (Command Line Interface) is a powerful tool that allows users to interact with AWS services using command-line commands. It is useful for automation, scripting, and managing AWS resources efficiently.

## Installation
### Step 1: Update the System
```bash
sudo apt update && sudo apt upgrade -y
```

### Step 2: Install AWS CLI
```bash
sudo apt install awscli -y
```

### Step 3: Verify Installation
```bash
aws --version
```
Output Example:
```
aws-cli/2.x.x Python/3.x.x Linux/x86_64
```

## Configuration
After installation, configure AWS CLI using the following command:
```bash
aws configure
```
You will be prompted to enter:
- AWS Access Key ID
- AWS Secret Access Key
- Default region name (e.g., us-east-1)
- Default output format (json, yaml, table, text)

## Basic AWS CLI Commands
### 1. List All S3 Buckets
```bash
aws s3 ls
```

### 2. Upload a File to S3
```bash
aws s3 cp myfile.txt s3://mybucket/
```

### 3. Download a File from S3
```bash
aws s3 cp s3://mybucket/myfile.txt .
```

### 4. List EC2 Instances
```bash
aws ec2 describe-instances
```

### 5. Start an EC2 Instance
```bash
aws ec2 start-instances --instance-ids i-xxxxxxxxxxxxxxxxx
```

### 6. Stop an EC2 Instance
```bash
aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxxxxxxx
```

### 7. List IAM Users
```bash
aws iam list-users
```

## Advanced AWS CLI Usage
### 1. Running Commands on a Remote EC2 Instance
```bash
aws ssm send-command \
  --document-name "AWS-RunShellScript" \
  --targets "Key=instanceIds,Values=i-xxxxxxxxxxxxxxxxx" \
  --parameters "commands=['uptime']"
```

### 2. Retrieve CloudWatch Logs
```bash
aws logs describe-log-groups
aws logs get-log-events --log-group-name my-log-group --log-stream-name my-log-stream
```

### 3. Creating an S3 Bucket
```bash
aws s3 mb s3://mynewbucket
```

### 4. Deleting an S3 Bucket
```bash
aws s3 rb s3://mynewbucket --force
```

## Automating AWS CLI Tasks
You can use AWS CLI within scripts to automate tasks. Example script to backup a directory to S3:
```bash
#!/bin/bash
aws s3 sync /home/user/backup s3://mybackupbucket/
```
Make it executable:
```bash
chmod +x backup.sh
./backup.sh
```

## Conclusion
AWS CLI is an essential tool for managing AWS services from the terminal. Learning its commands and automating tasks can significantly improve efficiency in cloud management.

---
*Note:* Ensure you manage AWS credentials securely and follow IAM best practices to minimize security risks.

