# 🚀 Enable Dynamic Configuration & Feature Flags with Azure DevOps

This project demonstrates how to implement **Dynamic Configuration Management** and **Feature Flags** using:

* Microsoft Azure DevOps
* Microsoft Azure App Configuration
* .NET .NET Applications
* YAML Pipelines
* Managed Identity + RBAC

This lab shows how to safely release features without redeploying applications.

---

# 📌 Objective

Learn how to:

* Manage application configuration centrally
* Enable runtime feature toggling
* Deploy configuration changes through pipelines
* Perform gradual feature rollouts
* Reduce deployment risk

---

# 📚 What are Feature Flags?

Feature Flags (Feature Toggles) allow developers to control application functionality **without changing code or redeploying**.

### Benefits

✅ Runtime enable/disable
✅ Canary releases
✅ Dark launches
✅ Safer production testing
✅ Instant rollback

---

# 🏗️ Architecture

```text
Developer
   ↓
Azure DevOps Pipeline
   ↓
Azure App Configuration
   ↓
Feature Flags / Config Values
   ↓
Application Runtime
```

---

# 🔧 Services Used

* Microsoft Azure DevOps
* Microsoft Azure App Configuration
* Microsoft Azure App Service
* Managed Identity
* Azure RBAC
* Feature Management Libraries

---

# Step 1: Create Azure Service Connection

Navigate to Azure DevOps:

[Azure DevOps Portal](https://aex.dev.azure.com?utm_source=chatgpt.com)

### Steps

1. Open **Project Settings**
2. Select **Service Connections**
3. Click **Create Service Connection**
4. Choose **Azure Resource Manager**
5. Select:

* Identity Type → App Registration (Automatic)
* Authentication → Workload Identity Federation
* Scope Level → Subscription

Set:

```text
Service Connection Name: azure subs
```

---

# Step 2: Create Azure App Configuration

In the Azure Portal:

[Azure Portal](https://portal.azure.com?utm_source=chatgpt.com)

Create:

```text
Resource Name: appcs-xxxxx
Tier: Standard
Authentication: Access Keys Enabled
```

---

# Step 3: Create Feature Flag

Navigate:

**Feature Manager → Create**

Example:

```text
Feature Flag Name: SalesWeekend
State: Enabled
Description: Enables promotional banner
```

---

# Step 4: Configure Managed Identity

Enable **System Assigned Managed Identity** for your App Service.

Assign RBAC role:

```text
App Configuration Data Reader
```

This allows your application to securely access configuration values.

---

# Step 5: Add Environment Variables

In App Service → Environment Variables

Add:

```text
AppConfigEndPoint=https://yourappconfig.azconfig.io
UseAppConfig=true
```

---

# Step 6: Install Feature Management Package

For .NET:

```bash
dotnet add package Microsoft.FeatureManagement.AspNetCore
```

---

# Step 7: Enable Feature Management

```csharp
builder.Services.AddFeatureManagement();
```

---

# Step 8: Use Feature Flags in Code

## Controller-based

```csharp
[FeatureGate("SalesWeekend")]
public class PromotionController : Controller
{
    public IActionResult Index()
    {
        return View();
    }
}
```

## Runtime Check

```csharp
if (await featureManager.IsEnabledAsync("SalesWeekend"))
{
    // Display banner
}
```

---

# Step 9: Azure DevOps Pipeline Integration

```yaml
trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- task: AzureCLI@2
  inputs:
    azureSubscription: 'azure subs'
    scriptType: bash
    scriptLocation: inlineScript
    inlineScript: |
      az appconfig feature set \
        --name myappconfig \
        --feature SalesWeekend \
        --yes
```

---

# Step 10: Dynamic Configuration Example

Create configuration value:

```text
Key: eShopWeb:Settings:NoResultsMessage
Value: Sorry, we couldn't find what you're looking for.
```

The application updates dynamically **without redeployment**.

---

# 🧪 Testing

### Feature Flag Testing

Toggle:

```text
SalesWeekend → Enabled / Disabled
```

Refresh application after ~10 seconds.

Observe:

* Banner appears
* Banner disappears

---

# 🎯 Real-World Use Cases

* Canary Deployments
* A/B Testing
* Beta Features
* Production Hotfixes
* Regional Rollouts

---

# 🔐 Best Practices

✔ Use meaningful names
✔ Remove stale flags
✔ Separate environments
✔ Audit changes
✔ Use Key Vault for secrets

---

# 🧹 Cleanup

Delete created resources:

* Resource Group
* App Configuration
* App Service
* Pipeline artifacts

---

# 📌 Key Learning Outcomes

By completing this lab, I learned how to:

* Implement centralized configuration management
* Enable runtime feature toggles
* Secure application access using Managed Identity
* Integrate App Configuration with CI/CD
* Perform zero-downtime configuration updates

---

# 🚀 Conclusion

Azure App Configuration combined with Azure DevOps enables safer, faster, and smarter deployments.

Dynamic configuration helps modern applications stay flexible while maintaining stability.

---


