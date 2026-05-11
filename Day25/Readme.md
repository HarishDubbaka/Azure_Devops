# 🚀 Azure DevOps Service Connection & Release Gates Lab

## 📌 Overview

This lab demonstrates how to:

- Create a **Service Connection** to access Azure resources
- Configure **CI/CD pipelines**
- Deploy applications to **Azure Web Apps**
- Configure **Application Insights**
- Create **Release Gates**
- Implement **Pre-deployment Approvals**
- Control deployments using **Azure DevOps Release Pipelines**

---

# 🔹 Part 1: Create a Service Connection

A Service Connection allows Azure DevOps pipelines to securely access Azure resources.

## Step 1: Open Azure DevOps Portal

Navigate to:

https://aex.dev.azure.com

Sign in using your Azure DevOps credentials.

---

## Step 2: Open Project Settings

- Open **eShopOnWeb** project
- Select **Project Settings** (bottom-left)

---

## Step 3: Create Service Connection

Navigate:

**Pipelines → Service connections**

Select:

**Create service connection**

---

## Step 4: Select Connection Type

Choose:

**Azure Resource Manager**

Click **Next**

---

## Step 5: Configure Authentication

Select:

- **Identity Type:** App registration (automatic)
- **Credential:** Workload Identity Federation
- **Scope Level:** Subscription

---

## Step 6: Fill Required Details

| Setting | Value |
|--------|------|
| Subscription | Your Azure Subscription |
| Resource Group | `az400m03l08-RG` |
| Service Connection Name | `azure subs` |

---

## Step 7: Save Connection

⚠️ Ensure:

**Grant access permission to all pipelines** → **Unchecked**

Click:

**Save**

---

# 🔹 Part 2: About Release Gates

Release gates validate conditions before deployment proceeds.

## Available Gate Types

### 1. Invoke Azure Function
Executes Azure Function and validates successful execution.

### 2. Query Azure Monitor Alerts
Checks if active alerts exist.

### 3. Invoke REST API
Calls external/internal APIs.

### 4. Query Work Items
Checks work item thresholds.

---

# 🔹 Part 3: Configure CI Pipeline

---

## Step 1: Create Pipeline

Navigate:

**Pipelines → Create Pipeline**

---

## Step 2: Select Repository

Choose:

**Azure Repos Git (YAML)**

Repository:

**eShopOnWeb**

---

## Step 3: Select Existing YAML

Configuration:

| Field | Value |
|------|------|
| Branch | `main` |
| Path | `.ado/eshoponweb-ci.yml` |

Click:

**Continue**

---

## Step 4: Run Pipeline

Click:

**Run**

Wait until build completes successfully.

---

## Step 5: Rename Pipeline

Rename to:

`eshoponweb-ci`

---

# 🔹 Part 4: Create Azure Resources

---

## Create Resource Group Variables

```bash
REGION='westeurope'
RESOURCEGROUPNAME='az400m03l08-RG'
````

---

## Create App Service Plan

```bash
SERVICEPLANNAME='az400m03l08-sp1'

az appservice plan create \
-g $RESOURCEGROUPNAME \
-n $SERVICEPLANNAME \
--sku S1 \
--location $REGION
```

---

## Create Web Apps

```bash
SUFFIX=61686223

az webapp create -g $RESOURCEGROUPNAME -p $SERVICEPLANNAME -n RGATES$SUFFIX-DevTest

az webapp create -g $RESOURCEGROUPNAME -p $SERVICEPLANNAME -n RGATES$SUFFIX-Prod
```

---

# 🔹 Part 5: Configure Application Insights

---

## Step 1: Create Application Insights

Azure Portal → Search:

**Application Insights**

Select:

**+ Create**

---

## Step 2: Configure Settings

| Setting        | Value                  |
| -------------- | ---------------------- |
| Resource Group | `az400m03l08-RG`       |
| Name           | DevTest Web App Name   |
| Region         | Same as Web App Region |

---

## Step 3: Link to Web App

Navigate:

**DevTest Web App → Monitoring → Application Insights**

Enable Application Insights.

Select:

**Existing Resource**

Apply changes.

---

# 🔹 Part 6: Create Monitor Alerts

---

## Create Alert Rule

Navigate:

**Application Insights → Alerts → Create Alert Rule**

---

## Configure Signal

Select:

**Failed Requests**

---

## Configure Threshold

| Setting          | Value        |
| ---------------- | ------------ |
| Aggregation Type | Count        |
| Operator         | Greater Than |
| Threshold        | 0            |

---

## Alert Details

| Setting         | Value                          |
| --------------- | ------------------------------ |
| Severity        | Warning                        |
| Alert Rule Name | `RGATESDevTest_FailedRequests` |

Create alert.

---

# 🔹 Part 7: Configure Release Pipeline

---

## Step 1: Create Release Pipeline

Navigate:

**Pipelines → Releases**

Select:

**New Pipeline**

Choose template:

**Azure App Service Deployment**

---

## Step 2: Rename Stages

Rename:

* Stage 1 → **DevTest**

Clone stage and rename:

* Stage 2 → **Production**

---

## Step 3: Rename Pipeline

Set name:

`eshoponweb-cd`

---

## Step 4: Add Artifact

Source Build Pipeline:

`eshoponweb-ci`

Enable:

**Continuous Deployment Trigger**

---

# 🔹 Part 8: Configure DevTest Stage

---

## Deployment Settings

| Setting            | Value                                          |
| ------------------ | ---------------------------------------------- |
| Azure Subscription | Your Subscription                              |
| App Type           | Web App on Windows                             |
| App Service Name   | DevTest Web App                                |
| Package            | `$(System.DefaultWorkingDirectory)/**/Web.zip` |

---

## App Settings

```text
-UseOnlyInMemoryDatabase true
-ASPNETCORE_ENVIRONMENT Development
```

---

## Agent Settings

| Setting             | Value           |
| ------------------- | --------------- |
| Agent Pool          | Azure Pipelines |
| Agent Specification | windows-latest  |

---

# 🔹 Part 9: Configure Production Stage

Use same configuration as DevTest but select:

**Production Web App**

---

# 🔹 Part 10: Test Release Pipeline

---

## Trigger Build

Navigate:

**Pipelines → Pipelines**

Select:

`eshoponweb-ci`

Click:

**Run Pipeline**

---

## Verify Deployment

Check:

**Pipelines → Releases**

Confirm deployment completed for:

* DevTest
* Production

---

## Validate Web Apps

Azure Portal → Resource Group

Open both web apps and click:

**Browse**

Ensure application loads successfully.

---

# 🔹 Part 11: Configure Release Gates

---

## Enable Pre-Deployment Approvals

Navigate:

**Pipelines → Releases → Edit**

Select:

**DevTest → Pre-deployment Conditions**

Enable:

**Pre-deployment approvals**

---

## Add Approver

Enter:

Your Azure DevOps Account

---

## Save Changes

Create new release.

---

## Approve Deployment

When release enters:

**Pending Approval**

Click:

**Approve**

---

# ✅ Lab Validation Checklist

Ensure all are successful:

* [x] Service connection created
* [x] CI pipeline successful
* [x] Azure resources deployed
* [x] Application Insights configured
* [x] Alerts created
* [x] Release pipeline deployed
* [x] Release gates enabled
* [x] Approval workflow tested

---

# 🎯 Key Learnings

After completing this lab, you should understand:

* Azure DevOps Service Connections
* YAML CI Pipelines
* Release Pipelines
* Azure Web App Deployments
* Application Insights Monitoring
* Deployment Gates
* Pre/Post Deployment Approvals
* Controlled Production Releases

---

# 🏁 Conclusion

This lab demonstrates how to build an enterprise-grade Azure DevOps deployment workflow using:

* CI/CD Automation
* Monitoring
* Quality Gates
* Approval Workflows
* Controlled Releases

A critical real-world DevOps implementation pattern.

```
```

