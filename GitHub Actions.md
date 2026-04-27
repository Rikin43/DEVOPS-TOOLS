# 🚀 GitHub Actions – Complete Overview

## 📌 What is GitHub Actions?

**GitHub Actions** is an automation platform built into GitHub that allows you to:

* Build, test, and deploy code automatically
* Run workflows based on repository events
* Create full CI/CD pipelines

👉 Think: **“When something happens → run automation.”**

---

## 🧩 Core Concepts

### 1. Workflows

A **workflow** is an automated process defined in a YAML file.

* Location: `.github/workflows/`
* A repo can have multiple workflows

```yaml
name: CI Pipeline
```

---

### 2. Events (Triggers)

Events determine **when workflows run**.

Common events:

* `push`
* `pull_request`
* `workflow_dispatch` (manual)
* `schedule` (cron jobs)
* `release`

```yaml
on: [push, pull_request]
```

---

### 3. Jobs

A workflow contains one or more **jobs**.

* Run in parallel by default
* Can depend on other jobs

```yaml
jobs:
  build:
  test:
```

---

### 4. Runners

A **runner** is the machine that executes jobs.

Types:

* GitHub-hosted (Ubuntu, Windows, macOS)
* Self-hosted (your own machine)

```yaml
runs-on: ubuntu-latest
```

---

### 5. Steps

Each job consists of **steps**.

```yaml
steps:
  - name: Checkout code
  - name: Install dependencies
  - name: Run tests
```

---

### 6. Actions

Reusable components that perform tasks.

```yaml
uses: actions/checkout@v4
```

👉 Think: **Plugins for workflows**

---

## ⚙️ Complete Workflow Example

```yaml
name: Node CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

---

## 🔁 Job Dependencies

```yaml
jobs:
  build:
  test:
    needs: build
```

👉 `test` runs after `build`

---

## 🔐 Secrets & Environment Variables

### Secrets

Stored securely in repository settings.

```yaml
env:
  API_KEY: ${{ secrets.API_KEY }}
```

### Variables

```yaml
env:
  NODE_ENV: production
```

---

## 📦 Artifacts

Store files between jobs.

```yaml
- uses: actions/upload-artifact@v4
```

Use cases:

* Build outputs
* Logs

---

## 🧪 Matrix Builds

Run jobs across multiple configurations.

```yaml
strategy:
  matrix:
    node-version: [16, 18, 20]
```

---

## ⏱️ Scheduling (Cron Jobs)

```yaml
on:
  schedule:
    - cron: "0 0 * * *"
```

---

## 🔄 Reusable Workflows

```yaml
uses: org/repo/.github/workflows/reusable.yml@main
```

---

## 📥 Inputs & Outputs

### Inputs (Manual trigger)

```yaml
on:
  workflow_dispatch:
    inputs:
      version:
```

### Outputs

```yaml
outputs:
  result: ${{ steps.step1.outputs.value }}
```

---

## 🧠 Expressions & Contexts

```yaml
${{ github.ref }}
${{ runner.os }}
${{ secrets.KEY }}
```

Common contexts:

* `github`
* `env`
* `job`
* `steps`

---

## 🛑 Conditional Execution

```yaml
if: github.ref == 'refs/heads/main'
```

---

## 🚀 Common Use Cases

### CI (Continuous Integration)

* Run tests on every push

### CD (Continuous Deployment)

* Deploy applications automatically

### Automation

* Auto-label PRs
* Auto-merge
* Dependency updates

---

## 🧰 Popular Built-in Actions

* `actions/checkout` → clone repo
* `actions/setup-node` → setup Node.js
* `actions/cache` → cache dependencies
* `actions/upload-artifact` → store files

---

## 🏗️ Advanced Features

### 1. Caching

```yaml
uses: actions/cache@v4
```

---

### 2. Services

```yaml
services:
  postgres:
    image: postgres
```

---

### 3. Self-hosted Runners

* More control
* Custom environments

---

### 4. Composite Actions

Reusable custom actions built by you.

---

## ⚠️ Common Pitfalls

* YAML indentation errors
* Secrets exposed in logs
* Missing job dependencies
* No caching → slow builds

---

## 🧭 Mental Model

```
Event → Workflow → Jobs → Steps → Actions
```

---

## ✅ Summary

GitHub Actions is:

* Event-driven automation
* YAML-based pipelines
* Modular and reusable
* Suitable for CI/CD and beyond

---
