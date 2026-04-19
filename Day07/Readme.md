# 📘 Day 07 Lab – Agile Planning & Portfolio Management with Azure Boards

## 🎯 Lab Objective

In this lab, you will learn how to use Azure Boards for Agile planning and portfolio management.

---

## 🧠 What You Will Learn

* Manage teams, areas, and iterations
* Manage work items (Epics, Features, PBIs, Tasks)
* Plan and track sprints
* Customize Kanban boards
* Define dashboards
* Customize team processes

---

## ⚙️ Prerequisites

* Browser: Microsoft Edge or supported browser
* Azure Subscription (Free account works)
* Azure DevOps Organization

---

# 🏗️ Exercise 1: Create a New Project

### 🔹 Steps

1. Navigate to: [https://dev.azure.com](https://dev.azure.com)
2. Click **New Project**
3. Use the following settings:

```
Name: eShopOnWeb  
Visibility: Private  
Version Control: Git  
Work Item Process: Scrum  
```

4. Click **Create**

---

# 📥 Exercise 2: Import Repository

We will use the sample project:

👉 eShopOnWeb

### 🔹 Steps

1. Go to **Repos → Files**
2. Click **Import Repository**
3. Paste:

```
https://github.com/MicrosoftLearning/eShopOnWeb
```

4. Click **Import**

---

## 📂 Repository Structure Overview

```
.ado           → Azure DevOps pipelines  
.devcontainer  → Dev container setup  
.azure         → Bicep & ARM templates  
.github        → GitHub workflows  
src            → .NET 8 application  
```

---

## 🔹 Set Default Branch

1. Go to **Repos → Branches**
2. Select **main branch → (...) → Set as default**

---

# 👥 Exercise 3: Manage Teams, Areas & Iterations

---

## 🔹 Create a Team

1. Go to **Project Settings → Teams**
2. Click **New Team**
3. Enter:

```
Team Name: EShop-Web
```

---

## 🔹 Configure Iterations (Sprints)

1. Go to **Boards → Iterations**
2. Add:

```
Sprint 1  
Sprint 2  
Sprint 3  
```

3. Set:

* Sprint duration → 3 weeks
* Assign to team

---

## 🔹 Configure Area Paths

1. Go to **Boards → Areas**
2. Enable:

* ✅ Include sub-areas

---

# 📝 Exercise 4: Manage Work Items

---

## 🔹 Create an Epic

1. Go to **Boards → Work Items**
2. Click **New Work Item → Epic**
3. Enter:

```
Title: Product training  
Area: EShop-Web  
Iteration: Sprint 2  
Assign: Yourself  
```

---

## 🔹 Add Feature (Child of Epic)

* Feature Name:

```
Training dashboard
```

---

## 🔹 Add Product Backlog Items (PBIs)

Under the feature, create:

```
1. As a customer, I want to view new tutorials  
2. As a customer, I want to see tutorials I recently viewed  
3. As a customer, I want to request new tutorials  
```

---

# 📊 Exercise 5: Manage Kanban Board

---

## 🔹 Move Work Items Across States

| Work Item         | State     |
| ----------------- | --------- |
| View tutorials    | Approved  |
| Recently viewed   | Committed |
| Request tutorials | Done      |

---

## 🔹 Assign Work Item

* Expand card
* Assign to yourself

---

# 📋 Exercise 6: Manage Tasks

---

## 🔹 Add Tasks to PBI

### Task 1

```
Title: Add page for most recent tutorials  
Remaining Work: 5  
Activity: Development  
```

### Task 2

```
Title: Optimize data query for most recent tutorials  
Remaining Work: 3  
Activity: Design  
```

---

# 📈 Exercise 7: Backlog View

* Switch to **View as Backlog**
* Use tabular format to manage tasks easily

---

# 🚀 Lab Outcome

After completing this lab, you will be able to:

✅ Create and configure Azure DevOps project
✅ Import Git repositories
✅ Organize teams and sprints
✅ Create and manage Agile work items
✅ Track work using Kanban boards
✅ Break down work into tasks

---

# 💡 Key Takeaways

* Agile hierarchy: **Epic → Feature → PBI → Task**
* Sprints help in structured delivery
* Boards provide visual tracking
* Azure Boards supports end-to-end traceability

