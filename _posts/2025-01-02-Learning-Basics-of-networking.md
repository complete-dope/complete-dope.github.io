---
layout: post
title: Learning Basics of networking
date: 2025-01-02
---

## Basics of Networking

[Google doc link ](https://docs.google.com/document/d/1dQU7fJDfAWogpLl-JptT1eaHzGoXHpcx_y3KVeejCAc/edit?usp=sharing)


### SSH explained 

`ssh` is a secure way to connect to a machine 

**Logic** 
A 2 layer key is setup , a public and private key you 

**Setup** 
Lets say a machine in London wants to talk to a machine in Delhi , london machine is connected to wifi and has a fixed internal IP ( 192.168.1.200 ) , the wifi IP is Dynamic , so in the router's setting we need to create a port forwarding rule to internal IP (192.168.1.200) on port 22

and on the Delhi machine we need to turn connect using: 
`ssh -p 2222 your_username@Public_IP` : This tells ssh to connect to router's public IP     

**Working** 



### TCP explained ( Transmission control protocol )

A protocol to send data over internet its nothing just a reliable method and ensures reliability of data. 

**Logic and Example** 

Example: 
Lets say you want to share 10MB of data from your device on internet
The OS just hands over it to networking stack that has TCP built into it 

TCP breaks it into smaller chunks called segments. 
Labeling, each segment gets a unique sequence number
IP layer to provide the headers to the data 

The Data Link layer (handled by your NIC and drivers) and the Physical layer (your network hardware, e.g., Ethernet, Wi-Fi).

**Setup**



**Working**
















