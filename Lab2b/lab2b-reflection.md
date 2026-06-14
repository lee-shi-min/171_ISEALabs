# Lab 2b: Cloud Web Server Deployment with AWS EC2

**Student Name:** LEE SHI MIN  
**Student ID:** 35702683  
**Date:** 17 June 2026

## Screenshots

All screenshots are located in the `screenshots/` folder.

| Figure | Description |
| :--- | :--- |
| Figure 2b-1 | EC2 Instance running (status = running) |
| Figure 2b-2 | Security Group with SSH (22) and HTTP (80) |
| Figure 2b-3 | SSH login successful |
| Figure 2b-4 | Apache installation |
| Figure 2b-5 | Apache welcome page (`http://public-ip`) |
| Figure 2b-6 | Custom index.html edited |
| Figure 2b-7 | File downloaded with `wget` |
| Figure 2b-8 | File copied to `/var/www/html/` |
| Figure 2b-9 | PDF accessible via browser |
| Figure 2b-10 | Budget alert set up |
| Figure 2b-11 | Instance stopped (cost control) |

## Commands Used

```bash
# Connect to EC2
ssh -i aws-ubuntu-key.pem ubuntu@<public-ip>

# Update and install Apache
sudo apt update
sudo apt install apache2 -y

# Edit index.html
sudo nano /var/www/html/index.html

# Download file
wget http://www.eecs.berkeley.edu/Pubs/TechRpts/2009/EECS-2009-28.pdf

# Move to web root
sudo cp EECS-2009-28.pdf /var/www/html/

# Check file permissions
ls -la /var/www/html/
```
Reflection Questions
1. Benefits of cloud deployment over local virtualisation?
Accessible from anywhere

No need for local hardware

Scalable resources

Pay-as-you-go model

2. How does Apache serve files?
Apache listens on port 80 and serves files from /var/www/html/ directory.

3. What did you learn about file ownership and permissions?
Web files need to be readable by the www-data user or world-readable.

4. Risks of leaving instances running?
Unexpected charges

Security vulnerabilities

5. DNS vs /etc/hosts?
DNS is global, /etc/hosts is local to the machine.

---



