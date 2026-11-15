# Armitage

## ​[Armitage](https://www.offsec.com/metasploit-unleashed/armitage/) - MSF GUI <a href="#armitage-msf-gui" id="armitage-msf-gui"></a>

🗒️ **Armitage** is a graphical user interface (GUI) for the Metasploit Framework, a widely used penetration testing and ethical hacking tool. Armitage provides a user-friendly interface for interacting with Metasploit's powerful features, making it easier for cybersecurity professionals to perform tasks related to network penetration testing, vulnerability assessment, and exploit development.

Some key features of Armitage include:

1. **Visual Interface:** Armitage offers a visual representation of network targets and their vulnerabilities, making it easier for users to understand and manage their testing environment.
2. **Automated Exploitation:** It simplifies the process of finding and exploiting vulnerabilities in target systems by providing automated tools and workflows.
3. **Session Management:** Armitage allows users to manage active sessions and connections to compromised systems, which is crucial for post-exploitation tasks.
4. **Reporting:** Users can generate reports detailing their penetration testing activities and findings.

> 🔬 **Port Scanning & Enumeration With Armitage** - lab by INE
>
> * Victim Machine 1: `10.2.21.86`
> * Victim Machine 2: `10.2.25.150`

```bash
service postgresql start && msfconsole -qdb_status
[*] Connected to msf. Connection type: postgresql. 
# Open a new tab and start Armitagearmitage
# Answer "YES" for the RPC serverArmitage
```



* **Hosts - Add Hosts**
  * Add victim 1 IP
  * Set the lab as `Victim 1`
* Right-click the target and **Scan** it



* Check **Services**
* Perform an **Nmap Scan** from the **Hosts** menu



* Check **Services**



#### Exploitation <a href="#exploitation" id="exploitation"></a>

* Search for `rejetto` and launch the exploit module



* Try **Dump Hashes** via the `registry method`

Metasploit - post/windows/gather/smart\_hashdump



* Saved hashes can be found under the **View - Loot** menu

Administrator:500:aad3b435b51404eeaad3b435b51404ee:5c4d59391f656d5958dab124ffeabc20:::

* **Browse Files**



* **Show Processes**



#### Pivoting <a href="#pivoting" id="pivoting"></a>

* Setup **Pivoting**



* Add, Enumerate and Exploit `Victim 2`



* Port forward the port `80` and use `nmap`

\# In the Meterpreter tabportfwd add -l 1234 -p 80 -r 10.2.25.150# In the msf Console tabdb\_nmap -sV -p 1234 localhost



* Remove the created localhost `127.0.0.1`
* Search for `BadBlue` and use the `badblue_passthru` exploit on `Victim 2`



* Migrate to an `x64` from the **Processes** tab
* Dump hashes with the `lsass method`

#### Armitage Kali Linux Install <a href="#armitage-kali-linux-install" id="armitage-kali-linux-install"></a>

sudo apt install armitage -ysudo msfdb initsudo nano /etc/postgresql/15/main/pg\_hba.conf# On line 87 switch “scram-sha-256” to “trust”sudo systemctl enable postgresqlsudo systemctl restart postgresqlsudo armitage
