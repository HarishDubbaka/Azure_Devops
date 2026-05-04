# Day 18 – Understanding GitHub & Importing eShopOnWeb Repository

## 📌 Overview

Today I explored **GitHub**, one of the most widely used platforms for version control and collaborative software development.

GitHub plays a critical role in modern DevOps practices by helping developers manage code, collaborate efficiently, track changes, and automate workflows.

As part of today’s hands-on lab, I imported the **eShopOnWeb** repository into my own GitHub account and configured it for future CI/CD pipeline integration.

---

# What is GitHub?

**GitHub** is a cloud-based platform built on **Git**, a distributed version control system.

It allows developers to:

- Store source code in repositories
- Track changes over time
- Collaborate with team members
- Review and merge code safely
- Automate build and deployment workflows

GitHub is widely used by:

- Individual developers
- Open-source contributors
- Development teams
- Large organizations

---

# Why GitHub is Important

GitHub is essential because it supports efficient and scalable software development.

## Key Benefits

### Version Control
Tracks every change made to project files and allows rollback when needed.

### Collaboration
Enables multiple developers to work on the same project simultaneously.

### Code Review
Allows teams to review changes before merging into production.

### Developer Portfolio
Acts as a showcase of projects and contributions.

### CI/CD Automation
Supports automated workflows through **GitHub Actions**.

---

# Features of GitHub

## 1. Version Control
GitHub is powered by Git and tracks file changes over time.

---

## 2. Collaboration
Multiple developers can work together on shared repositories.

---

## 3. Branching and Merging
Developers can create separate branches for:

- New features
- Bug fixes
- Experiments

Changes are later merged into the main branch.

---

## 4. Pull Requests
A structured way to review and approve code changes.

---

## 5. Issues and Project Management
Track:

- Bugs
- Tasks
- Enhancements
- Feature requests

---

## 6. GitHub Actions
Automates workflows such as:

- Build
- Testing
- Deployment
- Continuous Integration

---

# How GitHub Works

GitHub hosts repositories in the cloud.

Developers interact with repositories by:

### Clone
Download repository locally.

### Modify
Make code changes on the local machine.

### Commit
Save changes with messages.

### Push
Upload changes to GitHub.

### Pull Request
Request review before merging.

---

# Core GitHub Components

## Repository
Stores project files and version history.

Repositories can be:

- Public
- Private

---

## Branches
Allow isolated development.

Example:
- main
- feature/login-page
- bugfix/navbar

---

## Commits
Snapshots of code changes.

---

## Pull Requests
Enable review and approval workflow.

---

## Issues
Track project work and discussions.

---

# Hands-On Lab: Import eShopOnWeb to GitHub

## Objective

Import the **eShopOnWeb** repository into my own GitHub repository for Azure DevOps CI/CD labs.

---

# Repository Structure Explored

```text
.ado
.devcontainer
infra
.github
src
```

## Folder Details

### `.ado`
Azure DevOps YAML pipeline definitions

### `.devcontainer`
Container-based development setup

### `infra`
Infrastructure as Code templates

Includes:

- Bicep
- ARM templates

### `.github`
GitHub workflow definitions

### `src`
.NET 8 web application source code

---

# Task Completed

## Step 1: Create Repository

Created a new **public repository** in GitHub.

Repository Name:

```text
eShopOnWeb
```

---

## Step 2: Import Existing Repository

Imported from:

```text
https://github.com/MicrosoftLearning/eShopOnWeb
```

---

## Step 3: Configure Import Settings

| Field | Value |
|------|------|
| Source Repository | https://github.com/MicrosoftLearning/eShopOnWeb |
| Owner | My GitHub Account |
| Repository Name | eShopOnWeb |
| Privacy | Public |

---

## Step 4: Begin Import

Clicked:

**Begin Import**

Waited for repository migration to complete.

---

## Step 5: Enable GitHub Actions

Navigated to:

```text
Settings → Actions → General
```

Enabled:

✅ Allow all actions and reusable workflows

Saved configuration.

---

# What I Learned

Today’s lab helped me understand:

- GitHub repository management
- Importing external repositories
- Exploring repository structure
- Enabling workflow automation
- Preparing repositories for CI/CD pipelines

---

# Key Takeaway

GitHub is much more than a code hosting platform.

It is a complete collaboration and DevOps ecosystem that supports:

- Source control
- Automation
- Collaboration
- Continuous Integration
- Continuous Deployment

Understanding GitHub is a foundational skill for every DevOps Engineer.

---

# Next Learning

In the next lab, I will explore how to connect this imported GitHub repository with **Azure DevOps pipelines** to automate build and deployment processes.

---

# Author Harish Dubbaka
Learning | Building | Automating 

---
