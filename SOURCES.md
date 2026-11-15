# Sources and Coverage

## Primary study sources
1. **eJPTv2.pdf** — uploaded study-notes PDF, 85 pages. Extracted topics include OSINT and information gathering, DNS, web fingerprinting, subdomain discovery, Google dorking, reconnaissance, port scanning, and service discovery.
2. **eJPTv2_Pr.pdf** — uploaded practical/foundations PDF, 107 pages. Extracted topics include Linux command-line use, files and processes, permissions, text processing and regular expressions, networking fundamentals, IPv4/IPv6, routing, ARP, firewalls, endpoints, Active Directory, DHCP, ASN/BGP, TCP, packet inspection, cryptography, hashing, encryption, and encoding.

## Reference repository
- [dev-angelist/eJPTv2-Notes](https://github.com/dev-angelist/eJPTv2-Notes) is the older-account repository supplied as a structural and topic-navigation reference.
- Its prose is not treated as the user's source notes and is not copied.
- Destination: [mohamedghareeb9/ejptv2-notes](https://github.com/mohamedghareeb9/ejptv2-notes).

## Coverage map
| Source topic | Destination |
|---|---|
| OSINT, WHOIS, Netcraft, robots.txt, sitemaps, Wappalyzer/WhatWeb, DNS, subdomains, DNSRecon/DNSenum, Google dorks, theHarvester, HIBP | assessment-methodologies-and-auditing/1.1-information-gathering.md |
| IP/MAC, ARP, ICMP, host discovery, port scanning | assessment-methodologies-and-auditing/1.2-footprinting-and-scanning.md |
| SMB, FTP, SSH, HTTP, MySQL, SMTP enumeration | assessment-methodologies-and-auditing/1.3-enumeration/ |
| CVE, NVD, CVSS, vulnerability checks and examples | assessment-methodologies-and-auditing/1.4-vulnerability-assessment.md |
| Firewalls, IDS/IPS, endpoints, EDR, DHCP snooping, load balancers, cryptography | assessment-methodologies-and-auditing/1.5-auditing-fundamentals.md |
| Linux navigation, files, permissions, processes, text tools, regex | host-and-network-penetration-testing/2.1-system-host-based-attacks/ |
| TCP/UDP, DNS, ARP, routing, ASN/BGP, DHCP, sniffing, MITM concepts | host-and-network-penetration-testing/2.2-network-based-attacks.md |
| Metasploit workflow | host-and-network-penetration-testing/2.3-the-metasploit-framework/ |
| HTTP workflow, directory discovery, directory traversal | web-application-penetration-testing/3.1-intro-to-web-app-pentesting.md |

## Fidelity and review
The PDFs are personal study notes and contain shorthand, duplicated explanations, incomplete commands, and occasionally simplified or questionable statements. This repository rewrites the material for clarity but does not silently promote every source statement to verified fact.

When a statement needs correction or context, it is marked as an external clarification or review note. Command syntax should be checked against the installed tool version before use. No real target should be tested without explicit authorization.

This map is a coverage plan, not a claim that every topic has been fully expanded. Sections should be marked complete only after their corresponding source pages have been reviewed and the notes checked.
