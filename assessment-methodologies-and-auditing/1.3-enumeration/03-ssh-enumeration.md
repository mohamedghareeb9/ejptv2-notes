# SSH Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
SSH (Secure Shell), port 22, gives an encrypted remote shell. Despite being "secure" by design, misconfiguration (weak passwords, outdated versions) still makes it attackable.

## 2. The attacker's view
The version banner (e.g. "SSH-2.0-OpenSSH_7.9p1") can be matched to known CVEs for that exact build. Username enumeration is possible on some older/misconfigured servers via response timing differences.

## 3. Methodology
```
use auxiliary/scanner/ssh/ssh_version
set RHOSTS <target>
run

use auxiliary/scanner/ssh/ssh_enumusers
set RHOSTS <target>
set USER_FILE <wordlist>
run

use auxiliary/scanner/ssh/ssh_login
set RHOSTS <target>
set USER_FILE <wordlist>
set PASS_FILE <wordlist>
run
```
Manual: `ssh -V` locally only shows your client version; for the server, `nc <target> 22` shows the banner directly.

## 4. Real CVEs
- libssh authentication bypass (CVE-2018-10933), affecting libssh 0.6.0–0.8.0 (not OpenSSH itself).

## 5. Self-test
1. Why does the exact SSH version matter more than "SSH is open"?
2. Why brute-force SSH logins only with explicit authorization?

## 6. Quick recap
SSH is strong by design; the risk is weak credentials or an outdated/misconfigured build.
