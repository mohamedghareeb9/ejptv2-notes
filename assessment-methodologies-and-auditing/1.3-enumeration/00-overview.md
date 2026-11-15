# 1.3 Enumeration

Enumeration is the process of extracting useful information from discovered hosts and services. The goal is to identify what is running, how it is configured, and what information is exposed.

## Service notes
- [SMB](01-smb-enumeration.md)
- [FTP](02-ftp-enumeration.md)
- [SSH](03-ssh-enumeration.md)
- [HTTP](04-http-enumeration.md)
- [MySQL](05-mysql-enumeration.md)
- [SMTP](06-smtp-enumeration.md)
- [SNMP](07-snmp-enumeration.md)

## Workflow
1. Identify open ports and likely services.
2. Confirm service versions and protocol behavior.
3. Enumerate anonymously where permitted, then with authorized credentials if available.
4. Record users, shares, banners, configuration details, and other relevant findings.
5. Correlate findings with vulnerability information and engagement scope.
