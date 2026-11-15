# SMTP Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
SMTP (port 25, plus 465/587 for encrypted variants) handles outgoing mail. Some SMTP servers still support the old `VRFY`/`EXPN` commands, which can confirm whether a username/mailbox exists.

## 2. The attacker's view
Username enumeration via SMTP builds a list of valid accounts for later password-guessing or phishing (if in scope), and the banner names the exact mail server software.

## 3. Methodology
```
use auxiliary/scanner/smtp/smtp_version
set RHOSTS <target>
run

use auxiliary/scanner/smtp/smtp_enum
set RHOSTS <target>
set USER_FILE <wordlist>
run
```
Manual: `nc <target> 25` then try `VRFY root`.

## 4. Real CVEs
Version-dependent — check the exact mail server (Postfix, Exim, Haraka, etc.) and version.

## 5. Self-test
1. Why would an organization want to disable `VRFY`?
2. How does SMTP username enumeration feed into a later attack?

## 6. Quick recap
SMTP enumeration finds valid usernames and the mail server's exact version/software.
