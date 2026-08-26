# 🌐 Gora Landing Zone — Azure Infrastructure with Terraform ☁️

[![Terraform](https://img.shields.io/badge/Terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white)](https://www.terraform.io/)
[![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com/)
[![DevOps](https://img.shields.io/badge/DevOps-Batch%2018-blueviolet?style=for-the-badge)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

> 🚀 **Gora Landing Zone** is an automated Infrastructure as Code (IaC) project designed to provision baseline Azure infrastructure and Resource Groups using **HashiCorp Terraform**.

---

## 📑 Table of Contents

- [✨ Overview](#-overview)
- [🏗️ Repository Architecture](#️-repository-architecture)
- [📦 Resources Managed](#-resources-managed)
- [⚙️ Prerequisites](#️-prerequisites)
- [🚀 Getting Started & Deployment](#-getting-started--deployment)
  - [1. Clone Repository](#1-clone-repository)
  - [2. Azure Authentication](#2-azure-authentication)
  - [3. Initialize Terraform](#3-initialize-terraform)
  - [4. Validate & Plan](#4-validate--plan)
  - [5. Apply Infrastructure](#5-apply-infrastructure)
  - [6. Destroy / Cleanup](#6-destroy--cleanup)
- [🔒 Security & Best Practices](#-security--best-practices)
- [🤝 Contributing](#-contributing)
- [📝 License](#-license)

---

## ✨ Overview

An Azure Landing Zone provides a scalable, secure, and governed environment in Microsoft Azure. This repository houses Terraform definitions for provisioning foundational resource groups across multiple Azure regions (`West US`, `East US`), laying the groundwork for workloads, virtual networks, compute, and data services.

---

## 🏗️ Repository Architecture

```plaintext
gora_landing_zone/
├── 📁 azurerm_rg/          # Resource Group Module / Definitions
│   └── 📄 main.tf          # Azure Resource Group resource blocks
└── 📄 README.md            # Project documentation & usage guide
```

---

## 📦 Resources Managed

The [`azurerm_rg/main.tf`](file:///d:/devops%20_batch%2018/gora_landing_zone/azurerm_rg/main.tf) module configures the following Azure Resource Groups:

| 🏷️ Terraform Resource | 📛 Resource Group Name | 📍 Azure Region | 🎯 Purpose |
| :--- | :--- | :--- | :--- |
| `azurerm_resource_group.sun` | `abhirg` | `West US` | Baseline environment resource group |
| `azurerm_resource_group.sun23` | `neharg` | `East US` | East US workload resource group |
| `azurerm_resource_group.sun100` | `sumanrg` | `East US` | Multi-region deployment baseline |
| `azurerm_resource_group.sun1000` | `shaktiman` | `West US` | Workload / service environment |

---

## ⚙️ Prerequisites

Before executing the Terraform scripts, ensure you have the following installed and configured:

- 🧰 **[Terraform CLI](https://developer.hashicorp.com/terraform/downloads)** (v1.0.0 or higher)
- ☁️ **[Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)** (`az` command line tool)
- 🔑 **Active Azure Subscription** with Contributor or Owner access
- 💻 **Git** installed on your workstation

---

## 🚀 Getting Started & Deployment

Follow these step-by-step instructions to deploy the landing zone infrastructure:

### 1. Clone Repository 📥

```bash
git clone https://github.com/your-username/gora_landing_zone.git
cd gora_landing_zone/azurerm_rg
```

### 2. Azure Authentication 🔐

Login to your Microsoft Azure tenant and set your active subscription:

```bash
# Login interactively
az login

# List subscriptions
az account list --output table

# Select the target subscription ID
az account set --subscription "<YOUR_SUBSCRIPTION_ID>"
```

### 3. Initialize Terraform 🧩

Initialize the working directory to download the Azure provider plugin:

```bash
terraform init
```

### 4. Validate & Plan 🔍

Check the syntax, format the configuration, and generate an execution plan:

```bash
# Format code
terraform fmt

# Validate configuration syntax
terraform validate

# Review proposed changes
terraform plan
```

### 5. Apply Infrastructure 🚢

Provision the defined resource groups in your Azure environment:

```bash
terraform apply
```
> 💡 *Type `yes` when prompted to confirm the deployment.*

### 6. Destroy / Cleanup 🧹

When you need to tear down the provisioned resources to avoid unwanted cloud costs:

```bash
terraform destroy
```

---

## 🔒 Security & Best Practices

- 🛡️ **Remote State Management:** Use an Azure Blob Storage container with state locking (via Azure Storage lease) for production setups.
- 🏷️ **Tagging Strategy:** Ensure all resources are tagged with `Environment`, `Owner`, `Project`, and `CostCenter`.
- 🔑 **Least Privilege Access:** Use Service Principals / Managed Identities with restricted RBAC permissions for automated CI/CD pipelines.
- 🚫 **Secrets Prevention:** Never commit credentials or Azure secrets into Git repository history.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. 🍴 Fork the repository
2. 🌿 Create a feature branch (`git checkout -b feature/amazing-feature`)
3. 💾 Commit your changes (`git commit -m 'feat: add new resource group'`)
4. 📤 Push to the branch (`git push origin feature/amazing-feature`)
5. 🔀 Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License — feel free to use and customize it for your cloud deployments! 🎉