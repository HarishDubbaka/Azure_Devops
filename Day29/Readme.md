# 🚀 Azure Artifacts — Package Feeds, NuGet & npm

## 📦 What is Azure Artifacts?

Microsoft Azure Artifacts is a package management service inside Microsoft that helps teams store, manage, and share packages securely.

It allows developers to host private package feeds for technologies like:

* **NuGet** → .NET / C#
* **npm** → JavaScript / Node.js
* **Maven** → Java
* **PyPI** → Python
* **Universal Packages** → Any file type

Instead of downloading packages directly from public registries, teams can use a centralized private feed.

---

# 📚 What is a Package?

A **package** is reusable code bundled into a versioned file so multiple projects can use it.

Instead of copying code manually between projects:

✅ Create package
✅ Publish package
✅ Reuse package in many applications

Example:

```bash
MyLibrary v1.0.0
```

Projects can install and update the package whenever needed.

---

# 📦 Package Types

| Package Type           | Used For                                      |
| ---------------------- | --------------------------------------------- |
| **NuGet**              | .NET / C# packages (`.nupkg`)                 |
| **npm**                | JavaScript / Node.js packages                 |
| **Maven**              | Java packages                                 |
| **PyPI**               | Python packages                               |
| **Universal Packages** | Any file type (ZIPs, binaries, scripts, etc.) |

---

# 🗂️ What is a Feed?

A **Feed** is a private package registry inside Azure Artifacts.

Think of it like:

* Your own private npm registry
* Your own internal NuGet gallery

Teams publish packages into feeds and other applications consume them securely.

Example:

```text
TrainingFeed
CompanyPackages
InternalLibraries
```

---

# 🌐 Upstream Sources

Feeds can connect to public registries like:

* `nuget.org`
* `npmjs.com`

This is called an **Upstream Source**.

Benefits:

✅ Package caching
✅ Faster restores
✅ Security control
✅ Centralized dependency management
✅ Reduced internet dependency

Instead of developers downloading packages directly from the internet, everything flows through Azure Artifacts.

---

# 🛠️ Creating a Feed

## Steps

1. Open Azure DevOps
2. Go to **Artifacts**
3. Click **+ Create Feed**
4. Enter feed name

Example:

```text
TrainingFeed
```

5. Choose scope:

   * Project-scoped
   * Organization-scoped

6. Enable upstream sources if needed

7. Click **Create**

---

# 📤 Publishing a NuGet Package

## Step 1 — Create package

```bash
dotnet pack
```

This creates a `.nupkg` file.

---

## Step 2 — Push package to Azure Artifacts

```bash
dotnet nuget push *.nupkg --source MyFeed
```

Package is now available in the feed.

---

# 📥 Consuming Packages

Restore packages into your project:

```bash
dotnet restore
```

This downloads dependencies from the configured Azure Artifacts feed.

---

# 📦 Publishing an npm Package

```bash
npm publish --registry https://pkgs.dev.azure.com/YourOrg/_packaging/MyFeed/npm/registry/
```

Your npm package is now stored in Azure Artifacts.

---

# 🔢 Semantic Versioning (SemVer)

Package versions follow:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
2.1.3
```

---

## Version Meaning

| Version   | Meaning                          |
| --------- | -------------------------------- |
| **MAJOR** | Breaking changes                 |
| **MINOR** | New backward-compatible features |
| **PATCH** | Bug fixes only                   |

---

## Examples

| Change              | Version         |
| ------------------- | --------------- |
| Big breaking update | `1.0.0 → 2.0.0` |
| New feature         | `1.0.0 → 1.1.0` |
| Bug fix             | `1.0.0 → 1.0.1` |

---

# ⚠️ Important Best Practice

✅ Always publish a **new version**
❌ Never overwrite existing package versions

Good:

```text
1.0.0 → 1.0.1
```

Bad:

```text
Replace existing 1.0.0 package
```

---

# 🧪 Practice Task

## Day 5 Lab

Try this in Azure DevOps:

### Tasks

* Create a feed called `TrainingFeed`
* Add `nuget.org` as upstream source
* Browse available packages
* Open **Connect to Feed**
* Configure NuGet or npm locally

---

# 📝 Quick Cheat Sheet

| Term             | Meaning                    |
| ---------------- | -------------------------- |
| Azure Artifacts  | Package management service |
| Feed             | Private package registry   |
| Upstream Source  | Proxy to public registries |
| Semantic Version | MAJOR.MINOR.PATCH          |
| `dotnet pack`    | Creates NuGet package      |
| `dotnet restore` | Downloads packages         |
| `npm publish`    | Publishes npm package      |

---

# 🎯 Real-World Example

Imagine your company has:

* Shared authentication library
* Logging utility
* Common API SDK

Instead of copying code into every application:

1. Create package
2. Publish to Azure Artifacts
3. Reuse across all projects

This improves:

✅ Code reuse
✅ Version control
✅ Dependency management
✅ Team collaboration
✅ Security and governance
