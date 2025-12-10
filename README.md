# All-About-Terraform-
## What is Terraform
Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp that lets you create, manage, and automate your cloud infrastructure using simple, human-readable configuration files.
It allows you to provision resources on multiple cloud providers like AWS, Azure, GCP, Kubernetes, VMware, etc.
## Why Terraform Matters
Terraform matters because it makes managing infrastructure easy, automated, consistent, and scalable across any cloud.
It replaces manual work with code, reduces human errors, and allows teams to build infrastructure faster and safely.
## Terraform vs Ansible
### Terraform
    - Infrastructure as Code (IaC) tool used to provision and manage cloud infrastructure resources.
    - Uses HCL (HashiCorp Configuration Language), which is declarative and designed specifically for infrastructure definition.
    - Declarative – you define the desired state, and Terraform figures out how to reach that state.
    - Strong multi-cloud support; works with AWS, Azure, GCP, and others using providers.
### Ansible 
    - Configuration management tool used to automate tasks like software installation, updates, and system configuration.
    - Uses YAML, a simple and human-readable language for writing playbooks and defining automation tasks.
    -  Imperative – you define specific steps to be executed in order to reach the desired system state.
    - Supports cloud integration but primarily used for on-instance configuration; not a provisioning tool.
   ## Terraform vs CloudFormation
   ### Terraform 
      - Multi-cloud Infrastructure as Code tool by HashiCorp.
      - Works on AWS, Azure, GCP, Kubernetes, VMware, On-prem
      - Uses HashiCorp Configuration Language (HCL) – simple and readable.
      - Maintains a state file (local or S3/remote).
      - Strong module support, reusable across clouds.
  ### CloudFormation
      - AWS-only Infrastructure as Code service.
      - Only for AWS.
      - Uses YAML / JSON – often more verbose and complex.
      - State is managed internally by AWS (no state file needed).
      - Supports nested stacks, less flexible than Terraform modules.
## set up / install  terraform on aws ec2/ubuntu machine 
 ```bash
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```
## Terraform block types:

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F32dp7v0od58x78hsyrhi.jpeg?utm_source=chatgpt.com)

![Image](https://miro.medium.com/0%2AwwmllWIGPoYEvm7u.jpg?utm_source=chatgpt.com)

---

# ✅ **Main Block Types in Terraform**

## **1. `terraform {}` block**

This block is used to define Terraform-level settings.

### **Purpose**

* Set Terraform version
* Define backend for storing state
* Enable/disable experimental features

### **Example**

```hcl
terraform {
  required_version = ">= 1.5.0"
}
```

---

## **2. `provider {}` block**

Used to configure cloud/service providers (AWS, Azure, GCP, etc).

### **Example**

```hcl
provider "aws" {
  region = "ap-south-1"
}
```

---

## **3. `resource {}` block**

This is the **most important** block.
Used to create actual infrastructure (EC2, VPC, S3, etc).

### **Example**

```hcl
resource "aws_instance" "myvm" {
  ami           = "ami-0abcd"
  instance_type = "t2.micro"
}
```

---

## **4. `data {}` block**

Used for **reading** existing infrastructure (not creating).

### **Example**

```hcl
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["amazon"]
}
```

---

## **5. `variable {}` block**

Used to take input values from users.

### **Example**

```hcl
variable "instance_type" {
  type    = string
  default = "t2.micro"
}
```

---

## **6. `output {}` block**

Used to show values after `terraform apply`.

### **Example**

```hcl
output "public_ip" {
  value = aws_instance.myvm.public_ip
}
```

---

## **7. `locals {}` block**

Used to define local variables only used inside the configuration.

### **Example**

```hcl
locals {
  env = "dev"
}
```

---

## **8. `module {}` block**

Used to reuse Terraform code.

### **Example**

```hcl
module "vpc" {
  source = "./vpc-module"
}
```

# 🎯 **Interview-Ready One-Line Answer**

**Terraform has several block types like `terraform`, `provider`, `resource`, `data`, `variable`, `output`, `locals`, and `module`.
`resource` creates infrastructure, `provider` connects to cloud,
`variable` takes input, `output` shows results, `data` reads existing resources, `module` reuses code.**

---
Here is a **perfect interview-ready answer** for **Terraform Workflow** — short, clear, and easy to remember.

![Image](https://www.devopsschool.com/blog/wp-content/uploads/2023/04/terraform-workflow-1-1024x512.jpg?utm_source=chatgpt.com)

![Image](https://www.devopsschool.com/blog/wp-content/uploads/2021/07/terraform-architecture-components-workflow-1-768x333.jpg?utm_source=chatgpt.com)

---

## Terraform Workflow

**Terraform follows a simple 4-step workflow: Write → Init → Plan → Apply → Destroy.**

### **1. Write**

You write your infrastructure code in `.tf` files using HCL.
Example: resources, providers, variables.

---

### **2. Initialize (`terraform init`)**

This command initializes the working directory:

* Downloads provider plugins (AWS/Azure/GCP)
* Sets up backend (if configured)

**Init is done only once per project (or when providers change).**

---

### **3. Plan (`terraform plan`)**

Terraform shows an execution plan:

* What will be created
* What will be modified
* What will be destroyed

**Plan is only a preview. Nothing actually changes yet.**

---

### **4. Apply (`terraform apply`)**

Terraform executes the plan and provisions the infrastructure.
**This step actually creates, updates, or deletes resources.**

---

### **5. Destroy (`terraform destroy`)**

Used to clean up and remove all infrastructure created by Terraform.

---

# 🎯 **Simple Interview Answer**

“Terraform workflow is: write the code, run `terraform init` to initialize, run `terraform plan` to preview changes, run `terraform apply` to create resources, and `terraform destroy` to remove everything. This is the standard Terraform lifecycle.”
# Creating a file on local using HCL
```hcl
resource local_file my-file{
  filename = "automate.txt"
  content = "My first hcl file"
```
## run the commands in terminal after creating hcl file
```bash
terraform init
terraform validate
terraform plan
terraform apply
terraform apply -auto-approve   ##terraform apply -auto-approve is used to apply the Terraform changes without asking for manual confirmation.
terraform destroy ## ton delete created resources
```
## creating a s3 bucket uding HCL /terraform
```hcl
provider "aws"{
region = "ap-south-1"

}
resource "aws_s3_bucket" "mybucket"{
 bucket = "ganeshterraformbucket"

}
```

