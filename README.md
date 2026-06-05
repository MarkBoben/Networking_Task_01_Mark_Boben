# Networking Task 01: Understanding Your Network Environment
**White Band Associates | Submitted by: Mark**

---

## Part A: Network Information


| # | Detail | Value (Example) |
|---|--------|-----------------|
| 1 | Hostname (Device Name) | `DESKTOP-86E9DBM` |
| 2 | IPv4 Address | `192.168.1.8` |
| 3 | MAC Address | `7C-70-DB-D0-xx-xx` |
| 4 | Default Gateway | `192.168.1.1` |
| 5 | DNS Server | `192.168.1.1` (Google DNS) |

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
An IP (Internet Protocol) address is a unique numerical label assigned to every device connected to a network. It works like a home address — just as a postman uses your address to deliver letters, the network uses IP addresses to route data to the correct device. Example: `192.168.1.8`

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
         │   Hostname: DESKTOP-86E9DBM     │
         │   Private IP: 192.168.1.8 │
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
Yes, the ping to `google.com` was successful. All 4 packets were sent and received with **0% packet loss**. The response came from Google's IP `142.250.205.14` with a consistent round-trip time of **22ms** (min=22ms, max=22ms, avg=22ms), confirming stable internet connectivity.

**2. How many hops were shown?**
The `tracert` to `google.com` showed **8 hops** in total:
| Hop | Address | Note |
|-----|---------|------|
| 1 | 192.168.1.1 | Local router (Default Gateway) |
| 2 | 111.92.105.1 (asianet.co.in) | ISP — Asianet Broadband |
| 3 | * * * | Request timed out (firewall blocked) |
| 4 | 202.88.230.130 (asianet.co.in) | ISP backbone node |
| 5 | 142.250.173.164 | Google network |
| 6 | 142.251.227.215 | Google network |
| 7 | 209.85.248.211 | Google network |
| 8 | 142.250.205.14 (pnmaaa-bc-in-f14.1e100.net) | Google destination server |

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
