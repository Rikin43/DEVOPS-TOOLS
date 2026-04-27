# Ansible Overview

## 📌 What is Ansible?
Ansible is an open-source automation tool used for:
- Configuration management
- Application deployment
- Infrastructure provisioning
- Orchestration

It is agentless, meaning it does not require any software installed on managed nodes.

---

## ⚙️ Key Features
- **Agentless Architecture** (uses SSH)
- **Simple YAML Syntax** (playbooks)
- **Idempotent Operations**
- **Extensible via Modules**
- **Push-based Deployment**
- **Secure (uses SSH & no extra ports)**

---

## 🏗️ Architecture

### Components:
- **Control Node**: Machine where Ansible is installed
- **Managed Nodes**: Target systems
- **Inventory**: List of managed hosts
- **Modules**: Units of work executed on nodes
- **Playbooks**: YAML files defining automation tasks

---

## 📂 Ansible Directory Structure Overview

A typical Ansible project is organized to keep configurations modular, reusable, and clean.

```
ansible-project/
├── inventory
├── playbook.yml
├── roles/
│   └── webserver/
│       ├── tasks/
│       ├── handlers/
│       ├── templates/
│       ├── files/
│       ├── vars/
│       └── defaults/
```

---

## 📁 inventory

Defines the list of managed hosts.

### Example:
```ini
[web]
192.168.1.10
192.168.1.11

[db]
192.168.1.20
```

---

## 📄 playbook.yml

Main YAML file that defines what tasks to run on which hosts.

### Example:
```yaml
- name: Configure Web Servers
  hosts: web
  become: true

  roles:
    - webserver
```

---

## 📁 roles/

Roles are reusable components that organize tasks, variables, and handlers.

---

## 📁 roles/webserver/tasks/

Contains the main list of tasks to execute.

### Example (`main.yml`):
```yaml
- name: Install Nginx
  apt:
    name: nginx
    state: present

- name: Copy config file
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
  notify: Restart nginx
```

---

## 📁 roles/webserver/handlers/

Handlers are triggered when notified by tasks.

### Example (`main.yml`):
```yaml
- name: Restart nginx
  service:
    name: nginx
    state: restarted
```

---

## 📁 roles/webserver/templates/

Contains Jinja2 template files.

### Example (`nginx.conf.j2`):
```nginx
server {
    listen 80;
    server_name {{ server_name }};

    location / {
        root /var/www/html;
        index index.html;
    }
}
```

---

## 📁 roles/webserver/files/

Static files to copy directly to managed nodes.

### Example:
```yaml
- name: Copy static HTML file
  copy:
    src: index.html
    dest: /var/www/html/index.html
```

---

## 📁 roles/webserver/vars/

Stores variables specific to the role (higher priority).

### Example (`main.yml`):
```yaml
server_name: example.com
```

---

## 📁 roles/webserver/defaults/

Default variables (lowest priority, can be overridden).

### Example (`main.yml`):
```yaml
server_name: localhost
```

---

## 🔁 How Everything Works Together

1. **Inventory** defines servers  
2. **Playbook** assigns roles to servers  
3. **Role** executes:
   - Tasks → do the work  
   - Handlers → triggered actions  
   - Templates → dynamic configs  
   - Files → static assets  
   - Vars/Defaults → configuration values  

---

## 🚀 Run the Project

```bash
ansible-playbook -i inventory playbook.yml
```

---

## 📌 Summary

- Inventory → "Where to run"
- Playbook → "What to run"
- Roles → "How it is organized"
- Tasks → "Actual work"
- Handlers → "Triggered actions"
- Templates → "Dynamic configs"
- Files → "Static content"
- Vars/Defaults → "Configuration values"

---

## 🎯 Ansible DevOps Interview Q&A

---

### ❓ 1. What is Ansible and why is it used?
**Answer:**
Ansible is an open-source automation tool used for configuration management, application deployment, and orchestration. It is agentless and uses SSH to communicate with managed nodes.

---

### ❓ 2. What is an Ansible Inventory?
**Answer:**
Inventory is a file that defines the list of managed hosts and groups.

**Example:**
```ini
[web]
192.168.1.10
192.168.1.11
```

---

### ❓ 3. What is a Playbook in Ansible?
**Answer:**
A playbook is a YAML file that defines tasks to be executed on target machines.

**Example:**
```yaml
- name: Install Nginx
  hosts: web
  become: true

  tasks:
    - name: Install package
      apt:
        name: nginx
        state: present
```

---

### ❓ 4. What are Roles in Ansible?
**Answer:**
Roles are a way to organize playbooks into reusable and modular components.

**Structure:**
```
roles/
└── webserver/
    ├── tasks/
    ├── handlers/
    ├── templates/
    ├── files/
    ├── vars/
    └── defaults/
```

---

### ❓ 5. Difference between `vars` and `defaults`?
**Answer:**
- `defaults` → Lowest priority variables (can be overridden)
- `vars` → Higher priority variables (harder to override)

---

### ❓ 6. What are Tasks?
**Answer:**
Tasks are individual units of work executed on managed nodes.

**Example:**
```yaml
- name: Install nginx
  apt:
    name: nginx
    state: present
```

---

### ❓ 7. What are Handlers?
**Answer:**
Handlers are tasks that run only when notified by another task.

**Example:**
```yaml
notify: Restart nginx
```

---

### ❓ 8. What are Templates in Ansible?
**Answer:**
Templates use Jinja2 to create dynamic configuration files.

**Example:**
```nginx
server_name {{ server_name }};
```

---

### ❓ 9. Difference between `copy` and `template` module?
**Answer:**
- `copy` → Copies static files
- `template` → Copies dynamic files with variables (Jinja2)

---

### ❓ 10. What are Modules in Ansible?
**Answer:**
Modules are reusable units of code that perform tasks like installing packages, managing services, etc.

Examples:
- `apt`
- `yum`
- `copy`
- `service`

---

### ❓ 11. What is Idempotency in Ansible?
**Answer:**
It ensures that running the same playbook multiple times will not change the system after the first successful run.

---

### ❓ 12. What is Ansible Vault?
**Answer:**
It is used to encrypt sensitive data such as passwords.

**Command:**
```bash
ansible-vault create secrets.yml
```

---

### ❓ 13. What is the difference between Ad-hoc commands and Playbooks?
**Answer:**
- Ad-hoc → One-time quick commands
- Playbooks → Reusable automation scripts

---

### ❓ 14. How does Ansible communicate with nodes?
**Answer:**
Using SSH (Linux) and WinRM (Windows).

---

### ❓ 15. What is the role of `handlers` in real scenarios?
**Answer:**
Handlers are used to restart services only when configuration changes occur, improving efficiency.

---

### ❓ 16. How do you run an Ansible Playbook?
**Answer:**
```bash
ansible-playbook -i inventory playbook.yml
```

---

### ❓ 17. What is Ansible Galaxy?
**Answer:**
A platform to share and download reusable Ansible roles.

---

### ❓ 18. What are Tags in Ansible?
**Answer:**
Tags allow running specific tasks in a playbook.

**Example:**
```bash
ansible-playbook playbook.yml --tags "install"
```

---

### ❓ 19. What is a Handler vs Task (key difference)?
**Answer:**
- Task → Runs always
- Handler → Runs only when triggered

---

### ❓ 20. Real-world use of Ansible roles?
**Answer:**
- Web server setup (Nginx/Apache)
- Database configuration
- CI/CD pipelines
- Cloud provisioning

---

## 🧠 Pro Tips for Interviews

- Always mention **agentless architecture**
- Highlight **YAML simplicity**
- Explain **idempotency clearly**
- Give **real-world examples (Nginx setup, CI/CD)**

---
