# Summary

## Reconnaissance
TODO: OSINT, Google Dorking, etc.

## Enumeration

* [Network discovery](02-enumeration/01-network-discovery.md)
* [Port scanning](02-enumeration/02-port-scanning.md)
* [Webserver scanning](02-enumeration/03-webserver-scanning.md)
* [Exploit detection](02-enumeration/04-exploit-detection.md)
* [Fuzzing](02-enumeration/05-fuzzing.md)
* [Process monitoring](02-enumeration/06-process-monitoring.md)

## Services

* TCP
    * [TCP 21: FTP](XX-services/01-tcp/TCP-21-FTP.md)
    * [TCP 22: SSH](XX-services/01-tcp/TCP-22-SSH.md)
    * [TCP 23: Telnet](XX-services/01-tcp/TCP-23-Telnet.md)
    * [TCP 25, 587: SMTP](XX-services/01-tcp/TCP-25-587-SMTP.md)
    * [TCP 53: DNS](XX-services/01-tcp/TCP-53-DNS.md)
    * [TCP 80, 443: HTTP(S)](XX-services/01-tcp/TCP-80-443-HTTP.md)
    * [TCP 88: Kerberos](XX-services/01-tcp/TCP-88-Kerberos.md)
    * [TCP 110, 995: POP3(S)](XX-services/01-tcp/TCP-110-995-POP3.md)
    * [TCP 111: rpcbind](XX-services/01-tcp/TCP-111-rpcbind.md)
    * [TCP 135: MSRPC](XX-services/01-tcp/TCP-135-MSRPC.md)
    * [TCP 139, 445: NetBIOS, SMB](XX-services/01-tcp/TCP-139-445-NetBIOS-SMB.md)
    * [TCP 143, 993: IMAP(S)](XX-services/01-tcp/TCP-143-993-IMAP.md)
    * [TCP 389, 636, 3268, 3269: LDAP](XX-services/01-tcp/TCP-389-636-3268-3269-LDAP.md)
    * [TCP 1433, UDP 1434: MSSQL Server](XX-services/01-tcp/TCP-1433-UDP-1434-MSSQL-Server.md)
    * [TCP 2049: NFS](XX-services/01-tcp/TCP-2049-NFS.md)
    * [TCP 3306: MySQL](XX-services/01-tcp/TCP-3306-MySQL.md)
    * [TCP 3389: RDP](XX-services/01-tcp/TCP-3389-RDP.md)
    * [TCP 5985: WinRM](XX-services/01-tcp/TCP-5985-WinRM.md)
    * [TCP 6379: Redis](XX-services/01-tcp/TCP-6379-Redis.md)
    
* UDP
    * [UDP 137, 138, TCP 139: NetBIOS](XX-services/02-udp/UDP-137-138-TCP-139-NetBIOS.md)
    * [UDP 161: SNMP](XX-services/02-udp/UDP-161-SNMP.md)
    
* Misc
    * [Active Directoy](XX-services/03-misc/Active-Directoy.md)
    * [Apache Tomcat](XX-services/03-misc/Apache-Tomcat.md)
    * [H2 Databases](XX-services/03-misc/H2-Databases.md)
    * [IIS](XX-services/03-misc/IIS.md)
    * [IPsec](XX-services/03-misc/IPsec.md)
    * [IRC](XX-services/03-misc/IRC.md)
    * [Java Applets](XX-services/03-misc/Java-Applets.md)
    * [Java RMI](XX-services/03-misc/Java-RMI.md)
    * [Jenkins](XX-services/03-misc/Jenkins.md)
    * [Oracle](XX-services/03-misc/Oracle.md)
    * [PHP](XX-services/03-misc/PHP.md)
    * [SharePoint](XX-services/03-misc/SharePoint.md)

## Exploitation

* Shells
    * [Shells](03-exploitation/01-shells/01-shells.md)
    * [Terminal config & TTY](03-exploitation/01-shells/02-terminal-config-TTY.md)

* Passwords
    * [Hashcat](03-exploitation/02-passwords/01-hashcat.md)
    * [John the Ripper (JTR)](03-exploitation/02-passwords/02-john-the-ripper.md)
    * [Hydra](03-exploitation/02-passwords/03-hydra.md)
    * [Passwords & credentials](03-exploitation/02-passwords/04-passwords-credentials.md)

* Injections
    * [SQL Injection (SQLi)](03-exploitation/03-injections/01-SQL-injection.md)
    * [Cross Site Scripting (XSS)](03-exploitation/03-injections/02-cross-site-scripting.md)
    * [TODO: Template Injection]()

* File inclusions
    * [File inclusions (LFI, RFI)](03-exploitation/04-file-inclusions/01-file-inclusions.md)

* Buffer overflows
    * [TODO]()

* Databases
    * [SQSH](03-exploitation/06-databases/03-SQSH.md)

## Privilege escalation

* Linux
    * [Overview](04-privilege-escalation/01-linux/01-overview.md)

* Windows
    * [Overview](04-privilege-escalation/02-windows/01-overview.md)
    * [Mimikatz](04-privilege-escalation/02-windows/02-mimikatz.md)
    * [PowerSploit](04-privilege-escalation/02-windows/03-power-sploit.md)
    * [Juicy Potato, Rotten Potato (NG)](04-privilege-escalation/02-windows/04-juicy-potato-rotten-potato.md)
    * [JAWS](04-privilege-escalation/02-windows/05-jaws.md)
    * [Empire](04-privilege-escalation/02-windows/06-empire.md)
    * [SILENTTRINITY](04-privilege-escalation/02-windows/07-silenttrinity.md)

## Post eploitation
TODO: Cleanup, Pivoting, etc.
