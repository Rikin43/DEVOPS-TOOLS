# 🐧 Linux Operating System – Complete Overview

> A structured guide covering essential Linux concepts, commands, and system fundamentals.

---

## 📚 Table of Contents

- [📌 What is Linux?](#-what-is-linux)
- [🧠 Key Features](#-key-features-of-linux)
- [📂 File System Overview](#-1-file-system-overview)
- [📄 File Management](#-2-file-management)
- [🔐 File Permissions](#-3-file-permissions)
- [🔍 Viewing & Editing Files](#-4-viewing--editing-files)
- [🔎 Searching & Filtering](#-5-searching--filtering)
- [📦 Package Management](#-6-package-management)
- [⚙️ Process Management](#-7-process-management)
- [🌐 Networking](#-8-networking)
- [👤 User Management](#-9-user-management)
- [🗜️ Compression & Archiving](#-10-compression--archiving)
- [📊 Disk Management](#-11-disk-management)
- [🔄 System Information](#-12-system-information)
- [🧾 Environment Variables](#-13-environment-variables)
- [🛠️ Shell & Scripting](#-14-shell--scripting)
- [🔗 Redirection & Pipes](#-15-redirection--pipes)
- [📅 Scheduling Tasks](#-16-scheduling-tasks)
- [🔒 Security Basics](#-17-security-basics)
- [🧠 Important Concepts](#-18-important-concepts)
- [🎯 Conclusion](#-conclusion)

---

## 📌 What is Linux?

Linux is an **open-source, Unix-like operating system kernel** created by Linus Torvalds in 1991. It is widely used in servers, desktops, embedded systems, and cloud environments.

---

## 🧠 Key Features of Linux

- Open Source & Free  
- Multi-user & Multitasking  
- Secure & Stable  
- Portable across hardware  
- Powerful Command Line Interface (CLI)  

---

## 📂 1. File System Overview

### 📖 Theory
Linux uses a hierarchical file system starting from root `/`.

### 🔑 Important Directories
- `/` → Root directory  
- `/home` → User files  
- `/etc` → Configuration files  
- `/var` → Logs & variable data  
- `/bin` → Essential binaries  
- `/usr` → User programs  

### 💻 Commands
```bash
pwd
ls
ls -l
ls -a
cd dir
cd ..
tree
```

---

## 📄 2. File Management

### 📖 Theory
Used to create, delete, copy, and manage files and directories.

### 💻 Commands
```bash
touch file.txt
mkdir folder
rm file.txt
rm -r folder
cp file1 file2
mv file1 file2
```

---

## 🔐 3. File Permissions

### 📖 Theory
Linux permissions include read (r), write (w), and execute (x) for user, group, and others.

### 💻 Commands
```bash
ls -l
chmod 755 file
chown user file
chgrp group file
```

---

## 🔍 4. Viewing & Editing Files

### 📖 Theory
Commands to display and modify file contents.

### 💻 Commands
```bash
cat file.txt
less file.txt
head file.txt
tail file.txt
nano file.txt
vim file.txt
```

---

## 🔎 5. Searching & Filtering

### 📖 Theory
Tools to locate files and filter content.

### 💻 Commands
```bash
find / -name file
grep "text" file
locate file
```

---

## 📦 6. Package Management

### 📖 Theory
Install, update, and remove software packages.

### 💻 Debian/Ubuntu
```bash
apt update
apt upgrade
apt install package
apt remove package
```

### 💻 RedHat/CentOS
```bash
yum install package
dnf install package
```

---

## ⚙️ 7. Process Management

### 📖 Theory
Processes are running programs managed by the OS.

### 💻 Commands
```bash
ps aux
top
htop
kill PID
kill -9 PID
```

---

## 🌐 8. Networking

### 📖 Theory
Commands to configure and troubleshoot networks.

### 💻 Commands
```bash
ifconfig
ip a
ping google.com
netstat -tuln
ss -tuln
```

---

## 👤 9. User Management

### 📖 Theory
Manage users and permissions in the system.

### 💻 Commands
```bash
adduser username
passwd username
deluser username
whoami
id
```

---

## 🗜️ 10. Compression & Archiving

### 📖 Theory
Used to compress and archive files for storage or transfer.

### 💻 Commands
```bash
tar -cvf file.tar dir
tar -xvf file.tar
gzip file
gunzip file.gz
zip file.zip file
unzip file.zip
```

---

## 📊 11. Disk Management

### 📖 Theory
Monitor and manage disk usage and storage devices.

### 💻 Commands
```bash
df -h
du -sh folder
lsblk
mount
umount
```

---

## 🔄 12. System Information

### 📖 Theory
Retrieve system-level details and performance metrics.

### 💻 Commands
```bash
uname -a
uptime
free -h
top
hostname
```

---

## 🧾 13. Environment Variables

### 📖 Theory
Variables that affect system and user processes.

### 💻 Commands
```bash
echo $PATH
export VAR=value
env
```

---

## 🛠️ 14. Shell & Scripting

### 📖 Theory
Shell interprets commands; scripting automates tasks.

### 💻 Example Script
```bash
#!/bin/bash
echo "Hello Linux"
```

### ▶️ Run Script
```bash
chmod +x script.sh
./script.sh
```

---

## 🔗 15. Redirection & Pipes

### 📖 Theory
Redirect output and chain commands.

### 💻 Commands
```bash
echo "Hello" > file.txt
cat file.txt >> file2.txt
ls | grep txt
```

---

## 📅 16. Scheduling Tasks

### 📖 Theory
Automate tasks using cron jobs.

### 💻 Commands
```bash
crontab -e
```

### ⏱️ Example
```bash
* * * * * echo "Hello"
```

---

## 🔒 17. Security Basics

### 📖 Theory
Includes permissions, firewall, and secure access.

### 💻 Commands
```bash
sudo command
ufw enable
ufw status
ssh user@host
```

---

## 🧠 18. Important Concepts

- Kernel → Core of OS  
- Shell → Command interpreter  
- CLI → Command Line Interface  
- GUI → Graphical User Interface  
- Daemons → Background services  

---

## 🎯 Conclusion

Linux is widely used in:
- Servers  
- Cloud Computing  
- Cybersecurity  
- Software Development  

Mastering Linux commands and concepts builds strong system skills 🚀
