<!DOCTYPE html>
<html>
<head>
    <title>Aircrack-ng Cheatsheet</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        h1, h2, h3 {
            color: #333;
        }
        code {
            background-color: #f0f0f0;
            padding: 2px;
            border-radius: 4px;
        }
        pre {
            background-color: #f8f8f8;
            padding: 10px;
            border-radius: 4px;
        }
    </style>
</head>
<body>

<h1>Aircrack-ng Cheatsheet 🚀</h1>

<p>Aircrack-ng is a comprehensive toolkit for auditing wireless networks.</p>

<h2>Table of Contents</h2>
<ul>
    <li><a href="#airmon">Airmon-ng</a></li>
    <li><a href="#airodump">Airodump-ng</a></li>
    <li><a href="#aireplay">Aireplay-ng</a></li>
    <li><a href="#aircrack">Aircrack-ng</a></li>
    <li><a href="#conversion">Conversion to .pcapng</a></li>
</ul>

<h2 id="airmon">1. Airmon-ng ⚙️</h2>
<pre>
<code>airmon-ng start wlan0</code>
</pre>
<p>Initializes monitor mode on <code>wlan0</code>. Generates a virtual monitor interface, typically named <code>wlan0mon</code>.</p>
<pre>
<code>airmon-ng stop wlan0mon</code>
</pre>

<h2 id="airodump">2. Airodump-ng 📡</h2>
<pre>
<code>airodump-ng wlan0mon</code>
<code>airodump-ng wlan1 --band a</code>
</pre>

<h2 id="aireplay">3. Aireplay-ng 💥</h2>
<pre>
<code>aireplay-ng -0 1 -a [BSSID] -c [client MAC] wlan0mon</code>
</pre>

<h2 id="aircrack">4. Aircrack-ng 🔓</h2>
<pre>
<code>aircrack-ng -a 1 -b [BSSID] [capture.cap]</code>
<code>aircrack-ng -a 2 -b [BSSID] -w [dictionary.txt] [capture.cap]</code>
</pre>

<h2 id="conversion">5. Conversion to .pcapng ⚙️</h2>
<pre>
<code>tshark -r [input.cap] -w [output.pcapng]</code>
</pre>

<!-- Your screenshot can be added here -->
<img src="Screenshot_2023-09-29_235515.png" alt="Screenshot" />

</body>
</html>
