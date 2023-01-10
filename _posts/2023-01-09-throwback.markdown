---
layout: post
title:  "Throwback Writeup"
date:   2023-01-09 20:37:00 +0000
categories: thm
---

![throwback logo banner image](/assets/img/posts/throwback/banner.webp)

[Throwback] in Active Directory lab that teaches the fundamentals and core concepts of attacking a Windows network. The network simulates a realistic corporate environment that has several attack vectors you would expect to find in today’s organisations.

# Contents
1. [Network Enumeration](#Enumeration)
2. [THROWBACK-FW01](#throwback-fw01)
 - [Logging In](#logging-in)
 - [Reverse Shell](#reverse-shell)
 - [Flags](#flags)
 - [Credentials](#credentials)
3. [THROWBACK-MAIL](#throwback-mail)
 - [So](#)
 - [Cool!](#)
 - [Cool!](#)
3. [THROWBACK-PROD](#throwback-prod)
 - [So](#)
 - [Cool!](#)
 - [Cool!](#)

# Enumeration
---

The initial network scope looks like this:
![image of initial network map](/assets/img/posts/throwback/network_layout.webp)

Using nmap for initial enumeration, I discovered 3 of the in-scope machines and their open ports, as well as the name of the domain that they're apart of.

**Command**
```shell
nmap -sV -sC -p- -v 10.200.29.0/24 --min-rate 5000
```

**THROWBACK-FW01** (10.200.29.219)
```shell
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 7.5 (protocol 2.0)
| ssh-hostkey:
|_  4096 3804a0a1d0e6abd97dc0daf366bf7715 (RSA)
53/tcp  open  domain   (generic dns response: REFUSED)
80/tcp  open  http     nginx
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to https://10.200.29.138/
443/tcp open  ssl/http nginx
|_http-title: pfSense - Login
|_http-favicon: Unknown favicon MD5: 5567E9CE23E5549E0FCD7195F3882816
| ssl-cert: Subject: commonName=pfSense-5f099cf870c18/organizationName=pfSense webConfigurator Self-Signed Certificate
| Subject Alternative Name: DNS:pfSense-5f099cf870c18
| Issuer: commonName=pfSense-5f099cf870c18/organizationName=pfSense webConfigurator Self-Signed Certificate
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-07-11T11:05:28
| Not valid after:  2021-08-13T11:05:28
| MD5:   fe06fa474d838454e67a18407ea8d101
|_SHA-1: 672e5f8f9b287cad5789c5becb1cf3f26c63dfb2
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port53-TCP:V=7.93%I=7%D=1/8%Time=63BB2F58%P=x86_64-pc-linux-gnu%r(DNSVe
SF:rsionBindReqTCP,E,"\0\x0c\0\x06\x81\x05\0\0\0\0\0\0\0\0");
```

**THROWBACK-MAIL** (10.200.29.232)
```shell
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 16c4ef3847a61726faa58c24bffefad0 (RSA)
|   256 95e9e05ea4f691920dd34c9d1e633673 (ECDSA)
|_  256 7d82c060336364ed23c49d4f458d100a (ED25519)
80/tcp  open  http     Apache httpd 2.4.29 ((Ubuntu))
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-favicon: Unknown favicon MD5: 2D267521ED544C817FADA219E66C0CCC
|_http-server-header: Apache/2.4.29 (Ubuntu)
| http-title: Throwback Hacks - Login
|_Requested resource was src/login.php
143/tcp open  imap     Dovecot imapd (Ubuntu)
|_imap-capabilities: IDLE more SASL-IR ENABLE have LOGIN-REFERRALS listed capabilities Pre-login IMAP4rev1 STARTTLS ID LITERAL+ post-login LOGINDISABLEDA0001 OK
| ssl-cert: Subject: commonName=ip-10-40-119-232.eu-west-1.compute.internal
| Subject Alternative Name: DNS:ip-10-40-119-232.eu-west-1.compute.internal
| Issuer: commonName=ip-10-40-119-232.eu-west-1.compute.internal
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-07-25T15:51:57
| Not valid after:  2030-07-23T15:51:57
| MD5:   adc4c6e2d74fd9ebccde96aa5780bb69
|_SHA-1: 93aa5da038298ca3aa6bf1484f921ed0c568a942
|_ssl-date: TLS randomness does not represent time
993/tcp open  ssl/imap Dovecot imapd (Ubuntu)
| ssl-cert: Subject: commonName=ip-10-40-119-232.eu-west-1.compute.internal
| Subject Alternative Name: DNS:ip-10-40-119-232.eu-west-1.compute.internal
| Issuer: commonName=ip-10-40-119-232.eu-west-1.compute.internal
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-07-25T15:51:57
| Not valid after:  2030-07-23T15:51:57
| MD5:   adc4c6e2d74fd9ebccde96aa5780bb69
|_SHA-1: 93aa5da038298ca3aa6bf1484f921ed0c568a942
|_ssl-date: TLS randomness does not represent time
|_imap-capabilities: IDLE SASL-IR ENABLE more have LOGIN-REFERRALS ID capabilities Pre-login OK IMAP4rev1 LITERAL+ post-login listed AUTH=PLAINA0001
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

**THROWBACK-PROD** (10.200.29.219)
```
PORT      STATE SERVICE       VERSION
22/tcp    open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey:
|   2048 85b81f80463d910f8cf2f23f5c876772 (RSA)
|   256 5c0d46e942d44da036d619e5f3ce4906 (ECDSA)
|_  256 e22acb39850f7306a9239dbfbef7500c (ED25519)
80/tcp    open  http          Microsoft IIS httpd 10.0
| http-methods:
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Throwback Hacks
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
3389/tcp  open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=THROWBACK-PROD.THROWBACK.local
| Issuer: commonName=THROWBACK-PROD.THROWBACK.local
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2023-01-07T17:54:36
| Not valid after:  2023-07-09T17:54:36
| MD5:   6e5dc09a9b9f46a346ca0e4cbe314946
|_SHA-1: c4f43d1f164d858a57e15ef171975c6698a9383e
|_ssl-date: 2023-01-08T21:04:29+00:00; -3s from scanner time.
5357/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Service Unavailable
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49667/tcp open  msrpc         Microsoft Windows RPC
49669/tcp open  msrpc         Microsoft Windows RPC
49680/tcp open  msrpc         Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: -3s, deviation: 0s, median: -4s
| smb2-time:
|   date: 2023-01-08T21:02:56
|_  start_date: N/A
| smb2-security-mode:
|   311:
|_    Message signing enabled but not required
```

## Throwback FW01
---
Going to the firewall's web interface, it confirmed that it is running **pfsense**, which has an administrator login.

![pfsense login page](/assets/img/posts/throwback/1_pfsense_login_page.webp)

### Logging In

However, the default crededntials were never changed and therefore, I was able to simply login to the panel using the  default credentials `admin:pfsense`.

![logged in to pfsense panel](/assets/img/posts/throwback/2_pfsense_admin.webp)

### Reverse Shell

Then, after poking around what the panel has to offer, I found a diagnostics page (under Diagonistics > Command Prompt), which conveniently allowed for code execution in both bash shell and PHP form, as well as file upload and download. So naturally, I executed [this](https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php) PHP reverse shell in the interface, opened a listener on my machine, and got root access to THROWBACK-FW01. That was easy.

![php reverse shell in diagnostics tab](/assets/img/posts/throwback/3_pfsense_phprs.webp)

![reverse shell from my machine](/assets/img/posts/throwback/4_pfsense_root.webp)

### Flags

Using the following command, I was able to find search for .txt files on the machine to find the flags.

```shell
find / -iname "*.txt" 2>&1
```

This way, I found flags 3 and 4.

![flags 3 and 4](/assets/img/posts/throwback/5_fw01_flags.webp)

### Credentials

Also in `/var/logs/` I found the unusual log `login.log`, which contained encrypted credentials to a user **HumphreyW**.

![humphreyws credentials in login.log](/assets/img/posts/throwback/6_humphreyw_creds.webp)

His password was easily cracked using [Crackstation](https://crackstation.net/)

![humphreyws cracked password](/assets/img/posts/throwback/7_humphrey_cracked.webp)

And thats all I was able to get out of this machine for now.

[Throwback]: https://tryhackme.com/room/throwback
