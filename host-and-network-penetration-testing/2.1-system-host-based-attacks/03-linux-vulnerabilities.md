# Linux Vulnerabilities

Linux systems can be affected by vulnerabilities in the kernel, user-space applications, libraries, services, and system configuration. The following are common categories and examples.

## Common vulnerability categories

1. **Kernel vulnerabilities:** Flaws in the Linux kernel may allow privilege escalation, information disclosure, or denial of service. Kernel exploits are highly dependent on the exact kernel build, configuration, and available mitigations.
2. **Privilege escalation:** A local user may gain additional privileges through vulnerable software, unsafe SUID/SGID programs, excessive sudo permissions, writable service files, or incorrect file permissions.
3. **Memory corruption:** Buffer overflows and related memory-safety bugs can cause crashes or, in some cases, code execution. Exploitability depends on the bug and mitigations such as ASLR, NX, and stack canaries.
4. **Shellshock (CVE-2014-6271 and related CVEs):** A family of Bash vulnerabilities involving processing of environment variables and specially crafted function definitions. Affected systems should be updated to vendor-supported Bash packages.
5. **Heartbleed (CVE-2014-0160):** A flaw in affected OpenSSL versions that could disclose portions of process memory. It was a library vulnerability, not a Linux-kernel vulnerability, and affected multiple operating systems.
6. **Denial of service:** A flaw or resource-exhaustion condition may make a host or service unavailable. Causes include network floods, expensive requests, and software bugs.
7. **Remote code execution:** A vulnerability may allow code to run remotely through an exposed service or application. The attack path and required privileges vary by vulnerability.
8. **Misconfiguration:** Unnecessary services, weak authentication, permissive file permissions, exposed management interfaces, and unsafe sudo rules can create exploitable conditions.
9. **Web application vulnerabilities:** Linux-hosted web applications may contain issues such as SQL injection, cross-site scripting, file inclusion, or command injection. These are application vulnerabilities, not vulnerabilities unique to Linux.
10. **Insecure software supply and updates:** Unsupported packages, untrusted repositories, and delayed security updates can leave known vulnerabilities unpatched.
11. **Weak authentication:** Default or reused passwords, exposed SSH credentials, and missing multi-factor authentication can enable unauthorized access.
12. **Zero-day vulnerabilities:** A zero-day is a vulnerability exploited or disclosed before an effective vendor fix is available. The term describes the disclosure and patch situation, not a specific vulnerability class.

## Host review commands

These commands help identify the operating system, kernel, running services, and installed package versions during an authorized assessment.

```bash
uname -a
cat /etc/os-release
id
sudo -l
ps aux
ss -tulpn
systemctl --type=service --state=running
```

Review the output in context. An old-looking version string does not by itself prove that a package is vulnerable: distributions often backport security fixes without changing the upstream version number. Check the distribution's security advisories and package changelog.

## Mitigation

- Apply supported distribution security updates.
- Remove or disable unnecessary services.
- Restrict administrative privileges and review sudoers entries.
- Use least-privilege service accounts.
- Protect SSH with strong authentication and access restrictions.
- Keep application dependencies and exposed services patched.
- Monitor authentication logs and service behavior.
- Use supported operating-system releases and plan upgrades before end of life.

## Resources

- [Linux kernel security documentation](https://docs.kernel.org/security/)
- [Ubuntu Security Notices](https://ubuntu.com/security/notices)
- [Debian Security Advisories](https://www.debian.org/security/)
- [Red Hat CVE database](https://access.redhat.com/security/security-updates/)
- [CVE Program](https://www.cve.org/)
- [NIST National Vulnerability Database](https://nvd.nist.gov/)
