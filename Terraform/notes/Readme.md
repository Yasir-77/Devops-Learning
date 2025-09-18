# Introduction to terraform

## Infrastructure as code (IaC)

Infrastructure as Code (IaC) is Writing scripts/templates to define and manage infrastructure, Tools like Terraform or CloudFormation are commonly used. The code is deployed to cloud providers such as AWS, Azure, GCP.  

Terraform is a Cloud-Agnostic Tool meaning it can deploy to any cloud provider (not limited to AWS). Achieves this using providers and plugins from the Terraform Registry.  
- How Terraform Works with Providers:  
  - Downloads required provider plugins.  
  - Uses APIs of the target cloud/service to create and manage resources.  

IaC can be stored in version control systems like git. This allows you to track your changes, roll back to certain versions and colaborate amongts team members. 

In a production enviornment that would look like members in your team deploying to the same infrastructure, each pushing different bits of code, and that is often managed by the Terraform state file and the Terraform lock file.

## Infrastructure orchestration vs Config management:

Both are essential practices in DevOps, but serve different purposes.  They often work together to provision and configure infrastructure.  

### Orchestration Tools
- Examples: Terraform, AWS CloudFormation  
- **Purpose:**  
  - Automate the provisioning of infrastructure resources (servers, networks, storage, etc.).  
  - Arrange resources in the correct order of dependencies.  
- **Analogy (Hajj):**  
  - Like arranging transportation, hotels, and tents for millions of pilgrims.  
  - Ensuring the essentials are set up and ready.  

### Configuration Management Tools
- Examples: Ansible, Puppet, Chef  
- **Purpose:**  
  - Manage the setup and configuration inside servers once they are provisioned.  
  - Install packages, configure software, manage files, users, and services.  
- **Analogy (Hajj):**  
  - Like ensuring each individual pilgrim has their clothing, prayer mats, and utilities.  
  - Personalizes and configures the environment for actual use.  

## What is Terraform?

<img width="815" height="458" alt="image" src="https://github.com/user-attachments/assets/9e7d466c-47f5-4aca-bdb8-387984e15bed" />

### Key Concepts
- Terraform is an Infrastructure as Code (IaC) tool.  
- Cloud agnostic -> can deploy to AWS, Azure, GCP, and more.  
- Used to create, update, and version infrastructure consistently.  

### Terraform Workflow
1. Practitioner 
   - Writes infrastructure definitions using Terraform code.  

2. Infrastructure as Code (IaC)  
   - Code defines the desired state of resources.  

3. Plan (`terraform plan`)  
   - Compares current state vs. desired state.  
   - Shows proposed changes (create/update/delete).  
   - Ensures you know exactly what Terraform will do before applying.  

4. Apply (`terraform apply`)  
   - Executes the plan.  
   - Creates/updates resources in the chosen cloud provider.
  
### Benefits
- Creation of new resources.  
- Updating existing resources to match the code.  
- Versioning infrastructure for consistent and trackable changes.  

## Tips for using Terraform

- Get hands-on with the official HashiCorp Terraform documentation  
  - Covers what Terraform is, use cases, adoption phases, and comparisons with alternatives  

- Use the Terraform Registry daily  
  - Documentation for providers (e.g., AWS, Azure, GCP)  
  - Reference resources needed for deployments  

- Testing and validation are essential  
  - Always review terraform plan carefully  
  - Use validation commands to avoid breaking production infrastructure  

- Start with a small MVP (minimum viable product)  
  - Begin with a simple resource deployment  
  - Iterate by adding variables, modules, and more complex patterns later  

- Apply the DRY (do not repeat yourself) principle  
  - Use modules and templates to avoid repetitive code  
  - Cleaner, reusable, and maintainable Terraform configurations

---

# Terrafrom State file

The Terraform state file is the blueprint of your infrastructure. It is an up-to-date record of what resources actually exist. Critical for ensuring Terraform knows the difference between what’s deployed and what’s defined in code.  

### Idempotency
- Idempotency = running the same Terraform config multiple times will always produce the same result.  
- Prevents resources from being duplicated.  
- Only applies the specific changes made in your configuration.  
- Useful keyword to know for interviews.  

### Desired State vs Current State
- Desired state (.tf files):  
  - What you want your infrastructure to look like.  
  - Defined in Terraform configuration.  

- Current state (.tfstate file):  
  - What your infrastructure actually looks like right now.  
  - Stored in Terraform’s state file.  

Terraform compares desired state and current state to decide what actions to take. Example: If config defines 3 EC2 instances but state file has only 2, Terraform will deploy 1 more.  

---

# Deploying Infrastructure

## Terraform Providers

A Terraform provider is a plugin that allows you to interact with cloud platforms, services, or other technologies. It's what enables Terraform to manage your resources in the cloud.

### Terraform Provider code

<img width="280" height="317" alt="image" src="https://github.com/user-attachments/assets/614e5461-52e1-4170-b094-9c586a3dab73" />

### Terraform Block

Defines which providers are required and where they come from.
```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "5.62.0"
    }
  }
```
- required_providers: Lists the providers your configuration depends on
- source: Where the provider is fetched from (namespace/provider) Example: hashicorp/aws → AWS provider from HashiCorp registry
- version: Locks the provider version for consistency across environments


### Provider Block

Configures the chosen provider
```
provider "aws" {
  # Configuration options (e.g., region, profile)
}
```
- provider: Keyword that tells Terraform which provider to configure
- aws: The actual provider name (AWS in this case)
- Inside the block, you specify configuration like region or credentials

---

# Basic Terraform Commands

## Terraform init

### Key Concept
- `terraform init` = **initialize**
- First command to run in any new or existing Terraform project
- Prepares the working directory with everything needed to run Terraform

### What It Does
- **Initializes the backend**: Backend is where Terraform stores its state it can be local (on your machine) or remote (e.g., AWS S3). Ensures Terraform can track resources and maintain idempotency
- **Initializes provider plugins**: Reads configuration to identify required providers. It downloads providers from the Terraform Registry (or other sources). Providers act as plugins so Terraform can talk to cloud services (e.g., AWS)

### Why It’s Important
- Sets up the workspace before any `plan` or `apply`
- Ensures state management is configured correctly
- Ensures providers are installed and ready to use

## Terraform Plan

### Key Concept
- `terraform plan` = preview changes before they happen
- Security-first mindset: review changes before applying them
- Lets you confirm Terraform will do exactly what you expect


### What It Does
- Analyzes configuration files (**desired state**)  
- Compares with the Terraform state file (**current state**)  
- Generates a plan showing what changes will be made  

### Output Symbols
When reviewing the plan output, watch for these:

- `+` → **Create** (a new resource will be added)  
- `~` → **Update in place** (an existing resource will be modified)  
- `-` → **Destroy** (a resource will be removed)
  
e.g.
<img width="400" height="600" alt="image" src="https://github.com/user-attachments/assets/f9906f0c-d046-4757-9b22-46e641e2250c" />

In this example Terraform will perform the follwoing actions:
- An EC2 Instance will be created
- A Security group will have some properties updated
- An S3 bucket will be destroyed

## Terraform apply
### Key Concept
- `terraform apply` = executes the plan  
- Takes the proposed execution plan and applies it to real infrastructure  
- This is when your desired infrastructure becomes reality  


### What It Does
1. **Generates an execution plan**: Similar to running `terraform plan` shows what will be created, modified, or destroyed  
2. **Prompts for confirmation** Asks: *Do you want to perform these actions?*, Enter `yes` to proceed  
3. **Applies the changes**: Creates new resources, updates existing resources and destroys removed resources  
4. **Updates the state file**: State file reflects the new current state, ensures idempotency (running code again won’t duplicate resources)  



## Terraform destroy

Terraform destroy command is a convenient way to destroy all remote objects managed by a particular Terraform configuartion

### What It Does
1. **Reads configuration and state file**: Determines what resources are being managed  
2. **Generates a destruction plan**: Similar to `terraform plan` but focused on removal, lists all resources to be destroyed  
3. **Prompts for confirmation**: Asks before executing destruction, Safety feature to prevent accidental deletions  
4. **Executes destruction**: Sends delete commands to the cloud provider, removes resources safely and efficiently  
5. **Updates the state file**: Reflects that resources have been destroyed, keeps Terraform’s record accurate

## Summary
- `terraform init` → set up environment  
- `terraform plan` → preview changes  
- `terraform apply` → execute changes
- `terraform destroy` → remove all managed resources  
- Together, these form the core Terraform workflow

---

# Resource Block

A **resource block** defines a piece of infrastructure Terraform manages, Each resource block maps to a resource type provided by the provider it is used to create, update, or delete resources.  

### Example: AWS EC2 Instance

```
resource "aws_instance" "test" {
  ami           = "ami-1234567890abcdef0"
  instance_type = "t2.micro"

  tags = {
    Name = "Helloworld"
  }
}
```
- Resource: Keyword to define a resource block
  - aws_instance: Resource type (provided by the AWS provider)
  - test: Resource name within the configuration (local identifier)

## Attributes
- ami
  - Specifies the Amazon Machine Image (AMI) to use
  - Defines the operating system/template for the instance (e.g., Ubuntu)

- instance_type
  - Defines the hardware configuration (CPU, memory, etc.)
  - Example: t2.micro (free tier, small test instance)

- tags
  - Optional but good practice
  - Adds labels/metadata (e.g., environment = dev/prod/staging)

Resource blocks are the foundation of Terraform configs they define what infrastructure should exist and how it should be configured. The Attributes control details like OS image, size, and metadata tags.






