# 171_ISEALabs - Introduction to Server Environments and Architecture

**Student:** Lee Shi Min  
**Student ID:** 35702683  
**Course:** ISEA (ICT171)  
**Date:** June 2026

---

## 📚 About This Repository

This repository contains all my lab work and assignments for the **Introduction to Server Environments and Architecture (ISEA)** course. It documents my hands-on experience with:

- Linux server administration (Ubuntu)
- Virtualisation (VMware)
- Cloud computing (AWS EC2)
- Web server configuration (Apache2)
- DNS and SSL/TLS (Let's Encrypt)
- Database management (MariaDB)
- Automation (Bash scripting and Cron jobs)
- Version control (Git and GitHub)

---

## 📁 Repository Structure
171_ISEALabs/
├── README.md # This file
├── Lab1a/ # Virtualisation and Linux Setup
│ ├── lab1a-reflection.md
│ └── screenshots/
├── Lab1b/ # Linux Services, SSH, Permissions
│ ├── lab1b-reflection.md
│ └── screenshots/
├── Lab2a/ # Total Cost of Ownership (TCO) Analysis
│ ├── lab2a-reflection.md
│ ├── tco-spreadsheet.xlsx
│ └── screenshots/
├── Lab2b/ # Cloud Web Server (AWS EC2)
│ ├── lab2b-reflection.md
│ └── screenshots/
├── Lab3a/ # DNS and SSL/TLS (Let's Encrypt)
│ ├── lab3a-reflection.md
│ └── screenshots/
├── Lab3b/ # Automation (Bash Scripting + Cron)
│ ├── lab3b-reflection.md
│ └── screenshots/
└── Lab4a/ # Additional Server Service (MariaDB)
├── lab4a-reflection.md
└── screenshots/

text

---

## 🛠️ Technologies & Tools Used

| Category | Tools |
| :--- | :--- |
| **Operating System** | Ubuntu 26.04 LTS |
| **Virtualisation** | VMware Workstation Pro |
| **Cloud Platform** | AWS EC2 (Free Tier) |
| **Web Server** | Apache2 |
| **Database** | MariaDB |
| **SSL/TLS** | Let's Encrypt / Certbot |
| **DNS** | DuckDNS |
| **Scripting** | Bash |
| **Automation** | Cron |
| **Version Control** | Git / GitHub |

---

## 📋 Lab Summaries

### Lab 1a: Virtualisation and Linux Setup
- Installed Ubuntu 26.04 LTS on VMware Workstation Pro
- Learned basic Linux commands (`ls`, `cd`, `pwd`, `sudo apt`)
- Resolved CD-ROM error during `apt update`
- Integrated Git with GitHub

### Lab 1b: Linux Services, SSH, Permissions & File Searching
- Installed and configured Apache2 web server
- Set up UFW firewall (allowed ports 22, 80)
- Created users and managed file permissions (`chmod`, `chown`)
- Used `tar` and `bzip2` for compression
- Transferred files using `scp`

### Lab 2a: Total Cost of Ownership (TCO) Analysis
- Compared inkjet vs laser printers over 5 years
- Calculated total pages: 195,000
- Laser printer TCO: $7,579 (more cost-effective)
- Inkjet printer TCO: $10,334

### Lab 2b: Cloud Web Server Deployment (AWS EC2)
- Launched Ubuntu EC2 instance (t3.micro)
- Configured Security Groups (SSH, HTTP, HTTPS)
- Installed Apache2 and deployed custom webpage
- Downloaded and served PDF files
- Set up budget alerts for cost control

### Lab 3a: DNS and SSL/TLS Configuration
- Registered domain using DuckDNS (`leeshimin.duckdns.org`)
- Configured A record pointing to EC2 public IP
- Installed Certbot and obtained Let's Encrypt SSL certificate
- Enabled HTTPS with automatic HTTP → HTTPS redirect
- Verified auto-renewal with `certbot renew --dry-run`

### Lab 3b: Automation (Bash Scripting & Cron Jobs)
- Created `system_health.sh` script to monitor:
  - Disk usage (`df -h`)
  - Memory usage (`free -h`)
  - Apache service status
- Scheduled script to run daily at 2:00 AM using cron
- Verified cron job with `sudo crontab -l`

### Lab 4a: Additional Server Service (MariaDB)
- Installed MariaDB database server
- Secured installation (`mariadb-secure-installation`)
- Set root password, removed anonymous users, disabled remote root login
- Verified with `SHOW DATABASES;` query

---

## 🔗 Useful Links

| Resource | Link |
| :--- | :--- |
| **GitHub Repository** | https://github.com/lee-shi-min/171_ISEALabs |
| **AWS Console** | https://console.aws.amazon.com |
| **DuckDNS** | https://www.duckdns.org |
| **Let's Encrypt** | https://letsencrypt.org |

---

## 📧 Contact

For any questions regarding this repository, please contact me via the email (shiminstorage@gmail.com).

---

## 📝 Acknowledgments

- Course instructors and tutors for guidance
- AWS Educate for free cloud credits
- Let's Encrypt for free SSL certificates
- DuckDNS for free dynamic DNS

---

**© 2026 Lee Shi Min - ISEA Assignment**




