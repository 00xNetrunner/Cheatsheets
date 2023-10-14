# NMAP Cheat Sheet 🛠️👨‍💻

A comprehensive guide to using Nmap for network scanning.

## Table of Contents

1. [Introduction](#introduction)
2. [Ping Scanning](#ping-scanning)
3. [ARP Scanning](#arp-scanning)
4. [SYN Scanning](#syn-scanning)
5. [UDP Scanning](#udp-scanning)
6. [Useful Nmap Switches](#useful-nmap-switches)
7. [Identifying OS and Applications](#identifying-os-and-applications)
8. [Nmap Scripts](#nmap-scripts)
9. [Batch Scripts](#batch-scripts)

---

### Introduction 📖

Nmap ("Network Mapper") is an open-source tool for network exploration and security auditing. It was designed to rapidly scan large networks, but it also works well against single hosts.

---

### Ping Scanning 🏓

Ping scans are used for checking if the target is alive and responds to ICMP packets.

\`\`\`bash
nmap -sn 192.168.10.1
nmap -sP 192.168.10.2
\`\`\`

---

### ARP Scanning 🌐

ARP (Address Resolution Protocol) scans are particularly effective in LAN environments. It is non-intrusive and fast.

\`\`\`bash
nmap -sP -PR 192.168.10.1
\`\`\`
> **Tip**: Press the spacebar to show the current progression of the scan.

---

### SYN Scanning 🚀

Also known as half-open scanning, SYN scans are less likely to be detected compared to full TCP connection scans but still effective for port identification.

\`\`\`bash
nmap -sS 192.168.10.1
\`\`\`

---

### UDP Scanning 🚁

UDP scans are used for identifying open UDP ports. Note that UDP scans are generally slower than TCP scans.

\`\`\`bash
nmap -sU 192.168.10.1
\`\`\`

---

### Useful Nmap Switches 🎛️

Here are some Nmap switches for various purposes:

- `-h`: Display help menu
- `-v`: Verbose output
- `-vv`: Very verbose output
- `-n`: No DNS resolution
- `-T`: Timing options (0-5)
- `-p`: Specify port or port range
- `-o`: Output scan to file

---

### Identifying OS and Applications 🖥️

Identifying the operating system and applications running on a network can provide valuable information during an assessment.

- `-sV`: Version detection
- `-O`: OS detection
- `-A`: Advanced scan options
- `--osscan-guess`: More aggressive OS guessing

---

### Nmap Scripts 📜

Nmap has a powerful scripting engine that can perform a wide range of tasks.

**Syntax**: `nmap —script scriptname targetIP`

\`\`\`bash
nmap —script http-headers 192.168.10.1
nmap —script smtp-commands 192.168.10.1
\`\`\`

> **More Info**: [How to Use Nmap Script Engine (NSE) Scripts in Linux](https://www.tecmint.com/use-nmap-script-engine-nse-scripts-in-linux/)

---

### Batch Scripts 📚

Automating Nmap scans can save a lot of time. Here's how you can create your own batch script for Nmap.

1. Download and install `neovim` or your favorite text editor.
2. Create a script named `nmapScan.sh`.
3. Make the script executable.
4. Run the script.

\`\`\`bash
#!/bin/bash

nmap -sT -p 1-10000 -v -v -T5 -sV -O --osscan-guess --script=banner -oN 192.168.10.1TCP.txt 192.168.10.1
nmap -sU -p 1-500 -v -v --scan-delay 1s -sV --script=banner -oN 192.168.10.1UDP.txt 192.168.10.1
\`\`\`

