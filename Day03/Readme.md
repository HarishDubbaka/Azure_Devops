# 🚀 Azure DevOps – Day 1 Setup Guide

## 📌 Getting Started

Follow these steps to set up your Azure DevOps environment:

1. Create an Azure DevOps account
2. Create a new **Organization** (e.g., `AzureDevOps`)
3. Create a new **Project** inside it (e.g., `Day1`)
4. Explore the left sidebar features:

   * Boards
   * Repos
   * Pipelines
   * Test Plans
   * Artifacts

---

## ⚠️ Common Error

```
Error: VS850036: Maximum number of organizations reached
```

### ❓ Why This Happens

Azure DevOps limits the number of organizations per Microsoft account.

* Default limit: **5 organizations**
* Includes all previously created organizations

### ✅ Solution

* Delete unused organizations
* Or use another Microsoft account

---

## 🧩 Core Services in Azure DevOps

Azure DevOps provides a complete set of integrated tools:

---

### 🗂️ Azure Boards

Plan, track, and manage work using Agile tools.

**Features:**

* Kanban boards & backlogs
* Sprint planning
* User stories, bugs, tasks
* Burndown charts & dashboards

**Example:**

> A product team creates user stories for "User Sign-In", tracks bugs, and monitors sprint progress using boards.

---

### 📦 Azure Repos

Source code management using Git or TFVC.

**Features:**

* Unlimited private repositories
* Branch policies
* Pull requests & code reviews
* Conflict resolution

**Example:**

> Developers create feature branches, submit pull requests, and enforce code review before merging.

---

### ⚙️ Azure Pipelines

CI/CD pipelines to automate build, test, and deployment.

**Features:**

* Multi-language support
* Docker & Kubernetes integration
* Deployment approvals & gates
* Works with Azure, AWS, GCP

**Example:**

> Every commit triggers a pipeline to build, test, containerize, and deploy an application.

---

### 🧪 Azure Test Plans

Testing tools for manual and automated testing.

**Features:**

* Test cases & test suites
* Exploratory testing
* Screenshots & reporting
* Integration with work items

**Example:**

> QA team tests user registration across browsers and links results to user stories.

---

### 📚 Azure Artifacts

Package management for sharing code libraries.

**Features:**

* Supports NuGet, npm, Maven, Python
* Version control
* Secure package sharing
* Pipeline integration

**Example:**

> A shared authentication library is published and reused across multiple projects.

---

## 🎯 Summary

Azure DevOps is a powerful platform that brings together:

* Planning (Boards)
* Coding (Repos)
* Building & Deployment (Pipelines)
* Testing (Test Plans)
* Package Management (Artifacts)

---

## 🔗 Next Step

➡️ Start exploring each service in details

---

