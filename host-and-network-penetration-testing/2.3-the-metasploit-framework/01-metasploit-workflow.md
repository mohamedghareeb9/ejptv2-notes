# Metasploit Framework: Workflow and Core Concepts

**Source basis:** existing vulnerability-assessment notes and the eJPTv2 study structure. This is an introductory workflow to expand alongside hands-on lab practice.

## 1. What Metasploit is
The Metasploit Framework is a platform for organizing and running security testing modules. It includes modules for auxiliary tasks, exploit validation, payload handling, and post-exploitation activities.

The framework does not decide whether a test is authorized. Confirm scope and understand a module's effect before running it.

## 2. Module families
| Module type | General role |
|---|---|
| auxiliary | Scanning, enumeration, and supporting tasks |
| exploit | Attempts to trigger a vulnerability |
| payload | Code or behavior delivered after successful exploitation |
| post | Actions performed after access is obtained |
| encoder | Transforms payload representation for compatibility |
| nop | No-operation sequences used by some exploit techniques |

## 3. Starting and navigating
~~~text
msfconsole
help
search type:auxiliary name:smb
search cve:2017
info <module>
use <module>
show options
show advanced
back
exit
~~~

Read module information before use. Identify required options, target platform, side effects, and whether it is a scanner or exploit.

## 4. Workspaces and scan data
Workspaces help keep engagement data separate.

~~~text
workspace
workspace -a lab-name
workspace lab-name
hosts
services
vulns
~~~

The study notes show importing Nmap scan data into the Metasploit database:

~~~bash
db_nmap -sS -sV -O <authorized-target>
~~~

A scan result is evidence to investigate, not proof that an exploit will work.

## 5. Safe validation workflow
1. Confirm written authorization and target scope.
2. Identify the service and version independently.
3. Search for a relevant Metasploit module.
4. Read module documentation and inspect options.
5. Prefer a non-invasive auxiliary check where available.
6. Understand possible service impact before any exploit attempt.
7. Run only in a lab or under explicit engagement approval.
8. Record the result and clean up artifacts created by the test.

## 6. Self-check
1. Difference between an auxiliary module and an exploit module?
2. Why review module information and options before running it?
3. What does a workspace help organize?
4. Why is a version match not enough to prove exploitability?
5. Why is a scanner/check module preferable as initial validation?
