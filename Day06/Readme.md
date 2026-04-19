# 📘 Azure Test Plans & Azure Artifacts Guide

## 🔹 Overview

This repository provides an overview of:

* **Azure Test Plans** – for managing and executing testing activities
* **Azure Artifacts** – for managing and sharing packages

---

# 🧪 Azure Test Plans

Azure Test Plans offers powerful tools for improving **software quality and collaboration** across development teams.

It is a **browser-based test management solution** that supports:

* Manual testing
* User Acceptance Testing (UAT)
* Exploratory testing
* Stakeholder feedback

---

## ⚙️ Key Features

### ✅ Manual & Exploratory Testing

* Organize planned manual testing using **Test Plans** and **Test Suites**
* Assign testers and test leads
* Perform exploratory testing without predefined test cases

---

### 👥 User Acceptance Testing (UAT)

* Validate delivered features against customer requirements
* Reuse test cases created by engineering teams

---

### 💬 Stakeholder Feedback

* Allow non-technical stakeholders (marketing, sales, etc.) to test applications
* Collect real-world feedback

---

### 🤖 Test Automation Integration

* Integrate with **Azure Pipelines (CI/CD)**
* Associate test cases with build/release pipelines
* Automatically publish and review test results

---

### 🔗 Traceability

* Link test cases with:

  * User stories
  * Features
  * Requirements

* Automatically track:

  * Test execution
  * Defects
  * Build versions

---

### 📊 Reporting & Analytics

* Built-in reports:

  * Progress reports
  * Pipeline test reports
  * Analytics dashboards

* Use widgets and charts for real-time insights

---

## 🧰 Core Components

* **Test Plans**
* **Test Suites**
* **Test Runs**
* **Configurations**
* **Parameters**
* **Progress Reports**

---

## ⚠️ Note

* Applies to:

  * Azure DevOps Services
  * Azure DevOps Server 2020+

* UI has changed significantly in newer versions

---

# 📦 Azure Artifacts

Azure Artifacts helps teams **store, manage, and share dependencies** using a centralized feed.

---

## 🚀 Features

* Centralized package management

* Supports multiple package types:

  * NuGet
  * npm
  * Maven
  * Python
  * Cargo
  * Universal Packages

* Share packages:

  * Within team
  * Across organizations
  * Publicly

---

## 🏗️ Create a New Feed

Follow these steps:

1. Sign in to your **Azure DevOps organization**
2. Navigate to your **project**
3. Select **Artifacts**
4. Click **Create Feed**
5. Configure:

   * **Name** – descriptive name
   * **Visibility** – who can access
   * **Scope** – project/org level
   * **Upstream Sources** (optional)
6. Click **Create**

---

## 📥 Get Started with Packages

You can publish and consume packages using different technologies:

| Package Type           | Description                   |
| ---------------------- | ----------------------------- |
| **NuGet**              | Publish using NuGet.exe       |
| **Dotnet**             | Publish using dotnet CLI      |
| **npm**                | Publish JavaScript packages   |
| **Maven**              | Java-based package management |
| **Gradle**             | Build & publish automation    |
| **Python**             | Python package publishing     |
| **Cargo**              | Rust package manager          |
| **Universal Packages** | Generic file storage          |

---

## 🔄 Common Workflows

* 📤 Publish packages to feed
* 📥 Consume internal/external packages
* 🌐 Use public registries:

  * nuget.org
  * npmjs.com
  * Maven Central

---

# 🎯 Summary

| Tool                 | Purpose                             |
| -------------------- | ----------------------------------- |
| **Azure Test Plans** | Test management & quality assurance |
| **Azure Artifacts**  | Dependency & package management     |

---

# 📌 Best Practices

* Link test cases to requirements for traceability
* Automate tests using CI/CD pipelines
* Use feeds to centralize dependencies
* Enable upstream sources for external packages

---

# 📚 References

* Azure DevOps Documentation


