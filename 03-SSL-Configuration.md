# SSL and HTTPS Configuration

After the custom domain was successfully connected to the Azure virtual machine, a free SSL certificate was installed using Let's Encrypt and Certbot. This enabled secure HTTPS connections and automatically redirected all HTTP traffic to HTTPS.

For this project:

| Item | Value |
|---|---|
| Domain | `mehekx.com` |
| Certificate Authority | Let's Encrypt |
| SSL Client | Certbot |
| Web Server | Nginx |

---

## Step 1 — Install Certbot

Certbot and the Nginx plugin were installed on the Ubuntu server.

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Certbot automatically obtains, installs and manages SSL certificates from Let's Encrypt.

---

## Step 2 — Request an SSL Certificate

A certificate was requested for the domain using the Nginx plugin.

```bash
sudo certbot --nginx -d mehekx.com
```

During the setup process, Certbot:

- Verified ownership of the domain.
- Obtained a free SSL certificate from Let's Encrypt.
- Updated the Nginx configuration automatically.
- Enabled HTTPS for the website.

---

## Step 3 — Verify Secure HTTPS Access

After the certificate was installed, the website was opened using HTTPS.

```text
https://mehekx.com
```

The browser confirmed that the website was being served securely over HTTPS.

![SSL1 – Secure HTTPS Website](images/SSL1%20%E2%80%93%20Secure%20HTTPS%20Website.png)

---

## Step 4 — Verify Automatic HTTP to HTTPS Redirect

HTTP requests were tested using:

```bash
curl -I http://mehekx.com
```

The server responded with:

```text
HTTP/1.1 301 Moved Permanently
Location: https://mehekx.com/
```

This confirmed that all HTTP requests were automatically redirected to the secure HTTPS version of the website.

![SSL2 – Automatic HTTP to HTTPS Redirect](images/SSL2%20%E2%80%93%20Automatic%20HTTP%20to%20HTTPS%20Redirect.png)

---

## Step 5 — Verify the Installed Certificate

The installed certificate was verified using Certbot.

```bash
sudo certbot certificates
```

The output confirmed:

- Certificate name
- Protected domain
- Expiry date
- Certificate location
- Private key location

This verified that the SSL certificate was successfully installed and managed by Certbot.

![SSL3 – Verify Installed SSL Certificate](images/SSL3%20%E2%80%93%20Verify%20Installed%20SSL%20Certificate.png)

---

## Security Benefits

Using HTTPS provides several important security improvements:

- Encrypts all communication between the client and server.
- Protects sensitive information from interception.
- Confirms the identity of the website through a trusted certificate.
- Automatically redirects users from HTTP to HTTPS.

---

## Next Step

After securing the server with HTTPS, WordPress was installed and configured as the primary website.

Continue to: [WordPress Installation](04-WordPress.md)
