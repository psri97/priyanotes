# 📘 Terraform Quick Notes (Single Sheet)

---

## terraform init
**What:** Initializes Terraform in a project folder.  
**Why:** Downloads providers and sets up backend.  
**Where:** Run first time in any Terraform project.  
**Use-case:** Starting infra setup for AWS (EC2, S3, etc.).

---

## terraform plan
**What:** Shows execution plan of changes.  
**Why:** Preview what will be created/modified/deleted.  
**Where:** Before applying changes.  
**Use-case:** Verify infra changes before deployment.

---

## terraform apply
**What:** Executes changes to create/update infrastructure.  
**Why:** Actually provisions resources.  
**Where:** After reviewing plan.  
**Use-case:** Launch EC2 instance or create S3 bucket.

---

## terraform fmt
**What:** Formats Terraform code.  
**Why:** Keeps code clean and readable.  
**Where:** Anytime during development.  
**Use-case:** Standardize code before commit.

---

## terraform validate
**What:** Checks syntax and configuration errors.  
**Why:** Ensures code is correct before execution.  
**Where:** Before plan/apply.  
**Use-case:** Catch mistakes early in .tf files.

---

## terraform destroy
**What:** Deletes all managed infrastructure.  
**Why:** Clean up resources and avoid cost.  
**Where:** When infra is no longer needed.  
**Use-case:** Remove test environment after use.

---

## terraform state list
**What:** Lists resources in Terraform state file.  
**Why:** Track what Terraform manages.  
**Where:** During debugging or state inspection.  
**Use-case:** Check existing resources in state.

---

## terraform state mv
**What:** Moves resource in state file.  
**Why:** Rename or reorganize resources without recreation.  
**Where:** Refactoring Terraform code.  
**Use-case:** Renaming resource block safely.

---

# 🧠 Final Interview Answer

"Terraform commands help manage infrastructure lifecycle.  
Init sets up, plan previews, apply creates resources, and destroy removes them.  
State commands help manage resource tracking safely."

---


---

# 📚 Terraform Interview Questions & Answers

## 1. What is Terraform?
Terraform is an Infrastructure as Code (IaC) tool used to create and manage cloud resources.  
It automates infrastructure using configuration files.

---

## 2. What is Infrastructure as Code (IaC)?
Managing infrastructure using code instead of manual setup.  
Helps with automation, consistency, and version control.

---

## 3. What is a provider in Terraform?
A plugin that allows Terraform to interact with cloud services (AWS, Azure, GCP).  
Example: aws provider for creating EC2, S3.

---

## 4. What is a resource in Terraform?
A block that defines infrastructure components.  
Example: EC2 instance, S3 bucket.

---

## 5. What is terraform state?
A file that tracks real infrastructure managed by Terraform.  
Helps Terraform know what exists and what to change.

---

## 6. What is terraform plan?
Shows preview of changes before applying.  
Used to avoid unexpected modifications.

---

## 7. Difference between plan and apply?
plan → preview changes  
apply → execute changes

---

## 8. What is terraform init?
Initializes project by downloading providers and setting backend.  
First command to run in Terraform.

---

## 9. What is terraform destroy?
Deletes all infrastructure managed by Terraform.  
Used for cleanup.

---

## 10. What is backend in Terraform?
Stores Terraform state remotely (e.g., S3).  
Used for collaboration and state management.

---

## 11. What is remote state?
State stored outside local system (S3, etc.).  
Used in team environments.

---

## 12. What is state locking?
Prevents multiple users from modifying state simultaneously.  
Avoids conflicts.

---

## 13. What is terraform validate?
Checks syntax and configuration errors.  
Used before execution.

---

## 14. What is terraform fmt?
Formats code for readability.  
Maintains standard structure.

---

## 15. What is a module in Terraform?
Reusable block of Terraform code.  
Used to avoid duplication.

---

## 16. What is variable in Terraform?
Used to pass dynamic values.  
Makes code flexible.

---

## 17. What is output in Terraform?
Displays values after execution.  
Example: instance IP address.

---

## 18. What is dependency in Terraform?
Defines order of resource creation.  
Handled automatically or using depends_on.

---

## 19. What is drift in Terraform?
Difference between actual infra and Terraform state.  
Occurs when manual changes are made.

---

## 20. How do you handle drift?
Run terraform plan and apply to sync state.  
Or import resources if needed.

---

## 21. What is terraform import?
Adds existing resource into Terraform state.  
Used for already created infrastructure.

---

## 22. What is workspace in Terraform?
Used to manage multiple environments (dev, prod).  
Separates state files.

---

## 23. What is lifecycle block?
Controls resource behavior (create_before_destroy, prevent_destroy).  
Used for safe updates.

---

## 24. What is provisioner in Terraform?
Executes scripts on resources after creation.  
Used for configuration tasks.

---

## 25. Explain your Terraform workflow (Interview Answer)
"I write configuration files, run init, validate, and plan.  
Then I apply changes and use remote state for team collaboration."

---


---

# 🎯 Scenario-Based Terraform Questions

## 1. You changed code but resource not updating
Run:
terraform plan  
terraform apply  

Ensures changes are applied to infrastructure.

---

## 2. Someone manually changed infrastructure (drift)
Run:
terraform plan  

Shows difference → then apply to fix.

---

## 3. You want to manage existing resource in Terraform
terraform import <resource> <id>  

Brings existing infra into Terraform state.

---

## 4. State file is locked
Wait or check lock holder.  
If needed:
terraform force-unlock <lock-id>  

Used carefully to avoid corruption.

---

## 5. You renamed a resource block
terraform state mv old new  

Avoids recreation of resource.

---

## 6. You want separate environments (dev/prod)
terraform workspace new dev  

Creates isolated environments.

---

## 7. Apply failed in middle
Fix error → run:
terraform apply  

Terraform resumes safely.

---

## 8. Wrong resource created
terraform destroy  

Removes unwanted infrastructure.

---

## 9. You want to preview before deploy
terraform plan  

Always verify before applying.

---

## 10. Multiple team members working
Use remote backend (S3 + locking).  
Prevents conflicts.

---

## 🧠 Interview Tip
Explain problem → command → reason clearly.  
Focus on state, drift, and safety.

---

# 📊 Terraform Workflow Diagram
        ┌──────────────────────┐
        │   Write .tf Files    │
        │ (Resources, Vars)    │
        └─────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │  terraform init      │
        │ (Setup providers)    │
        └─────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │ terraform validate   │
        │ (Check syntax)       │
        └─────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │ terraform plan       │
        │ (Preview changes)    │
        └─────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │ terraform apply      │
        │ (Create resources)   │
        └─────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │ Terraform State File │
        │ (Tracks resources)   │
        └─────────┬────────────┘
                  │
        ┌─────────▼────────────┐
        │ Cloud Provider (AWS) │
        │ EC2 / S3 / VPC       │
        └──────────────────────┘



🔄 Workflow Explanation

Write code → init → validate → plan → apply → state updated.
Terraform tracks everything in state and manages infrastructure lifecycle.


🧠 Interview Explanation

"Terraform workflow starts with writing code, initializing providers, validating syntax, planning changes, and applying them. State file tracks resources, ensuring consistent infrastructure management."

🚀 Key Benefits
Automation of infrastructure
Consistent deployments
Easy rollback and updates
Team collaboration with remote state


# 🧠 Final Interview Answer

"Terraform is an IaC tool used to automate infrastructure.  
I follow workflow: init, validate, plan, apply.  
I use remote state for collaboration and handle drift using plan and apply."

---

# 🚀 Pro Tips

- Always run plan before apply  
- Use remote backend with locking  
- Avoid manual infra changes  
- Use modules for reuse  
- Keep state secure  


# Terraform Quick Notes

> Simple reference notes for future use.

---

# Terraform Workspaces

Terraform workspaces allow you to manage multiple environments (e.g., dev, test, prod) using the same Terraform configuration.

## List Existing Workspaces

```bash
terraform workspace list
```

Displays all available workspaces.

---

## Create a New Workspace

```bash
terraform workspace new <workspace-name>
```

Example:

```bash
terraform workspace new dev
```

Creates and switches to the new workspace.

---

## Switch Workspace

```bash
terraform workspace select <workspace-name>
```

Example:

```bash
terraform workspace select prod
```

Switches Terraform to the specified workspace.

---

## Delete Workspace

```bash
terraform workspace delete <workspace-name>
```

Example:

```bash
terraform workspace delete test
```

Deletes the workspace.

> Note: You cannot delete the currently selected workspace.

---

# Using Variable Files (.tfvars)

Variable files help provide environment-specific values.

Example structure:

```text
dev.tfvars
prod.tfvars
```

## Terraform Plan

```bash
terraform plan --var-file="dev.tfvars"
```

Uses values from `dev.tfvars` while generating the execution plan.

---

## Terraform Apply

```bash
terraform apply --var-file="dev.tfvars"
```

Creates/updates resources using values from the variable file.

---

## Terraform Destroy

```bash
terraform destroy --var-file="dev.tfvars"
```

Destroys resources using values from the variable file.

---

# Terraform Debug Logging

Used for troubleshooting Terraform issues.

## Enable Logging

```powershell
$env:TF_LOG="TRACE"
```

TRACE provides detailed logs.

Other levels:

- TRACE
- DEBUG
- INFO
- WARN
- ERROR

---

## Disable Logging

```powershell
$env:TF_LOG=""
```

---

## Save Logs to File

```powershell
$env:TF_LOG_PATH="terraform.log"
```

Terraform logs will be written to:

```text
terraform.log
```

---

## Disable Log File

```powershell
$env:TF_LOG_PATH=""
```

---

# Terraform Data Types

## String

Stores text values.

```hcl
name = "terraform"
```

---

## List

- Ordered collection
- Supports indexing
- Allows duplicate values

```hcl
users = ["john", "alice", "john"]
```

Access element:

```hcl
users[0]
```

Output:

```text
john
```

---

## Set

- Unordered collection
- Does not allow duplicate values
- Cannot access by index

```hcl
users = toset(["john", "alice", "john"])
```

Output:

```text
john
alice
```

(Duplicate removed)

---

## Map

- Key-value pairs
- Unordered collection

```hcl
user = {
  name = "john"
  age  = 25
}
```

Access value:

```hcl
user["name"]
```

Output:

```text
john
```

---

# Count

Used to create multiple identical resources.

```hcl
resource "aws_instance" "server" {
  count = 3
}
```

Creates:

```text
server[0]
server[1]
server[2]
```

---

# count.index

Provides the current index value inside a resource using `count`.

```hcl
resource "aws_instance" "server" {
  count = 3

  tags = {
    Name = "server-${count.index}"
  }
}
```

Output:

```text
server-0
server-1
server-2
```

---

# Length Function

Returns the number of elements.

```hcl
length(["a", "b", "c"])
```

Output:

```text
3
```

---

# Element Function

Returns a value from a list based on index.

```hcl
element(["dev", "test", "prod"], 1)
```

Output:

```text
test
```

---

# Conditional Expressions

Syntax:

```hcl
condition ? true_value : false_value
```

Example:

```hcl
environment == "prod" ? "large" : "small"
```

Output:

```text
large
```

if environment is prod, otherwise:

```text
small
```

---

# Local Variables

Used to store reusable values within Terraform.

```hcl
locals {
  project_name = "myapp"
}
```

Usage:

```hcl
tags = {
  Name = local.project_name
}
```

Benefits:

- Reusable
- Cleaner code
- Easy maintenance

---

# for_each

Used to create resources for multiple unique values.

```hcl
resource "aws_s3_bucket" "bucket" {
  for_each = toset(["dev", "test", "prod"])

  bucket = "app-${each.key}"
}
```

Creates:

```text
app-dev
app-test
app-prod
```

---

# Dynamic Blocks

Used to create nested blocks dynamically.

Example:

```hcl
dynamic "ingress" {
  for_each = var.ports

  content {
    from_port = ingress.value
    to_port   = ingress.value
    protocol  = "tcp"
  }
}
```

Useful when the number of nested blocks is not fixed.

---

# Join Function

Combines list elements into a single string.

```hcl
join(",", ["dev", "test", "prod"])
```

Output:

```text
dev,test,prod
```

---

# Distinct Function

Removes duplicate values from a list.

```hcl
distinct(["dev", "test", "dev"])
```

Output:

```text
["dev", "test"]
```

---

# Map Function Usage

Create a map:

```hcl
locals {
  instance_types = {
    dev  = "t2.micro"
    prod = "t3.large"
  }
}
```

Access value:

```hcl
local.instance_types["dev"]
```

Output:

```text
t2.micro
```

---

# Terraform Import

Used to bring existing infrastructure under Terraform management.

Syntax:

```bash
terraform import <resource_type>.<resource_name> <resource_id>
```

Example:

```bash
terraform import aws_s3_bucket.mybucket my-existing-bucket
```

Important:

- Imports resource into Terraform state.
- Does not automatically generate Terraform code.
- Resource configuration must still be written manually.

---

# Provisioners

Provisioners execute scripts or commands during resource creation or destruction.

> Use provisioners only when absolutely necessary.

---

## File Provisioner

Copies files from local machine to remote server.

```hcl
provisioner "file" {
  source      = "app.sh"
  destination = "/tmp/app.sh"
}
```

---

## Remote Exec Provisioner

Runs commands on the remote server.

```hcl
provisioner "remote-exec" {
  inline = [
    "sudo yum update -y",
    "sudo systemctl restart nginx"
  ]
}
```

---

## Local Exec Provisioner

Runs commands on the machine where Terraform is executed.

```hcl
provisioner "local-exec" {
  command = "echo Resource Created"
}
```

---

# null_resource

A resource that does not create any infrastructure.

Useful for:

- Running scripts
- Triggering provisioners
- Automation tasks

Example:

```hcl
resource "null_resource" "example" {

  provisioner "local-exec" {
    command = "echo Hello Terraform"
  }
}
```

---

# Terraform Taint

Marks a resource for recreation.

Syntax:

```bash
terraform taint <resource-address>
```

Example:

```bash
terraform taint aws_instance.web
```

During next apply:

```bash
terraform apply
```

Terraform will:

1. Destroy the existing resource.
2. Recreate it.

---

## Remove Taint

```bash
terraform untaint <resource-address>
```

Example:

```bash
terraform untaint aws_instance.web
```

---

# Quick Comparison

| Type | Ordered | Duplicates Allowed | Access By Index |
|--------|---------|-------------------|----------------|
| String | N/A | N/A | N/A |
| List | ✅ Yes | ✅ Yes | ✅ Yes |
| Set | ❌ No | ❌ No | ❌ No |
| Map | ❌ No | Keys must be unique | Access by Key |

---

# Commonly Used Terraform Functions

| Function | Purpose |
|-----------|----------|
| length() | Count elements |
| element() | Get item by index |
| join() | Combine list into string |
| distinct() | Remove duplicates |
| toset() | Convert list to set |
| tomap() | Convert value to map |

---

# Important Commands Cheat Sheet

```bash
terraform workspace list
terraform workspace new dev
terraform workspace select dev
terraform workspace delete dev

terraform plan --var-file="dev.tfvars"
terraform apply --var-file="dev.tfvars"
terraform destroy --var-file="dev.tfvars"

terraform import RESOURCE_NAME RESOURCE_ID

terraform taint RESOURCE_NAME
terraform untaint RESOURCE_NAME
```

---
**Tip:** Prefer `for_each` when working with unique items (maps/sets) and `count` when creating a fixed number of similar resources.