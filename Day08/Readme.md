# 📘 Day 08 – Sprint Management, Kanban Customization & Dashboards (Azure DevOps)

---

## 🎯 Lab Objective

This lab focuses on advanced Agile project management using Azure DevOps.  
You will learn how to effectively:

- Plan and manage sprints  
- Allocate team capacity and handle availability  
- Customize Kanban boards for better workflow visibility  
- Create dashboards for real-time insights  
- Use queries and charts for reporting  

---

## 🧠 Key Concepts Covered

- Agile Sprint Planning  
- Capacity Planning & Workload Distribution  
- Kanban Workflow & WIP Limits  
- Board Customization (Tags, Columns, Swimlanes)  
- Dashboards & Widgets  
- Query-based Reporting  

---

## ⚙️ Prerequisites

- Azure DevOps Organization  
- Existing Project (eShopOnWeb)  
- Configured Teams, Areas, and Iterations  
- Basic understanding of Agile & Scrum  

---

# 🏗️ Exercise 1: Manage Sprints & Capacity

## 🔹 Understanding Sprint Planning

A **Sprint** is a fixed time-boxed iteration where a team delivers a set of features.

### Sprint Planning has 2 parts:
1. **What to build?**
   - Select backlog items based on priority and team capacity  

2. **How to build?**
   - Break items into tasks  
   - Estimate effort (Remaining Work)  

---

## 🔹 Steps to Manage Sprint Tasks

1. Navigate to **Boards → Sprints**
2. Open **Taskboard**
3. Enable **Work Details View**
4. Filter by **Sprint 2**
5. Assign tasks to yourself  

---

## 🔹 Configure Team Capacity

1. Go to **Capacity Tab**
2. Set:
```

Activity: Development
Capacity per day: 1

```

### 📌 Why Capacity Planning?
- Prevents overload  
- Ensures realistic sprint commitments  
- Improves team productivity  

---

## 🔹 Add Days Off (Availability Management)

1. Select **Days Off**
2. Add:
```

Vacation: 4 working days

```

### 📌 Importance:
- Adjusts available capacity  
- Improves sprint accuracy  
- Avoids unrealistic workload  

---

# 📊 Exercise 2: Customize Kanban Board

---

## 🔹 What is Kanban?

Kanban is a **visual workflow management system** that helps track work progress.

---

## 🔹 Key Kanban Practices

- Visualize workflow  
- Limit Work in Progress (WIP)  
- Improve flow efficiency  

---

## 🔹 Add Tag Colors

1. Go to **Board Settings ⚙️ → Tag Colors**
2. Add:

```

Tag: data
Color: Yellow

```

### 📌 Use Case:
- Highlight critical work (e.g., data-related tasks)

---

## 🔹 Add Tags to Work Items

- Add:
  - `data`
  - `ux`

➡️ Improves filtering and visibility  

---

## 🔹 Add Custom Column

```

Column Name: QA Approved
WIP Limit: 1

```

### 📌 Why WIP Limits?
- Avoid bottlenecks  
- Maintain smooth workflow  
- Improve delivery speed  

---

## 🔹 Split Columns (Doing / Done)

Enable split column:

- Doing → Work in progress  
- Done → Work completed  

### 📌 Benefit:
- Shows real progress clearly  
- Enables pull-based workflow  

---

## 🔹 Define "Definition of Done"

```

Passes all tests

```

### 📌 Importance:
- Ensures quality  
- Standardizes completion criteria  

---

## 🔹 Add Swimlane

```

Name: Expedite
Color: Green

```

### 📌 Use Case:
- Highlight high-priority or urgent tasks  

---

# 📈 Exercise 3: Create & Customize Dashboards

---

## 🔹 What is a Dashboard?

A dashboard provides a **real-time visual overview** of project health.

---

## 🔹 Create Dashboard

1. Go to **Overview → Dashboards**
2. Click **New Dashboard**

```

Name: Product Training
Team: EShop-Web

```

---

## 🔹 Add Widgets

- Sprint Overview  
- Sprint Capacity  

### 📌 Benefits:
- Track sprint progress  
- Monitor team workload  

---

## 🔹 Widget Configuration

- Customize based on team needs  
- Save settings  

---

# 📊 Exercise 4: Query-Based Reporting

---

## 🔹 Why Queries?

Queries help filter and analyze work items for reporting.

---

## 🔹 Create Query

```

Work Item Type = Task
Area Path = eShopOnWeb\EShop-Web

```

---

## 🔹 Save Query

```

Name: Web Tasks
Location: Shared Queries

```

---

## 🔹 Create Chart

- Chart Type: Pie  
- Group By: Assigned To  

### 📌 Insight:
- Shows workload distribution  

---

## 🔹 Add Chart to Dashboard

- Add **Chart for Work Items widget**
- Connect to **Web Tasks query**

---

# 🚀 Lab Outcome

After completing this lab, you will be able to:

✅ Plan and manage sprints effectively  
✅ Allocate team capacity and handle availability  
✅ Customize Kanban workflows  
✅ Apply WIP limits and improve flow  
✅ Create dashboards for visibility  
✅ Use queries for analytics and reporting  

---

# 💡 Key Takeaways

- Agile success depends on proper planning  
- Capacity management prevents overload  
- Kanban improves visibility and efficiency  
- WIP limits reduce bottlenecks  
- Dashboards enable real-time decision-making  
- Queries provide actionable insights  

---

# ⚠️ Clean Up (Optional)

To delete the project:

1. Navigate to **Project Settings → Overview**
2. Select **Delete Project**
3. Confirm by entering project name  

> ⚠️ Warning: This will permanently delete all project data  

---

# 🎉 Conclusion

This lab demonstrates how Azure DevOps enables:

- End-to-end Agile planning  
- Workflow customization  
- Data-driven decision making  

Mastering these concepts helps teams deliver **high-quality software faster and more efficiently** 🚀
```

