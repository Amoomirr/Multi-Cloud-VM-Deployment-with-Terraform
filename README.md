# 🌍 Multi-Cloud VM Deployment with Terraform (AWS & GCP)

---

## 📌 Project Overview

This project demonstrates **automated provisioning of virtual machines** in both **AWS** and **GCP** using **Terraform**.

It highlights **multi-cloud infrastructure management** by deploying multiple **EC2 instances** in AWS and **Compute Engine VMs** in GCP with dynamic scaling using the `count` parameter.

The project emphasizes:

* ✅ Infrastructure as Code (IaC)
* ✅ Provider configuration (AWS & GCP)
* ✅ Reusable variables
* ✅ Clean resource definitions
* ✅ Multi-cloud automation

This project is an excellent demonstration of **cloud automation, IaC skills, and Terraform-based multi-cloud deployment**.

**Key Skills:** AWS, GCP, Terraform (IaC), Visual Studio Code, Linux (WSL)

---

## 🚀 Project Steps

### Step 1: Install Terraform

Terraform was installed on **WSL (Linux)** to enable infrastructure provisioning.
👉 [Terraform Installation Guide](https://developer.hashicorp.com/terraform/install)

Check installation:

```bash
terraform --version
```

---

### Step 2: Configure Providers (AWS & GCP)

Two cloud providers were set up:

* **AWS** provider for EC2 instances
* **GCP** provider for Compute Engine

```hcl
# Provider for AWS
provider "aws" {
  region = var.aws_region
}

# Provider for GCP
provider "google" {
  project = var.gcp_project
  region  = var.gcp_region
}
```

---

### Step 3: Define Resources (VMs)

#### AWS EC2 Instances

```hcl
resource "aws_instance" "aws_vm" {
  ami           = var.aws_ami
  instance_type = var.aws_instance_type
  count         = var.aws_instance_count
}
```

#### GCP Compute Engine VMs

```hcl
resource "google_compute_instance" "gcp_vm" {
  name         = "gcp-vm-${count.index}"
  machine_type = var.gcp_machine_type
  zone         = var.gcp_zone
  count        = var.gcp_instance_count

  boot_disk {
    initialize_params {
      image = var.gcp_image
    }
  }

  network_interface {
    network = "default"
    access_config {}
  }
}
```

---

### Step 4: Outputs

Define outputs to display VM details after `terraform apply`.

```hcl
output "aws_instance_ips" {
  value = aws_instance.aws_vm[*].public_ip
}

output "gcp_instance_ips" {
  value = google_compute_instance.gcp_vm[*].network_interface[0].access_config[0].nat_ip
}
```

This makes it easy to view **public IPs** of created VMs.

---

### Step 5: Variables

All configurable values are stored in `variables.tf`.

```hcl
variable "aws_region" { default = "us-east-1" }
variable "aws_instance_type" { default = "t2.micro" }
variable "aws_instance_count" { default = 2 }
variable "aws_ami" { default = "ami-0c02fb55956c7d316" }

variable "gcp_project" {}
variable "gcp_region" { default = "us-central1" }
variable "gcp_zone" { default = "us-central1-a" }
variable "gcp_machine_type" { default = "e2-medium" }
variable "gcp_instance_count" { default = 2 }
variable "gcp_image" { default = "debian-cloud/debian-11" }
```

---

### Step 6: Verified through Cloud Console

Once applied, resources were verified:

* ✅ AWS Console → EC2 Instances section
* ✅ GCP Console → Compute Engine section

---

## 📊 Architecture Diagram

Below diagram shows how **Terraform provisions VMs** across both **AWS** and **GCP**:

![Terraform Multi-Cloud Architecture](diagram.png)
*(Diagram: Terraform → AWS (EC2) + GCP (Compute Engine))*

---

## 📌 Commands Used

Initialize Terraform:

```bash
terraform init
```

Plan the deployment:

```bash
terraform plan
```

Apply changes:

```bash
terraform apply -auto-approve
```

Destroy resources:

```bash
terraform destroy -auto-approve
```

---

## ✅ Conclusion

This project successfully demonstrated **multi-cloud VM provisioning using Terraform**.

* Terraform managed **AWS EC2** and **GCP Compute Engine VMs** in a unified way.
* Infrastructure was reusable, scalable, and consistent across clouds.
* Verified deployment through **AWS & GCP Consoles**.

This proves the **power of Terraform** in managing **hybrid and multi-cloud environments** with ease, scalability, and automation.

---

📂 **Repository Structure**

```
├── variables.tf
├── provider.tf
├── main.tf
├── outputs.tf
└── README.md
```

<img width="1382" height="700" alt="terraforminit" src="https://github.com/user-attachments/assets/98ad195d-d5b2-4fb3-bd72-affb0383872a" />
<img width="1408" height="210" alt="terraformplan" src="https://github.com/user-attachments/assets/681f3be9-16f3-414e-98ec-4b6709fe4c72" />
<img width="1651" height="882" alt="terraform-apply1" src="https://github.com/user-attachments/assets/7cc039b8-f27e-42fa-b1e5-a6d76127e85d" />
<img width="935" height="687" alt="variablestf" src="https://github.com/user-attachments/assets/db26ce4b-5068-427d-884c-8b170e3f463b" />
<img width="996" height="367" alt="Providertf" src="https://github.com/user-attachments/assets/45f91a88-8513-4a80-b75b-98ed467a636b" />
<img width="990" height="702" alt="maintf" src="https://github.com/user-attachments/assets/a0b6a373-18f5-4e81-a3ce-b5aa1f5b8ba9" />
<img width="1132" height="557" alt="outputtf" src="https://github.com/user-attachments/assets/4e1098d1-5c4b-4e4c-9957-23d8dc566401" />
<img width="1287" height="683" alt="outputs" src="https://github.com/user-attachments/assets/9767d64d-7a9f-4003-945c-bfe9ab510ef5"/>
<img width="1907" height="616" alt="GCP-Dashboard-After" src="https://github.com/user-attachments/assets/a6ecbc6d-ea83-4439-8e9b-a6a1fc4618ed" />
<img width="1912" height="500" alt="AWS-Dashboard-after" src="https://github.com/user-attachments/assets/f93f3e43-e873-442d-aaee-33781865dfb0" />
<img width="1737" height="1008" alt="terraform-destroy" src="https://github.com/user-attachments/assets/2435678d-a9a3-48a7-a0bc-ede37ec648a4" />








Do you want me to also create a **ready-to-use Terraform project folder (all .tf files + diagram.png)** so you can just push it to GitHub?
