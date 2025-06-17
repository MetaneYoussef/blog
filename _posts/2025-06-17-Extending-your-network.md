---
title: Extending Your Network
date: 2025-06-17 19:46
tags:
  - Networking
  - configuration
  - basics
description: Introduction to homelab seyup from tryhackme.
toc: true
share: true
media_subpath: /Ressources/
---

# Extending Your Network

### Introduction to Port Forwarding

![Portfwd](eb63570eb9f31d26ebd8207ec08058bc.svg){: w="128" }

### Firewall 
Works on the layers 3 and 4
Think of a firewall as border security for a network. An administrator can configure a firewall to **permit** or **deny** traffic from entering or exiting a network based on numerous factors such as:

- Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
- Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
- What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
- What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is UDP, TCP or both?)

it is 2 types : 

Stateful: inspects the entire connection
Stateless: inspect individual packets

### VPN
 **V**irtual **P**rivate **N**etwork (or **VPN** for short)

* PPP:  This technology is used by PPTP (explained below) to allow for authentication and provide encryption of data. VPNs work by using a private key and public certificate (similar to **SSH**). A private key & certificate must match for you to connect.This technology is not capable of leaving a network by itself (non-routable).
* PPTP: The **P**oint-to-**P**oint **T**unneling **P**rotocol (**PPTP**) is the technology that allows the data from PPP to travel and leave a network. PPTP is very easy to set up and is supported by most devices. It is, however, weakly encrypted in comparison to alternatives.
* IPSec: Internet Protocol Security (IPsec) encrypts data using the existing **I**nternet **P**rotocol (**IP**) framework. IPSec is difficult to set up in comparison to alternatives; however, if successful, it boasts strong encryption and is also supported on many devices.
