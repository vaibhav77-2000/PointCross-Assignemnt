# PointCross-Assignment

This repository contains a complete setup using **Terraform**, **Ansible**, and **Kubernetes manifests** for provisioning infrastructure, applying configurations, and deploying applications.

---

## 🗂️ Project Structure
## 📁 Project Structure

```
PointCross-Assignment/
├── Application-Deployment/       # Contains Kubernetes YAMLs (manifests)
│   ├── tenant1-deployment.yaml
│   ├── tenant2-deployment.yaml
│   ├── svc-1.yaml
│   ├── svc-2.yaml
│   ├── namespace-1.yaml
│   ├── namespace-2.yaml
│   ├── resource-quota-1.yaml
│   └── resource-quota-2.yaml
│
├── Dockerfile
│
├── terraform/                    # Terraform code for infra provisioning
│   ├── main.tf
│   ├── provider.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── terraform.tfvars
│
├── ansible/                      # Ansible roles and tasks
│   ├── playbook.yaml
│   ├── ansible.cfg
│   └── tasks/
│       ├── apply_deployments.yml
│       ├── apply_services.yml
│       ├── apply_quotas.yml
│       └── apply_namespaces.yml
```
Terraform Setup

Navigate to the terraform directory:
```
# Step 1: Initialize Terraform
terraform init

# Step 2: Validate the code
terraform validate

# Step 3: Review the code
terraform plan -var-file="terraform.tfvars"

# Step 4: Apply the changes 
terraform apply -var-file="terraform.tfvars"
```

