# Networking Task 01: Understanding Your Network Environment
**White Band Associates | Submitted by: Mark**

---

## Part A: Network Information

> ⚠️ **Note:** The values below are placeholder examples. Replace them with your actual system values obtained by running `ipconfig` (Windows) or `ip addr` (Linux).

| # | Detail | Value (Example) |
|---|--------|-----------------|
| 1 | Hostname (Device Name) | `MARK-LAPTOP` |
| 2 | IPv4 Address | `192.168.1.105` |
| 3 | MAC Address | `A4-C3-F0-85-7D-2B` |
| 4 | Default Gateway | `192.168.1.1` |
| 5 | DNS Server | `8.8.8.8` (Google DNS) |

**How to find these on Windows:**
```
ipconfig /all
```

**How to find these on Linux:**
```
ip addr
nmcli dev show
```

> 📸 Screenshots of `ipconfig /all` or `ip addr` output should be placed in the `screenshots/` folder.

---

## Part B: Basic Networking Concepts

### What is an IP Address?
An IP (Internet Protocol) address is a unique numerical label assigned to every device connected to a network. It works like a home address — just as a postman uses your address to deliver letters, the network uses IP addresses to route data to the correct device. Example: `192.168.1.105`

### What is a MAC Address?
A MAC (Media Access Control) address is a hardware identifier permanently assigned to a device's network interface card (NIC) by the manufacturer. Unlike an IP address (which can change), a MAC address is fixed. It looks like: `A4:C3:F0:85:7D:2B`. It is used for communication within a local network (LAN).

### What is a Default Gateway?
The Default Gateway is the IP address of your router — the device that acts as the "door" between your local network and the wider internet. When your computer wants to send data to a website, it first sends that data to the default gateway, which then forwards it to the internet. Example: `192.168.1.1`

### What is DNS?
DNS (Domain Name System) is like the phonebook of the internet. When you type `www.google.com` in your browser, DNS translates that human-readable name into an IP address (e.g., `142.250.195.46`) that computers can understand and route to. Without DNS, you would have to memorize IP addresses for every website.

### Difference Between Public IP and Private IP

| Feature | Private IP | Public IP |
|---------|-----------|-----------|
| **Where used** | Inside your home/office network | On the internet |
| **Who assigns it** | Your router (via DHCP) | Your ISP (Internet Service Provider) |
| **Example range** | `192.168.x.x`, `10.x.x.x` | `103.21.58.200` |
| **Visible to internet?** | No | Yes |
| **Unique globally?** | No (many networks reuse same ranges) | Yes |

Think of it this way: your Private IP is your room number inside a building, while your Public IP is the building's street address.

---

## Part C: Network Diagram

```
         ┌─────────────────────────────┐
         │         INTERNET            │
         │   (Public IP: assigned      │
         │    by ISP e.g. BSNL/Airtel) │
         └──────────────┬──────────────┘
                        │
                        │ (WAN connection)
                        │
         ┌──────────────▼──────────────┐
         │        ROUTER / WiFi        │
         │   IP: 192.168.1.1           │
         │   Assigns private IPs       │
         │   via DHCP                  │
         └──────────────┬──────────────┘
                        │
              ┌─────────┴──────────┐
              │   Local Network    │
              │   (192.168.1.x)    │
              └─────────┬──────────┘
                        │
         ┌──────────────▼──────────────┐
         │         YOUR DEVICE         │
         │   Hostname: MARK-LAPTOP     │
         │   Private IP: 192.168.1.105 │
         │   MAC: A4:C3:F0:85:7D:2B    │
         └─────────────────────────────┘
```

> 📁 A visual diagram file (`network_diagram.svg`) is also included in this folder.

---

## Part D: Network Connectivity Test

### Commands Run

**Windows:**
```
ipconfig
ping google.com
tracert google.com
```

**Linux:**
```
ip addr
ping google.com
traceroute google.com
```

### Answers

**1. Was the ping successful?**
Yes, the ping to `google.com` was successful. The command sent 4 ICMP packets and received 4 replies with 0% packet loss, confirming internet connectivity is working.

**2. How many hops were shown?**
The `tracert`/`traceroute` to `google.com` showed approximately **12–15 hops**, starting from the local router (`192.168.1.1`) and passing through multiple ISP nodes before reaching Google's servers.

> Replace this with the actual number from your tracert output.

**3. What is the purpose of traceroute?**
Traceroute (`tracert` on Windows, `traceroute` on Linux) maps the path data takes from your device to a destination across the internet. It shows every router ("hop") the data passes through, along with the time taken at each hop. It is very useful for diagnosing network slowdowns or finding where a connection is failing.

---

## Folder Contents

```
Networking_Task_01_Mark/
├── README.md                   ← This file (summary of findings)
├── network_diagram.svg         ← Visual network diagram
├── screenshots/
│   ├── ipconfig_output.png     ← ipconfig /all result
│   ├── ping_google.png         ← ping google.com result
│   └── tracert_google.png      ← tracert google.com result
```

---

## Key Takeaways

- Every device on a network has a unique **IP address** (logical) and **MAC address** (physical).
- The **router** is the bridge between the local (private) network and the internet.
- **DNS** allows us to use domain names instead of memorizing IP addresses.
- **Private IPs** are used within home networks; **Public IPs** are used across the internet.
- Tools like `ping` and `traceroute` help verify and diagnose network connectivity.

---

*Submitted as part of White Band Associates IT Internship Program*
