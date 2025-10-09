# Introduction to Terraform

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


# Creating an EC2 Instance with Terraform (DEMO)

## Step 1: Create a new Terraform file
- Create a file named `ec2.tf` (all Terraform configs should end with `.tf`).
- This file will contain the resource block for an EC2 instance.

## Step 2: Find the EC2 resource in Terraform Registry
- Go to the [Terraform AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs).  
- Use the search bar to look for **EC2 instance**.  
- The correct resource block is `aws_instance`.  
- Review the Argument Reference section to identify required arguments:
  - `ami` (Amazon Machine Image ID)  
  - `instance_type`

## Step 3: Obtain the AMI ID
- Go to the AWS Console → EC2 → Launch Instance.  
- Choose an AMI (e.g., Ubuntu).  
- Copy the **AMI ID** from the console.  
- This will be used in your Terraform resource block.

### Step 4: Write the EC2 resource block
Example `ec2.tf`:

```
resource "aws_instance" "this" {
  ami           = "ami-xxxxxxxx"   # Replace with your AMI ID
  instance_type = "t2.micro"       # Free tier eligible
  tags = {
    Name = "Terraform-EC2-Demo"
  }
}
```
## Step 5: Configure AWS Provider
Make sure you have a provider block defined (in `provider.tf` or a separate file):

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "6.13.0"
    }
  }
}

provider "aws" {
  # Configuration options
}
```
## Step 6: Authenticate with AWS
Create an IAM user with programmatic access and attach the required permissions (e.g., EC2 Full Access for testing).  
Export your credentials as environment variables in your terminal:

```
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
export AWS_DEFAULT_REGION="eu-west-1"
```
## Step 7: Run Terraform Commands

1- Initialize the project (downloads provider plugins): `terraform init`

2- Preview changes:`terraform plan`

Output should show 1 to add.

3- Apply the configuration: `terraform apply`

Confirm with yes.

## Step 8: Verify in AWS Console

- Open the EC2 Dashboard in the AWS Console.
- You should see a running instance of type t2.micro with the Ubuntu AMI you selected.
- The tag (e.g., Terraform-Test) will be visible in the instance details.

---

# Terraform importing

## Terraform Importing Introduction

`terraform import` lets you bring existing cloud resources under Terraform management. It is Useful when resources were created manually or outside Terraform, avoids deleting and recreating infrastructure just to start using Terraform.  

### Why It’s Important
- In production environments, many resources may already exist.  
- When joining a company, infrastructure might not yet be managed as code.  
- Importing allows you to adopt Infrastructure as Code without disrupting existing systems.  

### How It Works
1. **Identify the existing resource**  
   - Example: EC2 instance, S3 bucket, VPC, etc.  

2. **Create a matching resource block** in Terraform configuration  
   - Import does **not** generate the block automatically.  
   - You must write the resource block that corresponds to the existing resource type.  

3. **Run `terraform import`**  
   - Maps the existing resource in your cloud account to the Terraform state file.  
   - From that point, Terraform manages it like any other resource.

## Terraform importing Code Block

In Terraform v1.5.0 and later, use an import block to import instances using the id.

In code:

```
Import {
  to = aws_instance.web
  id = "i-12345678"
}
```

##  Terraform Importing - Terraform Registry

Terraform documentation (Terraform Registry) explains how to import resources. Each resource has an Import section showing the syntax and required identifiers.  

Example: Importing an AWS Instance
- Documentation shows that AWS instances are imported using their Instance ID.  
- Syntax:  
```
terraform import aws_instance.web i-1234567890abcdef0
```

# Terraform Importing - Demo

### Overview
- `terraform import` brings **existing** cloud resources (created outside Terraform) under Terraform management.
- You **must** have:
  - A provider configured
  - A matching **resource block** in your `.tf` code
  - The resource’s unique **ID** (for EC2, the Instance ID like `i-0abc...`)

---

### 1) Prepare your configuration
Provider (example region shown):
```
provider "aws" {
  region = "eu-west-1"
}
```
Create a resource block that will represent the existing instance (use a clear local name):

```
resource "aws_instance" "import" {
  # Minimal skeleton — values will be reconciled after import
  ami           = "ami-placeholder"
  instance_type = "t2.micro"

  # If the real instance has tags, add them here to avoid drift
  tags = {
    Name = "Terraform-Import"
  }
}
```
Note: The ami value here is a placeholder; after import you’ll adjust attributes to match the real instance.

### 2) Get the resource ID
In AWS Console → EC2 → Instances → copy the Instance ID (e.g., i-0123456789abcdef0).

### 3) Run the import
Map the existing instance to your Terraform resource address:`terraform import aws_instance.import i-0123456789abcdef0`

- aws_instance.import = <resource_type>.<name> from your .tf code
- i-... = existing EC2 Instance ID

You should see messages like Import prepared and Import successful.

### 4) Reconcile configuration vs. real resource
Run a plan to ensure desired state = current state: `terraform plan`

- Goal: 0 to add, 0 to change, 0 to destroy.
- If the plan shows changes (e.g., missing tags, user data, credit/spec settings), update your resource block to match what exists.
- Repeat terraform plan until there are no changes.

Tip: Use the AWS Console (or terraform state show aws_instance.import) to see real attributes and mirror them in your .tf.

### 5) Importing multiple existing instances

For each additional instance add another resource block with a unique name:

```
resource "aws_instance" "import_2" {
  ami           = "ami-placeholder"
  instance_type = "t2.micro"
  tags = { Name = "Terraform-Import-2" }
}
```
Import it with its own ID:
`terraform import aws_instance.import_2 i-0fedcba9876543210`

Run terraform plan and reconcile attributes.

--- 

# Statefiles

Terraform uses a **state file** to track infrastructure.

## Local Statefiles 

By default, the state file is stored locally in the project directory.

### Characteristics of Local State
- Default behavior - no extra setup required.
- Easy to configure - automatically created in your working directory.
- Best for single-user projects - simple environments where only one person manages the infrastructure.
- Contained and isolated - avoids complications of shared access or external inputs.

Local Statefiles should be used when learning or experimenting with Terraform, creating Small personal projects and testing deployments like creating an EC2 instance.


## Remote Statefiles

- Remote statefiles store Terraform state in a central, secure location. They are designed for team collaboration and larger projects
  
### Benefits of Remote State
- Collaboration  
  - Multiple team members share the same state.  
  - Reduces risk of conflicts or inconsistencies.  

- State locking  
  - Prevents simultaneous changes.  
  - Supported by backends like AWS S3 and Terraform Cloud.  
  - Protects against state corruption during concurrent updates.  

- Backups & security  
  - Remote backends can automatically back up state.  
  - Encryption ensures state data is protected.  
  - Enhances recoverability and compliance.  

Remote Statefiles are used in team-based projects, production environments and workflows that involve CI/CD pipelines.  

## Configure Backend with Statefile

### Key Concept
- A backend defines where and how Terraform state is stored.  
- By default -> local file (`terraform.tfstate`) in your project folder.  
- You can configure a remote backend (e.g., AWS S3) for team use and added security.


### Example: Configure S3 Backend, add the following to provider.tf file.
```
terraform {
  backend "s3" {
    bucket = "terraform-state-demo"   # must be globally unique
    key    = "terraform.tfstate"      # path inside the bucket
    region = "eu-west-1"              # match your deployment region
  }
}
```
### Workflow
1- Set up an S3 bucket in AWS (e.g., terraform-state-demo).

2- Add the backend "s3" block to your configuration.

3- Run: `terraform init`
- Initializes the backend.
- Migrates local state to the S3 bucket.
- Prompts: “Do you want to copy the existing state to the new backend?” -> choose Yes.

From then on, Terraform stores state in S3, not locally.

## Terraform Workflow

<img width="812" height="452" alt="image" src="https://github.com/user-attachments/assets/8df644d0-2fa4-494f-98d9-c86ffdd8cf4f" />

---

# Variables

## Why are Variables used?

- Enable dynamic configuation changes without altering code
- Manage different environments with the same configuration files.
- Makes modules reusable across multiple projects
- Define values once and reference them multiple times
- Reduce redundancy and potential for errors
- Standardise variable names for better collaboration

## Types of Variables

## 1. Input Variable:

- Input variables make Terraform configurations dynamic and reusable.  
- Values can come from:
  - User prompts
  - CLI arguments
  - Variable definition files (`.tfvars`)

### Declaring Variables
Example `variables.tf`:

```
variable "instance_type" {
  type        = string
  default     = "t2.micro"
}
```

### Using Variables
Reference variables with the var. prefix:

```
resource "aws_instance" "example" {
  ami           = "ami-1234567890abcdef0"
  instance_type = var.instance_type
}
```

### Without Default Value

If no default is provided, Terraform will prompt for input during plan or apply:

```
variable "instance_type" {
  description = "EC2 instance type"
  type        = string
}
```
Prompt example:

var.instance_type
  Enter a value: t2.micro

## Input Variable - terraform.tfvars 

### What is `terraform.tfvars`?
- A special file Terraform automatically loads to assign values to input variables.  
- Keeps variable values separate from code, making configurations cleaner and easier to manage.  
- If present in the project directory, Terraform reads it by default without extra flags.  

### Example

**variables.tf**
```
variable "instance_type" {
  type = string
}

variable "region" {
  type = string
}
```

**terraform.tfvars**

Best practice: store variable values in a dedicated file → terraform.tfvars. File automatically loaded by Terraform.
```
instance_type = "t2.micro"
region        = "eu-west-1"
```

Then you would type in the terminal `terraform plan` followed by `terraform apply`. Terraform automatically uses the values from terraform.tfvars, no need to pass them on the command line.

## Local Variables

### What are Local Variables?
- Local variables are internal values within Terraform configurations.  
- Unlike input variables (provided by users), locals are defined inside the configuration only.  
- Used to reduce redundancy and keep code DRY (Don’t Repeat Yourself).  

### Defining Locals
- Defined in a `locals { }` block.  
- Can store one or multiple related values.  
- Example usage: AMI IDs, naming conventions, tags, or any value reused multiple times.

Example `variables.tf`:
```
variable "instance_type" {
  type = string
  default = "t3.micro"
}

locals {
  instance_ami = "ami-123456789"
}
```
### Referencing Locals
- Accessed with the `local.` prefix.  
- Works similarly to input variables (`var.`), but strictly for **internal use**.
```
   resource "aws_instance" "this" {
  ami                     = local.instance_ami
  instance_type           = var.instance_type
}

resource "aws_instance" "import" {
  ami                     = local.instance_ami
  instance_type           = var.instance_type
  tags = {
      Name        = "Terraform-import"
    }
user_data_replace_on_change = false    
```
### Benefits
- Centralises repeated values(e.g., AMI ID used across resources).  
- Improves readabilityand maintainability of configurations.  
- Makes it easier to update values — change once in locals, applied everywhere.  




## Output Variables

Output variables are used to display values after terraform apply.  

- They are useful for:
  - Retrieving IDs, IP addresses, or other resource attributes.  
  - Passing information to other configurations or automation tools.  
  - Making infrastructure details easily accessible.  


### Defining an Output Variable
- Use an `output` block with:
  - **name** → identifier of the output.  
  - **description** (optional, but good practice).  
  - **value** → what to output.  

Example:
```
    output "instance_id" {
      description = "The ID of the EC2 instance"
      value = aws_instance.this.id
    }
```    

### Using Outputs
- After `terraform apply`, the defined values are displayed:  
```
    Apply complete! Resources: 0 added, 0 changed, 0 destroyed.

    Outputs:

    instance_id = "i-0abcd1234efgh5678"
```
The outputs can be printed to the terminal and consumed by other Terraform configurations or scripts.  


### Best Practices
- **Use descriptive names**: e.g., `instance_id`, `db_endpoint`.  
- **Document outputs**: always include a description.  
- **Expose only critical information**: → outputs should be useful for automation or troubleshooting.  
- **Secure sensitive outputs**: use `sensitive = true` for secrets/passwords.  

Example with sensitive output:
```
    output "db_password" {
      description = "Database admin password"
      value       = random_password.db.result
      sensitive   = true
    }
```
## Variable Hierarchy

Terraform allows variables to be defined in multiple ways. When multiple definitions exist, Terraform uses a precedence order to decide which value is applied.  

### Precedence (Lowest → Highest)

1. **Default values**  
   - Defined inside the variable block.  
   - Used if no other value is provided.  
```
   Example: variables.tf file
  
       variable "instance_type" {
         type    = string
         default = "t2.micro"
       }
```
2. **TFVAR files**  
   - Terraform automatically loads `terraform.tfvars` or any file ending in `.tfvars`.  
   - Can also be passed explicitly with `-var-file`.  
```
   Example: terraform.tfvars 
       instance_type = "t3.micro"
```
   Usage:  
       terraform apply -var-file="filename.tfvars"

3. **TFVAR environment variables**  
   - Take precedence over both TFVAR files and defaults.  
   - Format: `TF_VAR_<variable_name>`  
```
   Example:  
       export TF_VAR_instance_type=t3.small
```

4. **Command line flags (Highest precedence)**  
   - Values provided directly in CLI override all others.  
```
   Example:  
       terraform apply -var="instance_type=t3.large"
```

## Types of Variables

Variables make Terraform code dynamic and reusable.  

- Two main categories:  
  - **Primitive types** - simple values (string, number, bool).  
  - **Complex types** - groupings of values (list, map, object).  
- Analogy:  
  - Primitive types = single ingredients (flour, sugar, eggs).  
  - Complex types = full recipes (multiple ingredients + instructions).  



### Primitive Types

- String: Simple text value.
```
    variable "example_string" {
      type    = string
      default = "hello world"
    }
```
- Number: Whole numbers or decimals.  
```
  variable "example_number" {
      type    = number
      default = 42
    }
```
- Bool: True or false values (yes/no logic).  
```
  variable "example_bool" {
      type    = bool
      default = true
    }
```

### Complex Types

- List: Ordered sequence of values, all the same type (like a shopping list).
```
    variable "example_list" {
      type    = list(string)
      default = ["flour", "sugar", "eggs"]
    }
```
- Map: Key-value pairs (like a cookbook index).
```  
    variable "example_map" {
      type = map(string)
      default = {
        flour = "500g"
        eggs  = "2"
      }
    }
```
- Object: Collection of attributes that can each have different types (like a recipe card).  
```
  variable "example_object" {
      type = object({
        name   = string
        age    = number
        active = bool
      })
      default = {
        name   = "John"
        age    = 30
        active = true
      }
    }
```
---
# Modules

## What is a Module?

A module is a collection of Terraform configuration files grouped together to serve a specific purpose. Think of a module as a blueprint for building infrastructure (e.g., an EC2 instance, networking setup, or full environment). By default, any Terraform configuration in a folder is treated as a root module.  


## Why Use Modules?

1. **Reusability**  
   - Write infrastructure code once -> reuse it across multiple projects or accounts.  
   - Example: the same EC2 module can be used in dev, staging, and prod.  

2. **Organization**  
   - Helps structure Terraform code as complexity grows.  
   - Keeps infrastructure manageable at scale.  

3. **Consistency**  
   - Enforce the same patterns, security rules, and naming conventions across all environments.  
   - Reduces drift between dev, staging, and production.  

4. **Collaboration**  
   - Teams can share modules instead of writing everything from scratch.  
   - Makes Terraform accessible to teams (like data engineers) who aren’t experts but need infrastructure.  

## What makes a good module?

### 1. Simplicity
- Keep the module **focused on a single responsibility**.  
- Example: An **EC2 module** should only launch EC2 instances, not mix in unrelated resources like RDS or load balancers.  
- This makes the module **clean, reusable, and easy to maintain**.


### 2. Documentation
- Always provide a **README.md** or inline comments.  
- Document:  
  - **Inputs (variables)**  
  - **Outputs**  
  - **Usage examples**  
- Well-documented modules are easier to **use, share, and collaborate on**.


### 3. Reusability
- Avoid **hardcoding values** (e.g., AMI IDs, regions, instance types).  
- Use **variables** to allow the module to adapt to different environments (dev, staging, prod).  
- Ensures the module can be applied in **multiple projects and accounts**.


### 4. Output Values
- Modules should expose **useful outputs** for other parts of your configuration.  
- Example: An EC2 module could output:  
  - Instance ID  
  - Public IP address  
- Outputs make modules more **valuable and easier to integrate**.

### Additional Best Practices
- **Testing**: Regularly test modules across environments and use cases.  
- **Versioning**: Tag versions to provide upgrade paths and rollbacks.  
- **Collaboration**: Modules allow cross-team reuse and consistency across environments.  

### Interview Tip
- When asked **“What makes a good module?”** remember these four keywords **Simplicity, Documentation, Reusability, Output Values**  
- **Modules & state** are two of the **most common Terraform interview topics**.  
- Being able to explain **why modules are useful** (reusability, consistency, collaboration) will set you apart from other candidates. 

## Terraform Module DEMO

In this demo, we modularize our EC2 configuration and learn how to deploy Terraform modules.

### File Structure
```
repo/
├── main.tf
├── provider.tf
├── variables.tf
├── terraform.tfvars
└── modules/
 └── ec2/
  ├── ec2.tf
  └── variables.tf
```
- provider.tf → contains the provider block and remote backend (e.g., S3 for state).
- terraform.tfvars → holds variable values.
- modules/ec2/ → contains the EC2 module code.
- main.tf → root configuration where the module is called.

### Why We Modularize
- Keeps Terraform code organized and reusable.
- Separates repeatable infrastructure (modules) from environment-specific configs (root).
- Ensures simplicity and scalability.

### Calling a Module

In your main.tf at the repo root:
```
module "ec2" {
 source = "./modules/ec2"
}
```
- module → keyword to call a module.
- "ec2" → name of the module.
- source → path to the module (can be relative, absolute, or even a Git/registry source).

### Workflow

1- `terraform init` - Initializes the backend, providers, and now modules.

2- `terraform plan` - Shows resources to add/update/destroy.

Important: When moving existing resources into a module, Terraform may show “to destroy” and “to create” because the resource addresses change.

3- `terraform apply` - Deploys infrastructure using the module, Confirms outputs.

### State Considerations

- By default, Terraform sees the move into a module as a change in resource address.
- This can cause Terraform to destroy and recreate resources.
- In production, avoid this by using:
  - `terraform state mv aws_instance.this module.ec2.aws_instance.this`
  - This moves the state reference to the new module address, preventing unnecessary destruction.

# Terraform interview questions


## Common Junior-Level Questions

### 1. What is Terraform? How does it work?

- Open-source Infrastructure as Code (IaC) tool by HashiCorp
- Cloud-agnostic – works across AWS, Azure, GCP, Kubernetes, and more
- Uses providers (plugins) to communicate with APIs
- Supports idempotency → repeated runs produce the same results

### 2. What are the benefits of using Infrastructure as Code (IaC)?
- Automation – reduces manual effort
- Consistency – environments are predictable and standardized
- Repeatability – same config can be reused across environments
- Version control – track changes in Git
- Faster and safer deployments

### 3. Difference between terraform plan and terraform apply
- Plan → Compares desired state (config) vs. current state (real infra)
  - Outputs preview of what will be added, changed, or destroyed
  - Like a dry run
- Apply → Executes the plan and updates infra + state file

### 4. What is a Terraform Provider?
- Plugin that allows Terraform to manage resources via APIs
- Example: hashicorp/aws for AWS resources
- Providers are declared in required_providers and configured with credentials/region

### 5. Explain the role of State in Terraform
- State file is Terraform’s blueprint of infrastructure
- Tracks resources Terraform manages
- Ensures idempotency and accurate plans
- Without state, Terraform wouldn’t know what to add, update, or delete

## Intermediate-Level Questions

### 6. Purpose of a Backend in Terraform

- Defines where and how state is stored
- Local backend → stores state in project directory
- Remote backend → S3, Terraform Cloud, etc.
- Enables collaboration, locking, security, and backups

### 7. Difference between terraform import and terraform init
- Import: Brings existing infrastructure (not created by Terraform) under management
  - Example: Import manually created EC2 instances
- Init: Initializes working directory
  - Downloads providers
  - Sets up backends
  - Initializes modules

### 8. How do you manage sensitive data in Terraform?
- Use environment variables (e.g., TF_VAR_db_password)
- Store secrets in secret managers (AWS Secrets Manager, Vault)
- Avoid committing state files (they may contain secrets)
- Use sensitive = true in variables to hide output in CLI

### 9. Purpose of terraform refresh
- Updates state file to match real-world infrastructure
- Queries live infra → ensures state file is accurate
= Helps avoid drift between desired and current state

## Behavioral/Scenario Questions

### 10. Describe a challenging problem you solved with Terraform
- Example: Debugging provider errors, state drift, IAM permission issues
- Show problem-solving: how you read errors, tested fixes, and documented solutions
- Emphasize ability to explain code clearly

### 11. How do you ensure Terraform code is maintainable and scalable?
- Use modules → keep code DRY and modular
- Leverage variables + tfvars files for flexibility
- Maintain documentation (README, comments)
- Version control (Git) for collaboration + tracking changes
- Testing and code reviews

### 12. Have you worked with Remote State Management?
- Yes → critical in team environments
- Enables collaboration, prevents conflicts with state locking
- Ensures security (encryption, access controls)
- Example: Store state in S3 + DynamoDB lock table

### Key Words & Concepts for Interviews
- Idempotency
- Cloud agnostic
- Consistency, automation, repeatability
- Desired state vs. current state
- Modules, DRY principle
- State file as blueprint
- Remote backend for collaboration
 

# Advanced Terraform Topics























  
