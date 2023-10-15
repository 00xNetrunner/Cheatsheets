You're right, my mistake. Here is the Markdown with the titles unboxed and the commands in code blocks:

# Wi-Fi Handshake Capture & Crack Cheatsheet 📡

## Table of Contents 📋

- [Preliminary Commands & Information Retrieval](#preliminary)
- [Capture & Conversion Phase](#capture)
- [Additional Scans & Information](#additional) 
- [Cracking Phase](#cracking)
- [5GHz Network Capturing Cheat Sheet](#5ghz)

## Preliminary Commands & Information Retrieval

**Secure Copy from Remote Device**

```
scp -r root@172.16.42.1:/root/example.pcapng /home/username/Desktop
```

📖 Downloads files from remote devices using SCP.

**Check Wireless Interfaces** 

```
iwconfig
```

📖 Displays wireless network interface details.

**Kill Interfering Services**

```  
airmon-ng check kill
```

📖 Stops services that might interfere with wireless tools.

## Capture & Conversion Phase

**Set Wireless Card to Monitor Mode**

```
sudo ip link set wlan0 down  
sudo iw wlan0 set monitor control
sudo ip link set wlan0 up
```

📖 Prepares the wireless card for capture.

**Capture Handshakes with hcxdumptool** 

```
hcxdumptool -i wlan1 -o dumpfile.pcapng --active_beacon --enable_status=15
```

📖 Captures packets from networks.

**Convert Captured File for Hashcat**

```
hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng
``` 

📖 Converts packets for password cracking.

## Additional Scans & Information

**Scan for Nearby Networks**

```
hcxdumptool --do_rcascan -i wlan1 
```

📖 Scans and displays nearby networks.

## Cracking Phase 

**Crack with Hashcat**

```
hashcat -m 22000 hash.hc22000 wordlist.txt
```

📖 Uses hashcat to attempt password cracks.

## 5GHz Network Capturing Cheat Sheet

1. **Install Necessary Tools**

   ```
   sudo apt-get install hcxdumptool hcxtools
   ```

2. **Check for 5GHz Support**

   ```
   iw list
   ```

3. **Enable Monitor Mode**

   ```
   sudo ip link set wlan0 down
   sudo iw dev wlan0 set type monitor
   sudo ip link set wlan0 up
   ```

4. **Set to 5GHz Channel**

   ```
   sudo iw dev wlan0 set channel 36
   ```

5. **Identify Target Networks**

   ```
   sudo hcxdumptool -i wlan0 --scan
   ```

6. **Capture Traffic**

   ```
   sudo hcxdumptool -i wlan0 --enable_status=1 -o output.pcapng --filterlist=filterlist.txt --filtermode=2
   ```

7. **Analyze Captured Traffic**

   ```
   hcxpcaptool -z output.hccapx output.pcapng
   ```

8. **Troubleshooting**

   ```
   sudo iw reg get
   sudo iw reg set US
   ```

9. **Switch Back to 2.4GHz**

   ```
   sudo ip link set wlan0 down
   sudo iw dev wlan0 set type monitor
   sudo iw dev wlan0 set channel 6
   sudo ip link set wlan0 up
   ```

10. **List 2.4GHz Channels**

    ```
    iw phy phy0 channels
    iwlist wlan0 channel
    ```

Let me know if this looks better or if you need any other changes!
