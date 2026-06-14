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

---

<img width="2032" height="1057" alt="image" src="https://github.com/user-attachments/assets/e531ff70-67a3-4de6-95f1-23ca682c55f2" />
Figure 2b-1 | EC2 Instance running (status = running) 

---
<img width="924" height="900" alt="image" src="https://github.com/user-attachments/assets/df72f463-3c98-4eb7-a771-287b10c93da5" />
Figure 2b-2 | Security Group with SSH (22) and HTTP (80) 
---

<img width="757" height="527" alt="image" src="https://github.com/user-attachments/assets/43da234e-9987-4e3a-92a4-b4d83998580d" />
Figure 2b-3 | SSH login successful 

<img width="940" height="156" alt="image" src="https://github.com/user-attachments/assets/4e503c4c-90a6-43c4-96ba-999cd317e358" />
Figure 2b-4 | Apache installation 

<img width="940" height="1111" alt="image" src="https://github.com/user-attachments/assets/409b67c5-5ae7-4579-a88f-9dae100cc60d" />
Figure 2b-5 | Apache welcome page (`http://public-ip`) 

<img width="1306" height="1060" alt="image" src="https://github.com/user-attachments/assets/85c6068b-1273-4d6e-93fc-827555ee1b8b" />
Figure 2b-6 | Custom index.html edited 

<img width="1007" height="582" alt="image" src="https://github.com/user-attachments/assets/1e0d7dbb-699b-4939-ad80-79b440c775dc" />
Figure 2b-7 | File downloaded with `wget` 

<img width="725" height="180" alt="image" src="https://github.com/user-attachments/assets/bcaac030-97c3-4008-a69e-8ae229691d06" />
Figure 2b-8 | File copied to `/var/www/html/`

<img width="1310" height="1150" alt="image" src="https://github.com/user-attachments/assets/62f0ee14-b4bd-454a-92d4-fbd6a48baf67" />
Figure 2b-9 | PDF accessible via browser 

<img width="1337" height="407" alt="image" src="https://github.com/user-attachments/assets/254866cf-c617-47c0-a2e2-f18d6cefc2e8" />
Figure 2b-10 | Budget alert set up 

<img width="1341" height="486" alt="image" src="https://github.com/user-attachments/assets/4fea65f5-d36d-48a7-9cb7-baf9a142066a" />
Figure 2b-11 | Instance stopped (cost control) 



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



