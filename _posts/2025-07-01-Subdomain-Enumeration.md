---
title: Subdomain Enumeration
date: 2025-07-01 01:00
tags:
  - red
  - try-hack-me
  - web
description: Short summary of the post.
toc: true
share: true
---

the process of searching for hidden subdomains that give you access to hidden parts of the website, there are 3 main ways to do it : Brute Force, OSINT and Virtual-Host.

## OSINT :
### 1. SSL/TLS Certificates :
you can use  [crt.sh](https://crt.sh/) to query for domains in Certificate Transparency (CT) logs, to see resembling domains and the history of their registry. 

### 2. Google search : 
querying for stuff like these gets you domains related to the website that are indexed : 
```
site:*.domain.com -site:www.domain.com
```

## BruteForce : 
### 1. DNS Recon :
[DNS Recon](https://www.kali.org/tools/dnsrecon/) a tool used to bruteforce subdomains using a wordlist : 
```bash
dnsrecon -t brt -d domain.com
```

### 2. Sublister : 
we automate the osint methods by using [Sublist3r](https://www.kali.org/tools/sublist3r/):  
```bash
./sublist3r.py -d domain.com
```

## Virtual Hosts : 
we can fuzz the host header  of the http request and monitor the response, we can do that by using ffuf :
```bash
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://MACHINE_IP
```
-w: wordlist
-H: add Header
-u: Url 

if we are getting all 200 OK responses we can use *-fs* flag to exlude responses with a certain size :
```bash
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://MACHINE_IP -fs {size}
```