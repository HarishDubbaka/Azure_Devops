# 🚀 DevOps Fundamentals & Azure DevOps Introduction

## 📌 Overview

Before diving deep into DevOps, it’s important to understand:
- What DevOps is
- How it differs from traditional and Agile approaches
- Basic prerequisites to get started with Azure DevOps

---

## 🧾 Prerequisites

To start practicing DevOps using Azure DevOps:

- Create a **free subscription**
- Access Azure DevOps portal: https://dev.azure.com
- Create:
  - Organization
  - Project
  - Resources

---

## ☁️ What is Azure DevOps?

**Azure DevOps** is Microsoft’s cloud platform that provides all the tools required to implement DevOps practices in one place.

### Key Benefits:
- Free for small teams
- Cloud-based and scalable
- Integrated tools for:
  - Planning
  - Development
  - Testing
  - Deployment
  - Monitoring

---

## 🔍 DevOps vs Traditional (Waterfall)

| Feature              | Waterfall                     | DevOps                          |
|---------------------|------------------------------|----------------------------------|
| Release Cycle       | 6–12 months                  | Hours to days                   |
| Team Structure      | Siloed (Dev & Ops separate)  | Unified & collaborative         |
| Testing             | Manual, at the end           | Continuous & automated          |
| Failure Risk        | Very high (big releases)     | Low (small frequent releases)   |

---

## 🔄 Waterfall vs Agile

| Feature                  | Waterfall                | Agile Approach                |
|--------------------------|--------------------------|-------------------------------|
| Approach                | Linear & Sequential      | Iterative & Incremental       |
| Flexibility             | Rigid                    | Highly Flexible               |
| Customer Involvement    | Low                      | High (continuous feedback)    |
| Testing                 | After development        | Continuous in every sprint    |
| Delivery                | Single release           | Frequent releases             |
| Best For                | Fixed requirements       | Changing requirements         |

---

## ⚙️ What is DevOps?

**DevOps** is a combination of Development and Operations practices that enables organizations to:

- Build software faster
- Improve quality
- Automate processes
- Enhance collaboration

### 🎯 Core Goal

👉 Deliver high-quality software quickly and efficiently with continuous integration, testing, and deployment.

---

## 🔁 DevOps Lifecycle & Key Processes 

### 🔹 Continuous Integration (CI)

**Stages:** Plan → Code → Build → Test

- Developers frequently integrate code into a shared repository
- Automated builds and tests run on each commit
- Helps detect issues early

---

### 🔹 Continuous Deployment / Delivery (CD)

**Stages:** Release → Deploy

- Code that passes CI is automatically deployed
- Minimal manual intervention
- Targets:
  - Staging
  - Production

---

### 🔹 Continuous Monitoring

**Stages:** Operate → Monitor

- Monitor application and infrastructure
- Track:
  - Performance
  - Security
  - Reliability
- Use feedback for continuous improvement

---

## 🧠 Key DevOps Terminology

| Term            | Description |
|-----------------|------------|
| **Pipeline**    | Automated steps to build, test, and deploy code |
| **Repository (Repo)** | Storage for code with version history |
| **Sprint**      | Fixed time period (usually 2 weeks) to complete work |
| **Build Agent** | Machine that executes pipeline tasks |
| **Artifact**    | Output of a build (e.g., `.zip`, `.jar`, Docker image) |
| **Environment** | Deployment targets like Dev, Staging, Production |

---

## ✅ Summary

- DevOps improves speed, quality, and collaboration
- It bridges the gap between development and operations
- Azure DevOps provides a complete platform to implement DevOps
- Understanding CI/CD and key terms is essential before hands-on practice

---

## 📚 Next Steps

- Create Azure DevOps account
- Create a new Organization (e.g. 'AzureDevOps') 
- Create a new Project inside it (e.g. 'Day1') 
- Explore the left sidebar — you will see Boards, Repos, Pipelines, Test Plans, Artifacts
