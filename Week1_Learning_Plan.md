# WEEK 1 — AWS IAM, S3, EC2 & CLI FOUNDATION
## Mentor Assignment - Complete Learning Guide

### 📋 Week Overview
**Goal**: Master AWS core services (IAM, S3, EC2) and Infrastructure as Code basics
**Duration**: 7 days
**Tools**: AWS Console, CLI, Terraform
**Region**: ap-south-1 (Mumbai)

---

## 🧠 Day 1: Research & Concepts

### Task: Research and Document
Create `Week1_Notes.txt` and write 2-3 lines on each topic:

#### IAM (Identity & Access Management)
**Research Questions:**
- What is IAM and why do we use it?
- Difference between Users, Groups, Roles, and Policies
- What are Access Keys and Secret Keys?

**Your Research Notes:**
```
IAM:
- 

Users vs Groups vs Roles vs Policies:
- 

Access Keys & Secret Keys:
- 
```

#### S3 (Simple Storage Service)
**Research Questions:**
- What is object storage?
- What is the purpose of buckets?
- What are storage classes in S3?

**Your Research Notes:**
```
Object Storage:
- 

S3 Buckets:
- 

Storage Classes:
- 
```

#### EC2 (Elastic Compute Cloud)
**Research Questions:**
- What is an EC2 instance?
- What are key pairs and security groups used for?
- What is an AMI?

**Your Research Notes:**
```
EC2 Instance:
- 

Key Pairs & Security Groups:
- 

AMI:
- 
```

#### AWS CLI
**Research Questions:**
- Why use CLI instead of the console?
- Where are CLI credentials stored?
- How do CLI commands communicate with AWS services?

**Your Research Notes:**
```
CLI vs Console:
- 

Credential Storage:
- 

CLI Communication:
- 
```

---

## 🧩 Day 2-3: Task 1A — IAM & S3 Using AWS Console

### Objective
Understand IAM users and S3 basics through AWS Management Console.

### Step-by-Step Instructions

#### Step 1: Create IAM User
1. **Navigate to IAM**
   - AWS Console → Services → IAM
   - Click "Users" in left sidebar

2. **Create User**
   - Click "Create user"
   - Username: `devops-junior`
   - Select both:
     - ✅ Provide user access to the AWS Management Console
     - ✅ Programmatic access (for CLI)

3. **Set Permissions**
   - Click "Attach policies directly"
   - Search and select: `AmazonS3FullAccess`
   - Click "Next"

4. **Review and Create**
   - Review settings
   - Click "Create user"
   - **IMPORTANT**: Download credentials CSV file
   - Save Access Key ID and Secret Access Key

#### Step 2: Create S3 Bucket
1. **Navigate to S3**
   - AWS Console → Services → S3
   - Click "Create bucket"

2. **Configure Bucket**
   - Bucket name: `devops-junior-learning-<yourname>`
   - Region: `Asia Pacific (Mumbai) ap-south-1`
   - **Uncheck** "Block all public access" (for testing only)
   - Acknowledge the warning
   - Click "Create bucket"

3. **Upload Test File**
   - Click on your bucket name
   - Click "Upload"
   - Add files → Select `notes.txt` or any image
   - Click "Upload"
   - Verify file appears in bucket

### 📸 Deliverables for Task 1A
- [ ] Screenshot of IAM user page showing `devops-junior` user
- [ ] Screenshot of S3 bucket with uploaded file
- [ ] Save credentials securely

---

## 💻 Day 4-5: Task 1B — AWS CLI Practice

### Objective
Set up AWS CLI and interact with AWS services programmatically.

### Step-by-Step Instructions

#### Step 1: Install AWS CLI
**For Windows:**
```cmd
# Download AWS CLI v2 installer
curl "https://awscli.amazonaws.com/awscli-exe-windows-x86_64.msi" -o "AWSCLIV2.msi"

# Install
msiexec /i AWSCLIV2.msi

# Verify installation
aws --version
```

**For macOS:**
```bash
# Using Homebrew
brew install awscli

# Or download installer
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```

**For Linux:**
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

#### Step 2: Configure CLI
```bash
aws configure
```
**Enter the following:**
- AWS Access Key ID: `<your-access-key-from-IAM>`
- AWS Secret Access Key: `<your-secret-key-from-IAM>`
- Default region name: `ap-south-1`
- Default output format: `json`

#### Step 3: Test CLI Commands
Run each command and document what it does:

```bash
# Command 1: List S3 buckets
aws s3 ls

# Command 2: Upload file to S3
aws s3 cp notes.txt s3://devops-junior-learning-<yourname>/

# Command 3: List EC2 instances
aws ec2 describe-instances --region ap-south-1
```

### Document in Week1_Notes.txt:
```
CLI Command Analysis:
1. aws s3 ls - 
2. aws s3 cp - 
3. aws ec2 describe-instances - 
```

### 📸 Deliverables for Task 1B
- [ ] Screenshot of successful CLI configuration
- [ ] Screenshot showing S3 upload via CLI
- [ ] Updated Week1_Notes.txt with command explanations

---

## 🧱 Day 6-7: Task 1C — Create Infrastructure with Terraform

### Objective
Learn Infrastructure as Code using Terraform.

### Step-by-Step Instructions

#### Step 1: Research Terraform
Add to your `Week1_Notes.txt`:
```
Terraform Research:
- What is Terraform? 
- What are providers? 
- What are resources? 
- What are state files? 
```

#### Step 2: Install Terraform
**For Windows:**
```cmd
# Download from https://www.terraform.io/downloads
# Extract to C:\terraform
# Add to PATH environment variable

# Verify
terraform -v
```

**For macOS:**
```bash
brew install terraform
terraform -v
```

**For Linux:**
```bash
wget https://releases.hashicorp.com/terraform/1.6.0/terraform_1.6.0_linux_amd64.zip
unzip terraform_1.6.0_linux_amd64.zip
sudo mv terraform /usr/local/bin/
terraform -v
```

#### Step 3: Create Terraform Files
Create a new folder: `terraform-week1`

**File 1: main.tf**
```hcl
provider "aws" {
  region = var.region
}

resource "aws_s3_bucket" "demo_bucket" {
  bucket = var.bucket_name
  tags = {
    Name        = "DevOps Junior Bucket"
    Environment = "Learning"
  }
}
```

**File 2: variables.tf**
```hcl
variable "bucket_name" {
  description = "Name of the S3 bucket"
  type        = string
}

variable "region" {
  description = "AWS region"
  type        = string
  default     = "ap-south-1"
}
```

**File 3: terraform.tfvars**
```hcl
bucket_name = "devops-junior-terraform-bucket"
region      = "ap-south-1"
```

#### Step 4: Execute Terraform Commands
```bash
# Navigate to terraform folder
cd terraform-week1

# Initialize Terraform
terraform init

# Validate configuration
terraform validate

# Plan infrastructure
terraform plan

# Apply changes
terraform apply -auto-approve

# Verify bucket creation
aws s3 ls

# Clean up resources
terraform destroy -auto-approve
```

### 📸 Deliverables for Task 1C
- [ ] Screenshot of `terraform plan` output
- [ ] Screenshot of `terraform apply` output
- [ ] Screenshot showing created bucket in AWS Console
- [ ] Screenshot of `terraform destroy` completion

---

## 🧭 End-of-Week Challenge

### Challenge Task
1. **Create Custom IAM Policy**
   - Create IAM user: `bucket-specific-user`
   - Create custom policy allowing access to only ONE specific S3 bucket
   - Attach policy to user

2. **Test Restricted Access**
   - Configure CLI with new user credentials
   - Upload file to allowed bucket
   - Try accessing other buckets (should fail)

### Custom Policy Example:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::your-specific-bucket-name/*"
        },
        {
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::your-specific-bucket-name"
        }
    ]
}
```

### Week Summary Report
Write a one-page summary covering:
1. **What you learned this week**
2. **What challenges you faced**
3. **What you found interesting**
4. **Next steps for learning**

---

## 📁 File Structure by End of Week
```
AWS Learning/
├── Week1_Notes.txt
├── terraform-week1/
│   ├── main.tf
│   ├── variables.tf
│   ├── terraform.tfvars
│   └── terraform.tfstate (after apply)
├── screenshots/
│   ├── iam-user-created.png
│   ├── s3-bucket-with-file.png
│   ├── cli-configuration.png
│   ├── cli-s3-upload.png
│   ├── terraform-plan.png
│   ├── terraform-apply.png
│   └── terraform-bucket-console.png
└── Week1_Summary_Report.txt
```

---

## ✅ Success Criteria
By end of Week 1, you should be able to:
- [ ] Create and manage IAM users and policies
- [ ] Create and manage S3 buckets via Console and CLI
- [ ] Configure and use AWS CLI effectively
- [ ] Write basic Terraform configurations
- [ ] Understand Infrastructure as Code principles
- [ ] Implement basic AWS security practices

---

## 🚀 Daily Schedule Recommendation

**Day 1**: Research and documentation
**Day 2**: IAM user creation and S3 setup
**Day 3**: Complete Task 1A and screenshots
**Day 4**: Install and configure AWS CLI
**Day 5**: Complete CLI practice and testing
**Day 6**: Install Terraform and create configurations
**Day 7**: Execute Terraform, challenge task, and summary

---

## 📚 Additional Resources
- [AWS IAM User Guide](https://docs.aws.amazon.com/iam/)
- [AWS S3 User Guide](https://docs.aws.amazon.com/s3/)
- [AWS CLI User Guide](https://docs.aws.amazon.com/cli/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

**Remember**: Document everything, take screenshots, and don't hesitate to experiment!