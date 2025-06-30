
---

## 🛰️ Task 1: Reconnaissance & Scanning

**Tools**: [`nmap`](https://nmap.org/), [`netdiscover`](https://github.com/alexxy/netdiscover)
**Goal**: Enumerate live hosts, detect open ports, discover services and gather OS-level information about target systems.

### 🔧 Steps

```bash
# Step 1: Discover live hosts on your local network
sudo netdiscover -r 192.168.1.0/24

# Step 2: Scan a specific host for open ports and service versions
nmap -sS -sV -T4 -Pn 192.168.1.10

# Step 3: Run an aggressive scan (includes OS detection, scripts, and traceroute)
nmap -A 192.168.1.10
```

### 🧠 What to Look For

* Live IPs and MAC addresses (via `netdiscover`)
* Open ports (e.g., 22, 80, 443, 3306)
* Running services and their versions
* Potential OS type and device fingerprinting

### ✅ Use Cases

* Network inventory before an attack simulation
* Target selection for vulnerability scanning
* Mapping unknown or undocumented subnets


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
