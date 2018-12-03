[+] Windows vulnerabilities:

Windows XP:
CVE-2012-4349        Unquoted windows search path - Windows provides the capability of including spaces in path names - can be root
CVE-2011-1345        Internet Explorer does not properly handle objects in memory - allows remote execution of code via object
CVE-2010-3138        EXPLOIT-DB 14765 - Untrusted search path vulnerability - allows local users to gain privileges via a Trojan horse
CVE-2011-5046        EXPLOIT-DB 18275 - GDI in windows does not properly validate user-mode input - allows remote code execution
CVE-2002-1214        ms02_063_pptp_dos - exploits a kernel based overflow when sending abnormal PPTP Control Data packets - code execution, DoS
CVE-2003-0352        ms03_026_dcom - exploits a stack buffer overflow in the RPCSS service
CVE-2003-0533        MS04-011 - ms04_011_lsass - exploits a stack buffer overflow in the LSASS service
CVE-2003-0719        ms04_011_pct - exploits a buffer overflow in the Microsoft Windows SSL PCT protocol stack - Private communication target overflow
CVE-2010-3970        ms11_006_createsizeddibsection - exploits a stack-based buffer overflow in thumbnails within .MIC files - code execution
CVE-2010-3147        EXPLOIT-DB 14745 - Untrusted search path vulnerability in wab.exe - allows local users to gain privileges via a Trojan horse 
CVE-2003-0812        ms03_049_netapi - exploits a stack buffer overflow in the NetApi32 
CVE-2003-0818        ms04_007_killbill -  vulnerability in the bit string decoding code in the Microsoft ASN.1 library
CVE-2003-0822        ms03_051_fp30reg_chunked - exploit for the chunked encoding buffer overflow described in MS03-051 
CVE-2004-0206        ms04_031_netdde - exploits a stack buffer overflow in the NetDDE service

Windows 7:
CVE-2014-4114        ms14_060_sandworm - exploits a vulnerability found in Windows Object Linking and Embedding - arbitrary code execution
CVE-2015-0016        ms15_004_tswbproxy -  abuses a process creation policy in Internet Explorer's sandbox - code execution
CVE-2014-4113        ms14_058_track_popup_menu - exploits a NULL Pointer Dereference in win32k.sys - arbitrary code execution
CVE-2010-3227        EXPLOIT-DB - Stack-based buffer overflow in the UpdateFrameTitleForDocument method - arbitrary code execution
CVE-2018-8494        remote code execution vulnerability exists when the Microsoft XML Core Services MSXML parser processes user input
CVE-2010-2744        EXPLOIT-DB 15894 - kernel-mode drivers in windows do not properly manage a window class - allows privileges escalation
CVE-2010-0017        ms10_006_negotiate_response_loop - exploits a denial of service flaw in the Microsoft Windows SMB client - DoS
CVE-2010-0232        ms10_015_kitrap0d - create a new session with SYSTEM privileges via the KiTrap0D exploit
CVE-2010-2550        ms10_054_queryfs_pool_overflow - exploits a denial of service flaw in the Microsoft Windows SMB service - DoS
CVE-2010-2568        ms10_046_shortcut_icon_dllloader - exploits a vulnerability in the handling of Windows Shortcut files (.LNK) - run a payload

Windows 8:
CVE-2013-0008        ms13_005_hwnd_broadcast - attacker can broadcast commands from lower Integrity Level process to a higher one - privilege escalation
CVE-2013-1300        ms13_053_schlamperei - kernel pool overflow in Win32k - local privilege escalation
CVE-2013-3660        ppr_flatten_rec - exploits EPATHOBJ::pprFlattenRec due to the usage of uninitialized data - allows memory corruption
CVE-2013-3918        ms13_090_cardspacesigninhelper - exploits CardSpaceClaimCollection class from the icardie.dll ActiveX control - code execution
CVE-2013-7331        ms14_052_xmldom - uses Microsoft XMLDOM object to enumerate a remote machine's filenames
CVE-2014-6324        ms14_068_kerberos_checksum - exploits the Microsoft Kerberos implementation - privilege escalation
CVE-2014-6332        ms14_064_ole_code_execution -  exploits the Windows OLE Automation array vulnerability 
CVE-2014-6352        ms14_064_packager_python - exploits Windows Object Linking and Embedding (OLE) - arbitrary code execution
CVE-2015-0002        ntapphelpcachecontrol - NtApphelpCacheControl Improper Authorization Check - privilege escalation
   
Windows 10:  
CVE-2015-1769        MS15-085 - Vulnerability in Mount Manager - Could Allow Elevation of Privilege
CVE-2015-2426        ms15_078_atmfd_bof MS15-078 - exploits a pool based buffer overflow in the atmfd.dll driver 
CVE-2015-2479        MS15-092 - Vulnerabilities in .NET Framework - Allows Elevation of Privilege
CVE-2015-2513        MS15-098 - Vulnerabilities in Windows Journal - Could Allow Remote Code Execution
CVE-2015-2423        MS15-088 - Unsafe Command Line Parameter Passing - Could Allow Information Disclosure
CVE-2015-2431        MS15-080 - Vulnerabilities in Microsoft Graphics Component - Could Allow Remote Code Execution
CVE-2015-2441        MS15-091 - Vulnerabilities exist when Microsoft Edge improperly accesses objects in memory - allows remote code execution
CVE-2015-0057        exploits GUI component of Windows namely the scrollbar element - allows complete control of a Windows machine

Windows Server 2003:
CVE-2008-4114        ms09_001_write - exploits a denial of service vulnerability in the SRV.SYS driver - DoS
CVE-2008-4250        ms08_067_netapi  - exploits a parsing flaw in the path canonicalization code of NetAPI32.dll - bypassing NX 
CVE-2017-8487        allows an attacker to execute code when a victim opens a specially crafted file - remote code execution
