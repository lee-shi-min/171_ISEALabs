# Lab 3a: DNS Setup and SSL Configuration

**Student Name:** LEE SHI MIN  
**Student ID:** 35702683  
**Date:** 17 June 2026

---

## Part 1: DNS Configuration

### Domain Setup

I used **DuckDNS** (free dynamic DNS service) to register a domain name for my EC2 instance.

| Setting | Value |
| :--- | :--- |
| Domain | `leeshimin.duckdns.org` |
| IP Address | EC2 public IP (54.84.96.5) |

### Screenshots

All screenshots are located in the `screenshots/` folder.

| Figure | Description |
| :--- | :--- |
| Figure 3a-1 | DuckDNS dashboard showing domain `leeshimin.duckdns.org` |
| Figure 3a-2 | Security Group with HTTPS (port 443) added |
---
<img width="752" height="846" alt="3a-1" src="https://github.com/user-attachments/assets/607b8a0a-92a5-4e46-915b-a976fda36ac8" />
Figure 3a-1 DuckDNS dashboard

<img width="752" height="255" alt="3a-2" src="https://github.com/user-attachments/assets/1a8efa30-7731-4954-8be0-917270094ef5" />
Figure 3a-2 | Security Group 

---

### DNS Records Explained

| Record Type | Purpose |
| :--- | :--- |
| **A Record** | Maps domain name to IPv4 address |
| **AAAA Record** | Maps domain name to IPv6 address |
| **CNAME** | Alias for another domain name |
| **MX** | Mail exchange server for email delivery |
| **TXT** | Text records for verification (SPF, DKIM, DMARC) |
| **NS** | Name server delegation |

---

## Part 2: SSL Certificate with Let's Encrypt

### Certbot Installation

I installed Certbot using the Snap package manager on Ubuntu:

```bash
sudo snap install core
sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

---

I ran Certbot with the Apache plugin:
```bash
sudo certbot --apache -d leeshimin.duckdns.org
```

### Certbot:

1. Verified domain ownership through HTTP validation
2. Obtained a certificate from Let's Encrypt
3. Automatically configured Apache to use HTTPS
4. Set up automatic redirect from HTTP to HTTPS

### Screenshots:
|Figure	    |Description                                   |
|:---|:---|
|Figure 3a-3|	Certbot installation                         |
|Figure 3a-4|	Certbot success message (certificate issued) |
|Figure 3a-5|	Browser showing https:// with padlock icon   |
|Figure 3a-6|	sudo certbot renew --dry-run success         |

<img width="642" height="175" alt="3a-3" src="https://github.com/user-attachments/assets/a2ffbf0f-286d-4649-854d-3a2a7c8c5bd5" />
Figure 3a-3	Certbot installation  

<img width="752" height="262" alt="3a-4" src="https://github.com/user-attachments/assets/48dd6490-c001-43bb-a792-441a5a05316f" />
Figure 3a-4	Certbot success message 

<img width="729" height="897" alt="3a-5" src="https://github.com/user-attachments/assets/8c8bc92d-dbb9-4192-be7b-1fe248284e0f" />
Figure 3a-5	Browser showing with padlock   

<img width="710" height="366" alt="3a-6" src="https://github.com/user-attachments/assets/74510b53-e27f-4678-aaa7-d12193269470" />
Figure 3a-6	certbot renew --dry-run 

---

Certificate Details
|Field	 | Value                              |
|:---|:---|
|Issuer	 | Let's Encrypt                      |
|Expiry	 | 90 days from issue date            |
|Renewal |	Automatic (Certbot systemd timer) |

---

# Test auto-renewal
```bash
sudo certbot renew --dry-run
```

# Check certificate info
```bash
sudo certbot certificates
```

---

### Reflection Questions
### 1. Why is HTTPS important for modern web applications?
HTTPS (HTTP over TLS) encrypts all data between the client and server, providing:

- Confidentiality: Prevents eavesdropping on sensitive data (passwords, credit cards, personal information)

- Integrity: Prevents data tampering during transmission

- Authentication: Verifies the server's identity, preventing man-in-the-middle attacks

- SEO benefit: Google ranks HTTPS sites higher

- Browser trust: Modern browsers mark HTTP sites as "Not Secure"

### 2. What entity issued your site's TLS certificate?
My certificate was issued by Let's Encrypt, a free, automated, and open certificate authority (CA) provided by the Internet Security Research Group (ISRG). Let's Encrypt is trusted by all major browsers and offers 90-day certificates with automated renewal.

### 3. How long is your certificate valid for, and how can it be renewed?
The certificate is valid for 90 days. Let's Encrypt uses short-lived certificates to encourage automation. Certbot automatically renews the certificate when it's close to expiry using a systemd timer or cron job. The renewal can be tested with:
```
bash

sudo certbot renew --dry-run
```

### 4. What happens if a certificate expires and is not renewed?

If a certificate expires:

- Browser warnings: Users see a "Connection is not secure" warning page

- Trust broken: The site appears untrustworthy to visitors

- Business impact: Customers may leave the site, causing revenue loss

- API failures: Any automated systems relying on the API will fail

- Search ranking: Google may lower the site's search ranking

### 5. Why does Let's Encrypt require port 80 or 443 to be open for verification?

Let's Encrypt uses the HTTP-01 challenge to verify domain ownership. It places a temporary file at http://domain.com/.well-known/acme-challenge/ and expects the web server to serve it. This requires:

- Port 80 (HTTP) to be open to the internet

- Apache/Nginx to be running and accessible

Alternative validation methods exist (DNS-01 challenge), but HTTP-01 is the simplest for web servers.

### 6. What is the difference between DNS and /etc/hosts?
|Feature     |	DNS	/etc/hosts|
|:---|:---|
|Scope       |	Global (entire internet)	Local (single machine)               |
|Management  |	Centralized by domain owners	Manual file editing              |
|Propagation |	Takes minutes to hours	Instant                                |
|Use case    |	Public websites, email, services	Local development, testing   |

### Commands Used in This Lab
|Command                              |	Purpose                                     |
|:---|:---|
|sudo snap install --classic certbot	          |Install Certbot                    |
|sudo certbot --apache -d leeshimin.duckdns.org	|Obtain and install SSL certificate |
|sudo certbot renew --dry-run	                  |Test auto-renewal                  |
|sudo certbot certificates                      |	List installed certificates       |
|dig leeshimin.duckdns.org                      |	DNS lookup                        |
|nslookup leeshimin.duckdns.org	                | Query DNS records                 |

### Conclusion:
Lab 3a successfully demonstrated how to:

1. Set up DNS using a free dynamic DNS service (DuckDNS)
2. Configure security groups to allow HTTPS traffic
3. Install and use Certbot to obtain a Let's Encrypt SSL certificate
4. Enable HTTPS on Apache with automatic HTTP → HTTPS redirection
5. Verify certificate installation with browser padlock icon
6. Test automatic certificate renewal

These skills are essential for securing public-facing web servers and are directly applicable to real-world system administration and DevOps roles.

