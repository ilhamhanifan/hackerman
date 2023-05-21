# Target Info
Target Machine IP = 10.129.72.7

# Solution
1. File Transfer Protocol
2. 21
3. sftp
4. ping
5. run nmap scan to find service version
```
○ sudo nmap 10.129.72.7 -sV
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 11:14 WIB
Nmap scan report for 10.129.72.7
Host is up (1.8s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 21.03 seconds
```
6. Unix (from -sV scan)
7. ftp -h
8. anonymous
```
○ ftp 10.129.72.7
Connected to 10.129.72.7.
220 (vsFTPd 3.0.3)
Name (10.129.72.7:zeta): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```
9. 230
10. ls
11. get
12 get the flag via ftp
```
○ ftp 10.129.72.7
Connected to 10.129.72.7.
220 (vsFTPd 3.0.3)
Name (10.129.72.7:zeta): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||56658|)
150 Here comes the directory listing.
-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
226 Directory send OK.
ftp> get flag.txt
local: flag.txt remote: flag.txt
229 Entering Extended Passive Mode (|||45704|)
150 Opening BINARY mode data connection for flag.txt (32 bytes).
100% |*************************************************************************************|    32        0.10 KiB/s    00:00 ETA
226 Transfer complete.
32 bytes received in 00:00 (0.03 KiB/s)
ftp> exit
221 Goodbye.

zeta at melforger in ~
○ cat flag.txt
035db21c881520061c53e0536e44f815%                                                                                                 
```

flag = 035db21c881520061c53e0536e44f815
