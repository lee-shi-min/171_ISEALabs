# Lab 3b: Automation and Cron Jobs

**Student Name:** LEE SHI MIN  
**Student ID:** 35702683  
**Date:** 17 June 2026

---

## Part 1: Bash Scripting and Cron Jobs

### System Health Check Script

I created a bash script called `system_health.sh` that performs daily system checks including disk usage, memory usage, and Apache service status.

### Script Code

```bash
#!/bin/bash
# System Health Check Script for ISEA Assignment

LOG_FILE="/var/log/system_health.log"
DATE=$(date '+%Y-%m-%d %H:%M:%S')

echo "========================================" >> $LOG_FILE
echo "System Health Check - $DATE" >> $LOG_FILE
echo "========================================" >> $LOG_FILE

echo "Disk Usage:" >> $LOG_FILE
df -h / >> $LOG_FILE
echo "" >> $LOG_FILE

echo "Memory Usage:" >> $LOG_FILE
free -h >> $LOG_FILE
echo "" >> $LOG_FILE

echo "Apache Status:" >> $LOG_FILE
systemctl is-active apache2 >> $LOG_FILE
echo "" >> $LOG_FILE

echo "Health check completed." >> $LOG_FILE
```

### Script Output:
```bash
========================================
System Health Check - 2026-06-07 08:03:51
========================================
Disk Usage:
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        49G   19G   30G  39% /

Memory Usage:
Mem:    3.3Gi    1.3Gi    472Mi    3.2Mi    314Mi    568Mi
```
### Apache Status:
active

### Health check completed.
```
Cron Job Setup
I scheduled the script to run automatically every day at 2:00 AM using cron.
```
### Crontab entry:
```bash
sudo crontab -l
0 2 * * * /usr/local/bin/system_health.sh
```
### Verification
```bash
sudo crontab -l
0 2 * * * /usr/local/bin/system_health.sh
```

---
### Part 2: Additional Server Service (MariaDB)
As my additional server service, I installed and configured MariaDB (a popular open-source relational database management system).

Installation Steps:
```bash
# Install MariaDB
sudo apt install mariadb-server -y

# Check status
sudo systemctl status mariadb
# Active: active (running)

# Secure installation
sudo mariadb-secure-installation
# - Set root password
# - Removed anonymous users
# - Disabled remote root login
# - Removed test database

# Test login
sudo mysql -u root -p
```
### Database Verification:
```bash
SHOW DATABASE;
```
|Database            |
|:---|
|information schema  |
|mysql               |
|performance         |
|sys                 |

Screenshots
All screenshots for this lab are located in the screenshots/ folder.

|Figure	     |Description                                        | 
|:---|:---|
|Figure 3b-1	 |System health check script code                  |
|Figure 3b-2	 |Script output (disk, memory, Apache status)      |
|Figure 3b-3	 |Cron job list (sudo crontab -l)                  |
|Figure 3b-4	 |MariaDB version (mariadb --version)              |
|Figure 3b-5	 |MariaDB service status (systemctl status mariadb)|
|Figure 3b-6	 |MariaDB login and SHOW DATABASES; output         |


### Reflection Questions
1. Why is using absolute paths important in scripts run by cron?

Cron runs with a minimal environment and does NOT load your user's shell profile (like .bashrc). It has a very limited PATH variable. Using absolute paths (e.g., /usr/bin/df instead of just df) ensures that cron can find the commands even though its environment is different from your interactive shell. Without absolute paths, cron jobs may fail silently.

2. What are the benefits of cloud exporting for backups?

- Offsite storage: Protects against local hardware failure, fire, or theft
- Disaster recovery: Backups are accessible from anywhere
- Automation: Can be scheduled with cron for regular, unattended backups
- Cost-effective: Pay only for storage used (e.g., AWS S3 charges ~$0.023 per GB per month)
- Versioning: Many cloud storage services keep file history

3. How does cron differ from manual execution?

|Aspect	      | Manual Execution	Cron Execution                          |
|:---|:---|
|Trigger      |	User runs command manually	Automatic based on schedule   |
|Environment	| User's full environment	Minimal environment (limited PATH)|
|Output	      | Visible in terminal	Logged to file or emailed             |
|Reliability	| Depends on user remembering	Runs consistently             |

4. What happens if SSH keys are not accepted ahead of time?

When you first connect to a server via SSH, you are prompted to accept the host key fingerprint. For automated scripts (e.g., scp in a cron job), this prompt causes the command to hang or fail because there is no user to type "yes". The solution is to manually connect once as the user running the cron job to accept the key, or use ssh-keyscan to pre-add the key.

5. Why is file compression important in server contexts?

- Saves storage space: Compressed files take up significantly less disk space
- Reduces transfer time: Smaller files transfer faster over networks
- Reduces bandwidth costs: Less data transferred = lower cloud egress charges
- Archiving: Multiple files can be combined into one archive (e.g., tar + bzip2)

6. What are the risks of adding users to the sudo group?
Users in the sudo group can execute commands as root, which gives them full system access. Risks include:

- Deleting critical system files
- Accessing other users' data
- Installing malicious software
- Changing system configurations
- Bypassing all file permission restrictions

Best practice: Only grant sudo access when absolutely necessary, and use the principle of least privilege.

7. What did you learn about Linux permissions?

I learned that Linux uses a simple but effective permission model with three categories:

|Category   |Symbol	|Example|
|:---|:---|
|Owner (u)	|rwx	  |Full control over own files   |
|Group (g)	|r-x	  |Shared access for team members|
|Others (o)	|---	  |No access for strangers       |

---

Commands like chmod 755 filename set permissions numerically:

- 7 (rwx) for owner
- 5 (r-x) for group
- 5 (r-x) for others
  
--- 

Commands Used in This Lab:

|Command	                                    |Purpose                    |
|:---|:---|
|sudo nano /usr/local/bin/system_health.sh	  |Create the script          |
|sudo chmod +x /usr/local/bin/system_health.sh|	Make script executable    |
|sudo /usr/local/bin/system_health.sh	        |Run script manually        |
|sudo cat /var/log/system_health.log	        |View script output         |
|sudo crontab -e	                            |Edit cron jobs             | 
|sudo crontab -l	                            |List cron jobs             |
|sudo apt install mariadb-server -y	          |Install MariaDB            |
|sudo systemctl status mariadb	              |Check MariaDB status       |
|sudo mariadb-secure-installation	            |Secure MariaDB             |
|sudo mysql -u root -p	                      |Login to MariaDB           |
|SHOW DATABASES;	                            |List databases             |

### Conclusion
Lab 3b successfully demonstrated essential Linux server automation skills:

1. Bash scripting for system health monitoring
2. Cron jobs for scheduled task automation
3. MariaDB installation and basic database management
4. Log file management for tracking script execution

These skills are fundamental for system administration and DevOps roles, where automation and monitoring are critical for maintaining reliable server infrastructure.


---

## Step-by-Step: Create Lab 3b on GitHub

### Step 1: Create the `Lab3b/` folder

1. Go to: `https://github.com/lee-shi-min/171_ISEALabs`
2. Click **"Add file"** → **"Create new file"**
3. Name: `Lab3b/lab3b-reflection.md`
4. Click **"Commit changes"**

### Step 2: Create the `screenshots/` folder

1. Click into `Lab3b/` folder
2. Click **"Add file"** → **"Create new file"**
3. Name: `screenshots/.gitkeep`
4. Click **"Commit changes"**

### Step 3: Copy the reflection content

1. Click into `Lab3b/` folder
2. Click on `lab3b-reflection.md`
3. Click the pencil icon (✏️) to edit
4. Paste the content above
5. Click **"Commit changes""

### Step 4: Upload screenshots

Copy screenshots from your assignment (Figures 6a, 6b, 6c, 7a-7e) to `Lab3b/screenshots/`.

Rename them as:

| Figure in Lab 3b | Original from assignment | New filename |
| :--- | :--- | :--- |
| Figure 3b-1 | script code | `3b-1-script-code.png` |
| Figure 3b-2 | script output | `3b-2-script-output.png` |
| Figure 3b-3 | cron job  `3b-3-cron-job.png` |
| Figure 3b-4 | MariaDB version | `3b-4-mariadb-version.png` |
| Figure 3b-5 | MariaDB status | `3b-5-mariadb-status.png` |
| Figure 3b-6 | SHOW DATABASES | `3b-6-mariadb-databases.png` |

---

Figure 3b-1: script code 
Figure 3b-2: script output 
Figure 3b-3: cron job  
Figure 3b-4: MariaDB version 
Figure 3b-5: MariaDB status 
Figure 3b-6: SHOW DATABASES















