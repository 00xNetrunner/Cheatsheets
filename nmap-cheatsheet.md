
```markdown
# NMAP Cheat Sheet 🛠️👨‍💻

## Table of Contents

1. [Ping Scanning](#ping-scanning)
2. [ARP Scanning](#arp-scanning)
3. [SYN Scanning](#syn-scanning)
4. [UDP Scanning](#udp-scanning)
5. [Useful Nmap Switches](#useful-nmap-switches)
6. [Identifying OS and Applications](#identifying-os-and-applications)
7. [Nmap Scripts](#nmap-scripts)
8. [Batch Scripts](#batch-scripts)

---

### Ping Scanning 🏓

```bash
nmap -sn 192.168.10.1
nmap -sP 192.168.10.2
```

### ARP Scanning 🌐

```bash
nmap -sP -PR 192.168.10.1
```
> **Tip**: Press the spacebar to show the current progression of the scan.

### SYN Scanning 🚀

```bash
nmap -sS 192.168.10.1
```

### UDP Scanning 🚁

```bash
nmap -sU 192.168.10.1
```

### Useful Nmap Switches 🎛️

- `-h` help
- `-v` verbose
- `-vv` very verbose
- `-n` no DNS reverse lookup
- `-T` sets the speed of the scan (`-T5` being the fastest, `-T0` the slowest)
- `-p 80` specific port
- `-p 1-10` range of ports
- `-p-` all ports
- `-o` to output a file

### Identifying OS and Applications 🖥️

- `-sV` enable version detection
- `-O` enables OS detection
- `-A` enables OS detection, Version detection, Script scanning, and traceroute
- `--osscan-guess` Aggressive OS guessing

### Nmap Scripts 📜

**Syntax**: `nmap —script scriptname targetIP`

```bash
nmap —script http-headers 192.168.10.1
nmap —script smtp-commands 192.168.10.1
```
> **More Info**: [How to Use Nmap Script Engine (NSE) Scripts in Linux](https://www.tecmint.com/use-nmap-script-engine-nse-scripts-in-linux/)

### Batch Scripts 📚

**Steps**:

1. Download `neovim` or your favorite text editor.
2. Create a script file: `nvim nmapScan.sh`
3. Paste the following content:

```bash
#!/bin/bash

nmap -sT -p 1-10000 -v -v -T5 -sV -O --osscan-guess --script=banner -oN 192.168.10.1TCP.txt 192.168.10.1
nmap -sU -p 1-500 -v -v --scan-delay 1s -sV --script=banner -oN 192.168.10.1UDP.txt 192.168.10.1
```

4. Save and exit.
5. Make the script executable:

```bash
sudo chmod +x nmapScan.sh
```

6. Run the script:

```bash
sudo ./nmapScan.sh
```
```

