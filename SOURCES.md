# Sources and Coverage

## Primary study sources
1. **eJPTv2.pdf** — uploaded study-notes PDF, 85 pages. Extracted topics include OSINT and information gathering, DNS, web fingerprinting, subdomain discovery, Google dorking, reconnaissance, port scanning, service discovery, Nmap scripting, SMB/NetBIOS, SNMP, Metasploit, and hashing/encryption/encoding.
2. **eJPTv2_Pr.pdf** — uploaded practical/foundations PDF, 107 pages. Extracted topics include Linux command-line use, files and processes, permissions, Vim, archives, file search, text processing and regular expressions, IPv4/IPv6, CIDR, switching, VLANs, routing, NAT, ARP, firewalls, endpoints, Active Directory, DHCP, ASN/BGP, TCP/UDP, TLS, packet inspection, cryptography, hashing, encryption, and encoding.

## Reference repository
- [dev-angelist/eJPTv2-Notes](https://github.com/dev-angelist/eJPTv2-Notes) is the older-account repository supplied as a structural and topic-navigation reference.
- Its prose is not treated as the user's source notes and is not copied.
- Destination: [mohamedghareeb9/ejptv2-notes](https://github.com/mohamedghareeb9/ejptv2-notes).

## Coverage map
| Source topic | Destination |
|---|---|
| OSINT, WHOIS, Netcraft, robots.txt, sitemaps, Wappalyzer/WhatWeb, DNS, subdomains, DNSRecon/DNSenum, Google dorks, theHarvester, HIBP, Gitleaks | assessment-methodologies-and-auditing/1.1-information-gathering.md |
| IP/MAC, ARP, ICMP, host discovery, Nmap port scans, NSE, firewall scan concepts | assessment-methodologies-and-auditing/1.2-footprinting-and-scanning.md |
| SMB, FTP, SSH, HTTP, MySQL, SMTP, SNMP enumeration | assessment-methodologies-and-auditing/1.3-enumeration/ |
| CVE, NVD, CVSS, vulnerability checks and examples | assessment-methodologies-and-auditing/1.4-vulnerability-assessment.md |
| Firewalls, IDS/IPS, endpoints, EDR, DHCP snooping, load balancers, cryptography | assessment-methodologies-and-auditing/1.5-auditing-fundamentals.md |
| Linux navigation, files, permissions, processes, Vim, archives, find/locate, text tools, regex, Active Directory, Kerberos/NTLM, LDAP, GPO, AD attack concepts | host-and-network-penetration-testing/2.1-system-host-based-attacks/ |
| TCP/UDP, IPv4/IPv6, CIDR, switches, VLANs, routing, NAT, ASN/BGP, DHCP, ARP, sniffing, MITM, TLS/HTTPS | host-and-network-penetration-testing/2.2-network-based-attacks.md |
| Metasploit module families, console workflow, workspaces, sessions, Meterpreter concepts | host-and-network-penetration-testing/2.3-the-metasploit-framework/ |
| Exploitation categories and validation workflow | host-and-network-penetration-testing/2.4-exploitation.md |
| Meterpreter/session concepts, privilege context, credential handling, persistence concept | host-and-network-penetration-testing/2.5-post-exploitation.md |
| Email discovery and authorized phishing simulation mention only; no substantive lesson in source | host-and-network-penetration-testing/2.6-social-engineering.md |
| HTTP workflow, directory discovery, directory traversal | web-application-penetration-testing/3.1-intro-to-web-app-pentesting.md |

## Fidelity and review
The PDFs are personal study notes and contain shorthand, duplicated explanations, incomplete commands, and occasionally simplified or questionable statements. This repository rewrites the material for clarity but does not silently promote every source statement to verified fact.

When a statement needs correction or context, it is marked as an external clarification or review note. Command syntax should be checked against the installed tool version before use. No real target should be tested without explicit authorization.

This map is a coverage plan, not a claim that every topic has been fully expanded. Some sections are deliberately labelled as source gaps where the PDFs do not contain enough material.
