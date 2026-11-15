# Active Directory Fundamentals


**Focus:** recognize the core directory concepts and the attack paths named in the study notes.

## 1. What Active Directory is
Active Directory (AD) is Microsoft's directory service for centrally managing identities and resources in a Windows domain environment. It stores and organizes information about users, computers, groups, and other network resources.

A **Domain Controller (DC)** hosts AD services and participates in domain authentication and directory operations.

## 2. Core terms

| Term | Meaning |
|---|---|
| Domain | Administrative and identity boundary in an AD environment |
| Domain Controller | Server providing AD domain services |
| User account | Identity used by a person or service |
| Computer account | Identity for a machine joined to the domain |
| Group | Collection of accounts used to simplify access management |
| Organizational Unit (OU) | Container used to organize directory objects and apply policy |
| Group Policy Object (GPO) | Collection of configuration and security settings applied to users/computers |

**OU is not the same as a group.** An OU organizes directory objects and can have policy linked to it; a security group is commonly used to assign permissions.

Key distinctions:
- **Security groups:** used for permissions.
- **Distribution groups:** used for email distribution rather than granting access permissions.

## 3. Authentication and authorization
- **Authentication:** determining who an identity is.
- **Authorization:** determining what that identity is allowed to access.

The practical notes identify two Windows authentication approaches:

### NTLM
NTLM is a challenge-response authentication protocol retained for compatibility with legacy environments.

### Kerberos
Kerberos is ticket-based authentication and is the default domain authentication protocol in modern AD environments. A client first obtains a Ticket-Granting Ticket (TGT) from the Key Distribution Center (KDC), then uses it to request a service ticket for a particular service. The service ticket is presented to that service; the user's password is not repeatedly sent to each service.

## 4. Group Policy and LSDOU
Group Policy is used to centrally enforce configuration and security settings, such as password policy, screen-lock settings, device restrictions, and scripts.

The study notes list the application order as **LSDOU**:
1. Local
2. Site
3. Domain
4. OU

The effective result depends on policy inheritance, links, enforcement, and conflicts; do not reduce every real-world case to “last applied always wins” without checking the actual policy configuration.

## 5. LDAP and DNS
**LDAP** is used to query and manage directory information, including users, groups, and computers. LDAP commonly uses TCP 389; LDAP over TLS (LDAPS) commonly uses TCP 636. Active Directory also uses DNS SRV records to advertise domain-controller services.

AD relies heavily on DNS to locate domain controllers and domain services. If clients cannot resolve the relevant AD DNS records, domain operations and authentication discovery can fail.

## 6. Common Active Directory attack concepts

The following concepts are useful to recognize:

| Concept | High-level idea |
|---|---|
| Password spraying | Trying a small number of candidate passwords across multiple accounts |
| Kerberoasting | Requesting service tickets for service accounts and attempting offline password recovery from the ticket material |
| AS-REP roasting | Targeting accounts configured without Kerberos pre-authentication |
| Pass-the-Hash | Reusing an NTLM hash as an authentication material |
| Pass-the-Ticket | Reusing a Kerberos ticket |
| Lateral movement | Moving from one compromised system to another |
| Privilege escalation | Obtaining a higher level of local or domain permissions |

The notes also name tools to recognize: **BloodHound, Mimikatz, CrackMapExec, Impacket, and PowerView**. Tool recognition is not permission to run them; use a lab or explicitly authorized environment.

## 7. Defensive perspective
- Enforce strong authentication and monitor unusual authentication patterns.
- Reduce legacy NTLM use where operationally possible.
- Protect service-account credentials and use managed service accounts where appropriate.
- Require Kerberos pre-authentication unless a documented exception exists.
- Apply least privilege and review privileged group membership.
- Audit GPO links, permissions, and changes.
- Monitor lateral movement and unusual remote administration.
- Keep domain controllers and member systems patched.

## 8. Self-check
1. What role does a Domain Controller play?
2. What is the difference between a user account and a computer account?
3. Why is an OU not the same thing as a security group?
4. What is the difference between authentication and authorization?
5. Which protocol is ticket-based: NTLM or Kerberos?
6. What does LDAP allow a client to query?
7. Why does AD depend on DNS?
8. What is the high-level difference between Kerberoasting and AS-REP roasting?
9. What do pass-the-hash and pass-the-ticket reuse?
10. What is lateral movement?

## 9. Quick recap
- AD centrally manages identities and resources in Windows domains.
- Domain Controllers provide core domain services.
- OUs organize objects and policy; groups help assign permissions.
- Kerberos is ticket-based; NTLM is a legacy challenge-response mechanism.
- LDAP queries directory information; DNS helps clients locate AD services.
- Common attack concepts include password spraying, Kerberoasting, AS-REP roasting, pass-the-hash, pass-the-ticket, lateral movement, and privilege escalation.


## Resources

- [Microsoft Learn: Active Directory Domain Services](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/)
- [Microsoft Learn: Kerberos authentication overview](https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview)
- [Microsoft Learn: LDAP](https://learn.microsoft.com/en-us/windows/win32/adsi/ldap)
- [Microsoft Learn: Group Policy](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-overview)
- [MITRE ATT&CK: Enterprise techniques](https://attack.mitre.org/techniques/enterprise/)
- [BloodHound documentation](https://bloodhound.specterops.io/)
