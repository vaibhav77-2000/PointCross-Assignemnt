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
|   └── Dockerfile
|   └── index.html
│
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
# Step 1: Navigate to the terraform directory:
cd terraform

# Step 2: Initialize Terraform
terraform init

# Step 3: Validate the code
terraform validate

# Step 4: Review the code
terraform plan -var-file="terraform.tfvars"

# Step 5: Apply the changes 
terraform apply -var-file="terraform.tfvars"
```

## 🔧 Build and Push Docker Image to Amazon ECR
```
# Step 1: Navigate to the terraform directory:
cd Application-Deployment

# Step 2: Setup AWS Profile
aws configure  

# Step 3:  ECR Login
aws ecr get-login-password --region ap-south-1| docker login --username AWS --password-stdin XXXXXXXXXX.dkr.ecr.ap-south-1.amazonaws.com

# Step 4: Build Docker Image
docker build -t nginx-deployment:latest .

# Step 5: Tag Docker Image for ECR
docker tag nginx-deployment:latest XXXXXXX.dkr.ecr.ap-south-1.amazonaws.com/nginx-deployment:latest

# Step 6: Push Image
docker push XXXXXX.dkr.ecr.ap-south-1.amazonaws.com/nginx-deployment:latest
```
## 🔧 Ansible Deployment Steps

To run the Ansible playbooks that apply Kubernetes resources, follow the steps below:
Before using Ansible, you must configure your AWS CLI with the correct credentials:

```
# Step 1: Navigate to the terraform directory:
cd ansible

# Step 2: Setup AWS Profile
aws configure  

# Step 3: Run the playbook:
ansible-playbook playbook.yaml

```

## 🔧 Testing Service On Nodeport
```
After successfully deploying your service with a `NodePort` type in Kubernetes, you can access it using the following method:

### ✅ Prerequisites

- Your EC2 instance’s security group allows inbound traffic on the NodePort (e.g., `30080`, `30001`, etc.).
- The application is deployed and the pod is in `Running` state.
- You know the **public IP** of your EC2 node and the assigned **NodePort**.

### 🔍 Find the NodePort

Use this command to check the NodePort:
```bash
kubectl get svc nginx-service -n tenant1
kubectl get svc nginx-service -n tenant2

Access the App in Browser
http://<EC2-PUBLIC-IP>:<NODEPORT>
```


![App Screenshot](./Screenshot%202025-08-07%20182552.png)
![App Screenshot](./Screenshot%202025-08-07%20182712.png)





