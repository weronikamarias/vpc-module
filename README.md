# VPC Module

This module creates a basic VPC with public and private subnets across multiple availability zones.

## Features

- Creates a VPC with configurable CIDR block
- Creates public subnets with internet gateway connectivity
- Creates private subnets
- Configurable number of subnets and availability zones
- Tagging support

## Usage

```hcl
module "vpc" {
  source = "spacelift://your-module-id"  # Will be replaced with actual ID

  name_prefix = "my-app"
  
  vpc_cidr = "10.0.0.0/16"
  
  public_subnet_cidrs  = ["10.0.1.0/24", "10.0.2.0/24"]
  private_subnet_cidrs = ["10.0.11.0/24", "10.0.12.0/24"]
  
  availability_zones = ["us-east-1a", "us-east-1b"]
  
  common_tags = {
    Environment = "dev"
    Project     = "my-project"
  }
}
```

## Inputs

| Name | Description | Type | Default |
|------|-------------|------|---------|
| name_prefix | Prefix for all resource names | string | n/a |
| vpc_cidr | CIDR block for VPC | string | "10.0.0.0/16" |
| public_subnet_cidrs | CIDR blocks for public subnets | list(string) | ["10.0.1.0/24", "10.0.2.0/24"] |
| private_subnet_cidrs | CIDR blocks for private subnets | list(string) | ["10.0.11.0/24", "10.0.12.0/24"] |
| availability_zones | AZs to use | list(string) | ["us-east-1a", "us-east-1b"] |
| common_tags | Tags to apply to all resources | map(string) | {} |

## Outputs

| Name | Description |
|------|-------------|
| vpc_id | ID of the created VPC |
| vpc_cidr | CIDR block of the VPC |
| public_subnet_ids | List of public subnet IDs |
| private_subnet_ids | List of private subnet IDs |
| internet_gateway_id | ID of the Internet Gateway |
