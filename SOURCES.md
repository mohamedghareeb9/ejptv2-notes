# References & Further Reading

This repository is an independent study resource. The chapters combine practical explanations, command examples, and workflows for learning penetration testing.

## Official and primary documentation
- [INE eJPT certification and exam objectives](https://security.ine.com/certifications/ejpt-certification/)
- [INE March 2026 eJPT update announcement](https://ine.com/newsroom/ine-security-launches-updated-ejpt-certification-with-expanded-web-app-testing-recon-training-and-offensive-ai)
- [INE Certifications](https://ine.com/learning/certifications)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [Nmap Scripting Engine](https://nmap.org/book/nse.html)
- [Metasploit Documentation](https://docs.metasploit.com/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [WordPress Security and Hardening](https://developer.wordpress.org/advanced-administration/security/)
- [WPScan User Documentation](https://github.com/wpscanteam/wpscan/wiki/WPScan-User-Documentation)
- [WPScan 4.0 release announcement (May 2026)](https://wpscan.com/blog/wpscan-4-0-0-were-back/)
- [Gobuster documentation](https://github.com/OJ/gobuster)
- [Nikto documentation](https://github.com/sullo/nikto)
- [Gophish documentation](https://docs.getgophish.com/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [MITRE CVE](https://www.cve.org/)
- [NIST National Vulnerability Database](https://nvd.nist.gov/)
- [Microsoft Learn](https://learn.microsoft.com/)
- [Linux man-pages](https://man7.org/linux/man-pages/)

## Original study notes and content map

This repository is maintained as a standalone study resource. Its chapters are organized around the supplied eJPTv2 study materials and the current official certification information; all diagrams and assets should be maintained within this repository.

The two study PDFs used during preparation contributed foundational Linux command-line material and network concepts. Their topics are represented in the following chapters:

- **Assessment methodologies:** information gathering, OSINT, DNS and public-source reconnaissance, footprinting, Nmap scanning, service enumeration, and vulnerability assessment.
- **Host and network auditing:** Linux command-line foundations, file and process inspection, permissions, Active Directory concepts, network configuration, packet analysis, and host information gathering.
- **Host and network penetration testing:** network attacks and defenses, Metasploit workflows, exploit research and validation, shells, post-exploitation, credential handling, pivoting, and social engineering.
- **Web application penetration testing:** HTTP fundamentals, reconnaissance, content discovery, and common web vulnerability classes.

## Coverage map

| Source topic | Repository chapter(s) |
|---|---|
| Passive and active reconnaissance; OSINT, DNS, ASN/BGP, WHOIS, subdomains, exposed secrets | [Information Gathering](assessment-methodologies-and-auditing/1.1-information-gathering.md) |
| Target scope and authorization boundaries | [Information Gathering — Target Scoping](assessment-methodologies-and-auditing/1.1-information-gathering.md) |
| IP/MAC addressing, ARP, ICMP, scanning, Nmap, NSE, Wireshark | [Footprinting & Scanning](assessment-methodologies-and-auditing/1.2-footprinting-and-scanning.md), [Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| SMB, FTP, SSH, HTTP, MySQL, SMTP, SNMP enumeration | [Enumeration index](assessment-methodologies-and-auditing/1.3-enumeration/README.md) |
| Linux commands, files, permissions, processes, packages, regular expressions, archives | [Linux Foundations](host-and-network-penetration-testing/2.1-system-host-based-attacks/01-linux-foundations.md) |
| Windows, Active Directory, NTLM, Kerberos, LDAP, Group Policy | [Active Directory Fundamentals](host-and-network-penetration-testing/2.1-system-host-based-attacks/02-active-directory-fundamentals.md), [Windows Vulnerabilities](host-and-network-penetration-testing/2.1-system-host-based-attacks/04-windows-vulnerabilities.md) |
| IPv4/IPv6, CIDR, switching, VLANs, routers, NAT, TCP/UDP, DHCP, ASN/BGP, TLS, Wi-Fi, firewalls, IDS/IPS, EDR, load balancing, cryptography | [Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| Metasploit modules, scanning, exploitation, sessions, Meterpreter, Armitage | [Metasploit chapters](host-and-network-penetration-testing/2.3-the-metasploit-framework/README.md) |
| Exploit research, SearchSploit, shells, exploitation workflow | [Exploitation](host-and-network-penetration-testing/2.4-exploitation.md) |
| Local enumeration, privilege escalation concepts, file transfer, sessions, cleanup | [Post-Exploitation](host-and-network-penetration-testing/2.5-post-exploitation.md) |
| Phishing, social-engineering concepts, GoPhish | [Social Engineering](host-and-network-penetration-testing/2.6-social-engineering.md) |
| HTTP, cookies, methods, status codes, Gobuster, Burp Suite, ZAP, Nikto, SQL injection, XSS, traversal | [Intro to Web App Pentesting](web-application-penetration-testing/3.1-intro-to-web-app-pentesting.md) |
| CMS identification, WordPress core/themes/plugins, WPScan, validation and hardening | [CMS and WordPress Testing](web-application-penetration-testing/3.2-cms-and-wordpress-testing.md) |

### PDF page-to-chapter map

Page numbers below refer to the two supplied study PDFs in their original upload order.

**eJPTv2.pdf (85 pages)**

| PDF pages | Main source topics | Destination |
|---|---|---|
| 1–23 | OSINT, passive and active reconnaissance, DNS, subdomains, ASN, email discovery | [1.1 Information Gathering](assessment-methodologies-and-auditing/1.1-information-gathering.md) |
| 24–34 | Google dorking and directory traversal examples | [1.1 Information Gathering](assessment-methodologies-and-auditing/1.1-information-gathering.md), [3.1 Intro to Web App Pentesting](web-application-penetration-testing/3.1-intro-to-web-app-pentesting.md) |
| 35–46 | Netcraft, technology fingerprinting, exposed secrets, DNS and zone-transfer reconnaissance | [1.1 Information Gathering](assessment-methodologies-and-auditing/1.1-information-gathering.md) |
| 47–66 | Network discovery, Nmap scan types, service/version detection, NSE, evasion/scan concepts | [1.2 Footprinting & Scanning](assessment-methodologies-and-auditing/1.2-footprinting-and-scanning.md) |
| 67–72 | RID/username enumeration, Hydra, Metasploit modules and sessions, post-exploitation | [1.3 Enumeration](assessment-methodologies-and-auditing/1.3-enumeration/README.md), [Metasploit](host-and-network-penetration-testing/2.3-the-metasploit-framework/README.md), [2.5 Post-Exploitation](host-and-network-penetration-testing/2.5-post-exploitation.md) |
| 73–76 | Network services and SMB enumeration / null sessions | [1.3 Enumeration](assessment-methodologies-and-auditing/1.3-enumeration/README.md), [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| 77–79 | Host and Windows vulnerability concepts | [2.1 Host-Based Attacks](host-and-network-penetration-testing/2.1-system-host-based-attacks/README.md), [2.4 Exploitation](host-and-network-penetration-testing/2.4-exploitation.md) |
| 80–85 | Hashing, encryption, encoding, symmetric/asymmetric cryptography | [2.2 Network-Based Attacks — Cryptography](host-and-network-penetration-testing/2.2-network-based-attacks.md) |

**eJPTv2_Pr.pdf (107 pages)**

| PDF pages | Main source topics | Destination |
|---|---|---|
| 1–33 | Linux shell, navigation, files, permissions, searching, regex, editors, archives and compression | [Linux Foundations](host-and-network-penetration-testing/2.1-system-host-based-attacks/01-linux-foundations.md) |
| 34–50 | IPv4/IPv6, subnetting/CIDR, switches, VLANs, routers, NAT, TTL | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| 51–61 | Firewalls, stateful/proxy/NGFW concepts, IDS/IPS, endpoints, EDR, lateral movement concepts | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md), [2.5 Post-Exploitation](host-and-network-penetration-testing/2.5-post-exploitation.md) |
| 62–70 | Active Directory, domain controllers, objects, OUs, Kerberos, Group Policy, NTLM and common attack concepts | [Active Directory Fundamentals](host-and-network-penetration-testing/2.1-system-host-based-attacks/02-active-directory-fundamentals.md) |
| 71–78 | Load balancers, algorithms, health checks, DHCP, ASN and BGP | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| 79–86 | DHCP details, ASN/BGP recap and routing context | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| 87–100 | TCP/UDP, TLS, certificates, HTTPS, ARP/MAC attacks, Wi-Fi managed/monitor modes | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |
| 101–107 | Wireshark display filters, encryption, hashing and common algorithms | [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md) |

### Known coverage gaps

The sources and current public exam announcement support the topics mapped above. The repository still needs more hands-on, lab-verified walkthroughs for the newer CMS/WordPress topics, more worked examples for some network and cryptography concepts, and a current practical validation pass across tool commands and screenshots. The remaining legacy illustrations that depended on the former GitBook CDN have been removed and replaced with original Mermaid diagrams and explanatory tables maintained in this repository. The remaining legacy screenshots have been removed rather than relying on external repositories. Visual explanations are being replaced with repository-maintained diagrams and text. The separate Offensive AI course is not treated as a core exam domain here; it should remain supplementary unless the official exam objectives change.

The source material is not a substitute for the current official exam objectives. See the INE certification page and March 2026 update announcement above for the current learning-path and exam information.
