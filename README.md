# Creating a VPC Infrastructure on AWS Using Ansible

This guide will walk you through the process of using Ansible to create a VPC infrastructure on AWS. The playbook will create a VPC with 3 availability zones, 3 public subnets with an internet gateway and route table connection, and 3 private subnets with a NAT gateway and route table connection. Additionally, it will create a bastion host and security group and key pair for it.

## Prerequisites

Before starting, you will need:

- An AWS account and access keys
- Basic knowledge of AWS and Ansible

## Setup

1. Clone the GitHub repository

2. Install Ansible and Boto3 using pip3:

```
sudo apt update
sudo apt install python3 python3-pip -y
sudo pip3 install ansible boto3
```

3. Configure AWS credentials:

   - Create a new IAM user with programmatic access in your AWS account.
   - Attach the AmazonEC2FullAccess policy to the user.
   - Create an access key for the user and save the access key ID and secret access key.

## Usage

1. Create a new EC2 key pair using Ansible

2. Create a new VPC infrastructure using Ansible

The playbook will create a new VPC infrastructure on AWS with the following resources:

- VPC with a CIDR block of 172.20.0.0/16
- 3 availability zones: us-east-2a, us-east-2b, us-east-2c
- 3 public subnets with CIDR blocks of 172.20.1.0/24, 172.20.2.0/24, and 172.20.3.0/24
- 1 internet gateway with a route table connection to the public subnets
- 3 private subnets with CIDR blocks of 172.20.4.0/24, 172.20.5.0/24, and 172.20.6.0/24
- 1 NAT gateway in each public subnet with a route table connection to the private subnets
- Bastion host with a security group and key pair

## Customization

You can customize the VPC infrastructure by modifying the variables in the `Variables/vpc_setup` file. 

Here are some of the variables that you can modify:

- `region`: The AWS region in which the VPC infrastructure will be created.
- `vpccidr`: The CIDR block for the VPC.
- `PublicSub#cidr`: The CIDR blocks for the public subnets.
- `PrivSub#cidr`: The CIDR blocks for the private subnets.
- `instance_type`: The instance type for the bastion host.
- `bastion_ami`: The AMI ID for the bastion host..

## Conclusion

In this guide, you learned how to use Ansible to create a VPC infrastructure on AWS. You can modify the playbook to suit your needs and customize the variables to create a VPC infrastructure that meets your requirements.
