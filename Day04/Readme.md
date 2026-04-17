# 📘 Day 04 – Azure DevOps Work Items & Overview & Azure Boards

Yesterday, we created the **Day 01 project** with the work item as **Basis**.

Now, let’s understand **what Work Items are** and explore the **Azure DevOps Overview & Navigation**.

---

# 📌 What are Work Items?

Work Items are used in Azure DevOps to **plan, track, and manage work** across the development lifecycle.

### 🔹 Types of Work Items:
- Tasks  
- Bugs  
- User Stories  
- Features  
- Epics  

✅ They help teams **organize work, assign responsibilities, and track progress efficiently**.

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
Configure:
- Teams  
- Permissions  
- Service connections  
- Repositories  

---

## 🏢 Organization Settings
Manage:
- Users  
- Billing  
- Policies  

👉 Applies across all projects  

---

## 🔍 Search Bar (Top)
Search across:
- Code  
- Work Items  
- Wiki  

---

# 🔍 Organization Settings vs Project Settings

👉 **Organization = Company level (Global control)**  
👉 **Project = Team/Product level (Local control)**  

---

# 🏢 Organization Settings (Global Level)

Applies across **ALL projects** in the organization.

### 🔑 Key Characteristics:
- Centralized control  
- Managed by Org Admins  
- Impacts every project  

### ⚙️ Configuration Includes:
- 👤 Users & Permissions (global access)  
- 🔐 Security policies (AAD integration)  
- 💳 Billing & subscriptions  
- 🔗 Service connections (shared)  
- 🧩 Extensions (Marketplace)  
- 🌐 Repo policies (optional)  
- 🛠️ Agent pools (shared)  

### 🧠 Example:
- Add user → Access to multiple projects  
- Create agent pool → Shared across projects  

---

# 📁 Project Settings (Local Level)

Applies only to a **specific project**.

### 🔑 Key Characteristics:
- Scoped to one project  
- Managed by Project Admins  
- Does NOT affect other projects  

### ⚙️ Configuration Includes:
- 👥 Project users & roles  
- 📌 Boards (Epics, Stories, Tasks)  
- 📦 Repositories (Git settings)  
- 🚀 Pipelines (build & release)  
- 🔐 Project-level permissions  
- 🔗 Service connections (project-specific)  
- 🧪 Test plans  

### 🧠 Example:
- Create repo → Visible only in that project  
- Pipeline → Runs only for that project  
- Add user → Limited to that project  

---

# ⚖️ Side-by-Side Comparison

| Feature        | Organization Settings | Project Settings          |
|---------------|----------------------|---------------------------|
| Scope          | Entire organization   | Single project            |
| Access Control | Global users          | Project-specific users    |
| Admin Level    | Org Admin             | Project Admin             |
| Agent Pools    | Shared                | Shared / Project-specific |
| Pipelines      | Not defined here      | Defined here              |
| Repos          | Not project-specific  | Managed here              |
| Billing        | Yes                   | No                        |
| Extensions     | Installed here        | Used in projects          |

---

# 🎯 Real-Time Analogy

### 🏢 Organization Settings = Head Office
- HR policies  
- Company-wide tools  
- Employee database  

### 📁 Project Settings = Teams
- Team tasks  
- Code repositories  
- Sprint planning  

---

# 🚀 When to Use What?

### ✅ Use Organization Settings when:
- Central governance is required  
- Sharing resources (agent pools, extensions)  
- Managing users across projects  

### ✅ Use Project Settings when:
- Working on a specific application/product  
- Managing pipelines, repos, boards  
- Controlling team-level access  

---

# 📖 Overview (Azure DevOps)

The **Overview section** is the **central entry point** of a project.

### 🔍 What You Can Do:
- View high-level summary  
- Track recent activities  
- Access dashboards & wiki  
- Provide onboarding info  
- Monitor project health  

---

## 📌 Sections Explained

### 📊 Overview
- Project name & description  
- Visibility (Public/Private)  
- Last updated details  

---

### 📄 Summary
- Recent commits  
- Work item updates  
- Pipeline activity  

---

### 📊 Dashboards
- Customizable views  
- Track:
  - Build status  
  - Bugs  
  - Sprint progress  

---

### 📘 Wiki
- Documentation tool  
- Used for:
  - Guides  
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

Azure Boards helps teams **plan, track, and manage work** using Agile methodologies.

---

# 🧩 Azure Boards Hub & Functions

## 📝 Work Items
- 👤 Assigned to you  
- ⭐ Items you follow  
- 🕒 Recently updated  

---

## 📌 Boards (Kanban)
- Drag-and-drop cards  
- Real-time updates  
- Visual workflow tracking  

---

## 📚 Backlogs
- Organize and prioritize work  

### Usage:
- Product backlog → Planning  
- Portfolio backlog → Epics & Features  

---

## 🏃 Sprints
- Plan iteration-based work  

### Features:
- Assign work to sprints  
- Taskboard for planning  
- Track sprint progress  

---

## 🔍 Queries
- Custom filtered views  

### Use Cases:
- Work item triage  
- Bulk updates  
- Dashboard charts  

---

## 📅 Delivery Plans
- Track work across teams  

### Features:
- Calendar view  
- Dependency tracking  
- Cross-team visibility  

---

## 📊 Analytics Views
- Reporting and insights  

### Features:
- Power BI integration  
- Custom dashboards  
- Trend analysis  

---

# 🔚 Final Note

The **Overview section** acts as a **single source of truth**, improving collaboration and visibility.

Combined with **Azure Boards**, it enables **end-to-end planning, tracking, and delivery of high-quality software**.
