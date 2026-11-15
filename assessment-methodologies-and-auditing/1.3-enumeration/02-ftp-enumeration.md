# FTP Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
FTP (File Transfer Protocol), port 21, transfers files. It predates modern security practice: by default it sends credentials **in cleartext**, and many servers allow **anonymous login**.

## 2. The attacker's view
The banner alone often names the exact FTP daemon and version (e.g. "vsftpd 2.3.4" — a version with a known backdoor, see 1.4). Anonymous access can expose or even allow writing files.

## 3. Methodology
```
# Banner / version
use auxiliary/scanner/ftp/ftp_version
set RHOSTS <target>
run

# Anonymous login check
use auxiliary/scanner/ftp/anonymous
set RHOSTS <target>
run

# Credential brute force (your own wordlists)
use auxiliary/scanner/ftp/ftp_login
set RHOSTS <target>
set USER_FILE <wordlist>
set PASS_FILE <wordlist>
run
```
Manual: `ftp <target>` then try `anonymous` / blank password.

## 4. Real CVEs
- vsftpd 2.3.4 backdoor (CVE-2011-2523) — see 1.4.

## 5. Self-test
1. Why is an FTP banner more useful to an attacker than an SSH banner?
2. What's the security risk of anonymous FTP even without a known CVE?

## 6. Quick recap
FTP leaks version easily and often allows anonymous login — check both first.
