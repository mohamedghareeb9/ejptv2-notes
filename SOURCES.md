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
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [MITRE CVE](https://www.cve.org/)
- [NIST National Vulnerability Database](https://nvd.nist.gov/)
- [Microsoft Learn](https://learn.microsoft.com/)
- [Linux man-pages](https://man7.org/linux/man-pages/)

## Original study notes and content map

The notes also draw on the author's earlier public [eJPTv2-Notes repository](https://github.com/dev-angelist/eJPTv2-Notes). Its chapter structure, enumeration material, Metasploit workflows, exploitation and post-exploitation notes, social-engineering material, and command cheat sheet informed the organization and practical examples in this repository. The current repository reorganizes and supplements that material.

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

### Known coverage gaps

The sources and current public exam announcement support the topics mapped above. The repository still needs more hands-on, lab-verified walkthroughs for the newer CMS/WordPress topics, more worked examples for some network and cryptography concepts, and a current practical validation pass across tool commands and screenshots. The separate Offensive AI course is not treated as a core exam domain here; it should remain supplementary unless the official exam objectives change.

The source material is not a substitute for the current official exam objectives. See the INE certification page and March 2026 update announcement above for the current learning-path and exam information.
