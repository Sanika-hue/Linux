# Linux
# Week 2 - Linux System Administration & Automation

Welcome back to **90 Days of DevOps - 2025 Edition**! This week, I dived deep into the world of **Linux System Administration & Automation**, mastering crucial skills to manage and automate tasks in a Linux-based production environment. Let’s take a closer look at what I accomplished! 

---

## Project Overview: DevOps Linux Server Monitoring & Automation
This week’s project focused on **real-world DevOps scenarios**:
- Efficient user & group management
- Securing file permissions
- Advanced log file analysis
- Volume management & disk usage optimization
- Process monitoring & automation

These tasks provided a comprehensive understanding of how to maintain and automate a Linux production server. Let’s break down each task!

---

## Key Tasks & Achievements

### 1️) User & Group Management
Efficiently managing users and groups ensures robust security and access control. I:
- Created a new user `devops_user` and added them to the group `devops_team`.
- Set a strong password and granted sudo privileges.
- Secured SSH access by restricting specific users.

**Commands Executed:**
```bash
sudo useradd devops_user
sudo passwd devops_user
sudo usermod -aG devops_team devops_user
sudo visudo  # Granting sudo access
```

---

### 2️) File & Directory Permissions
Protecting sensitive data is crucial. Here’s how I did it:
- Created a secure workspace: `/devops_workspace` with `project_notes.txt`.
- Configured permissions for maximum security: Owner (edit), Group (read), Others (no access).

**Commands Executed:**
```bash
mkdir /devops_workspace
touch /devops_workspace/project_notes.txt
chmod 740 /devops_workspace/project_notes.txt
ls -l /devops_workspace
```

---

### 3️) Log File Analysis & Security
Log analysis is vital for monitoring and maintaining system security. Using **AWK**, **Grep**, and **Sed**, I:
- Extracted all occurrences of the word “error”.
- Filtered timestamps and log levels for better insights.
- Anonymized IP addresses for enhanced security.

**Commands Executed:**
```bash
grep "error" Linux_2k.log
awk '{print $1, $2}' Linux_2k.log
sed -E 's/[0-9]{1,3}(\.[0-9]{1,3}){3}/[REDACTED]/g' Linux_2k.log
```

---

### 4️) Volume Management & Disk Usage
To efficiently manage storage, I:
- Created and mounted a new volume: `/mnt/devops_data`.
- Verified successful mounting and storage usage.

**Commands Executed:**
```bash
mkdir /mnt/devops_data
mount /dev/loop0 /mnt/devops_data
df -h
mount | grep devops_data
```

---

### 5️) Process Management & Monitoring
Maintaining server performance is crucial. I:
- Started a background process (`ping google.com`).
- Monitored system health using `ps`, `top`, and `htop`.
- Safely terminated the process when no longer needed.

**Commands Executed:**
```bash
ping google.com > ping_test.log &
ps aux | grep ping
top
kill <PID>
```

---

### 6️) Automating Backups with Shell Scripting
Automation is the backbone of DevOps! I created a script to:
- Backup `/devops_workspace` as `backup_$(date +%F).tar.gz`.
- Store backups in `/backups` and notify success with green text.

**Shell Script:**
```bash
#!/bin/bash
backup_dir="/backups"
mkdir -p $backup_dir
tar -czf "$backup_dir/backup_$(date +%F).tar.gz" /devops_workspace
echo -e "\e[32mBackup Successful!\e[0m"
```

**Scheduled with Cron:**
```bash
0 2 * * * /bin/bash /path/to/backup_script.sh
```

---


- Identified the top 5 most common log messages.
- Listed files modified in the last 7 days.
- Filtered and displayed only ERROR and WARNING logs.

---

## Key Learnings
- **User Management**: Strengthens security through proper access control.
- **File Permissions**: Protects sensitive information from unauthorized access.
- **Log Analysis**: Essential for proactive monitoring and issue resolution.
- **Automation**: Saves time and minimizes human errors.

---
