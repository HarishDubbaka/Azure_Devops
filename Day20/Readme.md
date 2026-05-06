# 🚀 Deploy Docker Containers to Azure App Service (CI/CD with Azure DevOps)

This project demonstrates how to build, push, and deploy a Dockerized application using Azure DevOps, Azure Container Registry (ACR), and Azure App Service.

---

# 📚 Fundamentals: Containers

## What are Containers?

A **container** is a lightweight package that includes:

- Application code
- Runtime
- Libraries
- Dependencies
- Configuration files

It ensures an application runs **consistently across environments**.

### ✅ Example

If your app works on your laptop, a container ensures it works the same on:

- Test server  
- Production server  
- Cloud  
- Kubernetes cluster  

### 🔧 Popular Container Tools

- Docker  
- Podman  
- Kubernetes  

💡 **Analogy:** A container is like a *lunchbox* — everything needed is packed inside.

---

## 🚀 Why Containers Are Popular

### 1. Faster Startup
- Containers: **seconds**
- VMs: **minutes**

👉 Containers share the host OS kernel.

---

### 2. Lightweight
- Containers: **MBs**
- VMs: **GBs**

👉 More efficient resource usage.

---

### 3. DevOps Friendly

Ideal for:
- CI/CD pipelines  
- Microservices  
- Automation  
- Scaling  

---

### 4. Portability

Same behavior across:
- Dev  
- QA  
- Production  
- Cloud  

❌ No more *“It works on my machine.”*

---

## ⚖️ VM vs Container

| Feature           | VM                | Container        |
|------------------|------------------|------------------|
| Virtualization   | Hardware         | OS-level         |
| Guest OS         | Required         | Not required     |
| Size             | Large (GBs)      | Small (MBs)      |
| Startup Time     | Slow             | Fast             |
| Resource Usage   | High             | Low              |
| Isolation        | Strong           | Moderate         |
| Performance      | Slight overhead  | Near native      |
| Best For         | Full OS control  | App deployment   |

---

## 🧠 Why Containers Don’t Need a Hypervisor

### VM Architecture
```

Physical Server
↓
Hypervisor
↓
Guest OS
↓
Application

```

### Container Architecture
```

Physical Server
↓
Host OS
↓
Container Runtime
↓
Containers

```

### 🔑 Key Idea

Containers use **OS-level virtualization** via:

- Namespaces → process isolation  
- cgroups → resource control  
- Union file systems → layered images  

👉 No hypervisor required.

---

## 🏠 Analogy

- **VM** = Renting a full apartment 🏢  
- **Container** = Renting a room 🛏️  

---

## 🎯 When to Use What?

### Use VMs when:
- Full OS isolation is required  
- Running different OS types  
- Legacy applications  
- Strong security boundaries  

### Use Containers when:
- Microservices  
- CI/CD pipelines  
- Cloud-native apps  
- Fast scaling  

---

# 🧪 Lab: CI/CD with Azure DevOps

⏱️ Duration: **~20 minutes**

---

## 📌 Overview

You will:

- Build a Docker image  
- Push it to Azure Container Registry  
- Deploy it to Azure App Service  
- Automate using CI/CD pipelines  

---

## 🧰 Prerequisites

- Azure DevOps Organization  
- Azure Subscription  
- Browser (Edge/Chrome)  
- Role: **Contributor** or **Owner**  

---

## 🏗️ Architecture

```

Source Code
↓
CI Pipeline (Build)
↓
Docker Image
↓
Azure Container Registry (ACR)
↓
CD Pipeline (Deploy)
↓
Azure App Service
↓
Live Web App 🌐

```

---

# ⚙️ Step 1: Create Service Connection

1. Go to **Project Settings → Service Connections**
2. Click **Create Service Connection**
3. Choose:
   - Azure Resource Manager  
   - App registration (automatic)  
   - Workload Identity Federation  
4. Fill:
   - Subscription  
   - Resource Group: `AZ400-RG161552160`  
   - Name: `azure subs`  
5. Click **Save**

---

# 🔁 Step 2: CI Pipeline (Build & Push Image)

### 📄 YAML File
```

.ado/eshoponweb-ci-docker.yml

```

### 🛠️ Update Values

- `YOUR-SUBSCRIPTION-ID`
- `resourceGroup = AZ400-RG161552160`
- `location = westeurope`

---

### ▶️ Run Pipeline

1. Go to **Pipelines → New Pipeline**
2. Select repo: `eShopOnWeb`
3. Choose YAML file
4. Click **Run**

---

### 🔍 What Happens

- Creates Azure Container Registry  
- Builds Docker image  
- Tags image (`latest` + build ID)  
- Pushes to ACR  

---

### ✅ Verify

Azure Portal → Container Registry → Repositories

```

eshoponweb/web

```

Check tags:
- `latest`
- `<build-id>`

---

# 🚀 Step 3: CD Pipeline (Deploy App)

### 📄 YAML File
```

.ado/eshoponweb-cd-webapp-docker.yml

```

### 🛠️ Update Values

- `YOUR-SUBSCRIPTION-ID`
- `resourceGroup = AZ400-RG161552160`
- `location = westeurope`

---

### ▶️ Run Pipeline

1. Create new pipeline  
2. Select YAML  
3. Run  
4. Approve permissions  

---

### 🔍 What Happens

- Creates App Service Plan  
- Creates Web App (Linux container)  
- Enables Managed Identity  
- Assigns **AcrPull role**  
- Deploys Docker image  

---

# 🌐 Step 4: Test

1. Open Azure Portal  
2. Go to App Service  
3. Click **Browse**

✅ Application should load

---

# ⚠️ Troubleshooting

### Permission Error
> "Pipeline needs permission"

✔ Fix: Permit access

---

### No Image in ACR

✔ Fix:
- Check CI logs  
- Ensure build succeeded  

---

### App Not Loading

✔ Fix:
- Wait 1–2 minutes  
- Check logs  
- Verify `latest` tag  

---

### Branch Protection Error
```

TF402455: Pushes not permitted

```

✔ Fix:
- Disable branch policy  

---

# 🧹 Cleanup

1. Go to **Resource Groups**
2. Select:
```

AZ400-RG161552160

```
3. Click **Delete**

---

# 📚 Key Concepts

- Docker  
- Azure Container Registry (ACR)  
- Azure App Service  
- CI/CD pipelines  
- Managed Identity  
- Bicep (Infrastructure as Code)  

---

# 🎯 Summary

- CI builds & pushes Docker image  
- CD deploys to Azure  
- App runs in App Service  
- Accessible via browser  

---

# ✅ Result

✔ Docker image built  
✔ Image pushed to ACR  
✔ App deployed to Azure  
✔ Live application running 🎉




