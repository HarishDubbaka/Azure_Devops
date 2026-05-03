# 🚀 Day 16 - Configure CI Pipeline as Code with YAML

## 📌 Overview

In this exercise, I configured a **Continuous Integration (CI) Pipeline as Code using YAML in Azure DevOps** for the **eShopOnWeb** application.

This lab focused on:

- Importing a YAML pipeline definition
- Enabling Continuous Integration triggers
- Applying Pull Request validation
- Testing automatic pipeline execution
- Verifying published build artifacts

---

# Task 1: Import the YAML Build Definition for CI

In this task, I added the YAML build definition to implement Continuous Integration.

## Steps Performed

### Step 1: Create a New Pipeline

Navigate to:

```text
Pipelines > Pipelines
```

Click:

```text
New Pipeline
```

---

### Step 2: Select Source Repository

Choose:

- Azure Repos Git (YAML)
- Repository: **eShopOnWeb**

---

### Step 3: Select Existing YAML File

Choose:

```text
Existing Azure Pipelines YAML File
```

Select:

```text
Branch: main
File: /.ado/eshoponweb-ci.yml
```

Click:

```text
Continue
```

---

## CI Definition Tasks

The pipeline consists of the following tasks:

### 🔹 DotNet Restore

Restores NuGet package dependencies without storing them in source control.

---

### 🔹 DotNet Build

Builds the project and all dependencies.

---

### 🔹 DotNet Test

Executes unit tests using the .NET test driver.

---

### 🔹 DotNet Publish

Publishes the application and dependencies to:

```text
Build.ArtifactStagingDirectory
```

---

### 🔹 Publish Artifact - Website

Publishes the application artifact for deployment.

---

### 🔹 Publish Artifact - Bicep

Publishes the infrastructure artifact (Bicep file).

---

### Step 4: Run Pipeline

Click:

```text
Run
```

Wait for successful pipeline execution.

---

# Task 2: Enable Continuous Integration

The default pipeline does not enable Continuous Integration.

---

## Edit Pipeline Definition

Navigate to the pipeline and click:

```text
Edit Pipeline
```

---

## Replace Existing Trigger

Remove:

```yaml
# trigger:
# - main
```

Add:

```yaml
trigger:
  branches:
    include:
      - main
  paths:
    include:
      - src/web/*
```

---

## Trigger Explanation

This configuration automatically triggers the build pipeline when:

- Changes are pushed to the **main** branch
- Changes are made inside:

```text
src/web/
```

---

## Save Pipeline Changes

Click:

```text
Validate and Save
```

Then:

- Select **Create a new branch for this commit**
- Keep default branch name
- Keep **Start a pull request** checked

Click:

```text
Save
```

---

## Rename Pipeline

Navigate to:

```text
Pipelines > Pipelines
```

Select the pipeline.

Click:

```text
Ellipsis (...) > Rename/Move
```

Rename it to:

```text
eshoponweb-ci
```

Click:

```text
Save
```

---

## Complete Pull Request

Navigate to:

```text
Repos > Pull Requests
```

Open:

```text
Update eshoponweb-ci.yml for Azure Pipelines
```

After validation succeeds:

- Click **Approve**
- Click **Complete**
- Click **Complete Merge**

---

# Task 3: Test the CI Pipeline

In this task, I tested CI by creating a Pull Request.

---

## Step 1: Create New Branch

Navigate to:

```text
Repos > Branches
```

Create:

```text
Feature02
```

Based on:

```text
main
```

---

## Step 2: Modify Source Code

Navigate to:

```text
/eShopOnWeb/src/Web/Program.cs
```

Click:

```text
Edit
```

Remove:

```csharp
// Testing my PR
```

---

## Step 3: Commit Changes

Click:

```text
Commit > Commit
```

Keep default commit message.

---

## Step 4: Create Pull Request

When prompted, click:

```text
Create a Pull Request
```

In the PR page:

- Leave defaults
- Click **Create**

---

## Step 5: Complete Validation

Wait for all validation checks to succeed.

Then:

- Click **Approve**
- Select **Set auto-complete**
- Click **Complete**
- Click **Complete Merge**

---

# CI Pipeline Verification

After merging, the **eshoponweb-ci** pipeline triggered automatically.

Navigate to:

```text
Pipelines > Pipelines
```

Open:

```text
eshoponweb-ci
```

Select the latest run.

---

# Published Artifacts

After successful execution, verify artifacts via:

```text
Related > Published
```

---

## 📦 Bicep

Infrastructure deployment artifact.

---

## 🌐 Website

Application deployment artifact.

---

# Key Learnings

Through this exercise, I learned:

- How to configure CI Pipeline as Code
- YAML-based pipeline automation
- Branch-based trigger configuration
- Pull Request validation workflow
- Automated artifact publishing
- CI best practices in Azure DevOps

---

# Technologies Used

- Azure DevOps
- YAML Pipelines
- .NET
- Bicep
- Azure Repos
- Pull Requests

---

# Final Outcome

Successfully configured an automated CI pipeline that:

✅ Builds source code automatically  
✅ Validates Pull Requests  
✅ Publishes deployment artifacts  
✅ Enforces branch quality gates

---

## 🔗 GitHub Repository

Add your repository link here:

```md
[GitHub Repository](https://github.com/yourusername/yourrepo)
```

---

## 📚 Next Learning

- Continuous Deployment (CD)
- Multi-stage YAML pipelines
- Deployment approvals
- Environment strategies
- Infrastructure as Code deployments
````
