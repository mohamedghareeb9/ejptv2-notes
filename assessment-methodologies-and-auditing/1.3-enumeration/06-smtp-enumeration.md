# SMTP Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

**SMTP (Simple Mail Transfer Protocol)** handles outgoing/relayed email, typically on port 25, with 465 and 587 used for encrypted/submission variants. Some SMTP servers still support two old commands — `VRFY` (verify a user exists) and `EXPN` (expand a mailing list to its members) — that were designed for mail administrators but can be abused for reconnaissance if left enabled.

## 2. The attacker's view

- **Username enumeration via VRFY/EXPN** builds a confirmed list of valid email accounts/usernames on the target organization — useful both for later password-guessing and (within authorized scope only) for phishing simulations.
- The **connection banner** usually names the exact mail server software (Postfix, Exim, Haraka, Microsoft Exchange, etc.) and sometimes the version, again feeding straight into CVE research.

## 3. Methodology

```
use auxiliary/scanner/smtp/smtp_version    # banner/version
use auxiliary/scanner/smtp/smtp_enum       # username enumeration via VRFY (USER_FILE)
```

Manual — useful to understand what the module is actually doing under the hood:
```bash
nc <target> 25
VRFY root
VRFY nonexistentuser123
# compare the responses: a real account vs. a fake one often reply differently
```

## 4. Real CVEs

Version-dependent — check the exact mail server software and version found in the banner.

## 5. Self-test

1. Why would a security-conscious organization disable `VRFY` and `EXPN`?
2. How does a list of confirmed valid email usernames feed into a later attack (within authorized scope)?
3. Why might the banner alone be enough to narrow down the mail server's CVE exposure?

## 6. Quick recap

SMTP enumeration finds valid usernames (via VRFY/EXPN, if enabled) and the exact mail server software/version from the banner.
