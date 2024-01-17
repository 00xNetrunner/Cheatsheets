
# NMAP Cheat Sheet 🖥️

## Table of Contents 📋

1. [Ping Scanning](#ping-scanning) 📡
2. [ARP Scanning](#arp-scanning) 📶
3. [SYN Scanning](#syn-scanning) 👾
4. [UDP Scanning](#udp-scanning) 💾
5. [Useful Nmap Switches](#useful-nmap-switches) ⚙️
6. [Identifying OS and Applications](#identifying-os-and-applications) 🤖
7. [Nmap Scripts](#nmap-scripts) 📜
8. [Batch Script for Nmap](#batch-script-for-nmap) 💻

## Ping Scanning 📡

```bash
nmap -sn 192.168.10.1
nmap -sP 192.168.10.2
```

## ARP Scanning 📶

```bash  
nmap -sP -PR 192.168.10.1
```

> **Note**: Press the spacebar to show the current progression of the scan.

## SYN Scanning 👾

```bash
nmap -sS 192.168.10.1 
```

## UDP Scanning 💾

```bash
nmap -sU 192.168.10.1
```

## Useful Nmap Switches ⚙️

- `-h` : Help  
- `-v` : Verbose
- `-vv` : Very Verbose
- `-n` : No DNS Reverse Lookup
- `-T` : Sets the speed of the scan (`-T5` being the fastest, `-T0` the slowest)
- `-p` : Specify ports
  - `-p 80` : Specific port
  - `-p 1-10` : Range of ports
  - `-p-` : All ports
- `-o` : To output a file

## Identifying OS and Applications 🤖

- `-sV` : Enable Version Detection
- `-O` : Enable OS Detection 
- `-A` : Enable OS Detection, Version Detection, Script Scanning, and Traceroute
- `--osscan-guess` : Aggressive OS guessing

## Nmap Scripts 📜

**Syntax**: `nmap —script scriptname targetIP`

Examples:

```bash
nmap —script http-headers 192.168.10.1
nmap —script smtp-commands 192.168.10.1  
nmap -sV --script=banner 192.168.10.1
nmap -sV --script=smb* 192.168.10.1
nmap --script=http-title 192.168.10.1
nmap --script=http-enum 192.168.10.0/24
```

> [How to Use Nmap Script Engine (NSE) Scripts in Linux](https://www.tecmint.com/use-nmap-script-engine-nse-scripts-in-linux/)

## Batch Script for Nmap 💻

1. First, download Neovim or your favorite text editor. 📝

2. Create a file named `nmapScan.sh`.

```bash
#!/bin/bash

nmap -sT -p 1-10000 -v -v -T5 -sV -O --osscan-guess --script=banner -oN 192.168.10.1TCP.txt 192.168.10.1 

nmap -sU -p 1-500 -v -v --scan-delay 1s -sV --script=banner -oN 192.168.10.1UDP.txt 192.168.10.1

nmap -sT -p 1-10000 -v -v -T5 -sV -O --osscan-guess --script=banner -oN 192.168.10.2TCP.txt 192.168.10.2

nmap -sU -p 1-500 -v -v --scan-delay 1s -sV --script=banner -oN 192.168.10.2UDP.txt 192.168.10.2
```

3. Save and exit. 💾

4. Make the script executable: 

```bash
sudo chmod +x nmapScan.sh
```

5. Run the script:

```bash 
sudo ./nmapScan.sh
```
