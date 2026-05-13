**Azure Key Vault** is a cloud service from Microsoft (part of Microsoft Azure) that lets you securely store and manage sensitive information used by your applications.

---

## 🔐 What it does

Azure Key Vault helps you protect:

* **Secrets** → passwords, API keys, connection strings
* **Keys** → encryption keys used for cryptography
* **Certificates** → SSL/TLS certificates

Instead of hardcoding sensitive values in your app, you store them in Key Vault and access them securely at runtime.

---

## ⚙️ Core features

### 1. Secure storage

* Uses hardware security modules (HSMs) for high protection (optional)
* Data is encrypted at rest and in transit

### 2. Access control

* Uses Azure Active Directory (AAD) for authentication
* Supports fine-grained permissions (who can read/update/delete secrets)

### 3. Secret management

* Versioning of secrets
* Automatic rotation (for keys/certificates)
* Centralized management

### 4. Integration

* Works seamlessly with:

  * Azure Virtual Machines
  * Azure App Service
  * Azure Kubernetes Service (AKS)
  * DevOps pipelines

---

## 🧠 Why use it?

Without Key Vault:

```text
Password = "MySuperSecret123"
```

With Key Vault:

```text
Password = get_secret_from_key_vault("db-password")
```

This improves:

* Security (no exposed secrets)
* Compliance
* Maintainability

---

## 🏗️ Basic architecture

Typical flow:

1. App authenticates using Azure AD
2. App requests a secret from Key Vault
3. Key Vault verifies permissions
4. Secret is returned securely

---

## 🚀 Common use cases

* Storing database connection strings
* Managing API keys for external services
* Encrypting application data
* Managing SSL certificates for web apps

---

## ⚠️ Best practices

* Use **Managed Identity** instead of storing credentials
* Restrict access using least privilege
* Enable **logging & monitoring**
* Rotate secrets regularly
* Avoid downloading secrets unless necessary

---

# 🚀 Integrate Azure Key Vault with Azure DevOps

Securely managing secrets is one of the most important practices in DevOps.
In this lab, you’ll integrate **Azure Key Vault** with **Azure DevOps Pipelines** to securely store and consume secrets during CI/CD deployments.

---

# 📚 Lab Overview

In this lab, you will:

* Create an Azure Key Vault
* Store Azure Container Registry (ACR) credentials as secrets
* Grant Azure DevOps access to Key Vault
* Create a Variable Group linked to Azure Key Vault
* Retrieve secrets securely inside Azure Pipelines
* Deploy a containerized application to Azure Container Instance (ACI)

---

# 🎯 Objectives

After completing this lab, you will be able to:

✅ Create and configure Azure Key Vault
✅ Store secrets securely in Key Vault
✅ Connect Azure DevOps Variable Groups with Key Vault
✅ Retrieve secrets inside YAML pipelines
✅ Deploy container images securely using secrets

---

# 🛠️ Prerequisites

Before starting, ensure you have:

* An Azure subscription
* An Azure DevOps organization/project
* Azure service connection configured
* eShopOnWeb repository imported into Azure DevOps

Repository used:

[eShopOnWeb GitHub Repository](https://github.com/MicrosoftLearning/eShopOnWeb.git?utm_source=chatgpt.com)

---

# 🧩 Exercise 1 — Setup CI Pipeline

## 📌 Create CI Pipeline

Navigate to:

`Azure DevOps → Pipelines → New Pipeline`

Choose:

* Azure Repos Git
* Existing Azure Pipelines YAML file

Select YAML file:

```yaml
/.ado/eshoponweb-ci-dockercompose.yml
```

Update:

* Resource Group Name
* Azure Subscription ID

Pipeline tasks include:

* Deploy Azure Container Registry (ACR)
* Build Docker images
* Push images to ACR

---

# 📦 Verify Azure Container Registry

After pipeline execution:

Navigate to:

`Azure Portal → Resource Group → Azure Container Registry`

Verify container images:

* eshoppublicapi
* eshopwebmvc

Enable:

`Access Keys → Admin User`

Copy the ACR password.

---

# 🔐 Exercise 2 — Create Azure Key Vault

## 📌 Create Key Vault

Navigate to:

`Azure Portal → Key Vaults → Create`

Provide:

| Setting          | Value               |
| ---------------- | ------------------- |
| Resource Group   | AZ400-EWebShop-NAME |
| Vault Name       | ewebshop-kv-NAME    |
| Pricing Tier     | Standard            |
| Purge Protection | Disabled            |

---

# 🔑 Configure Access Policies

Grant Azure DevOps Service Connection access:

Secret permissions:

* Get
* List

Select the Azure DevOps service principal connected to your service connection.

---

# 🧪 Add Secret to Key Vault

Navigate to:

`Key Vault → Secrets → Generate/Import`

Create secret:

| Setting | Value        |
| ------- | ------------ |
| Name    | acr-secret   |
| Value   | ACR Password |

---

# 🔗 Exercise 3 — Create Variable Group

Navigate to:

`Azure DevOps → Pipelines → Library`

Create Variable Group:

| Setting                           | Value       |
| --------------------------------- | ----------- |
| Variable Group Name               | eshopweb-vg |
| Link secrets from Azure Key Vault | Enabled     |

Select:

* Azure Subscription
* Key Vault
* Secret: `acr-secret`

Save the variable group.

---

# 🚀 Exercise 4 — Setup CD Pipeline

## 📌 Create CD Pipeline

Use YAML file:

```yaml
/.ado/eshoponweb-cd-aci.yml
```

Update:

* Azure Subscription ID
* Resource Group Name
* ACR Login Server
* ACR Username
* Container Instance Name

---

# 🔄 CD Pipeline Workflow

The deployment pipeline will:

1. Trigger after CI pipeline completion
2. Retrieve secrets from Azure Key Vault
3. Deploy Azure Container Instance (ACI)
4. Pull container image securely from ACR

---

# 🏗️ Azure Key Vault Integration in YAML

Example Variable Group reference:

```yaml
variables:
- group: eshopweb-vg
```

Using secret inside tasks:

```yaml
$(acr-secret)
```

---

# ✅ Verify Deployment

Navigate to:

`Azure Portal → Resource Group`

Verify:

* Azure Container Instance (ACI) created successfully
* Application container running properly

---

# 🔒 Benefits of Azure Key Vault Integration

✅ Centralized secret management
✅ No hardcoded passwords in YAML pipelines
✅ Improved security and compliance
✅ Fine-grained access control
✅ Secure CI/CD deployments

---

# 📝 Review

In this lab, you:

* Created Azure Key Vault
* Stored ACR credentials securely
* Granted Azure DevOps access
* Linked Variable Groups with Key Vault
* Retrieved secrets inside pipelines
* Deployed containers securely to Azure Container Instance

---

# ☁️ Technologies Used

* Microsoft
* Microsoft
* Microsoft
* Microsoft
* Docker
* YAML Pipelines


