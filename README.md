# ICT171 Cloud Server Project

**Student:** Mehek Mohammed Ashraf  
**Student ID:** 35419399

## Project Overview

This project demonstrates the deployment and administration of a cloud-based Ubuntu 24.04 LTS server hosted on Microsoft Azure using the Infrastructure as a Service (IaaS) model.

The server was configured with:

- Nginx web server
- Custom DNS domain
- HTTPS encryption using Let’s Encrypt
- WordPress website
- MediaWiki knowledge base
- WireGuard VPN
- Automated backup script

## Server Information

| Item | Value |
|---|---|
| Cloud platform | Microsoft Azure |
| Operating system | Ubuntu Server 24.04 LTS |
| VM size | Standard B1s |
| Web server | Nginx |
| Public IP | `20.46.48.69` |
| Domain | `mehekx.com` |
| Website | `https://mehekx.com/` |
| MediaWiki | `https://mehekx.com/mediawiki/` |

## Deployment Order

The server was built in the following order:

1. Created the Azure virtual machine
2. Connected to the VM through SSH
3. Updated Ubuntu
4. Installed and tested Nginx
5. Configured the custom domain and DNS record
6. Installed Certbot and enabled HTTPS
7. Installed WordPress
8. Installed MediaWiki
9. Configured WireGuard VPN
10. Created the automated backup script

## Documentation

1. [Azure Server Setup](01-Server-Setup.md)
2. [DNS Configuration](02-DNS-Configuration.md)
3. [SSL and HTTPS Configuration](03-SSL-Configuration.md)
4. [WordPress Installation](04-WordPress.md)
5. [MediaWiki Installation](05-MediaWiki.md)
6. [WireGuard VPN Configuration](06-WireGuard.md)
7. [Automated Backup Script](07-Backup-Script.md)

## Security Notes

Sensitive information has not been uploaded to this repository. Private SSH keys, WireGuard private keys, database passwords and client configuration files must remain confidential.

## Video Explainer

The project video link will be added after recording.
06-WireGuard.md
07-Backup-Script.md

## Video Explainer

Video link will be added after recording.
