---
title: Content Discovery
date: 2025-06-30 18:30
tags:
  - pentest
  - red
  - web
description: Short summary of the post.
toc: true
share: true
---

Content is all types of media : video, image, file, backup.
there are 3 main ways to discover these media : Manually, Automated and OSINT.
## Manual Discorvery :

### 1. Robots.txt :
a file made to tell search engines which pages to not index, usually you find the assets folder there.

### 2. Favicon : 
sometimes the devs forget to change the favicon from the default one, it tells us which framework they are using  so we can search for it's vulnerabilities.
we can use the OWASP website to compare our favicon to known ones.
we do that by taking the md5 hash of the favicon, using this kind of command :
```bash
curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
```
and then searching for it int their website : https://wiki.owasp.org/index.php/OWASP_favicon_database

### 3. sitemap.xml : 
this one indicate which pages to index in search engines.

### 4. HTTP Headers : 
we can use headers to know which stack/language/technologies the website is using, ex : 

```http
GET / HTTP/1.1 
Host: MACHINE_IP 
User-Agent: curl/7.68.0 
Accept: */* 

HTTP/1.1 200 OK 
Server: nginx/1.18.0 (Ubuntu) 
X-Powered-By: PHP/7.4.3 
Date: Mon, 19 Jul 2021 14:39:09 GMT 
Content-Type: text/html; charset=UTF-8 
Transfer-Encoding: chunked 
Connection: keep-alive
```
## OSINT
### 1. Google Dorking : 
using google specific syntax to search results otherwise not found

**site:tryhackme.com :** returns results from the specified website address.
**inurl:admin :** returns results that have the specified word in the URL.
**filetype:pdf :** returns results which are a particular file extension.
**ntitle:admin :** returns results that contain the specified word in the title.

### 2. Wappalyzer :
Wappalyzer ([https://www.wappalyzer.com/](https://www.wappalyzer.com/)) is an online tool and browser extension that helps identify what technologies a website use

### 3. Wayback Machine : 
The Wayback Machine ([https://archive.org/web/](https://archive.org/web/)) an archive of internet content since the 90s.

### 4. Github : 
Searching companies or individuals on github may reveal source code or credentials of their system.

### 5. S3 Buckets : 
S3 Buckets are a storage service provided by Amazon AWS, The format of the S3 buckets is http(s)://**{name}.**[**s3.amazonaws.com**](http://s3.amazonaws.com/) where {name} is decided by the owner,one common automation method of finding them is by using the company name followed by common terms such as **{name}**-assets, **{name}**-www, **{name}**-public, **{name}**-private, etc.

## Automated Discovery
we use fuzzing to discover hidden pages, by using tools like gobuster, ffuf and dirb.

- Using ffuf:
```shell-session
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt -u http://MACHINE_IP/FUZZ
```

- Using dirb:
```shell-session
user@machine$ dirb http://MACHINE_IP/ /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
```

* Using Gobuster:
```shell-session
user@machine$ gobuster dir --url http://MACHINE_IP/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
```