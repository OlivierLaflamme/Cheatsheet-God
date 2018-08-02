Useful commands
---------------

[+] Remove text using sed

cat SSL_Hosts.txt | sed -r 's/\ttcp\t/:/g'

[+] Port forwarding using NCAT

ncat -lvkp 12345 -c "ncat --ssl 192.168.0.1 443"

[+] Windows 7 or later, build port relay

C:\> netsh interface portproxy add v4tov4 listenport=<LPORT> listenaddress=0.0.0.0 connectport=<RPORT> connectaddress=<RHOST>

[+] Grab HTTP Headers

curl -LIN <host>

[+] Quickly generate an MD5 hash for a text string using OpenSSL

echo -n 'text to be encrypted' | openssl md5

[+] Shutdown a Windows machine from Linux

net rpc shutdown -I ipAddressOfWindowsPC -U username%password

[+] Conficker Detection with NMAP

nmap -PN -d -p445 --script=smb-check-vulns --script-args=safe=1 IP-RANGES

[+] Determine if a port is open with bash

(: </dev/tcp/127.0.0.1/80) &>/dev/null && echo "OPEN" || echo "CLOSED"