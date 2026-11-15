# eJPTv2 Study Notes

A practical, organized study guide for the **eLearnSecurity Junior Penetration Tester (eJPTv2)** certification. Use the chapters, command references, and examples to build the knowledge and hands-on workflow needed for an entry-level penetration-testing assessment.

The notes are organized around the main study domains and include foundational concepts, reconnaissance, enumeration, vulnerability assessment, host and network testing, Metasploit, post-exploitation, and web application testing.

## Current exam-version note

INE announced an updated eJPT exam and learning path on **March 26, 2026**. The announcement describes an expansion from 35 to 45 exam questions while retaining the 48-hour practical format, additional training on target scoping and passive versus active reconnaissance, and expanded web application material covering Nikto, file and directory discovery (including Gobuster), CMS security fundamentals, and WordPress security testing and exploitation. INE also introduced a separate **Offensive AI: Generative AI for Pentesters** course.

INE's certification page groups the exam into four weighted domains: **Assessment Methodologies (25%)**, **Host and Networking Auditing (25%)**, **Host and Network Penetration Testing (35%)**, and **Web Application Penetration Testing (15%)**.

These notes combine earlier study material and should be treated as a practical foundation, **not as a complete substitute for the current INE learning path**. The web-application chapter already introduces scanning and directory discovery, and [3.2 CMS and WordPress Security Testing](web-application-penetration-testing/3.2-cms-and-wordpress-testing.md) adds an introductory workflow based on official WordPress and WPScan documentation. The repository does not yet cover the separate Offensive AI course, and the CMS material should be expanded alongside the current INE labs.

- [INE: eJPT certification and exam objectives](https://security.ine.com/certifications/ejpt-certification/)
- [INE: March 2026 eJPT update announcement](https://ine.com/newsroom/ine-security-launches-updated-ejpt-certification-with-expanded-web-app-testing-recon-training-and-offensive-ai)

## Start studying

### 1. Assessment Methodologies & Auditing
- [1.1 Information Gathering](assessment-methodologies-and-auditing/1.1-information-gathering.md)
- [1.2 Footprinting & Scanning](assessment-methodologies-and-auditing/1.2-footprinting-and-scanning.md)
- [1.3 Enumeration](assessment-methodologies-and-auditing/1.3-enumeration/)
- [1.4 Vulnerability Assessment](assessment-methodologies-and-auditing/1.4-vulnerability-assessment.md)
- [1.5 Auditing Fundamentals](assessment-methodologies-and-auditing/1.5-auditing-fundamentals.md)

### 2. Host & Network Penetration Testing
- [2.1 System / Host-Based Attacks](host-and-network-penetration-testing/2.1-system-host-based-attacks/)
- [2.2 Network-Based Attacks](host-and-network-penetration-testing/2.2-network-based-attacks.md)
- [2.3 The Metasploit Framework](host-and-network-penetration-testing/2.3-the-metasploit-framework/)
- [2.4 Exploitation](host-and-network-penetration-testing/2.4-exploitation.md)
- [2.5 Post-Exploitation](host-and-network-penetration-testing/2.5-post-exploitation.md)
- [2.6 Social Engineering](host-and-network-penetration-testing/2.6-social-engineering.md)

### 3. Web Application Penetration Testing
- [3.1 Introduction to Web Application Pentesting](web-application-penetration-testing/3.1-intro-to-web-app-pentesting.md)
- [3.2 CMS and WordPress Security Testing](web-application-penetration-testing/3.2-cms-and-wordpress-testing.md)

## Quick reference
- [eJPT Command Cheat Sheet](CHEAT-SHEET.md)

## Suggested study workflow
1. Learn the networking and operating-system foundations.
2. Practice passive and active reconnaissance in a lab.
3. Enumerate discovered services systematically.
4. Understand how to validate vulnerabilities and identify relevant exploits.
5. Practice exploitation and post-exploitation workflows in intentionally vulnerable environments.
6. Apply the same methodology to web applications.
7. Revisit the cheat sheet while practicing, rather than memorizing commands without understanding their output.

## Important
Only scan, exploit, or enumerate systems that you own or are explicitly authorized to test. Some commands and techniques can disrupt services or expose sensitive data. Check the current documentation for the installed tool version before using version-sensitive options.

This is an independent study resource and is not an official INE publication or affiliated with INE.
