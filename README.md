# PointCross-Assignment

This repository contains a complete setup using **Terraform**, **Ansible**, and **Kubernetes manifests** for provisioning infrastructure, applying configurations, and deploying applications.

---
## 🗂️ Project Structure

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
## 🔧 Terraform Deployment Steps

Navigate to the terraform directory:
```
cd terraform

# Step 1: Initialize Terraform
terraform init

# Step 2: Validate the code
terraform validate

# Step 3: Review the code
terraform plan -var-file="terraform.tfvars"

# Step 4: Apply the changes 
terraform apply -var-file="terraform.tfvars"
```

## 🔧 Ansible Deployment Steps

To run the Ansible playbooks that apply Kubernetes resources, follow the steps below:

---

### 🔐 Step 1: Set Up AWS Credentials

Before using Ansible, you must configure your AWS CLI with the correct credentials:

```bash
aws configure  //Enter the credentails

cd ansible

Run the playbook:

ansible-playbook playbook.yaml
rm apply -var-file="terraform.tfvars"
```





