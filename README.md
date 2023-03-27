# IaC REPOSITORY INSTRUCTIONS

**## Prerequisites**

\- [Install AWS CLI](https://terraform-docs.io/user-guide/installation/)

\- [Install terraform](https://learn.hashicorp.com/collections/terraform/aws-get-started?utm_source=WEBSITE&utm_medium=WEB_IO&utm_offer=ARTICLE_PAGE&utm_content=DOCS)

\- [Install terraform-docs](https://terraform-docs.io/user-guide/installation/)

To create the IaC repository of a project, you must pay attention to:

## IAC Repository Structure

This is the structure of IaC repository

IaC-<PROJECT-NAME>-Infrastructure
│   README.md
└───app
|	└───tf_bastion
|	|	└───pem_dir				--> Directory to put pem file for ssh keys to login in ec2  (Not stage on git)
|	|	└───README.md			--> File app documentation generated with 
|	|	|							https://github.com/terraform-docs/terraform-docs
|	|	└───bastion.auto.tfvars	--> Vars for bastion app
|	|	└───main.tf				-->	Script tha contains de tf resources for implementation
|	|	└───provider.tf			--> Script tha contains de tf provider description 
|	|	|							an restrictions for implementation
|	|	└───variables.tf		-->	Script tha contains variables declaration
|	|	└───outputs.tf			--> Script tha contains outputs declaration
|	└───tf_infrastructure		--> App for create Networking, EC2, S3 Buckets, DymamoDB, 
|	|	|							RDS Databases
|	|	└───iam-policies		--> Directory put policies definitions related to AWS compute
|	|	|							resources (Networking, EC2, S3 Buckets, DymamoDB, RDS Databases)
|    |	└───README.md			--> File app documentation generated with 
|	|	|							https://github.com/terraform-docs/terraform-docs
|	|	└───ifr.auto.tfvars		--> Vars for tf_infrastructure app
|	|	└───main.tf				-->	Script that contains de tf resources for implementation
|	|	└───provider.tf			--> Script that contains de tf provider description an 
|	|	|							restrictions for implementation
|	|	└───variables.tf		-->	Script that contains variables declaration
|	|	└───outputs.tf			--> Script that contains outputs declaration
|	└───tf_services				--> App for create Services as ECS EKS Fargate EBL 
|	|	|							API Gateway and Serveless components
|	|	└───certificates		--> Directory for put policies definitions related to AWS services
|	|	|							resources (Services as ECS EKS Fargate EBL )    
|	|	└───iam-policies		--> Directory puy policies definitions related to AWS services 
|	|	|							resources (Services as ECS EKS Fargate EBL )
|	|	└───README.md			--> File app documentation generated with 
|	|	|							https://github.com/terraform-docs/terraform-docs
|	|	└───srv.auto.tfvars		--> Vars for tf_infrastructure app
|	|	└───main.tf				-->	Script that contains de tf resources for implementation
|	|	└───provider.tf			--> Script that contains de tf provider description an restrictions
|	|	|							for implementation
|	|	└───variables.tf		-->	Script that contains variables declaration
|	|	└───outputs.tf			--> Script that contains outputs declaration
└───backend						--> App that contains backed app for manage tf state
|	└───backend.auto.tfvars		--> Vars for bastion app
|	└───main.tf					-->	Script tha contains de tf resources for implementation
|	└───provider.tf				--> Script tha contains de tf provider description an 
|	|												restrictions for implementation
|	└───variables.tf			-->	Script tha contains variables declaration
|   └───outputs.tf				--> Script tha contains outputs declaration
└───modules
|	└───<MODULE-NAME>					--> Modules used on tf_infrastructure and tf_infrastructure app
|	|	└───README.md					--> File app documentation generated with 
|	|	|									https://github.com/terraform-docs/terraform-docs
|	|	└───main.tf or MODULE-NAME>.tf	-->	Script that contains de tf resources for implementation
|	|	└───variables.tf				-->	Script that contains variables declaration
|	|	└───outputs.tf					--> Script that contains outputs declaration



## IAC Deploy flow

This is the sequence execution for tf

1. tf_infrastructure deploy  

   terraform init  

   terraform plan

   terraform apply

2. tf_services

   terraform init  

   terraform plan

   terraform apply

This sequence cannot be altered or changed under any circumstances

## IaC Restrictions

- **NOT USE TERRAGRUNT**
- Not pull to repository pem keys or rsa certificates.
- Not use hardcode values on modules or apps
- Create system params on AWS Systems Manager console
- Use secrets for storage sensitive data
- Use chekov to validate the IaC implementation 





​	

