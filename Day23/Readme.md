# 🚀 Configure CI/CD Pipelines as Code with YAML in Azure DevOps

This lab demonstrates how to configure a complete CI/CD pipeline using YAML in Azure DevOps for the **eShopOnWeb** application.

You will learn how to:

* Create a YAML Build Pipeline
* Configure Continuous Integration (CI)
* Add Continuous Delivery (CD)
* Deploy to Azure App Service
* Validate deployment successfully

---

# 📚 Prerequisites

Before starting, ensure you have:

* ✅ An Azure Subscription
* ✅ Azure DevOps Organization
* ✅ Azure App Service already created
* ✅ eShopOnWeb repository imported into Azure DevOps
* ✅ Azure DevOps Service Connection configured

---

# 🏗️ Part 1 — Add a YAML Build Definition

## Step 1: Navigate to Pipelines

1. Open Azure DevOps
2. Navigate to:

```text
Pipelines → Pipelines
```

3. Select:

```text
Create Pipeline
```

---

## Step 2: Select Repository Source

On the **Where is your code?** pane:

Select:

```text
Azure Repos Git (YAML)
```

---

## Step 3: Select Repository

Choose the repository:

```text
eShopOnWeb-61644079
```

---

## Step 4: Use Existing YAML File

On the **Configure your pipeline** pane:

1. Scroll down
2. Select:

```text
Existing Azure Pipelines YAML File
```

---

## Step 5: Configure Existing YAML File

Specify the following:

| Setting | Value                    |
| ------- | ------------------------ |
| Branch  | `main`                   |
| Path    | `.ado/eshoponweb-ci.yml` |

Select:

```text
Continue
```

---

## Step 6: Run the Build Pipeline

From the **Review your Pipeline YAML** screen:

Select:

```text
Run
```

Wait for the build pipeline to complete successfully.

---

# 🔍 Verify Build Pipeline

Once completed successfully:

* Review each YAML task
* Check warnings/errors if any
* Confirm artifacts are generated successfully

---

# 🚀 Part 2 — Add Continuous Delivery (CD)

Now you'll extend the YAML pipeline to automatically deploy the application to Azure App Service.

---

# ✏️ Edit the Pipeline

1. Open the completed pipeline run
2. Select the ellipsis menu:

```text
⋯
```

3. Select:

```text
Edit pipeline
```

---

# ➕ Add Deploy Stage

Navigate to the end of the YAML file.

Add the following stage definition:

```yaml
- stage: Deploy
  displayName: Deploy to an Azure Web App
  jobs:
    - job: Deploy
      pool:
        vmImage: "windows-latest"
      steps:
```

---

# 📦 Add Download Build Artifacts Task

Under the `steps:` section, add:

```yaml
- task: DownloadBuildArtifacts@1
  inputs:
    buildType: "current"
    downloadType: "single"
    artifactName: "Website"
    downloadPath: "$(Build.ArtifactStagingDirectory)"
```

This downloads the build artifact generated during the Build stage.

---

# ☁️ Add Azure App Service Deploy Task

Below the Download Artifacts task, add:

```yaml
- task: AzureRmWebAppDeployment@4
  inputs:
    ConnectionType: "AzureRM"
    azureSubscription: "AZURE SUBSCRIPTION HERE"
    appType: "webApp"
    WebAppName: "eshoponWebYAML369825031"
    packageForLinux: "$(Build.ArtifactStagingDirectory)/**/Web.zip"
    AppSettings: "-UseOnlyInMemoryDatabase true -ASPNETCORE_ENVIRONMENT Development"
```

---

# ✅ Complete Deploy Stage Example

Your final deploy stage should look similar to this:

```yaml
- stage: Deploy
  displayName: Deploy to an Azure Web App
  jobs:
    - job: Deploy
      pool:
        vmImage: "windows-latest"

      steps:
        - task: DownloadBuildArtifacts@1
          inputs:
            buildType: "current"
            downloadType: "single"
            artifactName: "Website"
            downloadPath: "$(Build.ArtifactStagingDirectory)"

        - task: AzureRmWebAppDeployment@4
          inputs:
            ConnectionType: "AzureRM"
            azureSubscription: "AZURE SUBSCRIPTION HERE"
            appType: "webApp"
            WebAppName: "eshoponWebYAML369825031"
            packageForLinux: "$(Build.ArtifactStagingDirectory)/**/Web.zip"
            AppSettings: "-UseOnlyInMemoryDatabase true -ASPNETCORE_ENVIRONMENT Development"
```

---

# ⚠️ Important Notes

## YAML Indentation

YAML is indentation-sensitive.

Ensure tasks are properly indented under:

```yaml
steps:
```

Use spaces only — never tabs.

---

# 💾 Save the Pipeline

1. Select:

```text
Validate and save
```

2. Select:

```text
Save
```

This commits the updated YAML file to the `main` branch.

---

# ▶️ Run the Pipeline

Navigate to:

```text
Pipelines → Pipelines
```

Open:

```text
eShopOnWeb-61644079
```

Select:

```text
Run pipeline
```

Confirm the run.

---

# 🔍 Observe Pipeline Stages

You should now see two stages:

| Stage                    | Purpose               |
| ------------------------ | --------------------- |
| Build .NET Core Solution | Build the application |
| Deploy to Azure Web App  | Deploy to Azure       |

---

# 🔐 Grant Deployment Permission

When the Deploy stage starts:

1. Select:

```text
View
```

2. From the **Waiting for Review** pane select:

```text
Permit
```

3. Confirm by selecting:

```text
Permit
```

---

# ✅ Verify Successful Deployment

Wait for the Deploy stage to complete successfully.

---

# 🌐 Review the Deployed Website

## Step 1: Open Azure Portal

Navigate to your Azure App Service.

---

## Step 2: Browse the Application

From:

```text
Overview → Browse
```

Open the application in a new browser tab.

---

# 🎉 Expected Result

You should see the:

## eShopOnWeb E-Commerce Website

running successfully from Azure App Service.

---

# 📌 Key Learnings

✅ Configure Pipelines as Code using YAML
✅ Build .NET applications in Azure DevOps
✅ Create multi-stage YAML pipelines
✅ Download and use build artifacts
✅ Deploy applications to Azure App Service
✅ Implement CI/CD automation

---

# 🧠 YAML Concepts Practiced

| Concept   | Description                       |
| --------- | --------------------------------- |
| Stages    | Logical pipeline sections         |
| Jobs      | Units of execution                |
| Steps     | Individual tasks                  |
| Tasks     | Prebuilt Azure DevOps actions     |
| Artifacts | Files shared between stages       |
| CI/CD     | Continuous Integration & Delivery |

---

# 🔥 Final Outcome

You successfully implemented:

* CI using YAML Build Pipelines
* CD using Azure App Service Deployment
* Multi-stage Azure DevOps Pipelines
* Automated deployment workflow

---

# 📖 Sample Pipeline Flow

```text
Code Commit
    ↓
Build Stage
    ↓
Generate Artifact
    ↓
Deploy Stage
    ↓
Azure App Service
    ↓
Live eShopOnWeb Website
```

---

# 🚀 Next Steps

* ✅ Approval Gates
* ✅ Environment Variables
  
