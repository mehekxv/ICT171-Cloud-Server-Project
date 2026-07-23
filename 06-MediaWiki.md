# MediaWiki Installation

## Overview

MediaWiki was installed on the Ubuntu server to provide a wiki-based knowledge base for Elevate Fitness Studio.

The installation involved downloading the MediaWiki package, extracting it into the Nginx web directory, configuring a dedicated database, completing the web-based installation wizard, and uploading the generated `LocalSettings.php` configuration file.

The Staff Knowledge Base is accessible through:

```text
https://mehekx.com/mediawiki
```

---

## Step 1 – Download the MediaWiki Package

The MediaWiki package was downloaded onto the Ubuntu server.

![SS1 – Downloading the MediaWiki Package](images/SS1%20%E2%80%93%20Downloading%20the%20MediaWiki%20Package.png)

---

## Step 2 – Extract the Package

The MediaWiki package was extracted into:

```text
/var/www/html/mediawiki
```

The appropriate file ownership and permissions were then configured so that Nginx and PHP could access the application files.

![SS2 – MediaWiki Extracted into the Web Root Directory](images/SS2%20%E2%80%93%20MediaWiki%20Extracted%20into%20the%20Web%20Root%20Directory.png)

---

## Step 3 – Run the Installation Wizard

The MediaWiki installation wizard was accessed through the browser.

```text
https://mehekx.com/mediawiki
```

The initial language and installation settings were selected to begin the configuration.

![SS3 – MediaWiki Installation Wizard Ready](images/SS3%20%E2%80%93%20MediaWiki%20Installation%20Wizard%20Ready.png)

---

## Step 4 – Complete the Installation

The following information was configured through the installation wizard:

- Wiki name
- Database connection details
- Administrator account
- Website preferences

After the installation wizard was completed, MediaWiki generated the `LocalSettings.php` configuration file.

The generated file was uploaded to:

```text
/var/www/html/mediawiki/LocalSettings.php
```

This completed the MediaWiki configuration.

![SS4 – MediaWiki Installation Completed Successfully](images/SS4%20%E2%80%93%20MediaWiki%20Installation%20Completed%20Successfully.png)

---

## Step 5 – Verify the Installation

The installation was verified by opening the Staff Knowledge Base through the HTTPS domain.

The verification confirmed that:

- MediaWiki loaded successfully.
- The Staff Knowledge Base was accessible.
- The application connected successfully to its database.
- The existing HTTPS certificate remained active.

![SS5 – MediaWiki Successfully Installed](images/SS5%20%E2%80%93%20MediaWiki%20Successfully%20Installed%20.png)

---

## Outcome

MediaWiki was successfully deployed on the Azure Ubuntu virtual machine as a web-based knowledge management system.

The Staff Knowledge Base is:

- Hosted on the same Azure virtual machine as WordPress
- Accessible through the custom HTTPS domain
- Connected to its own database
- Configured using the generated `LocalSettings.php` file
- Available at `/mediawiki`

This provides Elevate Fitness Studio with a central location for staff documentation and internal knowledge sharing.

---

---

## Next Step

After MediaWiki was successfully deployed, WireGuard was configured to provide secure VPN access to the Azure virtual machine.

Continue to: [WireGuard VPN Configuration](07-WireGuard.md)
