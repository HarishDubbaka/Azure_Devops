# Day 19 – Setting Up GitHub Repository and Azure Access for CI/CD Deployment

## 📌 Overview

In this lab, I configured secure authentication between **GitHub Actions** and **Microsoft Azure** using an **Azure Service Principal**.

This setup is essential for enabling automated CI/CD deployment from GitHub to Azure App Service.

### What I accomplished

- Created an Azure Service Principal
- Stored credentials securely as GitHub Secrets
- Configured the GitHub workflow
- Deployed the application to Azure App Service
- Reviewed workflow execution
- Configured manual deployment approval (optional)
- Cleaned up Azure resources

---

# Why These Steps Are Mandatory in Azure DevOps / Cloud Deployment

Before deploying any project to the cloud, Azure DevOps engineers must complete a few critical setup tasks.

## 1. Create a Service Principal (SP)

A **Service Principal** is a secure identity used for automation.

### Why it is needed

Azure DevOps or GitHub Actions cannot directly access your Azure subscription.

A Service Principal is required to:

- Authenticate deployment pipelines with Azure
- Deploy resources automatically
- Follow secure access practices
- Avoid using personal credentials

---

## 2. Create a Service Connection

A **Service Connection** connects Azure DevOps or GitHub Actions to Azure using the Service Principal credentials.

### Why it is needed

It allows the pipeline to:

- Create cloud resources
- Deploy applications
- Manage infrastructure
- Execute Azure CLI / ARM / Bicep / Terraform deployments

Without it, deployment automation is not possible.

---

## 3. Import the Repository

The project source code must be available in GitHub or Azure DevOps Repos.

### Why it is needed

The pipeline requires access to:

- Application source code
- Infrastructure files
- YAML workflow definitions
- Deployment configurations

**Example:** Importing the `eShopOnWeb` repository.

---

## 4. Store Secrets Securely

Sensitive information must never be hardcoded.

### Examples of secrets

- Subscription ID
- Client ID
- Client Secret
- Tenant ID
- Database credentials
- API keys

### Secure storage options

- GitHub Secrets
- Azure DevOps Library
- Variable Groups
- Azure Key Vault

---

# Step-by-Step Setup

# Create Azure Service Principal and Save as GitHub Secret

The Azure Service Principal allows GitHub Actions to securely authenticate with Azure.

> **Alternative:** OpenID Connect (OIDC) can be used for secretless authentication.

---

## Step 1: Open Azure Portal

Navigate to:

```text
https://portal.azure.com
```

---

## Step 2: Open Resource Groups

In Azure Portal:

- Search for **Resource Groups**
- Select your resource group

Example:

```text
rg-eshoponweb
```

---

## Step 3: Open Cloud Shell

Click the **Cloud Shell** icon at the top.

If prompted:

- Select **No storage account required**
- Choose your subscription
- Click **Apply**

---

## Step 4: Create the Service Principal

Ensure Cloud Shell is running in **Bash mode**.

Run:

```bash
az ad sp create-for-rbac --name GH-Action-eshoponweb61512893 --role contributor --scopes /subscriptions/SUBSCRIPTION-ID/resourceGroups/RESOURCE-GROUP --sdk-auth
```

Replace:

- `SUBSCRIPTION-ID`
- `RESOURCE-GROUP`

with your actual values.

### Important

Paste the command as a **single line**.

---

## Why This Is Important

This command creates a Service Principal with **Contributor access** limited to your resource group.

This follows the **Principle of Least Privilege**, improving security.

---

## Step 5: Copy the JSON Output

Example output:

```json
{
  "clientId": "<GUID>",
  "clientSecret": "<GUID>",
  "subscriptionId": "<GUID>",
  "tenantId": "<GUID>"
}
```

Store it securely.

---

## Step 6: Register Azure App Service Provider

Run:

```bash
az provider register --namespace Microsoft.Web
```

This enables Azure App Service resource deployment.

---

## Step 7: Add GitHub Secret

Go to your GitHub repository:

```text
Settings → Secrets and variables → Actions
```

Click:

**New repository secret**

Add:

| Name | Secret |
|------|--------|
| AZURE_CREDENTIALS | Paste JSON output |

Click:

**Add Secret**

GitHub Actions can now authenticate with Azure.

---

# Modify and Execute GitHub Workflow

## Step 1: Open Workflow File

Navigate to:

```text
eShopOnWeb/.github/workflows/eshoponweb-cicd.yml
```

---

## Step 2: Enable Workflow Trigger

Uncomment:

```yaml
on:
  push:
    branches:
      - main
  workflow_dispatch:
```

This enables:

- Automatic execution on push
- Manual execution

---

## Step 3: Update Environment Variables

### Resource Group

Replace:

```yaml
RESOURCE-GROUP: rg-eshoponweb-NAME
```

With:

```yaml
RESOURCE-GROUP: rg-eshoponweb
```

---

### Location

```yaml
LOCATION: westeurope
```

---

### Subscription ID

Replace:

```yaml
SUBSCRIPTION-ID: YOUR-SUBS-ID
```

With your Azure Subscription ID.

---

### Web App Name

Replace:

```yaml
WEBAPP-NAME: eshoponweb-webappNAME
```

With:

```yaml
WEBAPP-NAME: eshoponweb-webapp61512893
```

This ensures global uniqueness.

---

## Step 4: Commit Changes

Click:

**Commit changes**

The workflow starts automatically.

---

# Review Workflow Execution

## Step 1: Open GitHub Actions

Navigate to:

```text
Repository → Actions
```

Select:

**eShopOnWeb Build and Test**

---

## Step 2: Monitor Workflow

Observe:

- Build Job
- Test Job
- Deploy Job

Check logs for detailed execution steps.

---

## Step 3: Verify Deployment

Navigate to:

```text
Azure Portal → Resource Groups → rg-eshoponweb
```

You should see:

- Azure App Service Plan
- Azure Web App

To test:

- Open the App Service
- Click **Browse**

The deployed website should load successfully.

---

# Optional: Add Manual Deployment Approval

GitHub Environments support deployment approvals.

---

## Step 1: Locate Environment

In workflow file:

```yaml
environment: Development
```

---

## Step 2: Create Environment

Navigate to:

```text
Repository → Settings → Environments
```

Click:

**New Environment**

Name it:

```text
Development
```

---

## Step 3: Enable Reviewers

Enable:

- **Required Reviewers**

Add your GitHub account.

Save settings.

---

## Step 4: Run Workflow

Navigate to:

```text
Repository → Actions
```

Click:

```text
Run workflow
```

---

## Step 5: Approve Deployment

When paused:

- Select **Review deployments**
- Choose **Development**
- Click **Approve and deploy**

Deployment resumes.

---

# Clean Up Resources

Cleaning resources prevents unnecessary Azure charges.

---

## Delete Resource Group

Navigate to:

```text
Azure Portal → Resource Groups
```

Select:

```text
rg-eshoponweb
```

Click:

**Delete Resource Group**

Confirm deletion.

---

## Optional: Delete GitHub Repository

Navigate to:

```text
Repository → Settings → Danger Zone
```

Select:

**Delete this repository**

### Warning

This permanently deletes:

- Source code
- Pull requests
- Issues
- Workflow history

---

# Best Practices

Always follow these cloud security practices:

✅ Use Service Principals  
✅ Restrict permissions to required scope  
✅ Store credentials securely  
✅ Never hardcode secrets  
✅ Use deployment approvals for production  
✅ Clean up unused resources

---

# Final Summary

In this lab, I successfully:

- Created an Azure Service Principal
- Connected GitHub Actions to Azure
- Configured deployment workflow
- Deployed application to Azure App Service
- Verified deployment
- Added approval gates
- Cleaned up cloud resources

This project demonstrates a real-world **GitHub Actions CI/CD deployment pipeline to Azure** and is a fundamental skill for Azure DevOps Engineers.
