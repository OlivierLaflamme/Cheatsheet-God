[+] Weak SSH Ciphers

sudo nano /etc/ssh/sshd_config

Add the following lines:

Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,arcfour
MACs hmac-sha1,hmac-ripemd160

Restart SSH


[+] Unquoted Service Paths 

Run Regedit and browse to HKLM\SYSTEM\CurrentControlSet\services
Find the service in question and simply add " " either side of the ImagePath string.

Check permissions:
C:\Users\user>icacls "C:\Program Files (x86)\Vuln\Vuln Software 7.0\software.exe"