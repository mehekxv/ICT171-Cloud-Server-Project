# WireGuard VPN Configuration

## Overview

WireGuard was installed and configured on the Ubuntu Azure virtual machine to provide secure remote access through an encrypted VPN tunnel.

The configuration included:

- Installing WireGuard
- Enabling IPv4 forwarding
- Allowing UDP port `51820` through the Azure Network Security Group
- Creating the WireGuard server interface
- Creating a client configuration
- Testing the VPN connection from a Mac
- Confirming VPN traffic and handshake status

---

## Step 1 – Install WireGuard

The Ubuntu package list was updated, and WireGuard was installed using the system package manager.

```bash
sudo apt update
sudo apt install wireguard -y
```

![WG1 – Updating Packages and Installing WireGuard](images/WG1%20%E2%80%93%20Updating%20Packages%20and%20Installing%20WireGuard.png)

---

## Step 2 – Enable IPv4 Forwarding

IPv4 forwarding was enabled so the Azure virtual machine could route traffic between the WireGuard VPN interface and the external network interface.

```bash
echo 'net.ipv4.ip_forward=1' | sudo tee /etc/sysctl.d/99-wireguard-forward.conf
sudo sysctl --system
```

The output confirmed that IPv4 forwarding was enabled:

```text
net.ipv4.ip_forward = 1
```

![WG2 – IPv4 Forwarding Enabled](images/WG2%20%E2%80%93%20IPv4%20Forwarding%20Enabled.png)

---

## Step 3 – Configure the Azure UDP Port Rule

An inbound security rule was added to the Azure Network Security Group to allow WireGuard VPN traffic to reach the virtual machine.

The rule used the following settings:

| Setting | Value |
|---|---|
| Destination port | `51820` |
| Protocol | `UDP` |
| Action | `Allow` |
| Priority | `350` |
| Name | `WireGuard` |

![WG3 – WireGuard UDP Port Rule Configured](images/WG3%20%E2%80%93%20WireGuard%20UDP%20Port%20Rule%20Configured.png)

---

## Step 4 – Configure the WireGuard Interface

Server and client key pairs were generated for secure authentication between the VPN server and client.

The WireGuard server configuration was created at:

```text
/etc/wireguard/wg0.conf
```

The server interface was configured with:

- VPN address: `10.8.0.1/24`
- Listening port: `51820`
- Protocol: UDP
- Network address translation through the VM's `eth0` interface

The WireGuard configuration file contains private cryptographic keys and must not be published in the GitHub repository.

The WireGuard service was enabled and started using:

```bash
sudo systemctl enable --now wg-quick@wg0
```

The active interface was verified using:

```bash
sudo wg show
```

![WG4 – WireGuard Interface Active](images/WG4%20%E2%80%93%20WireGuard%20Interface%20Active.png)

---

## Step 5 – Configure the Mac Client

A WireGuard client configuration was created using the client's private key, the server's public key, the Azure VM public IP address, and UDP port `51820`.

The client configuration was imported into the WireGuard application on the Mac, and the VPN tunnel was activated.

The client configuration contains private key information and was not uploaded to the GitHub repository.

---

## Step 6 – Test VPN Connectivity

Connectivity to the WireGuard server's private VPN address was tested from the Mac using:

```bash
ping -c 4 10.8.0.1
```

All four packets were received successfully with `0.0%` packet loss.

This confirmed that the Mac client could communicate with the Azure server through the encrypted VPN tunnel.

![WG5 – Successful WireGuard VPN Connectivity Test](images/WG5%20%E2%80%93%20Successful%20WireGuard%20VPN%20Connectivity%20Test.png)

---

## Step 7 – Verify Public IP Routing

While connected to the VPN, the public IP address was checked using:

```bash
curl https://api.ipify.org ; echo
```

The result displayed the Azure virtual machine's public IP address:

```text
20.46.48.69
```

This confirmed that the Mac client's internet traffic was being routed through the WireGuard VPN server.

![WG6 – Public IP Verified Through WireGuard VPN](images/WG6%20%E2%80%93%20Public%20IP%20Verified%20Through%20WireGuard%20VPN.png)

---

## Step 8 – Confirm the VPN Handshake

The WireGuard server status was checked again after connecting the Mac client.

```bash
sudo wg show
```

The output displayed:

- The configured WireGuard interface
- The connected client peer
- A recent handshake
- Data received and transmitted
- The client's endpoint address

This confirmed that the encrypted VPN tunnel was active and transferring data successfully.

![WG7 – WireGuard Handshake and Data Transfer](images/WG7%20%E2%80%93%20WireGuard%20Handshake%20and%20Data%20Transfer.png)

---

## Outcome

WireGuard was successfully deployed on the Azure Ubuntu virtual machine.

The completed VPN configuration provides:

- Encrypted remote access to the Azure server
- Secure authentication using public and private keys
- Private communication through the `10.8.0.0/24` VPN network
- Internet traffic routing through the Azure virtual machine
- Successful connectivity between the Mac client and VPN server
- Confirmed handshake and data transfer

WireGuard adds a secure remote-access component to the ICT171 Cloud Server Project and demonstrates the manual configuration of network security services within an IaaS environment.

---

## Next Step

After WireGuard was successfully configured and tested, an automated backup script was created to protect the website files, databases, and important server configuration files.

Continue to: [Backup Script](08-Backup-Script.md)
## Security

Private keys and client configuration files were not uploaded to the repository. Files such as `client.conf`, `wg0.conf`, `server_private.key`, and `client_private.key` contain sensitive information and must remain private.
