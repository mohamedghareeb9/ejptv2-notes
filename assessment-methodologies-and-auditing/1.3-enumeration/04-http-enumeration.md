# HTTP / Web Server Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

HTTP enumeration goes beyond "there's a website here" — it's about pulling out everything the web server and the application behind it are willing to reveal: exact server software, response headers, hidden files and directories, and any content the server returns when poked the right way.

## 2. The attacker's view

- **Server headers** (e.g. `Server: Apache/2.4.18 (Ubuntu)`) point directly to CVEs for that exact build.
- **Directory and file brute-forcing** finds paths that aren't linked anywhere on the visible site — admin panels, backup files (`.bak`), config files, leftover test pages.
- **robots.txt** (covered in 1.1) doubles as a enumeration source here: `Disallow` entries are effectively a list of paths the owner didn't want indexed, which is often exactly where something interesting lives.
- Combined, these turn "a website" into "Apache 2.4.18 running WordPress with an exposed `/wp-config.php.bak`" — a concrete, searchable target.

## 3. Methodology

```
use auxiliary/scanner/http/http_version     # server software/version
use auxiliary/scanner/http/http_header      # dump all response headers
use auxiliary/scanner/http/dir_scanner      # brute-force directories
use auxiliary/scanner/http/robots_txt       # fetch and display robots.txt directly
```

Command-line equivalents, often faster for a quick check:
```bash
curl -I <url>                                   # headers only
whatweb <url>                                   # technology fingerprint
gobuster dir -u <url> -w <wordlist>             # directory brute force
```

For HTTPS targets, remember to set the correct port/SSL option in whichever tool you're using — a scan run against the wrong port/scheme silently returns nothing useful.

## 4. Real CVEs

Entirely dependent on what gets enumerated here — the exact server software, CMS, and framework versions found feed directly into the vulnerability research done in 1.4.

## 5. Self-test

1. Why check `robots.txt` again here, separately from the recon done in 1.1?
2. Give a concrete reason a `.bak` file left on a web server is dangerous.
3. Why does setting the wrong port/SSL option make a scan look like it "found nothing" rather than erroring clearly?

## 6. Quick recap

HTTP enumeration = exact server/framework version + hidden paths. It's the step that turns a generic website into a specific, researchable target.
