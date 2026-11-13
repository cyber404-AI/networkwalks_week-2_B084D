# NetworkWalks Internship – Week 2 Project

**Domain:** Cybersecurity & Ethical Hacking  
**Organization:** NetworkWalks  
**Project:** Footprinting & Network Scanning  
**Target Domain:** `networkwalks.com`  
**Environment:** Kali Linux (VMware)  
**Date:** 13 November 2026

---

## 1. Project Overview

This project focuses on practical cybersecurity reconnaissance, domain footprinting, DNS enumeration, web technology identification, Web Application Firewall detection and network scanning.

The objective is to understand how security professionals collect publicly available information about a target domain and identify its exposed network services.

The project includes six Kali Linux tools and the compulsory Zenmap-based network scanning exercise.

## 2. Objectives

- Perform domain footprinting using WHOIS.
- Collect publicly available information using theHarvester.
- Enumerate DNS records using DNSenum.
- Identify web technologies using WhatWeb.
- Detect Web Application Firewall technology using WAFW00F.
- Identify open ports and running services using Nmap.
- Perform graphical network scanning using Zenmap.
- Document observations and security assessment results.

## 3. Tools and Technologies

| No. | Tool | Purpose |
|---|---|---|
| 1 | WHOIS | Domain registration information |
| 2 | theHarvester | Public information gathering |
| 3 | DNSenum | DNS enumeration |
| 4 | WhatWeb | Web technology fingerprinting |
| 5 | WAFW00F | WAF detection |
| 6 | Nmap | Network reconnaissance |
| 7 | Zenmap | Graphical network scanning |

**Operating System:** Kali Linux  
**Virtualization:** VMware Workstation  
**Terminal:** Kali Linux Terminal

## 4. Target Information

| Parameter | Information |
|---|---|
| Domain | networkwalks.com |
| IPv4 Address | 192.232.216.135 |
| Web Server | Apache |
| CMS | WordPress |
| Nameservers | ns6135.hostgator.com, ns6136.hostgator.com |
| Hosting indication | HostGator / UnifiedLayer |

## 5. Practical Implementation

### Tool 1: WHOIS

**Command:**
```bash
whois networkwalks.com
```

**Observations:**
- Registrar identified as GoDaddy.com, LLC.
- Domain creation date: 6 November 2019.
- Domain expiry date: 6 November 2027.
- Nameservers identified.
- DNSSEC reported as unsigned.

**Result:** Successfully retrieved domain registration information.

### Tool 2: theHarvester

**Command:**
```bash
theHarvester -d networkwalks.com -b crtsh
```

**Observations:**
- Data source: CRT.sh.
- No IP addresses returned.
- No email addresses returned.
- No people returned.
- No hostnames returned.

**Result:** The query completed successfully but returned no findings.

### Tool 3: DNSenum

**Command:**
```bash
dnsenum networkwalks.com
```

**Observations:**

- Domain IPv4 address identified: `192.232.216.135`.
- Nameservers identified:
  - ns6135.hostgator.com
  - ns6136.hostgator.com
- Mail server identified: `mail.networkwalks.com`.
- Associated hostnames identified:
  - autodiscover.networkwalks.com
  - ftp.networkwalks.com
  - mail.networkwalks.com
  - webmail.networkwalks.com
  - www.networkwalks.com

**DNS Zone Transfer:**

Both nameservers returned `REFUSED` for AXFR requests.

**Result:** DNS records and associated hostnames were identified. No successful zone transfer was observed.

### Tool 4: WhatWeb

**Command:**
```bash
whatweb networkwalks.com
```

**Observations:**

- Web server: Apache.
- CMS: WordPress 7.1.4 (detected fingerprint).
- Framework: Bootstrap 7.1.4 (detected fingerprint).
- JavaScript library: jQuery 3.7.1.
- WordPress Download Manager: 3.3.76.
- Website title: Networkwalks Academy.
- HTTPS response: 200 OK.
- HTTP response: 301 Moved Permanently.

**Result:** Successfully identified web technologies and server information.

### Tool 5: WAFW00F

**Command:**
```bash
wafw00f https://networkwalks.com
```

**Observations:**

- WAF detection: ModSecurity.
- Associated vendor: SpiderLabs.
- Number of HTTP requests: 2.
- WAFW00F version: 2.3.2.

**Result:** ModSecurity was identified as the likely Web Application Firewall protecting the website.

### Tool 6: Nmap

**Command:**
```bash
nmap -sS -sV networkwalks.com
```

**Command explanation:**
- `-sS`: TCP SYN scan.
- `-sV`: Service and version detection.

**Observations:**

- Target IP: `192.232.216.135`.
- Host status: Up.
- 13 open TCP ports identified.
- 7 filtered TCP ports identified.
- 980 closed TCP ports identified.
- Linux operating system family indicated.

Services identified included:
- FTP
- SSH
- SMTP
- DNS
- HTTP
- HTTPS
- POP3
- IMAP

**Result:** Identified network services, port states and detected software versions.

## 6. Essential Project: Zenmap Network Scanning

**Tool:** Zenmap  
**Target:** networkwalks.com

**Scan profile / command:**
```bash
nmap -sS -sV networkwalks.com
```

**Observations from Zenmap:**

- Host status: Up.
- Open TCP ports: 14.
- Filtered TCP ports: 6.
- Closed TCP ports: 980.
- Detected OS family: Linux.
- Apache web server detected.
- OpenSSH detected.
- MySQL detected on port 3306.

**Result:** Successfully performed network scanning through Zenmap's graphical interface and analyzed the discovered services.

**Note:** The terminal Nmap and Zenmap scans produced different port-state results. These are documented separately because they were separate scan executions.

## 7. Security Observations

The reconnaissance activities identified several areas that may warrant further authorized security assessment:

1. Review FTP access and encryption configuration.
2. Review SSH authentication and access restrictions.
3. Review exposed mail services and encryption configuration.
4. Review DNS configuration and access controls.
5. Review database network exposure.
6. Review HTTP security headers and web server configuration.
7. Review the detected WAF configuration.

These are assessment observations, not confirmed vulnerabilities. No exploitation or vulnerability validation is claimed in this project.

## 8. Learning Outcomes

Through this project, I gained practical experience in:

- Domain registration analysis.
- Passive information gathering.
- DNS enumeration.
- Web technology fingerprinting.
- Web Application Firewall identification.
- TCP port scanning.
- Service and version detection.
- Graphical network scanning with Zenmap.
- Technical documentation and evidence collection.

## 9. Conclusion

The NetworkWalks Week 2 project provided practical exposure to cybersecurity reconnaissance and network scanning techniques using Kali Linux.

By working with six footprinting tools and Zenmap, I gained experience in identifying domain information, DNS infrastructure, web technologies, WAF presence and exposed network services.

This project strengthened my understanding of the reconnaissance phase of penetration testing and the importance of documenting findings accurately.

---

## Authorization and Disclaimer

All security testing must be performed only against systems for which explicit authorization has been granted.

This repository documents educational cybersecurity activities. It does not claim ownership of the target infrastructure or authorization beyond the scope provided by the organization.

**Performed as part of the NetworkWalks Cybersecurity Internship – Week 2.**
