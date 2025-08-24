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

📂 **Repository Structure**

```
├── variables.tf
├── provider.tf
├── main.tf
├── outputs.tf
└── README.md


**Key Skills:** AWS, GCP, Terraform (IaC), Visual Studio Code, Linux (WSL)

---

## 🚀 Project Steps

### Step 1: Install Terraform

Terraform was installed on **WSL (Linux)** to enable infrastructure provisioning.
👉 [Terraform Installation Guide](https://developer.hashicorp.com/terraform/install)

Check installation:

terraform --version
```

---

### Step 2: Variables

All configurable values are stored in `variables.tf`.

<img width="935" height="687" alt="variablestf" src="https://github.com/user-attachments/assets/db26ce4b-5068-427d-884c-8b170e3f463b" />

---


### Step 3: Configure Providers (AWS & GCP)

Two cloud providers were set up:

* **AWS** provider for EC2 instances
* **GCP** provider for Compute Engine

<img width="996" height="367" alt="Providertf" src="https://github.com/user-attachments/assets/45f91a88-8513-4a80-b75b-98ed467a636b" />

---

### Step 4: Define Resources (VMs)


<img width="990" height="702" alt="maintf" src="https://github.com/user-attachments/assets/a0b6a373-18f5-4e81-a3ce-b5aa1f5b8ba9" />


### Step 5: Outputs

Define outputs to display VM details after `terraform apply`.

<img width="1132" height="557" alt="outputtf" src="https://github.com/user-attachments/assets/4e1098d1-5c4b-4e4c-9957-23d8dc566401"/>

This makes it easy to view **public IPs** of created VMs.

<img width="1287" height="683" alt="outputs" src="https://github.com/user-attachments/assets/9767d64d-7a9f-4003-945c-bfe9ab510ef5"/>


---


### Step 6: Verified through Cloud Console

Once applied, resources were verified:

* ✅ AWS Console → EC2 Instances section

<img width="1912" height="500" alt="AWS-Dashboard-after" src="https://github.com/user-attachments/assets/f93f3e43-e873-442d-aaee-33781865dfb0" />

* ✅ GCP Console → Compute Engine section

<img width="1907" height="616" alt="GCP-Dashboard-After" src="https://github.com/user-attachments/assets/a6ecbc6d-ea83-4439-8e9b-a6a1fc4618ed" />

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


Step 8: Destroying All Resources

Terraform ensures that all resources created by IaC are safely removed. This one-command clean-up prevents unnecessary costs and keeps your cloud environment tidy.  

<img width="1737" height="1008" alt="terraform-destroy" src="https://github.com/user-attachments/assets/2435678d-a9a3-48a7-a0bc-ede37ec648a4" />




