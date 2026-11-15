# MySQL Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

**MySQL** (port 3306) is a relational database server. In a well-architected system, a database should almost never be directly reachable from outside the internal network — if it's exposed to the internet or even just to your scanning position, that configuration choice is itself a finding worth noting before anything else.

## 2. The attacker's view

- **Default/weak root credentials** are surprisingly common on misconfigured, legacy, or lab/test systems that were never meant to stay exposed.
- Once authenticated, you can enumerate **databases, tables, and user accounts** directly, and in some configurations pull password hashes for offline cracking.
- Even failed login attempts confirm the database is reachable and give you the exact version, which (like every other service here) maps to known CVEs.

## 3. Methodology

```
use auxiliary/scanner/mysql/mysql_version    # version fingerprint
use auxiliary/scanner/mysql/mysql_login      # credential brute force (USERNAME + PASS_FILE)

# Once authenticated:
use auxiliary/admin/mysql/mysql_enum         # detailed server config + account enumeration
use auxiliary/admin/mysql/mysql_sql          # run arbitrary SQL, e.g. SQL "show databases;"
```

Manual:
```bash
mysql -h <target> -u root -p
```

## 4. Real CVEs

Version-dependent — always check the exact MySQL/MariaDB/Percona version found against the NVD; this family of software has had numerous authentication and privilege-escalation CVEs over the years tied to specific versions.

## 5. Self-test

1. Why is "a database is reachable from here at all" sometimes the actual finding, independent of any CVE?
2. What's the first thing to check before running any password list against a MySQL server?
3. Why does authenticating successfully change what you can enumerate, compared to the version scan alone?

## 6. Quick recap

MySQL exposure: note the exposure itself, check the version, test credentials carefully, then enumerate schema/accounts if authenticated.
