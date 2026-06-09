Terraform AWS EC2 Deployment
Project Overview

This project demonstrates how to use Terraform to provision an AWS EC2 instance using Infrastructure as Code (IaC).

The project covers:

Installing Terraform
Configuring AWS CLI
Creating Terraform configuration files
Initializing Terraform
Planning infrastructure changes
Deploying an EC2 instance
Managing infrastructure state
Version controlling the project with Git and GitHub
Prerequisites

Before starting, ensure the following are available:

AWS Account
IAM User with Programmatic Access
AWS Access Key
AWS Secret Access Key
Terraform Installed
Git Installed
GitHub Account
Step 1: Create Project Directory

Create a directory for the Terraform project.

mkdir terraform-project
cd terraform-project
Step 2: Create Terraform Configuration

Create the main Terraform file.

nano main.tf

Example configuration:

terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0c02fb55956c7d316"
  instance_type = "t2.micro"

  tags = {
    Name = "Terraform-Instance"
  }
}

Save the file.

Step 3: Configure AWS CLI

Configure AWS credentials.

aws configure

Provide:

AWS Access Key ID
AWS Secret Access Key
Default region name
Default output format

Example:

AWS Access Key ID: ********
AWS Secret Access Key: ********
Default region name: us-east-1
Default output format: json

Verify configuration:

aws sts get-caller-identity
Step 4: Initialize Terraform

Initialize the project.

terraform init

Purpose:

Downloads AWS provider
Creates .terraform directory
Creates lock file

Expected output:

Terraform has been successfully initialized!
Step 5: Validate Configuration

Check Terraform syntax.

terraform validate

Expected output:

Success! The configuration is valid.
Step 6: Generate Execution Plan

Preview resources before creation.

terraform plan

Terraform displays:

Plan: 1 to add, 0 to change, 0 to destroy.
Step 7: Apply Configuration

Create infrastructure.

terraform apply

Approve deployment:

Enter a value: yes

Terraform creates the EC2 instance.

Expected output:

Apply complete!
Resources: 1 added, 0 changed, 0 destroyed.

Example Instance ID:

i-0b2005714828322ac
Step 8: Verify Deployment

Check Terraform state:

terraform state list

View resource details:

terraform show

Verify from AWS Console:

Open EC2 Dashboard
Locate instance
Verify instance status
Step 9: Initialize Git Repository
git init

Configure Git:

git config --global user.name "OM0126"
git config --global user.email "your-email@example.com"
Step 10: Create .gitignore

Create:

nano .gitignore

Content:

.terraform/
*.tfstate
*.tfstate.*
terraform.tfvars
*.pem
crash.log
Step 11: Commit Project
git add .
git commit -m "Initial Terraform AWS EC2 setup"
Step 12: Create GitHub Repository

Create repository:

terraform-aws-ec2

Add remote:

git remote add origin https://github.com/OM0126/terraform-aws-ec2.git

Push code:

git branch -M main
git push -u origin main
Step 13: Destroy Infrastructure (Cleanup)

To avoid AWS charges:

terraform destroy

Approve:

yes

Terraform removes all resources.

Commands Summary
terraform init
terraform validate
terraform plan
terraform apply
terraform show
terraform state list
terraform destroy
Technologies Used
Terraform
AWS EC2
AWS CLI
Git
GitHub
Author

OM0126
