
````markdown
# 🛡️ Cybersecurity Hands-On Lab

This repository contains practical cybersecurity tasks for learning key techniques in network scanning, web application vulnerability assessment, password cracking, and packet analysis using industry-standard open-source tools.

---

## 🛰️ Task 1: Reconnaissance & Scanning

**Tools**: `nmap`, `netdiscover`  
**Goal**: Identify active hosts, open ports, services, and operating systems in a network.

### 🔧 Commands

```bash
# Discover live hosts on the local subnet
sudo netdiscover -r 192.168.1.0/24

# Perform a TCP SYN scan with service/version detection
nmap -sS -sV -T4 -Pn 192.168.1.10

# Comprehensive scan with OS detection and scripts
nmap -A 192.168.1.10
````

---

## 🌐 Task 2: Web Application Vulnerability Scanning

**Tool**: [OWASP ZAP](https://www.zaproxy.org/)
**Goal**: Identify vulnerabilities in web applications such as XSS, SQL Injection, and security misconfigurations.

### 🔧 Steps

```bash
# Launch OWASP ZAP on macOS
open -a "OWASP ZAP"
```

1. Start ZAP and explore a target app (e.g., DVWA, Juice Shop).
2. Use **Spider** or **Manual Explore** to map the app.
3. Right-click the target URL in the Sites pane → **Attack** → **Active Scan**.
4. Monitor the **Alerts** tab for detected vulnerabilities:

   * XSS (Reflected/Stored)
   * SQL Injection
   * Insecure Cookies
   * Missing Headers

---

## 🔓 Task 3: Password Cracking

**Tools**: `John the Ripper`, `Hashcat`
**Goal**: Crack password hashes using dictionary or brute-force methods.

### 🔧 Commands

```bash
# Crack hashes using John the Ripper with a wordlist
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt

# Crack MD5 hashes using Hashcat
hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt
```

> Replace `-m 0` with appropriate hash mode (e.g., `-m 100` for SHA1, `-m 1800` for SHA512crypt)

---

## 📡 Task 4: Packet Analysis with Wireshark

**Tool**: [Wireshark](https://www.wireshark.org/)
**Goal**: Capture and analyze packets to detect anomalies or attacks.

### 🔧 Tips

* Start Wireshark and capture traffic on your active network interface.
* Use filters to isolate useful data:

```wireshark
http.request
ip.addr == 192.168.1.10
tcp.port == 80
ftp || telnet
```
