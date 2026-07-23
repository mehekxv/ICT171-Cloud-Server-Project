# 02 - WordPress Installation

## Overview

This document describes the installation and configuration of WordPress on the Azure Ubuntu 24.04 virtual machine. The deployment follows an Infrastructure as a Service (IaaS) model, where all software components were installed and configured manually.

WordPress serves as the public website for **Elevate Fitness Studio** and is hosted on the custom domain:

**https://mehekx.com**

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 24.04 LTS |
| Web Server | Nginx |
| PHP | PHP 8.3 |
| Database | MySQL Community Server 8 |
| CMS | WordPress (Latest Stable Release) |

---

## Download WordPress

The latest WordPress package was downloaded from the official website and extracted on the server.

```bash
cd /tmp
wget https://wordpress.org/latest.tar.gz
tar -xzf latest.tar.gz
```

![Downloading and extracting WordPress](images/wordpress-files.png)

---

## Backup Existing Website

Before replacing the original website, a backup of the existing web directory was created to ensure the previous project could be restored if required.

```bash
sudo cp -r /var/www/html /var/www/html-proposal-backup
```

---

## Configure the Database

A dedicated MySQL database and database user were created for WordPress. The database credentials were then configured in the `wp-config.php` file to establish the connection between WordPress and MySQL.

The configuration file was validated before deployment.

```bash
sudo php -l /var/www/html/wp-config.php
```

---

## Configure Nginx

The Nginx virtual host configuration was updated to:

- Serve the WordPress website from `/var/www/html`
- Process PHP files using PHP-FPM
- Support WordPress permalink routing
- Continue using the existing Let's Encrypt SSL certificate

After the configuration was updated, Nginx was tested and reloaded.

```bash
sudo nginx -t
sudo systemctl reload nginx
```

---

## Complete the Installation

The WordPress installation wizard was accessed through the custom domain.

```
https://mehekx.com
```

The administrator account and website information were configured to complete the installation.

![WordPress installation wizard](images/wordpress-install-language.png)

After completing the setup, WordPress was successfully installed.

![Successful WordPress installation](images/wordpress-install-success.png)

---

## Verify the Deployment

The deployment was verified by accessing both the WordPress administrator dashboard and the public website over HTTPS.

### WordPress Dashboard

![WordPress Dashboard](images/wordpress-dashboard.png)

### Public Website

![WordPress Homepage](images/wordpress-homepage.png)

---

## Outcome

WordPress was successfully deployed on the Azure virtual machine using a manual IaaS installation. The website is fully operational, connected to a MySQL database, secured with HTTPS using a Let's Encrypt SSL certificate, and accessible through the custom domain.

This deployment provides the public-facing website for **Elevate Fitness Studio** and forms a core component of the cloud server solution developed for the ICT171 Cloud Server Project.
