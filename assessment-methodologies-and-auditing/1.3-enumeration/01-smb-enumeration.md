# SMB Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
SMB (Server Message Block) is Windows' file/printer-sharing protocol, also implemented on Linux as **Samba**. Default ports: 445 (SMB over TCP) and 139 (NetBIOS session service, older).

## 2. The attacker's view
SMB commonly leaks: OS/version, share names, and even valid usernames — all useful before you try any login.

## 3. Methodology
```
# Version / OS fingerprint
use auxiliary/scanner/smb/smb_version
set RHOSTS <target>
run

# Enumerate usernames (works against misconfigured/legacy targets)
use auxiliary/scanner/smb/smb_enumusers
set RHOSTS <target>
run

# Enumerate shares (add ShowFiles to list contents)
use auxiliary/scanner/smb/smb_enumshares
set ShowFiles true
run

# Credential check (change USER/PASS lists to your own wordlists)
use auxiliary/scanner/smb/smb_login
set SMBUser <user>
set PASS_FILE <wordlist>
run
```
Command-line alternatives: `smbclient -L //<target>/`, `enum4linux -a <target>`.

## 4. Real CVEs
- MS17-010 / EternalBlue (CVE-2017-0144) — see 1.4.

## 5. Self-test
1. What's the difference between port 445 and port 139?
2. Why enumerate shares before trying exploits?

## 6. Quick recap
SMB = Windows/Samba file sharing. Version, users, shares — in that order.
