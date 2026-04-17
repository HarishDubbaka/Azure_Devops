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

# 📋 Azure Boards

Modern development requires efficient work tracking and collaboration.  
Azure Boards provides Agile tools to manage the entire lifecycle.

---

## 🔑 Key Capabilities

### 📝 Work Item Management
- Create and manage:
  - User Stories  
  - Bugs  
  - Tasks  
  - Features  

---

### 📊 Queries & Charts
- Build custom queries  
- Visualize progress using charts  

---

### 📚 Backlog Management
- Prioritize work  
- Maintain clear and actionable backlog  

---

### 🏃 Sprint Planning
- Plan iterations  
- Track using:
  - Velocity  
  - Burndown charts  

---

### 📌 Task Boards
- Interactive Kanban boards  
- Drag-and-drop work tracking  

---

### 🗂️ Portfolio Management
- Organize hierarchy:
  - Epics → Features → Tasks  

---

### 🔄 Scrum Support
- Supports:
  - Daily standups  
  - Sprint reviews  
- Real-time collaboration  

---

## 📊 Benefits

- Complete project visibility  
- Improved collaboration  
- Data-driven decisions  
- Supports Scrum, Kanban, and Scrumban  

---

## 🖼️ Example (Backlogs View)

Azure Boards backlog page shows:
- New Items  
- Active Items  
- Items to Analyze  

This helps teams track work efficiently and visually.

---

## 🔚 Final Note

The Overview section acts as a single source of truth, improving collaboration and visibility. Together with Azure Boards, it enables end‑to‑end planning, tracking, and delivery of high‑quality software

