# Deploy-Two-Tier-Architecture-on-AWS-using-Terraform


<img width="926" height="1080" alt="image" src="https://github.com/user-attachments/assets/b92afd8b-4a16-4f94-9638-1ded97d9a0b5" />


# Introduction
In the world of cloud computing, infrastructure as code (IaC) plays a pivotal role in automating the deployment and management of resources. This blog post provides a step-by-step guide on creating a Two-Tier architecture on AWS using Terraform. We’ll explore the essential services involved, ensuring high availability, security, and scalability for hosting a static website.

Also, we are adopting a modular approach with enhanced security measures. The infrastructure is organized into dedicated modules, ensuring a scalable, maintainable, and secure deployment.


# Directory Overview


backend.tf: Configuration for Terraform backend, specifying where to store the Terraform state.

main.tf: Main Terraform configuration orchestrating the deployment.

variables.tf: Definition of variables used in the main Terraform configuration.

variables.tfvars: Input values for the defined variables.

modules:

alb-tg:

gather.tf: Terraform script to gather information about the Application Load Balancer (ALB) and Target Group (TG).

main.tf: Main Terraform configuration for ALB and TG.

variables.tf: Definition of variables used in the ALB and TG module.

aws-autoscaling:

deploy.sh: Shell script for deploying the Auto Scaling Group.

gather.tf: Terraform script to gather information about the Auto Scaling Group.

main.tf: Main Terraform configuration for the Auto Scaling Group.

variable.tf: Definition of variables used in the Auto Scaling Group module.

aws-iam:

iam-instance-profile.tf: Terraform configuration for IAM instance profile.

iam-policy.json: JSON file containing the IAM policy.

iam-policy.tf: Terraform configuration for IAM policy.

iam-role.json: JSON file containing the IAM role.

iam-role.tf: Terraform configuration for IAM role.

variables.tf: Definition of variables used in the IAM module.

aws-rds:

gather.tf: Terraform script to gather information about the RDS cluster.

main.tf: Main Terraform configuration for the RDS cluster.

variables.tf: Definition of variables used in the RDS module.

aws-vpc:

main.tf: Main Terraform configuration for the Virtual Private Cloud (VPC) and other Networking Services like Public/Private Subnet, ElasticIP, etc.

variables.tf: Definition of variables used in the VPC module.

aws-waf-cdn-acm-route53:

acm.tf: Terraform configuration for ACM (Amazon Certificate Manager).

cdn.tf: Terraform configuration for CDN (Content Delivery Network).

gather.tf: Terraform script to gather information about WAF, CDN, ACM, and Route 53.

route53.tf: Terraform configuration for Route 53.

variables.tf: Definition of variables used in the WAF, CDN, ACM, and Route 53 modules.

waf.tf: Terraform configuration for AWS WAF (Web Application Firewall).

security-group:

gather.tf: Terraform script to gather information about security groups.

main.tf: Main Terraform configuration for security groups.

variable.tf: Definition of variables used in the security group module.

This modular approach enhances the project’s maintainability, making it easier to manage and scale as your infrastructure requirements evolve. Each module focuses on a specific aspect of the infrastructure, promoting reusability and clarity in configuration.

Pre-requisites
Before diving into the infrastructure creation, make sure you have the following:

An AWS Account

Terraform installed on your local machine

AWS Access and Secret Access keys configured

Domain Name Configured manually and add the Name Servers to your Domain Provider


# Step-by-Step Guide


'''  print(hello world) ''' 



