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


## Resources

- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [Microsoft SMB documentation](https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview)
- [RFC 959: FTP](https://www.rfc-editor.org/rfc/rfc959)
- [OpenSSH manual pages](https://www.openssh.com/manual.html)
- [MDN: HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- [MySQL Reference Manual](https://dev.mysql.com/doc/refman/8.4/en/)
- [RFC 5321: SMTP](https://www.rfc-editor.org/rfc/rfc5321)
- [Net-SNMP documentation](https://www.net-snmp.org/docs/)
