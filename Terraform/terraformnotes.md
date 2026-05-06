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
