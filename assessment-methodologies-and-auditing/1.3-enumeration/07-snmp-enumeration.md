# SNMP Enumeration

**Scope:** Query only authorized devices.

## 1. What SNMP is
Simple Network Management Protocol (SNMP) is used to monitor and manage network devices such as routers, switches, printers, and servers. Administrators may use it to read device status and configuration information. Depending on configuration and permissions, management operations may also change device settings.

## 2. Ports and message concepts
SNMP commonly uses UDP:
- UDP 161 for manager-to-agent queries.
- UDP 162 for notifications/traps sent to a manager.

The source PDF names four operation types:
- **Read** — retrieve managed-object values.
- **Write** — change supported values when permitted.
- **Trap** — send an asynchronous notification.
- **Traversal** — walk through a branch of the management information tree.

## 3. Community strings and versions
The source notes describe SNMP community strings as shared-string access control, and name the common defaults **public** (often read access) and **private** (often write access). Treat these as historical/default examples, not guarantees. Real permissions depend on SNMP version and device configuration. SNMPv1/v2c community strings do not provide the security properties of modern authenticated/encrypted management protocols.

## 4. MIB and OID
A **Management Information Base (MIB)** defines the managed objects that an SNMP agent exposes. Objects are organized hierarchically. An **Object Identifier (OID)** identifies a specific object by its position in that hierarchy. A walk can enumerate a subtree and reveal information such as interface names, system descriptions, or device counters, depending on access.

## 5. Pentester workflow
1. Confirm that SNMP testing is in scope.
2. Identify whether UDP 161 is reachable.
3. Determine the SNMP version and permitted access.
4. Enumerate only the information authorized by the engagement.
5. Record exposed system details and whether read/write access is unexpectedly broad.
6. Avoid changing device settings during discovery unless explicitly approved.

## 6. Defensive checklist
- Prefer SNMPv3 with authentication and privacy where supported.
- Change default community strings and avoid guessable values.
- Restrict management access to trusted management networks.
- Use read-only access where write operations are unnecessary.
- Monitor management queries and unexpected configuration changes.

## 7. Self-check
1. What is SNMP used for?
2. What is the difference between an MIB and an OID?
3. What is the purpose of a trap?
4. Why should public and private not be assumed to exist on every device?
5. Why is SNMPv3 preferred over community-string-based versions?
6. Why is write access more sensitive than read-only access?
