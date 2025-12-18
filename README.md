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

```bash
git clone https://github.com/rabindra1x/Deploy-Two-Tier-Architecture-on-AWS-using-Terraform.git
```


```bash
terraform plan -var-file=variables.tfvars
```

<img width="736" height="233" alt="image" src="https://github.com/user-attachments/assets/f1085f8f-1104-4c0c-85f2-f15c04715dfa" />


```bash
terraform apply -var-file=variables.tfvars --auto-approve

```

<img width="736" height="208" alt="image" src="https://github.com/user-attachments/assets/be7d10fe-3273-4884-bd19-cf7fd2a7a5c1" />

Once the deployment is complete, you can inspect the created services using the provided snippets for each service.


# VPC & Other Networking related Services 

VPC 

<img width="736" height="83" alt="image" src="https://github.com/user-attachments/assets/5e5bbc9f-6c27-47f3-add5-92d3fdf6ce6b" />

Public and Private Subnets

<img width="736" height="94" alt="image" src="https://github.com/user-attachments/assets/b325d1d2-fea4-4580-aa0d-c3dff9757820" />


Public and Private Route tables

<img width="736" height="94" alt="image" src="https://github.com/user-attachments/assets/a938c520-9b4f-4570-96bd-8a9f2850a65f" />

Internet Gateway

<img width="736" height="94" alt="image" src="https://github.com/user-attachments/assets/620be178-1935-4b05-88aa-e39ba66d1f56" />


Elastic IP addresses 

<img width="736" height="94" alt="image" src="https://github.com/user-attachments/assets/106000aa-5a92-47ef-81c2-aa60145d20e5" />

NAT Gateways

<img width="736" height="94" alt="image" src="https://github.com/user-attachments/assets/7bce4872-227c-4997-9541-74ba150a5fa8" />

Security Groups

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/47644ecf-0765-48ae-85fe-e2885eda91d3" />

# EC2 & AutoScaling Group 

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/0bf6d28f-338f-44fd-8b97-f6d32a5481f7" />

AutoScaling Group

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/c9062d31-b4cc-40a4-b51a-974ec37633fa" />

# Target Group & Load Balancer

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/519351a0-f3f3-40f0-9713-d325c9a77694" />

Load balancer

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/7bfe66df-4832-4fe8-ad83-fa405e27bf39" />


# Database 

Subnet Group for RDS

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/642f41f2-3a1b-4e7e-a27e-0fd3315b2901" />

<img width="736" height="114" alt="image" src="https://github.com/user-attachments/assets/fc938bc8-ffe9-422d-84e5-47bcac594bea" />



# After Core Service, Deploy Service on Server 

<img width="736" height="234" alt="image" src="https://github.com/user-attachments/assets/13116726-3755-4a6f-bc77-346d87e39c7f" />

# TF State file and State lock

<img width="736" height="189" alt="image" src="https://github.com/user-attachments/assets/55a85ab5-ff9c-4238-bbd5-055312ac1bc9" />


Once the deployment is completed, you can enter your domain name in the browser to validate whether your servers are perfectly running or not.

As you can see in the below snippet, the Application is running

<img width="736" height="387" alt="image" src="https://github.com/user-attachments/assets/880565a5-85dc-4852-9570-d71eb9efafd0" />


# Clean-up

When you’re done exploring the Two-Tier architecture and want to avoid incurring unnecessary costs, follow these steps to clean up the resources:

Run the following command to initiate the destruction of the infrastructure.


```bash
terraform destroy -var-file=variables.tfvars --auto-approve
```

<img width="736" height="204" alt="image" src="https://github.com/user-attachments/assets/fffb63a5-00ae-4c2f-8d69-9d7653065d8b" />



















