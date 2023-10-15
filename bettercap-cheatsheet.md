Here is the Bettercap cheatsheet in Markdown format with emojis:

# 🕵️‍♀️ **Bettercap Cheatsheet** 🕵️

Bettercap is an indispensable tool for network reconnaissance, sniffing, and executing Man-In-The-Middle (MITM) attacks on local networks.

---

## Table of Contents

1. [🔍 Network Reconnaissance](#-network-reconnaissance)
2. [🥷 ARP Spoofing](#-arp-spoofing)
3. [📡 Network Sniffing](#-network-sniffing)  
4. [🕸 Web Proxy](#-web-proxy)
5. [🚦 TLS Proxy](#-tls-proxy)
6. [🌀 DNS Spoofing](#-dns-spoofing)
7. [💻 HTTPS & HSTS Bypass](#-https--hsts-bypass)
8. [📌 Miscellaneous Commands](#-miscellaneous-commands)

---

## 🔍 **Network Reconnaissance**

- `net.probe on` 👀

- Initiate an ARP scan to discover live hosts on the network.

- `net.show` 📡  

- Display detected devices on the network, complete with IPs, MAC addresses, and other details.

- `net.recon on/off` 🕵️‍♂️

- Enable/disable passive network traffic analysis to discover hosts.

---

## 🥷 **ARP Spoofing** 

- `set arp.spoof.targets [IP]` ✨

- Designate a target IP for ARP cache poisoning to reroute its traffic.

- `arp.spoof on/off` 💥

- Engage/disengage ARP spoofing against the chosen target. 

- `set arp.spoof.internal true` 🔁

- Poison ARP caches for all connections between internal hosts on the LAN.

---

## 📡 **Network Sniffing**

- `net.sniff on/off` ▶️⏸️

- Begin/halt packet capture to log network traffic.

---

## 🕸 **Web Proxy**

- `set proxy.port [PORT]` 🤖

- Assign the listening port for the proxy server.

- `proxy on/off` 🎚️🛑

- Activate/deactivate the proxy server to intercept and manipulate HTTP requests.

---

## 🚦 **TLS Proxy** 

- `tls.proxy on/off` 🔓🔒

- Enable/disable the TLS proxy. This intercepts and decrypts HTTPS traffic by mimicking certificate validation.

---

## 🌀 **DNS Spoofing**

- `set dns.spoof.domains [DOMAIN]` 🌐

- Select a domain for DNS hijacking.  

- `dns.spoof on` 🥷

- Activate DNS response spoofing for the specified domain.

---

## 💻 **HTTPS & HSTS Bypass**

- `hstshijack.load` 🛡️

- Load the module to overcome HSTS, a web security protocol, useful for exploiting HTTPS sites.

---

## 📌 **Miscellaneous Commands**

- `events.clear` 🧹

- Wipe out all recorded network events.

- `set [OPTION] [VALUE]` ⚙️

- Adjust configuration options to suit your needs.

- `help` ❓

- Display the help menu with an overview of commands.

---

Let me know if you need any changes to the formatting!
