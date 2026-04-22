# 📘 Version Control with Git in Azure Repos

## 📌 Overview

In this guide, you will learn how to:

* Set up a **local Git repository**
* Synchronize it with a **centralized repository in Azure DevOps**
* Understand **branching and merging in Git**
* Use **Visual Studio Code** as your Git client

Azure DevOps supports two version control systems:

* **Git** (Recommended ✅)
* **Team Foundation Version Control (TFVC)**

> Git is a **distributed version control system**, meaning every developer has a full copy of the repository locally.

---

## ⚙️ Prerequisites

Make sure you have the following installed:

* **Git 2.47.0 or later**
* **Visual Studio Code**
* **C# Extension for Visual Studio Code**

---

## 🛠️ Configure Git and Visual Studio Code

### 1. Open VS Code

* Launch **Visual Studio Code**

### 2. Open Terminal

* Go to:
  `Terminal → New Terminal`

### 3. Ensure PowerShell is Selected

* Verify terminal shows:

  ```
  1: powershell
  ```
* If not:

  * Click dropdown → **Select Default Shell**
  * Choose **Windows PowerShell**
  * Open a new terminal

---

### 4. Configure Git Credential Helper

```bash
git config --global credential.helper wincred
```

---

### 5. Configure Git Username & Email

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

> Replace with your actual name and email.

---

## 📥 Clone an Existing Repository

In this section, you'll clone the **eShopOnWeb** repository.

---

### 🔹 Step 1: Open Azure DevOps

* Navigate to your **Azure DevOps organization**
* Open the **eShopOnWeb project**

---

### 🔹 Step 2: Go to Repos

* Click **Repos** in the left navigation

---

### 🔹 Step 3: Clone Repository

* Click **Clone** (top right)
* Select **HTTPS**
* Copy the repository URL

---

### 🔹 Step 4: Open Command Palette in VS Code

* Go to:

  ```
  View → Command Palette
  ```
* Shortcut:

  ```
  Ctrl + Shift + P
  ```

---

### 🔹 Step 5: Run Git Clone

* Type:

  ```
  Git: Clone
  ```
* Paste the copied repository URL
* Press **Enter**

---

### 🔹 Step 6: Select Destination Folder

* Navigate to `C:\`
* Create a folder named:

  ```
  Git
  ```
* Select it as destination

---

### 🔹 Step 7: Authenticate

* Sign in to your **Azure DevOps account** when prompted

---

### 🔹 Step 8: Open Repository

* After cloning completes:

  * Click **Open** in VS Code

> ⚠️ Note: You may see warnings about project build issues. These can be ignored since this lab focuses only on Git operations.

---

## 🌿 Notes on Git Branching

* The **main branch** is the default branch
* All changes in this lab will be made to the **main branch**

---

## 📚 Summary

You have successfully:

* Configured Git globally
* Connected VS Code with Git
* Cloned a repository from Azure DevOps
* Prepared your environment for version control workflows

---

## 🚀 Next Steps

- 💾 **Commit Changes**: Save work with clear, descriptive commit messages  
- 🔍 **Review Commits**: Check author, time, message, and changes in Azure DevOps  
- 📜 **Review History**: Ensure accuracy, standards compliance, and no unintended changes  



