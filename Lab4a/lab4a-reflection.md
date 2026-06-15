# Lab 4a: Additional Server Service - MariaDB

**Student Name:** LEE SHI MIN  
**Student ID:** 35702683  
**Date:** 17 June 2026

---

## Service Selected

I selected **MariaDB** as my additional server service. MariaDB is a popular open-source relational database management system (RDBMS) that serves as a drop-in replacement for MySQL. It is widely used in web applications, content management systems, and enterprise software.

---

## Installation Steps

### 1. Update package lists

```bash
sudo apt update
```

### 2. Install MariaDB server
```bash
sudo apt install mariadb-server -y
```

### 3. Check MariaDB service status
```bash
sudo systemactl status mariadb
```
Output shows Active: active (running)

### 4. Secure MariaDB installation

```bash
sudo mariadb-secure-installation
```
I answered the prompts as follows:

- Set root password → Yes
- Remove anonymous users → Yes
- Disallow remote root login → Yes
- Remove test database → Yes
- Reload privilege tables → Yes

### 5. Test login to MariaDB
```bash
sudo mysql -u root -p
```
### 6. Verify database

```bash
SHOW DATABASES;
```

Output shows:

- information_schema
- mysql
- performance_schema
- sys

### Screenshots:
All screenshots for this lab are located in the screenshots/ folder.

|Figure	      |Description|
|:---|:---|
|Figure 4a-1	|MariaDB version (mariadb --version)|
|Figure 4a-2	|MariaDB service status (sudo systemctl status mariadb)|
|Figure 4a-3	|MariaDB secure installation completion|
|Figure 4a-4	|MariaDB login (sudo mysql -u root -p)|
|Figure 4a-5	|SHOW DATABASES; output|


### Reflection Questions
### 1. Why did you choose this service?

I chose MariaDB because it is:

- Open-source and free to use
- Widely used in production environments
- Well-documented with a large community
- Compatible with MySQL (easy migration)
- Lightweight enough to run on minimal hardware

### 2. What are the key features of this service?

- Relational database management system
- Supports ACID compliance (Atomicity, Consistency, Isolation, Durability)
- Uses SQL (Structured Query Language)
- Supports multiple storage engines (InnoDB, MyISAM, etc.)
- Provides replication and clustering capabilities
- Includes security features like user privileges and SSL encryption

### 3. How did you verify the service was working correctly?

I verified MariaDB was working by:

- Checking the service status with systemctl status mariadb (active/running)
- Logging into the database with sudo mysql -u root -p
- Running SHOW DATABASES; to confirm connectivity
- The secure installation script confirmed all security settings were applied

### 4. What are common use cases for this service?

- Web applications (WordPress, Drupal, Joomla)
- E-commerce platforms (Magento, PrestaShop)
- ERP and CRM systems (Odoo, SuiteCRM)
- Data analytics and reporting
- Content management systems
- Mobile application backends

### 5. What security considerations are important for this service?

- Set a strong root password during installation
- Remove anonymous users (done via mariadb-secure-installation)
- Disable remote root login (prevents external attacks)
- Remove test database (eliminates unnecessary access points)
- Create application-specific users with limited privileges instead of using root
- Regular backups using mysqldump
- Enable SSL/TLS for encrypted connections

### 6. How does this service compare to alternatives?

|Feature	|MariaDB	|MySQL	|PostgreSQL|
|:---|:---|
|License	|GPL	|GPL|	PostgreSQL| License|
|Storage |engines	Multiple (InnoDB, MyISAM)|	Multiple|	Single (ACID compliant)
|Performance|	Very fast|	Fast|	Moderate|
|JSON support|	Yes|	Yes|	Excellent|
|Replication|	Master-Slave, Galera|	Master-Slave|	Master-Slave, Logical|
|Community|	Large|	Very large|	Large|

### Commands Used in This Lab

|Command	|Purpose|
|:---|:---|
|sudo apt update	|Update package lists|
|sudo apt install mariadb-server -y	|Install MariaDB|
|sudo systemctl status mariadb	|Check service status|
|sudo mariadb-secure-installation	|Secure the installation|
|sudo mysql -u root -p	|Login to MariaDB|
|SHOW DATABASES;	|List all databases|
|EXIT;	|Exit MariaDB prompt|
|mariadb --version	|Display version information|

### Conclusion
Lab 4a successfully demonstrated how to install, configure, and secure MariaDB on Ubuntu Linux. I learned about:

- Installing database servers using apt
- Securing databases with mysql_secure_installation
- Verifying service status with systemctl
- Basic database management commands

These skills are essential for system administrators, DevOps engineers, and backend developers who work with data-driven applications.












