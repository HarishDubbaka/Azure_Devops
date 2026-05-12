# 🚀 Azure Test Plans & CI Testing in Azure DevOps

This guide explains how to:

- Use Azure Test Plans for manual testing
- Create and manage test cases
- Configure Azure Service Connections
- Set up CI pipelines with automated testing
- Run Unit, Integration, and Functional Tests in Azure DevOps

---

# 📚 What is Azure Test Plans?

Azure Test Plans is a testing management tool in Azure DevOps that helps teams:

- Create and organize test cases
- Execute manual tests
- Track test results
- Manage bugs
- Maintain traceability between requirements, tests, and defects

It integrates directly with:

- Azure Boards
- Azure Repos
- Azure Pipelines

---

# 🧩 Testing Terminology

| Term | Description |
|------|-------------|
| **Test Plan** | A container for all testing activity in a sprint or release |
| **Test Suite** | A group of related test cases |
| **Test Case** | A step-by-step scenario used to verify a feature |
| **Test Step** | One action + expected result |
| **Test Run** | An execution session where tests are performed |
| **Test Result** | Outcome of a test case: Passed, Failed, or Blocked |
| **Bug** | A work item created when a test case fails |

---

# 🛠️ Creating a Test Plan

## Steps

1. Go to **Test Plans**
2. Select **+ New Test Plan**
3. Enter:
   - Test Plan Name
   - Iteration/Sprint
4. Select **Create**

A default test suite is automatically created.

You can organize suites by:

- Feature
- Module
- Sprint
- User Story

---

# 🧪 Creating Test Cases

## Steps

1. Open a Test Suite
2. Select **+ New Test Case**
3. Add:
   - Title
   - Test Steps
   - Expected Results

---

## Example Test Case

### Verify user can log in with valid credentials

| Action | Expected Result |
|--------|-----------------|
| Enter username `admin@test.com` | No validation error shown |
| Enter password | Password accepted |
| Click Login | Redirect to dashboard |

---

# ▶️ Running Tests Manually

## Steps

1. Select test cases
2. Click:
   - **Run**
   - **Run for web application**
3. Execute each step
4. Mark results:
   - ✅ Passed
   - ❌ Failed
   - ⛔ Blocked

---

# 🐞 Creating Bugs During Testing

If a test step fails:

1. Select **Create Bug**
2. Azure DevOps automatically captures:
   - Failed steps
   - Screenshots
   - Repro steps
   - Test context
3. Save the bug work item

---

# 📊 Test Metrics & Reporting

| Metric | Description |
|--------|-------------|
| **Pass Rate** | Percentage of tests passed |
| **Test Coverage** | Coverage of requirements |
| **Bug Count by Severity** | Critical, High, Medium, Low |
| **Traceability Matrix** | Relationship between stories and tests |

---

# 🔐 Create a Service Connection to Access Azure Resources

You need a Service Connection so Azure DevOps can deploy resources to Azure.

---

# 🛠️ Steps to Create a Service Connection

1. Open the Azure DevOps portal:

   https://aex.dev.azure.com

2. Sign in to your Azure DevOps organization

3. Open the **eShopOnWeb** project

4. Select:

   **Project Settings → Service Connections**

5. Click:

   **Create Service Connection**

6. Select:

   - **Azure Resource Manager**
   - Click **Next**

7. Configure:

| Setting | Value |
|---------|-------|
| Identity Type | App registration (automatic) |
| Credential | Workload Identity Federation |
| Scope Level | Subscription |

---

# 📋 Fill Required Details

| Field | Value |
|------|-------|
| Subscription | Your Azure Subscription |
| Resource Group | `AZ400-RG1` |
| Service Connection Name | `azure subs` |

⚠️ Leave **Grant access permission to all pipelines** unchecked.

Select **Save**.

---

# 🧪 About Software Testing

Testing ensures application quality after changes are made.

Manual testing is:

- Slow
- Expensive
- Less reliable

Automated testing improves speed and consistency.

---

# 🧪 Types of Automated Tests

| Test Type | Purpose |
|-----------|---------|
| **Unit Tests** | Test individual components in isolation |
| **Integration Tests** | Verify components work together |
| **Functional Tests** | Validate behavior from the user's perspective |

---

# 📦 Import the eShopOnWeb Repository

## Steps

1. Go to:

   **Repos → Files**

2. Select:

   **Import Repository**

3. Use Repository URL:

```text
https://github.com/MicrosoftLearning/eShopOnWeb.git
```

4. Select **Import**

---

# 📁 Repository Structure

| Folder | Purpose |
|--------|---------|
| `.ado` | Azure DevOps YAML pipelines |
| `.devcontainer` | Container development setup |
| `infra` | Bicep & ARM templates |
| `.github` | GitHub workflows |
| `src` | Application source code |
| `tests` | Unit, Integration & Functional tests |

---

# 🌿 Set Main Branch

1. Go to:

   **Repos → Branches**

2. Hover over `main`
3. Select ellipsis (`...`)
4. Click:

   **Set as default branch**

---

# 🚀 Setup Tests in CI Pipeline

---

# 📥 Import YAML Build Definition

## Steps

1. Go to:

   **Pipelines → Pipelines**

2. Click:

   **New Pipeline**

3. Select:

   - Azure Repos Git (YAML)
   - Repository: `eShopOnWeb`

4. Choose:

   **Existing Azure Pipelines YAML File**

5. Select:

```text
/.ado/eshoponweb-ci.yml
```

6. Click **Continue**

---

# ⚙️ CI Pipeline Tasks

The pipeline includes:

| Task | Purpose |
|------|---------|
| DotNet Restore | Restore dependencies |
| DotNet Build | Build application |
| DotNet Test | Execute tests |
| DotNet Publish | Publish app |
| Publish Artifact | Store deployable artifacts |

---

# ➕ Add Integration Tests to Pipeline

Add this task after Unit Tests:

```yaml
- task: DotNetCoreCLI@2
  displayName: Integration Tests
  inputs:
    command: "test"
    projects: "tests/IntegrationTests/*.csproj"
```

---

# ➕ Add Functional Tests to Pipeline

Add this task after Integration Tests:

```yaml
- task: DotNetCoreCLI@2
  displayName: Functional Tests
  inputs:
    command: "test"
    projects: "tests/FunctionalTests/*.csproj"
```

---

# 💾 Save Pipeline

1. Click **Validate and Save**
2. If validation succeeds:
   - Click **Save**
3. Commit changes directly to `main`

---

# ▶️ Run the Pipeline

## Steps

1. Select **Run**
2. Click **Run Pipeline**
3. Wait for the build to complete
4. Open the **Tests** tab

You can review:

- Passed tests
- Failed tests
- Test duration
- Test categories

---

# 📊 Test Summary

Azure DevOps displays:

- Test execution history
- Pass/fail statistics
- Test logs
- Detailed test runs

If the table appears empty:

- Reset filters to display all tests

---

# ⚠️ Troubleshooting Functional Test Failure

## Common Error

```text
System.IO.FileNotFoundException:
Could not load file or assembly
'Microsoft.Extensions.Configuration.Abstractions, Version=9.0.0.0'
```

---

# 📌 Cause

The repository targets .NET 8.0, but some dependencies reference .NET 9.0 assemblies.

---

# ✅ Workaround Options

## Option 1 — Skip Functional Tests (Recommended)

Temporarily remove Functional Tests from the pipeline.

Run only:

- Unit Tests
- Integration Tests

---

## Option 2 — Fix Package Versions

Edit:

```text
Directory.Packages.props
```

Update package versions:

| Package | Change |
|---------|--------|
| Microsoft.EntityFrameworkCore.Tools | 9.0.4 → 8.0.8 |
| System.Text.Json | 9.0.x → 8.0.1 |

---

# 🎯 Summary

In this lab you learned how to:

- Create Azure Test Plans
- Execute manual testing
- Create bugs from failed tests
- Configure Azure Service Connections
- Import repositories into Azure DevOps
- Configure CI pipelines using YAML
- Run Unit, Integration, and Functional Tests

Automated testing in CI/CD pipelines helps:

- Detect issues early
- Improve code quality
- Increase deployment confidence
- Support reliable software delivery

---
