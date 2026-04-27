# Jenkins – Complete Guide (Overview, CI/CD, Pros & Cons, Alternatives)

## 1. What is Jenkins?

**Jenkins** is an open-source automation server used to implement Continuous Integration (CI) and Continuous Delivery/Deployment (CD) pipelines.

- Building applications
- Running tests
- Performing static code analysis
- Deploying applications

Jenkins works using a master–agent architecture and supports thousands of plugins to integrate with almost every DevOps tool.

Jenkins is written in **Java** and is extensible via **plugins**.

---
## 2. Why Jenkins is Used in Industry

In real-world software development:
- Developers commit code frequently
- Teams want fast feedback
- Releases must be reliable and repeatable

Jenkins helps by:
- Automatically triggering builds on code changes
- Detecting bugs early
- Reducing manual deployment errors
- Supporting DevOps practices

---
## 3. Advantages & Disadvantages of Jenkins

### ✅ Advantages of Jenkins

- Open-source and free
- Huge plugin ecosystem
- Supports CI and CD
- Works with any programming language
- Integrates with Git, GitHub, Docker, Kubernetes, AWS, Azure
- Highly customizable
- Strong community support
- Supports pipeline as code (Jenkinsfile)

---

### ❌ Disadvantages of Jenkins

- Initial setup is complex
- Requires regular maintenance
- Plugin compatibility issues
- UI is outdated
- Not cloud-native by default
- Scaling is manual
- Security misconfiguration risks

---
## 4. Jenkins Architecture

### Core Components

- **Jenkins Controller (Master)**
  - Manages jobs, pipelines, UI, and plugins
  - Schedules jobs on agents

- **Jenkins Agents (Workers/Slaves)**
  - Execute jobs (build, test, deploy)
  - Can run on Linux, Windows, Docker, Kubernetes, Cloud VMs

### Key Concepts

- **Job / Project** – A task Jenkins executes
- **Pipeline** – Code-based workflow (CI/CD)
- **Plugin** – Extends Jenkins functionality
- **Workspace** – Directory where job runs

---
## 5. Jenkins Alternatives

| Tool | Type | Best Use Case |
|---|---|---|
| GitHub Actions | Cloud-native | GitHub projects |
| GitLab CI/CD | Built-in | GitLab repositories |
| CircleCI | Cloud | Fast CI pipelines |
| Travis CI | Cloud | Open-source projects |
| Azure DevOps | Enterprise | Microsoft ecosystem |
| Bamboo | On-prem | Atlassian tools |
| TeamCity | Enterprise | Large teams |

---
## 6. Jenkins CI/CD Workflow (Real-Time Industry Example)

### Example: Web Application Deployment

#### Step-by-Step Workflow

1. **Developer pushes code**
   - GitHub / GitLab / Bitbucket

2. **Webhook triggers Jenkins**
   - Jenkins detects code change

3. **Build Stage**
   - Compile code
   - Install dependencies

4. **Test Stage**
   - Unit tests
   - Integration tests

5. **Code Quality & Security**
   - SonarQube scan
   - Dependency vulnerability scan

6. **Package Artifact**
   - Create JAR / WAR / Docker image

7. **Deploy to Environment**
   - Dev / QA / Staging
   - Kubernetes / VM / Cloud

8. **Approval (Optional)**
   - Manual approval for production

9. **Production Deployment**
   - Blue-Green / Rolling / Canary

10. **Monitoring & Notification**
    - Slack / Email alerts
    - Rollback on failure

---
# 7. Jenkins Pipeline Overview (Detailed)

## What is Jenkins Pipeline?

A **Jenkins Pipeline** is a code-based CI/CD workflow defined using a `Jenkinsfile`.

## Benefits

- **Version controlled**
- **Reusable**
- **Easy rollback**
- **Automated CI/CD**

---
## 8. Jenkins Pipeline Types

### 1. Declarative Pipeline (Recommended)

- Easier to read
- Less error-prone
- Structured syntax

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```
---

### 2. Scripted Pipeline

- More flexible
- Written in Groovy
- Used for complex logic

```groovy
node {
    stage('Build') {
        echo 'Building...'
    }
    stage('Test') {
        echo 'Testing...'
    }
}
```
---
## 9. How to Create Your First Jenkins Job (Step-by-Step)

### Step 1: Login to Jenkins
- Open browser → `http://localhost:8080`
- Login using admin credentials

### Step 2: Create Job
- Click **New Item**
- Enter job name
- Select **Freestyle Project**
- Click **OK**

### Step 3: Configure Job
- Add description (optional)
- Go to **Build Steps**
- Select **Execute Shell**
- Add command:
```bash
echo "Hello Jenkins"
```

### Step 4: Save & Build

- Click Save
- Click Build Now
- Check Console Output
---

## 10. Scheduling Jenkins Jobs (CRON Jobs)

Jenkins allows scheduling jobs using **CRON expressions**.

### Step-by-Step: Schedule a Jenkins Job

1. Open Jenkins dashboard
2. Select your job
3. Click **Configure**
4. Go to **Build Triggers**
5. Enable **Build periodically**
6. Enter CRON schedule
7. Click **Save**

### CRON Syntax Format
```text
MIN HOUR DAY MONTH DAY-OF-WEEK
H/5 * * * *
```

## Common CRON Examples

| CRON Expression       | Meaning                 |
|-----------------|-------------------------|
| `H/5 * * * *`   | Every 5 minutes         |
| `0 0 * * *`     | Daily at midnight       |
| `0 9 * * 1-5`   | Weekdays at 9 AM        |
| `@hourly`       | Every hour              |
---

## 11. How to Pull Code from GitHub & Run in Jenkins

## Step-by-Step GitHub Integration

### Step 1: Install Git Plugin
- Manage Jenkins → Plugins → Install **Git Plugin**

### Step 2: Create Jenkins Job
- New Item → **Freestyle Project**

### Step 3: Configure GitHub Repo
- Go to **Source Code Management**
- Select **Git**
- Add Repository URL: https://github.com/username/repository.git

### Step 4: Add Credentials (If Private Repo)
- Add GitHub **username** & **token**

### Step 5: Add Build Step
```bash
ls -la
```

### Step 6: Save & Build
- Click Build Now
- Code will be pulled into Jenkins workspace
 ---
 
## 12. GitHub Auto Build Workflow (Webhook)

GitHub Webhooks trigger Jenkins automatically when code is pushed.

## Auto Build Workflow

1. Developer pushes code to GitHub  
2. GitHub sends webhook event  
3. Jenkins receives webhook  
4. Jenkins pulls latest code  
5. Jenkins runs build/test pipeline  
6. Jenkins sends notifications  

## Step-by-Step Webhook Setup

### In Jenkins

1. Open job → **Configure**  
2. Go to **Build Triggers**  
3. Enable **GitHub hook trigger for GITScm polling**  
4. Click **Save**

### In GitHub

1. Go to **Repository → Settings → Webhooks**  
2. Click **Add Webhook**  
3. Set **Payload URL**: http://<jenkins-url>/github-webhook/
4. Set **Content type**: `application/json`  
5. Select **Event**: `Push`  
6. Click **Save webhook**
---

## 13. Jenkins Email Notification Setup (Step-by-Step)

## Step 1: Install Email Plugin
- Manage Jenkins → Plugins  
- Install **Email Extension Plugin**

## Step 2: Configure SMTP Server
- Manage Jenkins → Configure System  
- Email Notification settings:
  - **SMTP Server**: `smtp.gmail.com`
  - **Port**: `465`
  - **Use SSL**: Yes  
- Add email credentials

## Step 3: Configure Job Email Notification
- Job → Configure  
- Go to **Post-build Actions**  
- Select **Editable Email Notification**  
- Add:
  - **Recipients**: `team@example.com`
  - **Triggers**: Failure, Success
---

## 14. Jenkins User Management & Role Assignment

## Step 1: Enable Security
- Manage Jenkins → Security  
- Enable **Jenkins Own User Database**  
- Authorization: **Role-Based Strategy**

## Step 2: Install Role Strategy Plugin
- Manage Jenkins → Plugins  
- Install **Role-based Authorization Strategy**

## Step 3: Create Users
- Manage Jenkins → Users  
- Click **Create User**  
- Provide **username**, **password**, and **email**

## Step 4: Create Roles
- Manage Jenkins → **Manage and Assign Roles**  
- Create roles:
  - `admin`
  - `developer`
  - `viewer`

## Step 5: Assign Permissions

| Role      | Permissions        |
|-----------|--------------------|
| Admin     | All permissions    |
| Developer | Build, Read        |
| Viewer    | Read-only          |

## Step 6: Assign Users to Roles
- Assign users to appropriate roles  
- Click **Save** changes
---






   
