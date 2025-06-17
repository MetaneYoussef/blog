---
title: Pakcets & Frames
date: 2025-06-17 20:00
tags:
  - Networking
  - basics
description: OSI model continuation.
toc: true
share: true
media_subpath: /Ressources/
---
Status : #In_Progress 
Tags : [Networking](Networking.md),[basics](basics.md)


## Packets & Frames
#### Packet : envelope
#### Frame : the letter

## TCP/IP (The Three-Way Handshake)

Only 4 layers :
- Application
- Transport
- Internet
- Network Interface

### TCP 3 Way Handshake
![handshake 1](/Ressources/TCP-three-way-handshake-process-1-1-2048x695.png)
![handshake 2](/Ressources/TCP-three-way-handshake-process-2-1024x171.png)
![handshake 3](/Ressources/TCP-three-way-handshake-process-3-1024x171.png)

- **DATA :** Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message.
- **FIN :** This packet is used to Cleanly (properly) close the connection after it has been complete.
- **RST :** This packet abruptly ends all communication.
## UDP 

UDP is **stateless**. No acknowledgement is sent during a connection.
![53d459ccda57e5fdea0dafe7e64ffe7c.svg](53d459ccda57e5fdea0dafe7e64ffe7c.svg)

## Ports
These ports enforce what can park and where — if it isn't compatible, it cannot park here. Networking devices also use ports to enforce strict rules when communicating with one another. When a connection has been established (recalling from the OSI model's room), any data sent or received by a device will be sent through these ports. In computing, ports are a numerical value between **0** and **65535** (65,535).
Resource Material : https://www.vmaxx.net/techinfo/ports.htm