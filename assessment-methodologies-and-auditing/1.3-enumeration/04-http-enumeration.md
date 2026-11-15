# HTTP/Web Server Enumeration

**Status:** draft | **Authorized targets only**

## 1. How it works
HTTP serves web applications. Enumeration here looks beyond "a website is up" to the server software, hidden directories, files, and headers that reveal the tech stack.

## 2. The attacker's view
Server headers (e.g. "Apache/2.4.18 (Ubuntu)") point to CVEs for that exact build. Hidden directories (`/admin`, `/backup`) and leftover files (`.bak`, `.cfg`) are common findings from directory brute-forcing.

## 3. Methodology
```
use auxiliary/scanner/http/http_version
set RHOSTS <target>
run

use auxiliary/scanner/http/http_header
set RHOSTS <target>
run

use auxiliary/scanner/http/dir_scanner
set RHOSTS <target>
run

use auxiliary/scanner/http/robots_txt
set RHOSTS <target>
run
```
Equivalent manual tools: `whatweb`, `gobuster dir -u <url> -w <wordlist>`, `curl -I <url>`.

## 4. Real CVEs
Depends entirely on what's enumerated (CMS, framework, server version) — this step feeds directly into 1.4.

## 5. Self-test
1. Why check `robots.txt` as part of enumeration, not just recon (1.1)?
2. Give one reason a `.bak` file is dangerous if left on a web server.

## 6. Quick recap
HTTP enumeration = headers + hidden paths + exact software version, feeding vulnerability research.
