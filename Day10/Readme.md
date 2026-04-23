# 🚀 Git Commits, Staging & History in Azure DevOps

## 📌 Overview

This lab demonstrates how to:

* ✅ Save work using Git commits
* ✅ Stage specific changes
* ✅ Review commit history in Azure DevOps

---

## 🧪 Exercise 1: Save Work with Commits

### 🔹 Steps

1. Open `Program.cs` in VS Code
2. Add a comment:

   ```csharp
   // My first change
   ```
3. Save the file (`Ctrl + S`)
4. Go to **Source Control**
5. Enter a commit message:

   ```
   My commit
   ```
6. Press `Ctrl + Enter` to commit
7. Click **Synchronize Changes** to push

---

## 🧪 Exercise 2: Review Commits

### 🔹 Steps

1. Open Azure DevOps Portal
2. Navigate to **Repos → Commits**
3. Verify your commit appears at the top

---

## 🧪 Exercise 3: Stage Changes

### 🔹 Steps

1. Update `Program.cs`:

   ```csharp
   // My second change
   ```
2. Open `Constants.cs` and add:

   ```csharp
   // My third change
   ```
3. Go to **Source Control**
4. Stage only `Program.cs` (click ➕)
5. Enter commit message:

   ```
   Added comments
   ```
6. Click **Commit Staged**
7. Click **Synchronize Changes**

📌 **Note:** Only staged files are committed. Other changes remain pending.

---

## 🧪 Exercise 4: Review History

### 🔹 Key Concepts

* 📌 Git tracks history using **parent commits**
* 🔀 History may not be linear due to **branches & merges**
* 🔍 Compare changes between commits instead of relying on time

---

## 🔍 Task: Compare Files

### 🔹 Steps

1. In VS Code, open `Constants.cs` to view changes
2. In Azure DevOps:

   * Go to **Repos → Commits**
   * Select a commit
   * Click **Browse Files**

📌 This shows the exact repository state at that specific commit.

---

## ✅ Key Takeaways

* 🧠 Commits capture snapshots of your work
* 🎯 Staging enables selective commits
* 📜 History helps track and compare changes
* 🌐 Azure DevOps provides a visual commit history

