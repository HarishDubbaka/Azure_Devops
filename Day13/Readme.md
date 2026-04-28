# 🌿 Git Branch Management & Azure DevOps Guide

This guide walks through **deleting branches**, **applying branch policies**, **working with pull requests**, and **tagging releases** using Azure DevOps and Visual Studio Code.

---

# 🗑️ Delete a Branch

Git allows you to work on multiple versions of code simultaneously using branches.

## 🔹 Steps to Delete a Branch

1. Open **Visual Studio Code** → Go to **Source Control**.
2. Click **Publish Changes** (next to your branch name, e.g., `dev`).
3. Open **Azure DevOps Portal** → Navigate to **Repos > Branches**.
4. In the **Mine** tab, locate the `dev` branch.
5. Hover over the branch → Click **⋯ (ellipsis)** → Select **Delete branch**.
6. Confirm deletion.

## 🔄 Verify & Restore Deleted Branch

1. Go to **All** tab in Branches.
2. Search for `dev`.
3. Check the **Deleted branches** section.
4. Click **⋯ (ellipsis)** → Select **Restore branch**.

> 💡 You can restore a deleted branch only if you know its exact name.

---

# 🔒 Branch Policies

Branch policies enforce rules before code can be merged into important branches like `main`.

## 🔹 Configure Policies on `main`

1. Go to **Repos > Branches**.
2. Hover over `main` → Click **⋯** → Select **Branch Policies**.
3. Enable:
   - ✅ Require minimum number of reviewers → Set to `1`
   - ✅ Allow requestors to approve their own changes *(for lab/demo)*
   - ✅ Check for linked work items → Set to **Required**

---

# 🧪 Test Branch Policies

1. Navigate to **Repos > Files**.
2. Ensure `main` branch is selected.
3. Open file: `/eShopOnWeb/src/Web/Program.cs`.
4. Add:
---
    ```csharp
   // Testing main branch policy
````
---
5. Click **Commit**.

🚫 You will see a warning:

> Changes to the main branch must be done via Pull Request.

6. Click **Cancel**.

---

# 🔀 Working with Pull Requests (PR)

## 🔹 Create a Work Item

1. Go to **Boards > Work Items**.
2. Click **+ New Work Item → Product Backlog Item**.
3. Title: `Testing my first PR` → Save.

## 🔹 Make Changes in `dev` Branch

1. Go to **Repos > Files** → Select `dev` branch.
2. Open `/eShopOnWeb/src/Web/Program.cs`.
3. Add:

   ```csharp
   // Testing my first PR
   ```
4. Click **Commit**.

## 🔹 Create Pull Request

1. Click **Create a Pull Request** (popup).
2. Review and click **Create**.

---

# ✅ Complete Pull Request Requirements

## 🔹 Fix Policy Checks

* 🔗 Link Work Item:

  * Click **+ Work Items** → Select created item
* 👨‍💻 Approve Changes:

  * Go to **Overview** → Click **Approve**

## 🔹 Complete Merge

1. Click **Complete**.
2. Choose:

   * Merge Type: **Merge (no fast forward)**
3. Optional:

   * ✅ Complete associated work item
4. Click **Complete Merge**

---

# 🏷️ Applying Tags

## 🔹 Create a Tag

1. Go to **Repos > Tags**.
2. Click **New Tag**.
3. Enter:

   * Name: `v1.1.0-beta`
   * Description: `Beta release v1.1.0`
4. Click **Create**

> 📌 Tags mark specific commits (useful for releases).

---

# ❌ Remove Branch Policies

1. Go to **Repos > Branches**.
2. Hover over `main` → Click **⋯** → **Branch Policies**.
3. Disable:

   * ❌ Require minimum reviewers
   * ❌ Check for linked work items

---

# 🧹 Clean Up Resources

Azure DevOps projects remain available for reuse.

## 🔹 Delete Project (Optional)

1. Go to: [https://aex.dev.azure.com](https://aex.dev.azure.com)
2. Open your project (`eShopOnWeb`).
3. Navigate to **Project Settings > Overview**.
4. Click **Delete**.
5. Enter project name → Confirm.

⚠️ **Warning**: Deleting a project removes:

* Work items
* Repositories
* Pipelines
* All associated data

---

# 🎯 Summary

* 🌿 Branches allow parallel development
* 🗑️ Deleted branches can be restored
* 🔒 Policies enforce code quality
* 🔀 Pull Requests enable safe merging
* 🏷️ Tags help manage releases
* 🧹 Cleanup keeps environment organized

---

🚀 **Best Practice**: Always use Pull Requests with policies for production branches!


