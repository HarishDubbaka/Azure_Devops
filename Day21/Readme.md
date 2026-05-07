# 📘 Day 07 – Introduction to YAML in Azure DevOps

## 1️⃣ What is YAML?

**YAML** stands for **Yet Another Markup Language** (or **YAML Ain’t Markup Language**).

It is a **human-readable configuration language** used to define settings and automation workflows.

In Azure DevOps, YAML is used to create **Pipelines as Code**, which means your CI/CD pipeline configuration is stored directly inside your repository.

### ✅ Why YAML is Important in Azure DevOps

* Easy to read and write
* Version-controlled with source code
* Reusable and maintainable
* Enables CI/CD automation

---

# 2️⃣ YAML Rules — CRITICAL

## ✅ YAML Formatting Rules

| Rule                 | Description               |
| -------------------- | ------------------------- |
| Spaces only          | NEVER use tabs            |
| Standard indentation | 2 spaces per level        |
| Case-sensitive       | `name` ≠ `Name`           |
| Lists                | Use `-` followed by space |
| Key-value pairs      | `key: value`              |
| Comments             | Start with `#`            |
| Special characters   | Use quotes                |

---

## ✅ Correct Examples

### Key-Value Pair

```yaml
name: MyPipeline
version: 1
enabled: true
```

---

### List Example

```yaml
fruits:
  - apple
  - banana
  - mango
```

---

### Nested Object

```yaml
server:
  host: localhost
  port: 8080
  secure: false
```

---

### Multi-line String

```yaml
script: |
  echo Hello
  echo World
```

---

# 3️⃣ Azure Pipeline YAML Structure

## Basic Azure Pipeline

```yaml
trigger:
  - main

pool:
  vmImage: ubuntu-latest

stages:
  - stage: Build
    jobs:
      - job: BuildJob
        steps:
          - script: echo Hello World
            displayName: Print hello
```

---

# 4️⃣ YAML Hierarchy in Azure Pipelines

| Component | Description                     |
| --------- | ------------------------------- |
| Pipeline  | Complete workflow               |
| Stage     | Major phase (Build/Test/Deploy) |
| Job       | Unit of work inside stage       |
| Step      | Single action                   |
| Task      | Prebuilt Azure DevOps action    |
| Script    | Command-line execution          |

---

# 5️⃣ Understanding Pipeline Flow

```text
Pipeline
 └── Stage
      └── Job
           └── Step
                └── Task / Script
```

---

# 6️⃣ Common YAML Mistakes

| Mistake                     | Problem             |
| --------------------------- | ------------------- |
| Using tabs                  | YAML parsing error  |
| Wrong indentation           | Invalid hierarchy   |
| Missing space after colon   | `key:value` invalid |
| Unquoted strings with colon | Parsing failure     |

---

## ❌ Incorrect Example

```yaml
message: Hello: World
```

## ✅ Correct Example

```yaml
message: "Hello: World"
```

---

# 7️⃣ Practice Task – Day 07

## ✍️ Task 1: Create Your Own YAML File

Open VS Code or Notepad and create:

```yaml
name: Harish Dubbaka
age: 28

skills:
  - Azure DevOps
  - Docker
  - Git
  - SAP
  - YAML

address:
  city: Chennai
  state: Tamil Nadu
  country: India
```

---

## ✍️ Task 2: Validate YAML

Use:

[YAML Lint Validator] (https://www.yamllint.com?utm_source=chatgpt.com)

Paste your YAML and validate formatting.

---

## ✍️ Task 3: Explore Azure DevOps Starter Pipeline

Go to:

1. Azure DevOps
2. Pipelines
3. New Pipeline
4. Select repository
5. View starter YAML pipeline

---

# 🎯 Key Takeaways

✅ YAML is the foundation of Azure DevOps pipelines

✅ Indentation and spacing are extremely important

✅ Pipelines are written as code using YAML

✅ Understanding stages, jobs, and steps is critical for CI/CD

---

# 🚀 What’s Next?

Lab Flow: Configure Pipelines as Code with YAML 

