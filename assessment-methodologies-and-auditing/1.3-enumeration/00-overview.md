# 1.3 Enumeration — Overview

**Status:** draft | **Authorized targets only**

## 1. How it works (from zero)

A **server** is a machine that provides a resource or function to other machines (web pages, files, a database, email, an app) and listens for requests on one or more ports. A **service** is the specific software behind a listening port (vsftpd on 21, OpenSSH on 22, Apache on 80, MySQL on 3306...).

**Enumeration** is the step after scanning: for every open port, you actively connect and pull out everything the service is willing to tell you — version, configuration, usernames, shares, files, banners. Scanning tells you a door is open; enumeration tells you what's behind it and often how to open it further.

This matters because almost every later phase (vulnerability research, exploitation) depends on having the **exact service name and version** first.

## 2. Methodology (general, any service)

1. Confirm the port is open and get a banner (`nc`, `curl`, or `nmap -sV`).
2. Identify exact product + version.
3. Check for default/weak credentials.
4. List what the service exposes (shares, directories, databases, users).
5. Try safe, authenticated or anonymous access before attempting any exploit.
6. Record everything (host, port, version, findings) before moving to vulnerability research (1.4).

## Services covered here
- [SMB](01-smb-enumeration.md)
- [FTP](02-ftp-enumeration.md)
- [SSH](03-ssh-enumeration.md)
- [HTTP](04-http-enumeration.md)
- [MySQL](05-mysql-enumeration.md)
- [SMTP](06-smtp-enumeration.md)
- [SNMP](07-snmp-enumeration.md)

Each uses both manual tools and Metasploit auxiliary modules (`msfconsole`), since both show up on the exam and in real engagements.
