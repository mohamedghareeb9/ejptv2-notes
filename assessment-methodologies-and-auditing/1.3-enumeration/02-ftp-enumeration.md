# FTP Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

**FTP (File Transfer Protocol)**, port 21, is one of the oldest protocols still in common use for moving files to/from a server. It predates modern security practice in two important ways:

- By default, **credentials and data travel in cleartext** — anyone sniffing the connection can read a username/password sent over plain FTP.
- Many FTP servers are intentionally configured to allow **anonymous login** (username `anonymous`, any password, often an email address by convention) so the public can download files without an account.

## 2. The attacker's view

- **The banner alone is often enough.** FTP servers typically announce their exact software and version on connection (e.g. "220 ProFTPD 1.3.5a Server" or "220 (vsFTPd 2.3.4)"). That version string is what you take straight to a CVE search.
- **Anonymous login**, even when not a vulnerability by itself, often grants read (and sometimes write) access to files that were never meant to be public — configuration backups, source code, credentials left in scripts.
- A specific version is itself sometimes the finding: **vsftpd 2.3.4** shipped from a compromised source mirror with a deliberate backdoor (CVE-2011-2523) — the version string alone tells you the server is compromisable, no further scanning needed. See 1.4.

## 3. Methodology

```
use auxiliary/scanner/ftp/ftp_version     # grab the banner/version
use auxiliary/scanner/ftp/anonymous       # check if anonymous login is accepted
use auxiliary/scanner/ftp/ftp_login       # credential brute force (USER_FILE/PASS_FILE)
```

Manual / command-line check — often faster for a single quick look:
```bash
ftp <target>
# Name: anonymous
# Password: (blank, or anonymous@example.com by convention)
```

If anonymous access succeeds, immediately `ls`/`dir` and look for anything unusual before downloading indiscriminately — large or unexpected files are often the actual finding.

## 4. Real CVEs

- **vsftpd 2.3.4 backdoor — CVE-2011-2523.** A specific compromised build of this exact version opens a shell on port 6200 when a username containing `:)` is sent. This is a backdoor planted in a specific released binary, not a bug in the FTP protocol or in vsftpd generally — it only affects that one version.

## 5. Self-test

1. Why is an FTP banner usually more immediately useful to an attacker than an SSH banner?
2. What's the actual security risk of anonymous FTP, separate from any named CVE?
3. Why doesn't the vsftpd 2.3.4 case mean "vsftpd is insecure" as a product?

## 6. Quick recap

FTP leaks its exact version easily and often allows anonymous access by design — check both before anything else, since either can hand you a result with zero brute-forcing.
