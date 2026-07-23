# ICT171 Cloud Server Project

## Project Overview

This repository documents the design, deployment, configuration, and testing of a cloud server hosted on Microsoft Azure.

The project was completed using an Infrastructure as a Service (IaaS) model. An Ubuntu virtual machine was created and manually configured to host a public WordPress website, a MediaWiki knowledge base, a WireGuard VPN service, and an automated backup solution.

The project website represents a fictional business called **Elevate Fitness Studio**.

---

## Live Services

| Service | Address |
|---|---|
| WordPress Website | [https://mehekx.com](https://mehekx.com) |
| MediaWiki Knowledge Base | [https://mehekx.com/mediawiki](https://mehekx.com/mediawiki) |
| Server Public IP | `20.46.48.69` |
| WireGuard VPN Port | `51820/UDP` |

---

## Cloud Environment

| Component | Configuration |
|---|---|
| Cloud Provider | Microsoft Azure |
| Deployment Model | Infrastructure as a Service |
| Operating System | Ubuntu Server 24.04 LTS |
| Virtual Machine Size | Standard B1s |
| Web Server | Nginx |
| Domain | `mehekx.com` |
| SSL Certificate | Let's Encrypt |
| SSL Management | Certbot |
| Database | MySQL Community Server 8 |
| PHP Version | PHP 8.3 |
| Content Management System | WordPress |
| Knowledge Base | MediaWiki |
| VPN Service | WireGuard |

---

## Project Architecture

The Azure virtual machine hosts several services:

- **Nginx** serves the WordPress and MediaWiki web applications.
- **WordPress** provides the public Elevate Fitness Studio website.
- **MediaWiki** provides a staff knowledge base.
- **MySQL** stores the WordPress and MediaWiki databases.
- **Let's Encrypt and Certbot** provide HTTPS encryption.
- **WireGuard** provides secure remote VPN access.
- **Automated backup scripts** protect website files, databases, and server configurations.

---

## Documentation

The project documentation follows the order in which the cloud environment was deployed and configured.

### 1. Server Setup

Creation and configuration of the Azure Ubuntu virtual machine, including SSH access, system updates, and Nginx installation.

[View Server Setup](01-Server-Setup.md)

### 2. DNS Configuration

Configuration of the custom domain and verification that it resolves to the Azure virtual machine's public IP address.

[View DNS Configuration](02-DNS-Configuration.md)

### 3. SSL and HTTPS Configuration

Installation of Certbot, configuration of the Let's Encrypt SSL certificate, and automatic HTTP-to-HTTPS redirection.

[View SSL Configuration](03-SSL-Configuration.md)

### 4. WordPress Installation

Manual installation and configuration of WordPress, PHP, MySQL, and the Nginx virtual host.

[View WordPress Installation](04-WordPress-Installation.md)

### 5. WordPress Website Development

Design and customisation of the Elevate Fitness Studio website, including pages, navigation, branding, content, and final deployment verification.

[View WordPress Website Development](05-WordPress-Website-Development.md)

### 6. MediaWiki Installation

Installation and configuration of MediaWiki as a staff knowledge base on the same Azure virtual machine.

[View MediaWiki Installation](06-MediaWiki.md)

### 7. WireGuard VPN Configuration

Installation and configuration of WireGuard, Azure UDP access, client connectivity, routing, and VPN handshake testing.

[View WireGuard VPN Configuration](07-WireGuard.md)

### 8. Backup Script

Creation of an automated backup solution for website files, databases, and important server configuration files.

[View Backup Script](08-Backup-Script.md)

---

## Repository Structure

```text
ICT171-Cloud-Server-Project/
│
├── README.md
├── 01-Server-Setup.md
├── 02-DNS-Configuration.md
├── 03-SSL-Configuration.md
├── 04-WordPress-Installation.md
├── 05-WordPress-Website-Development.md
├── 06-MediaWiki.md
├── 07-WireGuard.md
├── 08-Backup-Script.md
│
└── images/
    ├── Server setup screenshots
    ├── DNS screenshots
    ├── SSL screenshots
    ├── WordPress screenshots
    ├── MediaWiki screenshots
    ├── WireGuard screenshots
    └── Backup screenshots
```

---

## Security Features

The project includes the following security controls:

- SSH key authentication for remote server access
- HTTPS encryption using a trusted Let's Encrypt certificate
- Automatic redirection from HTTP to HTTPS
- Azure Network Security Group firewall rules
- WireGuard encrypted VPN access
- Separate databases and database users for web applications
- Restricted storage of private keys and credentials
- Automated backups of important project data

Sensitive information such as passwords, private keys, database credentials, and full VPN configuration files has not been published in this repository.

---

## Testing and Verification

The completed environment was tested by confirming:

- The Azure virtual machine was accessible through SSH.
- The custom domain resolved to the correct public IP address.
- The website loaded securely over HTTPS.
- HTTP traffic redirected automatically to HTTPS.
- WordPress connected successfully to its MySQL database.
- MediaWiki loaded through the configured domain path.
- WireGuard established a successful VPN handshake.
- VPN traffic was routed through the Azure virtual machine.
- Backup files were created successfully.

---

## Project Outcome

The project successfully demonstrates the deployment and management of a multi-service cloud server using Microsoft Azure.

The final solution includes:

- A public WordPress website
- A MediaWiki staff knowledge base
- A secure WireGuard VPN
- HTTPS encryption
- Domain name configuration
- Database-backed web applications
- Automated backup protection

The solution demonstrates practical skills in cloud computing, Linux administration, web hosting, networking, security, and service management.

---

## Author

**ICT171 Cloud Server Project**

Domain: [https://mehekx.com](https://mehekx.com)
