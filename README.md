# PointCross-Assignment

This repository contains a complete setup using **Terraform**, **Ansible**, and **Kubernetes manifests** for provisioning infrastructure, applying configurations, and deploying applications.

---

## 🗂️ Project Structure
PointCross-Assignment/
│
├── Application-Deployment/ # Contains Kubernetes YAMLs (manifests)
│ ├── tenant1-deployment.yaml
│ ├── tenant2-deployment.yaml
│ ├── svc-1.yaml, svc-2.yaml
│ ├── namespace-1.yaml, namespace-2.yaml
│ ├── resource-quota-1.yaml, resource-quota-2.yaml
│ └── Dockerfile
│
├── terraform/ # Terraform code for infra provisioning
│ ├── main.tf
│ ├── provider.tf
│ ├── outputs.tf
│ ├── variables.tf
│ └── terraform.tfvars
│
├── ansible/ # Ansible roles and tasks
│ ├── playbook.yaml
│ ├── ansible.cfg
│ └── tasks/
│ ├── apply_deployments.yml
│ ├── apply_services.yml
│ ├── apply_quotas.yml
│ └── apply_namespaces.yml

