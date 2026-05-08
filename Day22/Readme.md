# 🚀 Azure DevOps Service Connection & Azure Resource Setup for Configure Pipelines as Code with YAML

This lab demonstrates how to:

* Create an Azure DevOps Service Connection
* Import the eShopOnWeb sample repository
* Configure Azure resources for deployment
* Prepare Azure App Service for CI/CD pipelines

---

# 📚 Prerequisites

Before starting, ensure you have:

* 🌐 A supported browser like Microsoft Edge
* ☁️ An active Azure subscription
* 🏢 An Azure DevOps organization
* 🔐 Required permissions:

  * **Owner** role in Azure subscription
  * **Global Administrator** role in Microsoft Entra ID

Useful references:

* [Azure Portal](https://portal.azure.com?utm_source=chatgpt.com)
* [Azure DevOps Portal](https://aex.dev.azure.com?utm_source=chatgpt.com)
* [Create Azure DevOps Organization](https://learn.microsoft.com/azure/devops/organizations/accounts/create-organization?utm_source=chatgpt.com)

---

# 🔗 Create Azure DevOps Service Connection

The service connection allows Azure DevOps pipelines to securely access Azure resources.

## Step 1 — Open Azure DevOps

1. Open:

   * [Azure DevOps Portal](https://aex.dev.azure.com?utm_source=chatgpt.com)
2. Sign in using your Azure DevOps credentials.

> If signing in for the first time:
>
> * Create your profile
> * Accept the terms
> * Select **Continue**

---

## Step 2 — Open Project Settings

1. Open the project:

   * `eShopOnWeb-61628259`
2. Select **Project Settings** (bottom-left corner)

---

## Step 3 — Create Service Connection

1. Navigate to:

   * **Pipelines → Service connections**
2. Select:

   * **Create service connection**

---

## Step 4 — Choose Connection Type

1. Select:

   * **Azure Resource Manager**
2. Select:

   * **Next**

---

## Step 5 — Configure Authentication

1. Identity type:

   * **App registration (automatic)**
2. Credential:

   * **Workload Identity federation**
3. Scope level:

   * **Subscription**

---

## Step 6 — Fill Service Connection Details

Use the following configuration:

| Field                   | Value                   |
| ----------------------- | ----------------------- |
| Subscription            | Your Azure Subscription |
| Resource Group          | `az400m03l07-RG`        |
| Service Connection Name | `azure subs`            |

⚠️ Ensure:

* **Grant access permission to all pipelines** → **Unchecked**

> This option is not recommended for production environments.

---

## Step 7 — Save

Select:

* **Save**

> If permission issues occur, retry or configure the connection manually.

---

# 📦 Create and Configure Azure DevOps Project

> In Cloudslice labs, this task may already be completed.

## Steps

1. Open your Azure DevOps organization
2. Select:

   * **New Project**
3. Project name:

   * `eShopOnWeb-61628259`
4. Leave remaining settings as default
5. Select:

   * **Create**

---

# 📥 Import eShopOnWeb Git Repository

## Step 1 — Open Repository Section

1. Open:

   * `eShopOnWeb-61628259`
2. Navigate to:

   * **Repos → Files**

---

## Step 2 — Import Repository

1. Select:

   * **Import a Repository**
2. Select:

   * **Import**
3. Paste repository URL:

```text
https://github.com/MicrosoftLearning/eShopOnWeb.git
```

4. Select:

   * **Import**

---

# 📁 Repository Structure

| Folder          | Purpose                           |
| --------------- | --------------------------------- |
| `.ado`          | Azure DevOps YAML pipelines       |
| `.devcontainer` | Container-based development setup |
| `infra`         | Bicep & ARM IaC templates         |
| `.github`       | GitHub workflow YAML files        |
| `src`           | .NET 8 web application            |

---

# 🌿 Set Default Branch

1. Navigate to:

   * **Repos → Branches**
2. Hover over:

   * `main`
3. Select:

   * **⋯ (ellipsis menu)**
4. Choose:

   * **Set as default branch**

> If already default, continue with the next step.

---

# ☁️ Create Azure Resources

Now you'll create Azure resources required for deployment.

---

# 🖥️ Open Azure Cloud Shell

1. Open:

   * [Azure Portal](https://portal.azure.com?utm_source=chatgpt.com)
2. Sign in
3. Select:

   * **Cloud Shell** icon
4. Choose:

   * **Bash**

> If prompted:
>
> * Select **No storage account required**
> * Choose your subscription
> * Select **Apply**

---

# 🌍 Configure Azure Region

Select a region with available capacity:

```bash
LOCATION='eastus'
RESOURCEGROUPNAME='az400m03l07-RG'
```

Possible regions:

* eastus
* eastus2
* westus
* westus2
* westus3
* westeurope
* canadacentral
* southeastasia
* australiaeast

---

# 🏗️ Create App Service Plan

Run:

```bash
SERVICEPLANNAME='az400m03l07-sp1'

az appservice plan create \
  --resource-group $RESOURCEGROUPNAME \
  --name $SERVICEPLANNAME \
  --sku B3 \
  --location $LOCATION
```

---

## ⚠️ Possible Error Fix

If you receive:

```text
The subscription is not registered to use namespace 'Microsoft.Web'
```

Run:

```bash
az provider register --namespace Microsoft.Web
```

Then retry the previous command.

---

# 🌐 Create Azure Web App

Run:

```bash
WEBAPPNAME='eshoponWebYAML61628259'

az webapp create \
  --resource-group $RESOURCEGROUPNAME \
  --plan $SERVICEPLANNAME \
  --name $WEBAPPNAME
```

---

# 📝 Important

Record the web app name:

```text
eshoponWebYAML61628259
```

You will use this later in Azure DevOps YAML pipelines.

---

# ✅ Lab Summary

In this lab, you successfully:

* Created an Azure DevOps project
* Imported the eShopOnWeb repository
* Created an Azure Resource Manager service connection
* Configured Azure App Service resources
* Prepared infrastructure for CI/CD deployment

---

# 🔥 Next Steps

You can now proceed with:

* Azure DevOps YAML Pipelines
* Continuous Integration (CI)
* Continuous Deployment (CD)
* App Service Deployments
* Infrastructure as Code (IaC)

