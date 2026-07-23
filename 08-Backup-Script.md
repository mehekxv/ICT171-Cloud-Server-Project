# Backup Script

## Overview

To improve reliability and data protection, an automated backup script was created to back up the website and database files. The script stores each backup in a timestamped directory before compressing the contents into a single archive for easier storage and management.

---

## Backup Process

The backup script performs the following tasks:

- Creates a backup directory using the current date and time.
- Backs up the WordPress website files.
- Backs up the WordPress database.
- Backs up the MediaWiki database.
- Compresses all backup files into a single archive.

The script can be executed whenever a backup is required.

---

## Running the Script

The backup script can be executed using the following command:

```bash
~/backup.sh
```

Once completed, the script confirms that the backup has been successfully created and displays the location of the backup archive.

---

## Screenshots

### Screenshot 1 – Backup Script

![Backup Script](images/backup-script.png)

---

### Screenshot 2 – Running the Backup Script

![Running the Backup Script](images/running-backup-script.png)

---

### Screenshot 3 – Backup Files Created


![Backup Files Created](images/backup-files-created.png)

---

## Summary

The automated backup solution successfully creates backups of the website files and databases while packaging them into a compressed archive. This provides a simple recovery mechanism and helps protect the project against accidental data loss.

---

## Previous

⬅️ **Previous:** [07 - WireGuard](07-WireGuard.md)
