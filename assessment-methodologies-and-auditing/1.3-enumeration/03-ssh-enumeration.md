# SSH Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

**SSH (Secure Shell)**, port 22, provides an encrypted remote shell and is the standard way to administer Linux/Unix systems remotely (and increasingly Windows too). Unlike FTP or Telnet, SSH was designed from the start with security in mind — but "secure by design" doesn't mean "unattackable in practice."

## 2. The attacker's view

- The **version banner** is sent before any authentication happens — e.g. `SSH-2.0-OpenSSH_7.9p1`. That exact build (OpenSSH 7.9p1) can be checked against known CVEs the same way an FTP or HTTP version would be.
- **Weak/default/reused credentials** are the most common real-world way into an SSH server — not a protocol exploit. This is why a username + password brute force is still a standard part of SSH enumeration, authorized scope permitting.
- **Username enumeration via timing differences** is possible on some older or misconfigured SSH servers: the server responds measurably faster/slower depending on whether a submitted username actually exists, even before the password is checked. Modern OpenSSH has mitigations for this, but it's still worth checking on older targets.

## 3. Methodology

```
use auxiliary/scanner/ssh/ssh_version       # grab the version banner
use auxiliary/scanner/ssh/ssh_enumusers     # attempt username enumeration (USER_FILE)
use auxiliary/scanner/ssh/ssh_login         # credential brute force (USER_FILE/PASS_FILE)
```

Manual banner grab (no MSF needed):
```bash
nc <target> 22
# (the server sends its version string immediately on connect)
```

## 4. Real CVEs

- **libssh authentication bypass — CVE-2018-10933**, affecting libssh (not OpenSSH itself) versions 0.6.0 through 0.8.0. A crafted message could let an attacker skip authentication entirely — a good reminder that "SSH" isn't one single implementation, and the library matters as much as the protocol.

## 5. Self-test

1. Why does the exact SSH version matter more than simply "port 22 is open"?
2. Why is brute-forcing SSH logins something you'd only ever do with explicit written authorization?
3. Why would two servers both "running SSH" have completely different vulnerability profiles?

## 6. Quick recap

SSH's design is strong; its real-world weak points are outdated/misconfigured builds and weak credentials, not the protocol itself.
