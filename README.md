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
```bash
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```
      
