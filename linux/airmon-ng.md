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



