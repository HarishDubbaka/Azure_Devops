# 🚀 Understanding Azure DevOps Pipelines 

## 🔷 Overview

When we want to **build code, run applications, or deploy Infrastructure as Code (IaC)** in an automated way, we need a compute environment to execute those commands.

This is where **Azure DevOps Pipelines** come in.

Pipelines enable us to:

* Integrate with source control
* Trigger automation based on events
* Execute CLI commands
* Perform security scanning
* Automate build, test, and deployment workflows

---

# ⚙️ Agent Hosting Options

Azure DevOps provides two main options to run pipelines:

## 1️⃣ Microsoft-Hosted Agents

* Managed by Azure
* Pre-configured virtual machines
* No setup required
* Free tier available (limited usage)

## 2️⃣ Self-Hosted Agents

* Hosted on your own infrastructure
* Full control over environment
* Useful for:

  * Custom tools and dependencies
  * Private network access
  * Compliance requirements

👉 These agents act as the **compute layer** where pipeline jobs and tasks are executed.

---

# 🧩 Pipeline Architecture

An Azure DevOps pipeline is structured as:

```text
Pipeline → Stages → Jobs → Steps
```

---

# 🔁 Pipeline Flow Diagram

![Alt Text](https://github.com/HarishDubbaka/Azure_Devops/blob/0439f0ea164146a7c056241fe6cd1a4b92837638/Day14/pipeline.jpg)


```text
        ┌──────────────┐
        │   TRIGGER    │
        │ (Code Push / │
        │  Manual Run) │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │   PIPELINE   │
        │ (Full Flow)  │
        └──────┬───────┘
               │
     ┌─────────┼─────────┐
     ▼         ▼         ▼
┌────────┐ ┌────────┐ ┌────────┐
│ Stage  │ │ Stage  │ │ Stage  │
│ Build  │ │ Test   │ │ Deploy │
└───┬────┘ └───┬────┘ └───┬────┘
    │           │           │
    ▼           ▼           ▼
┌────────┐ ┌────────┐ ┌────────┐
│  Job   │ │  Job   │ │  Job   │
│ Agent  │ │ Agent  │ │ Agent  │
└───┬────┘ └───┬────┘ └───┬────┘
    │           │           │
    ▼           ▼           ▼
┌────────┐ ┌────────┐ ┌──────────────┐
│ Steps  │ │ Steps  │ │ Steps        │
│ Script │ │ Test   │ │ Deploy Task  │
│ Task   │ │ Task   │ │ Azure CLI    │
└────────┘ └────────┘ └──────────────┘
```

---

# 🟡 1. Trigger (Start Point)

Defines **when the pipeline runs**.

### Examples:

* Code push (CI trigger)
* Pull request
* Manual execution
* Scheduled runs

👉 Without a trigger, the pipeline will not start.

---

# 🔵 2. Pipeline

The **complete automation workflow**.

### Example:

```text
Pipeline
 ├── Build Stage
 ├── Test Stage
 └── Deploy Stage
```

👉 Pipeline = End-to-end automation

---

# 🟣 3. Stages

Stages represent **high-level phases** of execution.

### Common stages:

* **Build** → Compile code
* **Test** → Run validations
* **Deploy** → Release application

👉 Stages typically run **sequentially** (but can be configured to run in parallel).

---

# ⚙️ 4. Jobs

* A **job** is a unit of work within a stage
* Each job runs on a **single agent**

### Key points:

* 1 Job = 1 Agent
* Jobs can run in parallel (if multiple agents are available)
* Jobs can depend on other jobs

---

# 💻 5. Agents

Agents are the **execution environments** where jobs run.

### Types:

* Microsoft-hosted (cloud-managed)
* Self-hosted (user-managed)

👉 Agent = Machine that executes pipeline tasks

---

# 🧩 6. Steps

Steps are the **individual actions** performed within a job.

### Types:

* **Script** → Bash / PowerShell commands
* **Task** → Prebuilt actions (e.g., `AzureCLI@2`)

### Examples:

* Install dependencies
* Build application
* Run tests
* Deploy resources
* Call REST APIs

---

# 🔗 7. Dependencies

Dependencies control the **execution order**.

```text
Job A → Job B → Job C
```

* Job B runs only after Job A succeeds

👉 Ensures a safe and logical execution flow

---

# ⚠️ Concurrency & Parallel Jobs

This is a **critical concept** in Azure DevOps:

* Free tier includes:

  * **1 parallel job**
  * **1,800 minutes/month**
* Only **one job runs at a time**

### Need parallel execution?

👉 You must **purchase additional parallel jobs (concurrency)**

---

# 🔄 End-to-End Example

### Scenario: Code Push

1. Developer pushes code
2. Trigger starts the pipeline
3. **Build Stage**

   * Install dependencies
   * Compile code
   * Publish artifacts
4. **Test Stage**

   * Run test cases
5. **Deploy Stage**

   * Deploy using CLI or tasks

---

# 🔁 Comparison with GitHub

* GitHub provides **free runners for public repositories**
* Azure DevOps primarily uses **private projects**
* Parallel job limits apply differently compared to GitHub

---

# 🧠 Quick Memory Trick

```text
Trigger → Pipeline → Stage → Job → Step → Output
```

---

# 🔥 Key Takeaways

* Pipeline = Full automation workflow
* Stage = Major phase
* Job = Execution unit
* Agent = Machine running the job
* Step = Individual command/task
* Concurrency = Ability to run jobs in parallel

---

# 🔷 Agent vs Agent Pool

## 💻 Agent (Single Machine)

An **Agent** is:

* A machine (VM, server, or container)
* Executes pipeline jobs and steps
* Can be Microsoft-hosted or self-hosted

👉 **1 Agent executes 1 job at a time**

---

## 🏊 Agent Pool (Collection of Agents)

An **Agent Pool** is:

* A group of agents
* Used to manage and organize compute resources
* Pipelines select an available agent from the pool

```text
Agent Pool = Collection of Agents
```

---

# 🔁 Simple Analogy

```text
Agent       = Worker 👷
Agent Pool  = Team of Workers 👷👷👷
```

* One worker handles one task
* A team enables parallel execution

---

# 🔄 How They Work Together

```text
Pipeline → Job → Agent Pool → Agent → Steps
```

### Flow:

1. Pipeline starts
2. Job is triggered
3. Job requests an agent from the pool
4. Azure DevOps assigns an available agent
5. Steps execute on that agent

---

## 📌 Summary

Azure DevOps Pipelines provide a **scalable and automated solution** to build, test, and deploy applications. By leveraging stages, jobs, steps, and agents, teams can efficiently manage CI/CD workflows with flexibility and control.



Next Learning Phase
In the next learning phase, I will complete the below labs. Through these, you will learn how to:

Create an Agent Pool
Download and configure a Self-Hosted Agent
Generate a Personal Access Token (PAT)
Connect the agent to Azure DevOps
Author a YAML-based pipeline
---

