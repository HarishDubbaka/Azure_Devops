# 📘 Day 04 – Azure DevOps Work Items & Overview & Azure Boards

Yesterday, we created the **Day 01 project** with the work item as **Basis**.

Now, let’s understand **what Work Items are** and explore the **Azure DevOps Overview & Navigation**.

---

# 📌 What are Work Items?

Work Items are used in Azure DevOps to **plan, track, and manage work** across the development lifecycle.

They include:
- Tasks  
- Bugs  
- User Stories  
- Features  
- Epics  

They help teams **organize work, assign responsibilities, and track progress efficiently**.

---

# ⚙️ Process Types Explained

Azure DevOps provides different process templates based on project needs:

## 🟢 Agile
- Uses:
  - Epics  
  - Features  
  - User Stories  
  - Tasks  
  - Bugs  
- ✅ Best for most teams  
- Flexible and widely adopted  

---

## 🔵 Scrum
- Uses:
  - Epics  
  - Features  
  - Product Backlog Items (PBIs)  
  - Tasks  
  - Bugs  
- ✅ Sprint-focused approach  
- Ideal for iterative development  

---

## 🟣 CMMI
- More **structured and formal**
- Includes:
  - Change Requests  
  - Reviews  
- ✅ Used in regulated industries  

---

## ⚪ Basic
- Simplest model  
- Uses:
  - Issues  
  - Tasks  
- ✅ Best for beginners and learning  

---

# 🧭 Navigation Overview

Azure DevOps provides a simple and powerful navigation system:

## 📌 Left Sidebar
Quick access to:
- Boards  
- Repos  
- Pipelines  
- Test Plans  
- Artifacts  

---

## ⚙️ Project Settings (Bottom Left)
- Configure:
  - Teams  
  - Permissions  
  - Service connections  
  - Repositories  

---

## 🏢 Organization Settings
- Manage:
  - Users  
  - Billing  
  - Policies  
- Applies across all projects  

---

## 🔍 Search Bar (Top)
- Search across:
  - Code  
  - Work Items  
  - Wiki  

---

# 🔍 Organization Settings vs Project Settings (Azure DevOps)

Think of it like this:

👉 **Organization = Company level (Global control)**
👉 **Project = Team/Product level (Local control)**

---

# 🏢 Organization Settings (Global Level)

These settings apply across **ALL projects** inside your Azure DevOps organization.

### 🔑 Key Characteristics:

* Centralized control
* Managed by Org Admins
* Impacts every project

### ⚙️ What you configure here:

* 👤 **Users & Permissions (global access)**
* 🔐 Security policies (AAD integration, policies)
* 💳 Billing & subscriptions
* 🔗 Service connections (shared across projects)
* 🧩 Extensions (marketplace installs)
* 🌐 Repositories policies (optional org-level)
* 🛠️ Agent pools (shared across projects)

### 🧠 Example:

If you:

* Add a user at **organization level** → they *can access multiple projects*
* Create an agent pool → *all projects can use it*

---

# 📁 Project Settings (Local Level)

These settings apply only to a **specific project**.

### 🔑 Key Characteristics:

* Scoped to one project
* Managed by Project Admins
* Does NOT affect other projects

### ⚙️ What you configure here:

* 👥 Project users & roles
* 📌 Boards (Epics, Stories, Tasks)
* 📦 Repositories (Git settings)
* 🚀 Pipelines (build & release)
* 🔐 Project-level permissions
* 🔗 Service connections (project-specific)
* 🧪 Test plans

### 🧠 Example:

If you:

* Create a repo → only that project sees it
* Configure pipeline → runs only for that project
* Add user to project → access limited to that project

---

# ⚖️ Side-by-Side Comparison

| Feature        | Organization Settings | Project Settings          |
| -------------- | --------------------- | ------------------------- |
| Scope          | Entire organization   | Single project            |
| Access Control | Global users          | Project-specific users    |
| Admin Level    | Org Admin             | Project Admin             |
| Agent Pools    | Shared                | Can use shared or project |
| Pipelines      | Not defined here      | Defined here              |
| Repos          | Not project-specific  | Managed here              |
| Billing        | Yes                   | No                        |
| Extensions     | Installed here        | Used in projects          |

---

# 🎯 Simple Real-Time Analogy

👉 Imagine a company:

* 🏢 **Organization Settings = Head Office**

  * HR policies
  * Company-wide tools
  * Employee database

* 📁 **Project Settings = Individual Teams**

  * Team tasks
  * Code repos
  * Sprint planning

---

# 🚀 When to Use What?

### Use **Organization Settings** when:

* You want **central governance**
* Sharing resources (agent pools, extensions)
* Managing users across projects

### Use **Project Settings** when:

* You work on **specific application/product**
* Managing pipelines, repos, boards
* Controlling team-level access

---

# 🔎 Let’s Deep Dive into Each Section

---

# 📖 Overview (Azure DevOps)

The **Overview section** is the **central entry point of a project**, helping teams understand project status, activity, and resources.

---

## 🔍 What You Can Do in Overview

- Get a **high-level summary**  
- Track **recent activities**  
- Access **Dashboards & Wiki**  
- Provide **documentation & onboarding info**  
- Monitor **project health**

---

## 📌 Sections Explained

### 📊 Overview
- Shows:
  - Project name & description  
  - Visibility (Public/Private)  
  - Last updated details  
- Helpful for new team members  

---

### 📄 Summary
- Displays:
  - Recent commits  
  - Work item updates  
  - Pipeline activity  
- Gives a quick activity snapshot  

---

### 📊 Dashboards
- Customizable views  
- Track:
  - Build status  
  - Bugs  
  - Sprint progress  
- Enables real-time monitoring  

---

### 📘 Wiki
- Built-in documentation tool  
- Used for:
  - Project guides  
  - SOPs  
  - Architecture notes  
- Supports Markdown & version control  

---

## 🎯 Best Practices

- Keep Overview updated  
- Use Dashboards regularly  
- Maintain proper Wiki documentation  
- Monitor Summary frequently  

---

# 📊 Azure Boards

Azure Boards is a service in Azure DevOps that helps teams plan, track, and manage work using Agile methodologies like Scrum and Kanban.

---

# 🧩 Azure Boards Hub & Functions

## 📝 Work Items

View and manage lists of work items filtered by different criteria such as:

* 👤 Items assigned to you
* ⭐ Items you follow
* 🕒 Recently viewed or updated items

---

## 📌 Boards (Kanban Boards)

Visualize work items as cards and manage workflow efficiently.

### 🔑 Features:

* 🧲 Drag-and-drop cards across columns
* 🔄 Update status in real time
* 📊 Implement Kanban practices
* 👀 Visualize team progress

---

## 📚 Backlogs

Organize and prioritize work items effectively.

### 🔑 Usage:

* 🗂️ Product backlog → Project planning
* 🏗️ Portfolio backlog → Group work under:

  * Features
  * Epics

---

## 🏃 Sprints

Manage work for a specific iteration.

### 🔑 Features:

* 📅 Assign work to sprints
* 🧲 Drag items from backlog to sprint
* 📋 Use Taskboard for sprint planning
* 📈 Track sprint progress

---

## 🔍 Queries

Create custom filtered views of work items.

### 🔑 Use Cases:

* 🧹 Work item triaging
* 🔄 Bulk updates
* 📊 Generate charts for dashboards

---

## 📅 Delivery Plans

Track work across multiple teams.

### 🔑 Features:

* 🗓️ Calendar-based view
* 🔗 Track dependencies
* 📊 View progress of features and epics
* 👥 Monitor cross-team deliverables

---

## 📊 Analytics Views

Create reports and dashboards using Azure Boards data.

### 🔑 Features:

* 📈 Build Power BI reports
* ⚙️ Use default or custom views
* 📊 Track trends and performance

---

## 🔚 Final Note

The Overview section acts as a single source of truth, improving collaboration and visibility. Together with Azure Boards, it enables end‑to‑end planning, tracking, and delivery of high‑quality software

