# AWS EC2 Tutorial

This Terraform configuration creates a complete AWS infrastructure from scratch, including:
- VPC with public subnet
- Internet Gateway
- EC2 instance with SSH access
- SSH key pair generation

## Prerequisites

1. AWS CLI installed and configured with credentials
2. Terraform installed (>= 1.0)
3. Appropriate AWS permissions to create VPC, EC2, and related resources

## Setup Instructions

1. **Initialize Terraform:**
   ```bash
   terraform init
   ```

2. **Review the execution plan:**
   ```bash
   terraform plan
   ```

3. **Apply the configuration:**
   ```bash
   terraform apply
   ```
   Type `yes` when prompted to confirm.

4. **After successful deployment, you'll see outputs including:**
   - Public IP address
   - SSH command to connect

5. **Connect to your EC2 instance:**
   ```bash
   ssh -i aws-tutorial-key.pem ec2-user@<PUBLIC_IP>
   ```
   Or use the SSH command from the Terraform output.

## Configuration

Default values can be modified in `variables.tf`:
- `aws_region`: AWS region (default: us-east-1)
- `instance_type`: EC2 instance type (default: t2.micro)
- `vpc_cidr`: VPC CIDR block (default: 10.0.0.0/16)
- `public_subnet_cidr`: Public subnet CIDR (default: 10.0.1.0/24)

## Cleanup

To destroy all resources:
```bash
terraform destroy
```

## Security Note

The SSH key pair files (`.pem` and `.pub`) are generated locally and should be kept secure. They are automatically added to `.gitignore` to prevent accidental commits.

