# 🚀 Azure DevOps Self-Hosted Agents & YAML Pipelines Lab

## 📌 Overview

This lab demonstrates how to:

- Create an Azure Virtual Machine
- Configure a **Self-Hosted Azure DevOps Agent**
- Create and manage **Agent Pools**
- Configure **Personal Access Tokens (PAT)**
- Install required build tools
- Create YAML-based Azure Pipelines
- Run pipelines using self-hosted infrastructure

This setup is commonly used in enterprise environments where organizations require:

- Full control over build environments
- Custom software installations
- Enhanced security and compliance
- Faster pipeline execution through caching

---

# 🏗️ Exercise 1: Create Agents and Configure Agent Pools

---

## Task 1: Create and Connect to an Azure VM

### Steps

### 1. Open Azure Portal
Navigate to:

https://portal.azure.com

---

### 2. Create Virtual Machine

Search for:

**Virtual Machines**

Click:

**Create → Azure Virtual Machine**

---

### 3. Select Presets

Choose:

- **Workload Environment:** Dev/Test
- **Workload Type:** General Purpose

---

### 4. Configure Basics

| Setting | Value |
|---------|------|
| Resource Group | `rg-eshoponweb-agentpool` |
| VM Name | `eshoponweb-vm` |
| Region | Closest Azure Region |
| Availability | No infrastructure redundancy |
| Security Type | Trusted launch |
| Image | Windows Server 2022 Datacenter |
| Size | Cheapest Standard size |
| Inbound Ports | RDP (3389) |

---

### 5. Enable Managed Identity

Navigate to:

**Management Tab**

Enable:

✅ System Assigned Managed Identity

---

### 6. Deploy VM

Click:

**Review + Create → Create**

Wait for provisioning.

---

### 7. Connect to VM

- Open VM resource
- Select **Connect**
- Download **RDP file**
- Connect using Remote Desktop

---

# Task 2: Create Agent Pool

Inside VM browser:

Navigate to Azure DevOps:

https://aex.dev.azure.com

---

### Steps

Go to:

**Project Settings → Pipelines → Agent Pools**

Click:

**Add Pool**

Configure:

| Setting | Value |
|--------|------|
| Pool Type | Self-hosted |
| Pool Name | `eShopOnWebSelfPool` |

Leave unchecked:

❌ Grant access permission to all pipelines

Click:

**Create**

---

# Task 3: Download and Extract Agent Files

Go to:

**Agent Pool → Agents → New Agent**

Download Windows agent.

---

### Create Agent Directory

```powershell
mkdir agent
cd agent
```

---

### Extract Agent

```powershell
Add-Type -AssemblyName System.IO.Compression.FileSystem
[System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win-x64-4.255.0.zip", "$PWD")
```

---

# Task 4: Create Personal Access Token (PAT)

Navigate to:

**User Settings → Personal Access Tokens**

Click:

**New Token**

---

### Configure PAT

| Setting | Value |
|--------|------|
| Name | `eShopOnWebToken` |
| Scope | Agent Pools (Read & Manage) |
| Expiration | Minimum required |

---

⚠️ **Important**

Use least privilege access.

---

# Task 5: Configure Agent

Inside extracted agent directory:

```powershell
.\config.cmd
```

---

## Configuration Inputs

| Prompt | Value |
|-------|------|
| Server URL | `https://dev.azure.com/{organization}` |
| Auth Type | PAT |
| PAT | Your generated token |
| Agent Pool | `eShopOnWebSelfPool` |
| Agent Name | `eShopOnWebSelfAgent` |
| Work Folder | `_work` |
| Run as Service | Y |
| Enable SID | Y |
| Service Account | `NT AUTHORITY\SYSTEM` |

---

### Verify Agent

Navigate to:

**Agent Pools → Agents**

Status should show:

✅ Online

---

# Install Required Tools

---

## Install Azure CLI

```powershell
$ProgressPreference = 'SilentlyContinue'
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
Remove-Item .\AzureCLI.msi
```

---

## Install .NET SDK

Install:

**.NET 8 SDK or higher**

Download from:

https://dotnet.microsoft.com/

---

# 🧩 Exercise 2: Author YAML-Based Azure Pipelines

---

# Task 1: Create YAML Pipeline

Navigate to:

**Pipelines → New Pipeline**

---

### Select Repository

Choose:

- Azure Repos Git
- eShopOnWeb

---

### Choose Existing YAML

Branch:

`main`

Path:

```yaml
/.ado/eshoponweb-ci-pr.yml
```

Save pipeline.

---

## Pipeline Workflow

The pipeline performs:

### Restore
Restores NuGet packages

### Build
Compiles application

### Test
Executes unit tests

### Publish
Publishes application artifacts

---

# Task 2: Update Pipeline for Self-Hosted Agent

Replace:

```yaml
vmImage: ubuntu-latest
```

With:

```yaml
pool:
  name: eShopOnWebSelfPool
  demands: Agent.Name -equals eShopOnWebSelfAgent
```

---

### Validate and Save

Click:

**Validate and Save**

Then:

**Run**

---

# Successful Pipeline Execution

Pipeline should complete successfully on your self-hosted agent.

---

# 📚 Key Learnings

## Azure VM Provisioning
Learned how to create and configure build infrastructure.

---

## Self-Hosted Agents
Configured dedicated build agents for custom CI/CD execution.

---

## Agent Pools
Managed pipeline execution environments.

---

## PAT Security
Applied least privilege access.

---

## YAML Pipelines
Created reusable Infrastructure-as-Code pipelines.

---

## Enterprise DevOps Practices
Implemented production-grade CI/CD setup.

---

# 💡 Benefits of Self-Hosted Agents

✅ Full control over environment  
✅ Custom software installations  
✅ Better security  
✅ Improved performance  
✅ Reduced dependency on hosted runners

---

# 🛠️ Technologies Used

- Azure Virtual Machines
- Azure DevOps
- Self-Hosted Agents
- YAML Pipelines
- Azure CLI
- .NET 8 SDK
- PowerShell

---

# 🎯 Conclusion

This lab provided hands-on experience with:

- Building custom CI/CD infrastructure
- Configuring Azure DevOps self-hosted agents
- Running YAML pipelines on dedicated agents

A strong foundational step toward enterprise DevOps engineering.

