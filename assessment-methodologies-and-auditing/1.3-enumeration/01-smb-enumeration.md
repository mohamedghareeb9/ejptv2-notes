# SMB Enumeration

**Status:** draft | **Authorized targets only**

---

## 1. How it works

**SMB (Server Message Block)** is the protocol Windows uses for sharing files, printers, and other resources across a network. It's deeply tied to how Windows networks have historically authenticated and browsed each other — which is exactly why it has such a long history of serious vulnerabilities (MS17-010/EternalBlue being the most famous, see 1.4).

**Samba** is the open-source reimplementation of SMB for Linux/Unix, letting Linux machines participate in Windows-style file sharing and even act as a domain controller. When you enumerate "SMB" on a Linux box, you're usually actually talking to Samba.

Default ports:
- **445/tcp** — SMB directly over TCP (modern, used by Windows Vista and later by default)
- **139/tcp** — NetBIOS Session Service (older, used for SMB over NetBIOS)

A server can have one, the other, or both open — worth noting which, since it hints at OS age/configuration.

## 2. The attacker's view

SMB is unusually "chatty" by design — it's meant to let a Windows network browse itself (see what shares and machines exist), which means a lot of that same information is available to an attacker who isn't supposed to be on the network at all. Specifically:

- **Version/OS fingerprint** narrows down exact patch level, which maps directly to known CVEs.
- **Username enumeration** works against misconfigured or legacy targets (particularly ones allowing "null sessions" — unauthenticated connections that still leak information). A found username becomes the first half of a login attempt.
- **Share enumeration** can reveal shares meant to be internal-only, sometimes even listing file contents directly if permissions are loose.
- **Login testing** against found usernames with a password wordlist is the natural next step once you have both pieces.

## 3. Methodology

Using Metasploit's auxiliary SMB scanner modules (run each with `set RHOSTS <target>` then `run`):

```
use auxiliary/scanner/smb/smb_version          # fingerprint OS/SMB version from the banner
use auxiliary/scanner/smb/smb_enumusers        # attempt username enumeration
use auxiliary/scanner/smb/smb_enumshares       # list shares; "set ShowFiles true" to list contents too
use auxiliary/scanner/smb/smb_login            # test USER_FILE/PASS_FILE combinations
```

Command-line (non-MSF) alternatives, useful when you don't want to spin up a whole Metasploit session just to check one thing:
```bash
smbclient -L //<target>/ -N        # -N = no password (anonymous/null session attempt)
enum4linux -a <target>             # all-in-one SMB enumeration (users, shares, policies, OS info)
```

A finding worth specifically checking for: whether **anonymous/guest access** is allowed at all (`smbclient -L //target/ -N` succeeding with no credentials is the quickest signal).

### NetBIOS, null sessions, and RID enumeration
The source PDF explains the historical relationship between NetBIOS and SMB:
- NetBIOS over TCP/IP commonly uses UDP 137 for name service, UDP 138 for datagrams, and TCP 139 for session service.
- Modern SMB can run directly over TCP 445 without a NetBIOS session.
- The source notes use the Windows command `nbtstat` to inspect NetBIOS information.

A **null session** is an unauthenticated SMB/RPC connection that may expose information on a misconfigured or legacy Windows host. The source describes connecting to the IPC$ administrative share and querying information without supplying a username/password. This behavior is not guaranteed on modern, hardened systems.

Tools and examples named in the source:

~~~bash
smbclient -L //<target>/ -N
rpcclient -N -U "" <target>
enum4linux -a <target>
~~~

The source says enum4linux can organize target information, workgroup/domain, Domain SID, OS details, users, shares, password policy, groups, user SIDs, and printer information. The notes also describe **RID cycling**: querying candidate Relative Identifier values appended to a known domain SID to discover account names where the server permits such enumeration. Treat any discovered account information as sensitive and stay within scope.

## 5. Real CVEs

- **MS17-010 / EternalBlue (CVE-2017-0144)** — SMBv1 remote code execution; see 1.4 for the full case study and detection script.

## 6. Self-test

1. What does it mean practically if a target has 139 open but not 445, versus the reverse?
2. Why check for anonymous/null sessions before trying any password list?
3. What is `enum4linux` actually doing that `smb_version` alone doesn't?

## 7. Quick recap

SMB/Samba is chattier than most protocols by design — version, usernames, and shares often leak before you've authenticated at all. Check anonymous access first, then enumerate, then attempt logins.
