# Demo App – DevOps Bootcamp Training (TechWorld with Nana)
This repository is part of the DevOps Bootcamp from TechWorld with Nana.

# Demo Project: EC2 Instance State Checker

This is a demo project that demonstrates how to work with AWS EC2 instances using Python.

## Overview

- The project provisions **three EC2 instances** on AWS.
- It includes a **Python script** that retrieves and displays the current state (e.g., running, stopped) of each EC2 instance.

## Features

- Automated creation of three EC2 instances.
- Python script to fetch and print the state of each instance using AWS APIs.

## Prerequisites

- AWS account with necessary permissions to create EC2 instances.
- Python 3.x installed.
- AWS CLI configured or appropriate credentials set up for boto3.
- **Terraform client installed** ([Download Terraform](https://www.terraform.io/downloads.html))


---

## Terraform Setup Instructions

This project uses [Terraform](https://www.terraform.io/) to provision AWS resources.

### 1. Configure `terraform.tfvars`

Create or edit the `terraform.tfvars` file with your desired configuration.  
Below is an example reflecting the latest variable names and structure:

```hcl
#vpc_cidr_block = "10.0.0.0/16"
#private_subnet_cidr_blocks = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
#public_subnet_cidr_blocks = ["10.0.4.0/24", "10.0.5.0/24", "10.0.6.0/24"]

vpc_cidr_block    = "10.0.0.0/16"
subnet_cidr_block = "10.0.10.0/24"  # Subnet CIDR block
avail_zone        = "eu-west-2a"    # Availability zone
env_prefix        = "dev"
instance_type     = "t2.micro"      # EC2 instance type 
my_ip             = "106.138.123.21/32" # Your IP address for security group access
public_key_location = "c:/users/<username>/.ssh/id_rsa.pub"  # Path to your public key
```

**Notes:**

* Update `my_ip` to your own public IP address for SSH access.
* Set `public_key_location` to the path of your SSH public key.
* The commented-out lines can be used for more advanced networking setups if needed.

### 2. Initialize Terraform

```bash
terraform init
```

### 3. Review the Plan

```bash
terraform plan
```

### 4. Apply the Configuration

```bash
terraform apply
```

This will provision the VPC, subnet, and three EC2 instances as defined.

### 5. Destroy the Infrastructure

When you are done, you can destroy all resources with:

```bash
terraform destroy
```

---

## Python Script Usage

The included Python script retrieves the state of each EC2 instance.

**Important:**  
The script must specify the same AWS region where the instances are launched (e.g., `eu-west-2`).  
Update the region in the script as needed:

```python
import boto3

ec2 = boto3.client('ec2', region_name='eu-west-2')
# ... rest of the script ...
```

Run the script:

```bash
python ec2-status-checks.py
```
```

