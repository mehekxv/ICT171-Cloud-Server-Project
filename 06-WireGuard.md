# WireGuard VPN Configuration

WireGuard was installed and configured on the Ubuntu Azure virtual machine to provide secure remote access through an encrypted VPN tunnel. The configuration included enabling IP forwarding, creating the WireGuard interface, allowing UDP port `51820` through Azure, creating a client configuration, and testing the VPN connection from a Mac.

---

## Step 1 – Install WireGuard

The Ubuntu package list was updated, and WireGuard was installed using the system package manager.

```bash
sudo apt update
sudo apt install wireguard -y
```

![WG1 – Updating Packages and Installing WireGuard](<images/WG1 – Updating Packages and Installing WireGuard.png>)


---

## Step 2 – Enable IPv4 Forwarding

IPv4 forwarding was enabled so the Azure VM could route traffic between the WireGuard VPN interface and the external network interface.

```bash
echo 'net.ipv4.ip_forward=1' | sudo tee /etc/sysctl.d/99-wireguard-forward.conf
sudo sysctl --system
```

The output confirmed that IP forwarding was enabled:

```text
net.ipv4.ip_forward = 1
```

![WG2 – IPv4 Forwarding Enabled](images/WG2%20%E2%80%93%20IPv4%20Forwarding%20Enabled.png)

---

## Step 3 – Configure the Azure UDP Port Rule

An inbound security rule was added to the Azure Network Security Group to allow WireGuard traffic.

The rule used the following settings:

- Destination port: `51820`
- Protocol: `UDP`
- Action: `Allow`
- Priority: `350`
- Name: `WireGuard`

![WG3 – WireGuard UDP Port Rule Configured](images/WG3%20%E2%80%93%20WireGuard%20UDP%20Port%20Rule%20Configured.png)

---

## Step 4 – Configure the WireGuard Interface

Server and client key pairs were generated, and the WireGuard server configuration was created at:

```text
/etc/wireguard/wg0.conf
```

The server interface was assigned the VPN address `10.8.0.1/24` and configured to listen on UDP port `51820`. Network address translation was configured through the VM's `eth0` interface.

The WireGuard service was then enabled and started:

```bash
sudo systemctl enable --now wg-quick@wg0
```

The active interface was verified using:

```bash
sudo wg show
```

![WG4 – WireGuard Interface Active](images/WG4%20%E2%80%93%20WireGuard%20Interface%20Active.png)

---

## Step 5 – Test VPN Connectivity

The client configuration was imported into the WireGuard application on the Mac and the tunnel was activated.

Connectivity to the WireGuard server's private VPN address was tested using:

```bash
ping -c 4 10.8.0.1
```

All four packets were received successfully with `0.0%` packet loss.

![WG5 – Successful WireGuard VPN Connectivity Test](images/WG5%20%E2%80%93%20Successful%20WireGuard%20VPN%20Connectivity%20Test.png)

---

## Step 6 – Verify Public IP Routing

While connected to the VPN, the public IP address was checked using:

```bash
curl https://api.ipify.org ; echo
```

The result displayed the Azure VM's public IP address, confirming that the client's internet traffic was being routed through the WireGuard VPN server.

![WG6 – Public IP Verified Through WireGuard VPN](images/WG6%20%E2%80%93%20Public%20IP%20Verified%20Through%20WireGuard%20VPN.png)

---

## Step 7 – Confirm the VPN Handshake

The WireGuard server status was checked again after connecting the client.

```bash
sudo wg show
```

The output displayed a recent handshake and transferred data between the server and client, confirming that the encrypted VPN tunnel was functioning successfully.

![WG7 – WireGuard Handshake and Data Transfer](images/WG7%20%E2%80%93%20WireGuard%20Handshake%20and%20Data%20Transfer.png)

---

## Security

Private keys and client configuration files were not uploaded to the repository. Files such as `client.conf`, `wg0.conf`, `server_private.key`, and `client_private.key` contain sensitive information and must remain private.
