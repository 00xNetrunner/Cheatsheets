Here is the Aircrack-ng cheatsheet converted to Markdown:

# Aircrack-ng Cheatsheet 🚀

Aircrack-ng is a comprehensive toolkit for auditing wireless networks.

## Table of Contents

- [Airmon-ng](#airmon)
- [Airodump-ng](#airodump)
- [Aireplay-ng](#aireplay) 
- [Aircrack-ng](#aircrack)
- [Conversion to .pcapng](#conversion)

## 1. Airmon-ng ⚙️

```
airmon-ng start wlan0
```

Initializes monitor mode on `wlan0`. Generates a virtual monitor interface, typically named `wlan0mon`.

```
airmon-ng stop wlan0mon
```

## 2. Airodump-ng 📡

```
airodump-ng wlan0mon
airodump-ng wlan1 --band a
```

## 3. Aireplay-ng 💥

```
aireplay-ng -0 1 -a [BSSID] -c [client MAC] wlan0mon 
```

## 4. Aircrack-ng 🔓

```
aircrack-ng -a 1 -b [BSSID] [capture.cap]
aircrack-ng -a 2 -b [BSSID] -w [dictionary.txt] [capture.cap]
```

## 5. Conversion to .pcapng ⚙️

```
tshark -r [input.cap] -w [output.pcapng]
```

![Screenshot](Screenshot_2023-09-29_235515.png)

Let me know if you need any changes to the Markdown formatting!
