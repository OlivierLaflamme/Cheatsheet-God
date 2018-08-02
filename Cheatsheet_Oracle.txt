Oracle Penetration Testing
--------------------------

Tools within Kali:

oscanner
root@kali:~# oscanner -s 192.168.1.15 -P 1040

sidguess
root@kali:~# sidguess -i 192.168.1.205 -d /usr/share/wordlists/metasploit/unix_users.txt

tnscmd10g
root@kali:~# tnscmd10g version -h 192.168.1.20

Nmap
nmap -p 1521 -A 192.168.15.205

Nmap nse scripts
Metasploit auxiliaries