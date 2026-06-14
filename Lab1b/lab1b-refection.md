# Lab 1b: Linux Services, Permissions, and File Searching

**Student Name:** LEE SHI MIN  
**Student ID:** 35702683  
**Date:** 17 June 2026

---

## Part 1: Linux Services, SSH, Firewalls & Compression

### Screenshots

All screenshots for this lab are located in the `screenshots/` folder.

| Figure | Description |
| :--- | :--- |
| Figure 1b-1a | Apache installed and running (`systemctl status apache2`) |
| Figure 1b-1b | Apache welcome page (`http://localhost`) |
| Figure 1b-1c | IP address (`ip a`) and Nmap scan results |
| Figure 1b-1d | UFW firewall enabled and port 80 allowed |
| Figure 1b-1e | SSH login to partner's machine |
| Figure 1b-1f | New user created (`sudo adduser`) |
| Figure 1b-1g | tar and bzip2 compression commands |
| Figure 1b-1h | scp file transfer between machines |

---

<img width="1021" height="537" alt="image" src="https://github.com/user-attachments/assets/63fcf05b-2cfe-438c-b2f5-071863c49e1d" />
Figure 1b-1a Apache installed and running (`systemctl status apache2`) 

---

<img width="567" height="645" alt="image" src="https://github.com/user-attachments/assets/fa54575e-b2cc-405e-a10c-c5af2ad5cad1" />
Figure 1b-1b Apache welcome page (`http://localhost`) 

---

<img width="921" height="492" alt="image" src="https://github.com/user-attachments/assets/1aa0bc5e-5fde-4471-98b8-66d777823b59" />
Figure 1b-1c IP address (`ip a`) and Nmap scan results 

---

<img width="802" height="462" alt="image" src="https://github.com/user-attachments/assets/217ad55f-fabd-49b5-b25a-aa81f22dd08d" />
Figure 1b-1d UFW firewall enabled and port 80 allowed 

---

<img width="1017" height="587" alt="image" src="https://github.com/user-attachments/assets/c02a102d-0ac7-496e-9f0f-2fd9edc76d09" />
Figure 1b-1e SSH login to partner's machine

---

<img width="917" height="280" alt="image" src="https://github.com/user-attachments/assets/b4825500-b89a-4abe-a73b-174463098fea" />
Figure 1b-1f New user created (`sudo adduser`) 

---

<img width="905" height="536" alt="image" src="https://github.com/user-attachments/assets/402daffc-18ac-490f-b680-943b24dd5b74" />
Figure 1b-1g tar and bzip2 compression commands 

---

<img width="1007" height="92" alt="image" src="https://github.com/user-attachments/assets/48da37a1-3b30-43b8-a517-f4c1b3132e77" />
Figure 1b-1h scp file transfer between machines 

---

### Reflection Questions

#### 1. What is the role of a firewall in managing services?

A firewall controls incoming and outgoing network traffic based on predetermined security rules. In Linux, UFW (Uncomplicated Firewall) allows administrators to block or allow specific ports. For example, allowing port 80 (HTTP) enables web server access, while blocking port 22 (SSH) prevents remote logins. Firewalls are essential for reducing attack surfaces on production servers.

#### 2. How did SSH access deepen your understanding of Linux as a server?

SSH (Secure Shell) allows remote command-line access to Linux servers. This lab taught me how to:
- Log into remote machines using `ssh user@ip`
- Transfer files using `scp`
- Create and manage users remotely

Most production servers are headless (no GUI), so SSH is the primary administration tool for system administrators.

#### 3. Why is file compression important in server contexts?

Compression reduces file sizes, which saves storage space and reduces network transfer times. Using `tar` and `bzip2`, I compressed a directory of books from ~10MB to ~3MB (70% compression ratio). This is critical for:
- Backing up server data
- Transferring log files
- Distributing software packages
- Archiving old data

#### 4. How does user privilege management help secure systems?

Creating separate users with specific permissions follows the **principle of least privilege**. Users should only have access to what they need. For example:
- Regular users cannot install software (requires `sudo`)
- Different groups can have different file access levels
- The root user should rarely be used directly

This prevents accidental damage and limits the impact of compromised accounts.

#### 5. What commands did you find most useful in this lab?

| Command | Purpose |
| :--- | :--- |
| `sudo systemctl status apache2` | Check if Apache is running |
| `nmap [IP]` | Scan open ports on a remote machine |
| `sudo ufw allow 80/tcp` | Allow HTTP traffic through firewall |
| `ssh user@ip` | Remote login to another machine |
| `tar cf archive.tar folder/` | Create a tar archive |
| `bzip2 archive.tar` | Compress the tar file |
| `scp file.txt user@ip:/path/` | Securely copy files over network |

---

## Part 2: Linux File Permissions and Group Access Control

### Screenshots

| Figure | Description |
| :--- | :--- |
| Figure 1b-2a | Three users created (alice, bob, mallory) |
| Figure 1b-2b | Group `sharedgroup` created with alice and bob as members |
| Figure 1b-2c | Directory `/home/shared` with 10 files |
| Figure 1b-2d | Permissions set using `chmod 770` and `chmod 750` |
| Figure 1b-2e | Access verified as each user (`su - alice`, `ls -l`) |

---

### Reflection Questions

#### 1. How do Linux permissions differ from Windows ACL?

Linux uses a simple permission model: **read (r), write (w), execute (x)** for three categories: **Owner, Group, Others**. Windows ACLs are more granular, allowing specific users and groups with fine-grained permissions. Linux permissions are faster to configure but less detailed.

#### 2. What is the effect of `chmod 770` vs `chmod 750`?

| Permission | Owner | Group | Others | Effect |
| :--- | :--- | :--- | :--- | :--- |
| `chmod 770` | rwx | rwx | --- | Owner and group have full access; others have none |
| `chmod 750` | rwx | r-x | --- | Owner has full access; group can read/execute but NOT write |

#### 3. What is the risk of adding users to the sudo group?

Users in the `sudo` group can execute commands as root, bypassing all permission restrictions. This is dangerous because:
- They can delete system files
- They can access other users' data
- They can install malicious software

Mallory should only have sudo access if absolutely necessary.

#### 4. Why is it important to verify with `su` and `whoami`?

- `su - username` switches to another user, allowing you to test permissions from their perspective
- `whoami` confirms which user you are logged in as

Without these commands, you might incorrectly assume permissions work as configured. Testing as each user is the only way to be certain.

---

## Part 3: Searching File Systems (Gutenberg Archive)

### Screenshots

| Figure | Description |
| :--- | :--- |
| Figure 1b-3a | Archive extracted (`bunzip2` and `tar -xvf`) |
| Figure 1b-3b | `find` command searching for filenames |
| Figure 1b-3c | `grep` command searching for "verdigris" |
| Figure 1b-3d | `find -size` command for 255258 byte file |
| Figure 1b-3e | `du -a` and `sort -nr` for largest files |

---

### Answers to Lab Questions

| Question | Answer |
| :--- | :--- |
| How many times does the string "verdigris" appear? | 9 |
| What is the surname of the author of the filename "1107.txt"? | Shakespeare |
| What is the surname of the author of the file that is exactly 255258 bytes? | Lobo |
| What is the filename of the file with the 3rd oldest creation date? | 1498.txt |
| Find the word that follows "Next day there was a surprise for Jack" | Halliday |

---

### Commands Used

```bash
# Extract archive
bunzip2 gutenberg.tar.bz2
tar -xvf gutenberg.tar

# Search for filename
find . -name "*.txt"

# Search for text
grep -r "verdigris" .
grep -r -C 3 "Next day there was a surprise for Jack" .

# Search by file size
find . -type f -size 255258c

# Find largest files
du -a . | sort -nr | head -20

# Find oldest files
find . -type f -printf '%T+ %p\n' | sort | head -10

```

### Conclusion
Lab 1b taught me essential Linux system administration skills:

Managing services (Apache, SSH) and firewalls (UFW)

Using compression (tar, bzip2) and secure transfers (scp)

Implementing file permissions and group-based access control

Searching filesystems with find and grep

These skills are fundamental for secure server management and DevOps roles.

---



