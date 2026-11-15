# MSF Introduction

## What is Metasploit (MSF)?

Metasploit Framework is an open-source penetration testing and exploitation tool used for testing and evaluating the security of computer systems and networks. Developed by Rapid7, Metasploit is one of the most popular and widely used tools in the field of ethical hacking and cybersecurity. It provides a comprehensive and extensible framework for finding vulnerabilities, conducting penetration tests, and developing and executing exploits.

Key features and components of Metasploit Framework include:

1. Exploits: Metasploit contains a vast collection of exploits that can be used to target known vulnerabilities in various software applications, operating systems, and network devices. These exploits are used to gain unauthorized access to target systems for testing and assessment purposes.
2. Payloads: Payloads are code snippets or scripts that are delivered to a compromised system after a successful exploitation. These payloads can be used for tasks such as creating reverse shells, running arbitrary commands, or exfiltrating data from the target.
3. Post-exploitation Modules: Metasploit includes a range of post-exploitation modules that allow testers to perform tasks on compromised systems, such as gathering information, escalating privileges, and maintaining access.
4. Auxiliary Modules: These modules provide additional functionality, such as scanning, fingerprinting, and brute-force attacks. They are not directly involved in exploitation but assist in the overall penetration testing process.
5. Meterpreter: Meterpreter is a powerful post-exploitation payload included with Metasploit. It provides a command shell with extensive capabilities for interacting with the compromised system, including file manipulation, privilege escalation, and network pivoting.
6. Exploit Development: Metasploit Framework allows security professionals to develop and test their own exploits for new vulnerabilities.
7. Resource Scripts: Users can create resource scripts to automate tasks and actions within Metasploit, simplifying the process of penetration testing.

{% embed url="https://www.offsec.com/metasploit-unleashed/" %}

#### Terminology <a href="#terminology" id="terminology"></a>

| Term              | Description                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------------- |
| **Interface**     | Methods of interacting with the Metasploit Framework (`msfconsole`, Metasploit cmd)                       |
| **Module**        | Pieces of code that perform a particular task (an exploit)                                                |
| **Vulnerability** | Exploitable flaw or weakness in a computer system or network                                              |
| **Exploit**       | Code/Module used to take advantage of a vulnerability                                                     |
| **Payload**       | Piece of code delivered to the target by an exploit (execute arbitrary commands or provide remote access) |
| **Listener**      | Utility that listens for an incoming connection from a target                                             |

>  **Exploit** is launched (takes advantage of the vulnerability)  **Payload** dropped (executes a reverse shell command)  Connects back to the **Listener**

## Interfaces <a href="#interfaces" id="interfaces"></a>

 **Metasploit Framework Console** ([**MSFconsole**](https://www.offsec.com/metasploit-unleashed/msfconsole/)) - an all in one interface that provides with access to all the functionality of the MSF.msfconsole **Metasploit Framework Command Line Interface** ([**MSFcli**](https://www.offsec.com/metasploit-unleashed/msfcli/)) - a command line utility used to facilitate the creation of automation scripts that utilize Metasploit modules.



* Discontinued in 2015, MSFconsole can be used with the same functionality of _redirecting output from other tools into `msfcli` and vice versa._

 **Metasploit Community Edition GUI** - a web based GUI front-end of the MSF. [**Armitage**](https://www.kali.org/tools/armitage/) - a free Java based GUI front-end cyber attack management tool for the MSF.

* Visualizes targets and simplifies network discovery
* Recommends exploits
* Exposes the advanced capabilities of the MSF

## ​[Architecture](https://www.offsec.com/metasploit-unleashed/metasploit-architecture/)​ <a href="#architecture" id="architecture"></a>

Metasploit Framework Architecture - oreilly.com A **module** is the piece of code that can be utilized and executed by the MSF.The MSF **libraries** (Rex, Core, Base) allow to extend and initiate functionality, facilitating the execution of modules without having to write additional code.



### ​[Modules](https://www.offsec.com/metasploit-unleashed/modules-and-locations/)​ <a href="#modules" id="modules"></a>

| MSF Module    | Description                                                                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Exploit**   | Used to take advantage of a vulnerability, usually paired with a payload                                                                                                                        |
| **Payload**   | Code delivered and remotely executed on the target _after successful exploitation_ - **e.g.** a reverse shell that initiates a connection                                                       |
| **Encoder**   | Used to encode payloads in order to avoid Anti Virus detection - **e.g.** [shikata\_ga\_nai](https://www.mandiant.com/resources/blog/shikata-ga-nai-encoder-still-going-strong) encoding scheme |
| **NOPS**      | Keep the payload sizes consistent across exploit attempts and ensure the _stability of a payload_ on the target system                                                                          |
| **Auxiliary** | Is not paired with a payload, used to perform additional functionality - **e.g.** port scanners, fuzzers, sniffers, etc                                                                         |

### ​[Payload Types](https://www.offsec.com/metasploit-unleashed/payloads/)​ <a href="#payload-types" id="payload-types"></a>

**Payloads** are created at runtime from various components. Depending on the target system and infrastructure, there are two types of payloads that can be used:

* **Non-Staged Payload** - sent to the target system as is, along with the exploit
* **Staged Payload** - sent to the target in two parts:
  * the **stager** (first part) establish a stable communication channel between the attacker and target. It contains a payload, the stage, that initiates a reverse connection back to the attacker
  * the **stage** (second part) is downloaded by the stager and executed
    * executes arbitrary commands on the target
    * provides a reverse shell or Meterpreter session

 The [**Meterpreter**](https://www.offsec.com/metasploit-unleashed/about-meterpreter/) is an advanced multi-functional payload executed by in memory DLL injection stagers on the target system.

* Communicates over the stager socket
* Provides an interactive command interpreter on the target system

### ​[File System](https://www.offsec.com/metasploit-unleashed/filesystem-and-libraries/)​ <a href="#file-system" id="file-system"></a>

ls /usr/share/metasploit-frameworkls /usr/share/metasploit-framework

* MSF filesystem is intuitive and organized by directories.
* Modules are stored under:
  * `/usr/share/metasploit-framework/modules/`
  * `~/.msf4/modules` - user specified modules







## Pentesting with MSF <a href="#pentesting-with-msf" id="pentesting-with-msf"></a>

 [**PTES**](http://www.pentest-standard.org/index.php/Main\_Page) (**P**enetration **T**esting **E**xecution **S**tandard) is a methodology that contains 7 main sections, defined by the standard as a comprehensive basis for penetration testing execution.

* can be adopted as a roadmap for Metasploit integration and understanding of the phases of a penetration test.

> The various phases involved in a typical pentest should be: **Pre-Engagement Interactions** **Information Gathering** **Enumeration**
>
> * Threat Modeling
> * Vulnerability Analysis
>
>  **Exploitation**
>
> * Identify Vulnerable Services
> * Prepare Exploit Code
> * Gaining Access
> * Bypass AV detection
> * Pivoting
>
>  **Post Exploitation**
>
> * Privilege Escalation
> * Maintaining Persistent Access
> * Clearing Tracks
>
>  **Reporting**

| Pentesting Phase                        | MSF Implementation                     |
| --------------------------------------- | -------------------------------------- |
| **Information Gathering & Enumeration** | Auxiliary Modules, `nmap` reports      |
| **Vulnerability Scanning**              | Auxiliary Modules, `nessus` reports    |
| **Exploitation**                        | Exploit Modules & Payloads             |
| **Post Exploitation**                   | Meterpreter                            |
| **Privilege Escalation**                | Post Exploitation Modules, Meterpreter |
| **Maintaining Persistent Access**       | Post Exploitation Modules, Persistence |

PTES - infopulse.com



## Metasploit Fundamentals <a href="#metasploit-fundamentals" id="metasploit-fundamentals"></a>

### ​[Database](https://www.offsec.com/metasploit-unleashed/using-databases/)​ <a href="#database" id="database"></a>

 The **Metasploit Framework Database** (**msfdb**) contains all the data used with MSF like assessments and scans data, etc.

* Uses PostgreSQL as the primary database - `postgresql` service must be running
* Facilitates the import and storage of scan results (from Nmap, Nessus, other tools)

### ​[MSF Kali Configuration](https://www.kali.org/docs/tools/starting-metasploit-framework-in-kali/)​ <a href="#msf-kali-configuration" id="msf-kali-configuration"></a>

* Use APT package manager on Kali Linux (or on Debian-based distros)

sudo apt update && sudo apt install metasploit-framework -y

* Enable `postgresql` at boot, start the service and initialize MSF database

sudo systemctl enable postgresqlsudo systemctl restart postgresqlsudo msfdb init

* Run **`msfconsole`** to start the Metasploit Framework Console

msfconsole

* Check the db connection is on in the `msfconsole`

db\_status

>  Check this article by StationX  [How to Use Metasploit in Kali Linux + Metasploitable3](https://www.stationx.net/how-to-use-metasploit-in-kali-linux/) which will cover:
>
> * Deploying a Kali Linux virtual machine with Metasploit pre-installed
> * Setting up a target in a virtual lab, Metasploitable3, with Vagrant
> * A sample walkthrough against a vulnerable MySQL Server
> * Frequently Asked Questions (FAQ)

### ​[MSFConsole](https://www.offsec.com/metasploit-unleashed/msfconsole/)​ <a href="#msfconsole" id="msfconsole"></a>

 The **Metasploit Framework Console** (**msfconsole**) is an all-in-one interface and centralized console that allows access to all of the MSF options and features.

* It is launched by running the `msfconsole` command

msfconsole

* Run it in quiet mode without the banner with

msfconsole -q

#### Module Variables <a href="#module-variables" id="module-variables"></a>

An MSF module requires additional information that can be configured through the use of MSF **variables**, both _local_ or _global_ variables, called **`options`** inside the msfconsole.**Variables e.g.** (they are based on the selected module):

* `LHOST` - attacker's IP address
* `LPORT` - attacker's port number (receive reverse connection)
* `RHOST` - target's IP address
* `RHOSTS` - multiple targets/networks IP addresses
* `RPORT` - target port number

#### Useful Commands <a href="#useful-commands" id="useful-commands"></a>

* Run `msfconsole` and check these useful commands:

helpversion​show -hshow allshow exploits​search \<STRING>use \<MODULE\_NAME>set \<OPTION>runexecute # same as run​sessionsconnect





### **Port Scan Example**

search portscanuse auxiliary/scanner/portscan/tcpshow optionsset RHOSTS \<TARGET\_IP>set PORTS 1-1000run# CTRL+C to cancel the running processback



**CVE Exploits Example**

search cve:2017 type:exploit platform:windowssearch cve:2017 type:exploit platform:window



**Payload Options Example**

search eternalblueuse 0# specify the identifierset payload \<PAYLOAD\_NAME>set RHOSTS \<TARGET\_IP>run# orexploit





#### ​[Workspaces](https://docs.rapid7.com/metasploit/managing-workspaces/)​ <a href="#workspaces" id="workspaces"></a>

 Metasploit **Workspaces** allows to manage and organize the hosts, data, scans and activities stored in the `msfdb`.

* Import, manipulate, export data
* Create, manage, switch between workspaces
* Sort and organize the assessments of the penetration test

>  _It's recommended to create a new workspace for each engagement._

msfconsole -qdb\_status\[\*] Connected to msf. Connection type: postgresql.workspace -hworkspace -hworkspace# current working workspace\* default



* **Create** a new workspace

workspace -a Test



* **Change** workspace

workspace \<WORKSPACE\_NAME>workspace -a INE

* **Delete** a workspace

workspace -d Test


## Resources

- [Metasploit documentation](https://docs.metasploit.com/)
- [Metasploit Framework source repository](https://github.com/rapid7/metasploit-framework)
- [Metasploit Unleashed](https://www.offsec.com/metasploit-unleashed/)


## Resources

- [Metasploit documentation](https://docs.metasploit.com/)
- [Metasploit Framework source repository](https://github.com/rapid7/metasploit-framework)
- [Metasploit Unleashed](https://www.offsec.com/metasploit-unleashed/)
