# MySQL Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
MySQL (port 3306) is a relational database. If exposed to the network (it often shouldn't be), it's a direct path to the application's data.

## 2. The attacker's view
Default/weak root credentials are common on misconfigured or lab/legacy systems. Once authenticated, you can enumerate databases, tables, and sometimes dump credential hashes.

## 3. Methodology
```
use auxiliary/scanner/mysql/mysql_version
set RHOSTS <target>
run

use auxiliary/scanner/mysql/mysql_login
set RHOSTS <target>
set USERNAME root
set PASS_FILE <wordlist>
run

# Once authenticated:
use auxiliary/admin/mysql/mysql_enum
set USERNAME <user>
set PASSWORD <password>
run

use auxiliary/admin/mysql/mysql_sql
set USERNAME <user>
set PASSWORD <password>
set SQL "show databases;"
run
```
Manual: `mysql -h <target> -u root -p`.

## 4. Real CVEs
Version-dependent; always check the exact MySQL/MariaDB version against the NVD.

## 5. Self-test
1. Why should a database server rarely be exposed directly to the internet?
2. What's the first thing to check before trying any password list against MySQL?

## 6. Quick recap
MySQL exposure = version check, then credential check, then enumerate schema if authenticated.
