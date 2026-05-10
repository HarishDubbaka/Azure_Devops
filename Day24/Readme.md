# 🚀 Azure DevOps Environments & Deployment Types

## Approvals, Deployment History & Deployment Strategies

This guide explains how to use **Azure DevOps Environments** and **Deployment Jobs** to build secure, traceable, and production-ready CI/CD pipelines.

---

# 📚 What is an Environment in Azure DevOps?

An **Environment** in Azure DevOps represents a deployment target such as:

* Development
* Staging
* Production
* Kubernetes clusters
* Virtual machine infrastructure

Environments provide:

✅ Deployment history
✅ Approval workflows
✅ Traceability and auditing
✅ Resource management
✅ Deployment strategies
✅ Security checks and governance

Unlike standard pipeline stages, environments maintain a **complete history of deployments**.

---

# 🔍 Why Environments Matter

Using environments helps teams:

* Track which version is deployed and where
* Identify who approved deployments
* Reduce production deployment risks
* Implement enterprise governance
* Support compliance and auditing
* Enable safer rollout strategies

---

# 🏗️ Creating Environments

Navigate to:

```text
Pipelines → Environments → New Environment
```

## Steps

1. Enter the environment name

Example:

```text
Development
Staging
Production
```

2. Add an optional description

3. Select a resource type

| Resource Type    | Purpose                    |
| ---------------- | -------------------------- |
| None             | Generic deployment target  |
| Kubernetes       | AKS/Kubernetes deployments |
| Virtual Machines | Direct VM deployments      |

4. Click **Create**

---

# 🎯 Environment Resource Types

## 1️⃣ None

Used for:

* Basic deployment tracking
* Approval workflows
* Simple CI/CD pipelines

No infrastructure connection is required.

---

## 2️⃣ Kubernetes Resources

Useful for:

* AKS deployments
* Namespace-level deployments
* Containerized applications

### Benefits

* Namespace tracking
* Kubernetes deployment visibility
* Rolling and canary deployment support

---

## 3️⃣ Virtual Machine Resources

Useful for:

* IIS applications
* Windows/Linux VM deployments
* On-premises deployments

Requires installing the Azure Pipelines agent on target VMs.

---


# ⚙️ Deployment Strategies

Azure DevOps supports multiple deployment strategies for safe application updates.

---

# 1️⃣ runOnce Strategy

The `runOnce` strategy is the default deployment pattern.

## How It Works

* Executes deployment steps sequentially
* Deploys once to the target environment
* No phased rollout or traffic management

## Best For

* Development environments
* Test environments
* Low-risk deployments

## Example

```yaml
strategy:
  runOnce:
    deploy:
      steps:
      - script: echo Deploy web app...
```

---

# 2️⃣ Rolling Deployment Strategy

Rolling deployments gradually replace instances of the previous version with the new version.

## How It Works

* Updates targets in batches
* Reduces downtime
* Limits the impact of failures
* Supports readiness checks and rollback

## Best For

* Production VM deployments
* Medium-risk applications
* Highly available systems

## Key Configuration

* `maxParallel` → Maximum number of targets updated simultaneously

## Example

```yaml
strategy:
  rolling:
    maxParallel: 5

    preDeploy:
      steps:
      - script: echo Initialize deployment

    deploy:
      steps:
      - script: echo Deploy web app...

    routeTraffic:
      steps:
      - script: echo Route traffic...

    postRouteTraffic:
      pool: server
      steps:
      - script: echo Monitor application health...

    on:
      failure:
        steps:
        - script: echo Rollback deployment...

      success:
        steps:
        - script: echo Deployment successful...
```

---

# 3️⃣ Canary Deployment Strategy

Canary deployments reduce risk by rolling out changes gradually to a small subset of users or instances.

## How It Works

1. Deploy to a small percentage of users/instances
2. Monitor application health
3. Continue rollout if successful
4. Roll back if issues are detected

## Benefits

✅ Lower production risk
✅ Easier rollback
✅ Real-world validation before full rollout

## Key Configuration

* `increments` → Percentage-based rollout steps

## Example

```yaml
strategy:
  canary:
    increments: [10, 20]

    preDeploy:
      steps:
      - script: echo Initialize deployment

    deploy:
      steps:
      - script: echo Deploy updates...

    routeTraffic:
      steps:
      - script: echo Route traffic...

    postRouteTraffic:
      pool: server
      steps:
      - script: echo Monitor application health...

    on:
      failure:
        steps:
        - script: echo Perform rollback...

      success:
        steps:
        - script: echo Deployment checks passed...
```

---

# 🔄 Deployment Lifecycle Hooks

Deployment strategies support lifecycle hooks for advanced control.

| Hook             | Purpose                               |
| ---------------- | ------------------------------------- |
| preDeploy        | Initialization and preparation tasks  |
| deploy           | Main deployment steps                 |
| routeTraffic     | Redirect traffic to new deployment    |
| postRouteTraffic | Monitor health after traffic routing  |
| on: success      | Execute tasks after successful deploy |
| on: failure      | Execute rollback or cleanup actions   |

---

# 🖥️ Virtual Machine Targets

For VM environments:

1. Install the Azure Pipelines Agent
2. Register the VM with the environment
3. Execute deployment jobs directly on target machines

## Benefits

✅ Centralized deployments
✅ Remote deployment execution
✅ Infrastructure visibility

---

# 📜 Deployment History & Traceability

Every deployment to an environment is automatically tracked.

Recorded information includes:

| Information  | Description              |
| ------------ | ------------------------ |
| Build Number | Pipeline run version     |
| Commit ID    | Source code commit       |
| Branch       | Deployment source branch |
| Approver     | User who approved        |
| Timestamp    | Deployment time          |
| Result       | Success or failure       |

---

# 🔄 Deployment Benefits

## ✅ Traceability

Track exactly what was deployed and when.

---

## ✅ Audit Compliance

Maintain deployment records for governance and compliance requirements.

---

## ✅ Faster Troubleshooting

Quickly identify failed deployments and affected versions.

---

## ✅ Rollback Visibility

Know which version should be redeployed if rollback is required.

---

# 🛡️ Best Practices

## ✅ Use Separate Environments

Create dedicated environments for:

* Development
* Staging
* Production

---

## ✅ Add Production Approvals

Never allow direct production deployments without approval.

---

## ✅ Restrict Production Branches

Allow only:

```text
main
release/*
```

---

## ✅ Use Appropriate Deployment Strategies

| Environment | Recommended Strategy |
| ----------- | -------------------- |
| Development | runOnce              |
| Staging     | rolling              |
| Production  | canary               |

---

## ✅ Use Deployment Jobs

Always use deployment jobs instead of regular jobs for environment deployments.

---
