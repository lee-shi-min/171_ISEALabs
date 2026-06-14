Lab 1a: Virtualisation and Linux Setup+ Ubuntu CLI Familiarisation

Student Name: LEE SHI MIN
Student ID: 35702683
Date: 17 June 2026

Part 1: Virtualisation and Linux Setup




All screenshots for this lab are located in the 'screenshot/' folder:

| Figure   | Description                                               |
| Figure 1a | Ubuntu 26.04 LTS Desktop                                  |
| Figure 1b | System verification (kernel, os version, RAM, disk space) |
| Figure 1c | Hostnamectl output showing Ubuntu 26.04 LTS               |

Figure 1a: Ubuntu 26.04 LTS Desktop
<img width="940" height="560" alt="image" src="https://github.com/user-attachments/assets/ce7ac234-fd4f-4482-92ee-7f2dff4bcf37" />

Figure 1b: System verification (`uname -a`, `lsb_release -a`, `free -h`, `df -h`) 
<img width="940" height="435" alt="image" src="https://github.com/user-attachments/assets/f1c285d5-7016-4e9e-a422-1613708dfb22" />

Figure 1c: Hostnamectl output showing Ubuntu 26.04 LTS 
<img width="940" height="322" alt="image" src="https://github.com/user-attachments/assets/08e35bde-fabc-46f5-8c7f-2e0d7d9a601c" />


Reflection Questions:

1. What challenges did you encounter during the virtual machine setup?

The main challenge I encountered was the "CD-ROM error" when running 'sudo apt update'. The error message said:

Err: file:/cdrom resolute Release
File not found- /cdrom/dists/resolute/Release (2:No such file or directory)

I solved this by removing the CD-ROM entry from the sources list using the command:

``` bash

sudo sed -i '/cdrom/d' /etc/apt/sources.list

```
After running this command, sudo apt update worked without errors.

2. What did you learn about virtualisation tools and their differences?

I learned that virtualisation allows multiple operating systems to run on a single physical computer. The host OS (Windows 11) runs the hypervisor (VMware Workstation Pro), which creates and manages guest VMs(Ubuntu 26.04)

Tool: VMware Workstation
Pros: Good performance, easy to use	
Cons: Free version limited

Tool: VirtualBox	
Pros: Completely free, open source	
Cons: Slower performance

Tools: Hyper-V	
Pros: Built into Windows	
Cons: Complex setup for beginners

3. How confident do you feel using Ubuntu after completing this lab?

I feel confident navigating the Ubuntu desktop, opening the terminal and running basic commands such as:

ls - list files and directories
cd - change directory
pwd - print working directory
sudo apt update - update package lists
free -h - check RAM usage
df -h - check disk space
ip a - check IP addresses

4. In what ways can a virtualised Linux environment help in industry scenarios?

Virtualisation is used extensively in industry for:

Testing and Development - Test new software without affecting production systems
Isolation - Problems inside a VM don't affect the host computer
Cost Savings - Run multiple virtual servers on one physical machine
Cloud Computing - AWS, Azure use virtualisation for scalable resources

5. What would you do differently if setting up another VM?

If I set up another VM, I would:

Allocate more disk space (60GB instead of 50GB)
Take screenshots during installation
Document errors immediately
Use a static IP for easier SSH access



Part 2: Ubuntu Desktop and Command Line Familiarisation

Reflection Questions: 

6. Which file editors are best for remote access and why?

nano is best for remote access because:

It runs entirely in the terminal (no GUI required)
It is pre-installed on most Linux distributions
Commands are shown at the bottom of the screen
It works over slow connections

7. Compare software installation methods

|Method	          | Description	Example                                        |
|SaaS	            | Software accessed via web browser	Google Docs, Office 365  |
|Binary (.deb)     |	Download and install executable	Chrome, Opera              |
|Repository (apt)  |	Install from trusted repository	sudo apt install vlc       |
|Source            |	Compile from source code	gcc hello.c -o hello             |

8. Pros and cons of each method
|Method	    |Pros	                                      |Cons                                 |
|SaaS	      |No installation, auto updates	            |Requires internet, subscription fees |
|Binary	    |Easy for users	                            |Security risks, manual updates       |
|Repository	|Automatic dependencies, verified security	|Limited to available packages        |
|Source	    |Full control, latest versions	            |Time-consuming, complex              |

9. How did using CLI improve your understanding of Linux?

Using the command line improved my understanding of:

1. Filesystem structure - /etc for config, /var for logs, /home for users
2. Permissions - chmod and chown taught me about Linux security
3. Process management - ps, top, kill show how Linux manages programs
4. Package management - apt commands for installing software
5. Troubleshooting - Reading error messages and finding solutions

Commands Used in This Lab:

|Command	          |Purpose                      |
|sudo apt update    |	Update package lists        |
|sudo apt upgrade -y|	Upgrade all packages        |
|uname -a           |	Display kernel information  |
|lsb_release -a     |	Display Ubuntu version      |
|hostnamectl        |	Display system details      |
|free -h            |	Display RAM usage           |
|df -h              |	Display disk space          |
|ip a               |	Display IP addresses        | 
|ls -la             |	List files with permissions |
|nano               |	Terminal text editor        |
|chmod              |	Change file permissions     |

Conclusion

Lab 1a successfully introduced me to virtualisation, Ubuntu Linux installation, and command-line basics. I can now create and manage virtual machines, navigate the Linux filesystem, and troubleshoot common errors. These skills are essential for system administration and cloud computing roles.





