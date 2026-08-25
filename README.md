**Terraform**

Definition: Terraform is an Infrastructure as Code (IaC) tool used to provision and manage infrastructure through configuration files.

Terraform allows you to define infrastructure such as virtual machines, networks, databases, storage, and DNS using code instead of manually creating them.

**Infrastructure as Code (IaC)**

Definition: IaC is the practice of managing and provisioning infrastructure using machine-readable configuration files.

Benefits of IaC
Automation
Consistency
Version control
Repeatability
Faster deployments
Reduced human error


**Terraform Architecture
**
Definition: Terraform architecture consists of configuration files, Terraform Core, providers, state, and infrastructure resources.

Basic flow:

Terraform Configuration
        ↓
Terraform Core
        ↓
Provider
        ↓
Cloud/API
        ↓
Infrastructure


**Terraform Configuration**

Definition: Terraform configuration is a collection of .tf files that describe the desired infrastructure.
Terraform reads these files and determines what infrastructure needs to be created or changed.
Example:

resource "local_file" "example" {
  filename = "example.txt"
  content  = "Hello Terraform"
}


HCL (HashiCorp Configuration Language) is the configuration language commonly used to write Terraform code.


**Terraform Providers**

Definition: A provider is a plugin that allows Terraform to communicate with an external platform or service.

Examples:

AWS, Azure, Google Cloud, Kubernetes, GitHub, Docker, VMware

provider "aws" {
  region = "us-east-1"
}

**Resources**

A resource represents an infrastructure object that Terraform creates, updates, or destroys.

resource "<RESOURCE_TYPE>" "<RESOURCE_NAME>" {
  # arguments
}

**Data Sources**

Definition: A data source allows Terraform to retrieve information about existing infrastructure or external data without managing the object itself.

data "aws_ami" "example" {
  # filters
}

Resources generally manage infrastructure, while data sources read information


**Variables**

Definition: Variables are inputs that allow Terraform configurations to be customized without changing the main configuration code.

**Syntax:**

variable "username" {
  type = string
}


**Input Variables**

Definition: Input variables allow users to provide values to a Terraform module from outside the module.

variable "username" {
  type = string
}

resource "local_file" "welcome" {
  filename = "welcome_${var.username}.txt"
}


**terraform.tfvars**

Definition: terraform.tfvars is a conventional file used to assign values to Terraform input variables.

username = "user123"
message  = "Welcome to Terraform training"


**Outputs**

Definition: Outputs expose useful information from Terraform after infrastructure is created.
After applying, Terraform can display the output value.

output "filename" {
  value = local_file.welcome.filename
}


**Terraform State**

Definition: Terraform state is a record of the infrastructure Terraform manages and the relationships between configuration and real-world resources.

The default state file is:

terraform.tfstate


State helps Terraform determine:

What already exists
What needs to be created
What needs to be changed
What needs to be destroyed


**Modules**

Definition: A Terraform module is a reusable collection of Terraform configuration files.

A simple module might contain:

main.tf
variables.tf
outputs.tf


**Terraform Workflow**

Definition: The Terraform workflow is the sequence of commands used to initialize, validate, plan, apply, and manage infrastructure.

Typical workflow:

Write Configuration
        ↓
terraform init
        ↓
terraform validate
        ↓
terraform plan
        ↓
terraform apply
        ↓
Infrastructure


**terraform init**

Definition: terraform init initializes a Terraform working directory and installs required providers and modules.


**terraform validate**

Definition: terraform validate checks whether Terraform configuration is syntactically valid and internally consistent

**terraform fmt**

Definition: terraform fmt automatically formats Terraform configuration files according to Terraform's standard style.

**terraform plan**

Definition: terraform plan shows the changes Terraform intends to make without applying them.

**terraform apply**

Definition: terraform apply executes the planned changes and creates or modifies infrastructure.

**terraform show**

Definition: terraform show displays the current Terraform state or a saved plan in human-readable form.

**terraform output**

Definition: terraform output displays values defined in Terraform output blocks.



**Drift**

Definition: Infrastructure drift occurs when real infrastructure changes outside Terraform and no longer matches the Terraform configuration or state.


