# Table of contents

* [Introduction](README.md)

## Reconnaissance

* [Recon](01-reconnaissance/01-reconnaissance.md)
* [OSINT](01-reconnaissance/02-OSINT.md)

## Enumeration

* [Network discovery](02-enumeration/01-network-discovery.md)
* [Port scanning](02-enumeration/02-port-scanning.md)
* [Webserver scanning](02-enumeration/03-webserver-scanning.md)
* [Exploit detection](02-enumeration/04-exploit-detection.md)
* [Fuzzing](02-enumeration/05-fuzzing.md)
* [Process monitoring](02-enumeration/06-process-monitoring.md)

## Exploitation

* Shells
  * [Shells](03-exploitation/01-shells/01-shells.md)
  * [TTY](03-exploitation/01-shells/02-TTY.md)
* Passwords
  * [Hashcat](03-exploitation/02-passwords/01-hashcat.md)
  * [John the Ripper (JTR)](03-exploitation/02-passwords/02-john-the-ripper.md)
  * [Hydra](03-exploitation/02-passwords/03-hydra.md)
  * [Passwords & credentials](03-exploitation/02-passwords/04-passwords-credentials.md)
* Web
  * [SQL injection (SQLi)](03-exploitation/03-web/sql-injection.md)
  * [Cross site scripting (XSS)](03-exploitation/03-web/cross-site-scripting.md)
  * [File inclusions (LFI, RFI)](03-exploitation/03-web/file-inclusions.md)
  * [Cross site request forgery (CSRF)](03-exploitation/03-web/cross-site-request-forgery.md)
  * [XML external entity (XXE)](03-exploitation/03-web/xml-external-entity-injection.md)
  * [Cross origin resource sharing (CORS)](03-exploitation/03-web/cross-origin-resource-sharing.md)
  * [Server-side request forgery (SSRF)](03-exploitation/03-web/server-side-request-forgery.md)
  * [Clickjacking](03-exploitation/03-web/clickjacking.md)
  * [File uploads](03-exploitation/03-web/file-uploads.md)
  * [Host header attacks](03-exploitation/03-web/host-header-attacks.md)
  * [Logic flaws](03-exploitation/03-web/logic-flaws.md)
  * [HTTP Request smuggling](03-exploitation/03-web/http-request-smuggling.md)

  * [Template injection](03-exploitation/03-web/template-injection.md)  
* Buffer overflow
  * [General](03-exploitation/05-buffer-overflow/01-general.md)
  * [Linux](03-exploitation/05-buffer-overflow/02-linux.md)
  * [Windows](03-exploitation/05-buffer-overflow/03-windows.md)
* Misc
  * [Evasion](03-exploitation/06-misc/01-evasion.md)
  * [SQSH](03-exploitation/06-misc/02-sqsh.md)

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

## Post exploitation

* [Loot](05-post-exploitation/01-loot.md)
* [Pivoting](05-post-exploitation/02-pivoting.md)
* [Standalone Tools](05-post-exploitation/03-tools.md)

## Services

* TCP
  * [TCP 21: FTP](11-services/01-tcp/TCP-21-FTP.md)
  * [TCP 22: SSH](11-services/01-tcp/TCP-22-SSH.md)
  * [TCP 23: Telnet](11-services/01-tcp/TCP-23-Telnet.md)
  * [TCP 25, 587: SMTP](11-services/01-tcp/TCP-25-587-SMTP.md)
  * [TCP 53: DNS](11-services/01-tcp/TCP-53-DNS.md)
  * [TCP 80, 443: HTTP(S)](11-services/01-tcp/TCP-80-443-HTTP.md)
  * [TCP 88: Kerberos](11-services/01-tcp/TCP-88-Kerberos.md)
  * [TCP 110, 995: POP3(S)](11-services/01-tcp/TCP-110-995-POP3.md)
  * [TCP 111: rpcbind](11-services/01-tcp/TCP-111-rpcbind.md)
  * [TCP 135: MSRPC](11-services/01-tcp/TCP-135-MSRPC.md)
  * [TCP 139, 445: NetBIOS, SMB](11-services/01-tcp/TCP-139-445-NetBIOS-SMB.md)
  * [TCP 143, 993: IMAP(S)](11-services/01-tcp/TCP-143-993-IMAP.md)
  * [TCP 389, 636, 3268, 3269: LDAP](11-services/01-tcp/TCP-389-636-3268-3269-LDAP.md)
  * [TCP 1433, UDP 1434: MSSQL Server](11-services/01-tcp/TCP-1433-UDP-1434-MSSQL-Server.md)
  * [TCP 2049: NFS](11-services/01-tcp/TCP-2049-NFS.md)
  * [TCP 3306: MySQL](11-services/01-tcp/TCP-3306-MySQL.md)
  * [TCP 3389: RDP](11-services/01-tcp/TCP-3389-RDP.md)
  * [TCP 5985: WinRM](11-services/01-tcp/TCP-5985-WinRM.md)
  * [TCP 6379: Redis](11-services/01-tcp/TCP-6379-Redis.md)
  * [TCP 27017: MongoDB](11-services/01-tcp/TCP-27017-MongoDB.md)
* UDP
  * [UDP 137, 138, TCP 139: NetBIOS](11-services/02-udp/UDP-137-138-TCP-139-NetBIOS.md)
  * [UDP 161: SNMP](11-services/02-udp/UDP-161-SNMP.md)
* Misc
  * [Active Directoy](11-services/03-misc/Active-Directoy.md)
  * [Apache Tomcat](11-services/03-misc/Apache-Tomcat.md)
  * [Drupal](11-services/03-misc/Drupal.md)
  * [H2 Databases](11-services/03-misc/H2-Databases.md)
  * [IIS](11-services/03-misc/IIS.md)
  * [IPsec](11-services/03-misc/IPsec.md)
  * [IRC](11-services/03-misc/IRC.md)
  * [Java Applets](11-services/03-misc/Java-Applets.md)
  * [Java RMI](11-services/03-misc/Java-RMI.md)
  * [Jenkins](11-services/03-misc/Jenkins.md)
  * [Joomla](11-services/03-misc/Joomla.md)
  * [Oracle](11-services/03-misc/Oracle.md)
  * [PHP](11-services/03-misc/PHP.md)
  * [SharePoint](11-services/03-misc/SharePoint.md)
  * [WordPress](11-services/03-misc/WordPress.md)

## File transfer

* [Overview](12-file-transfer/01-overview.md)
* [Wget](12-file-transfer/02-wget.md)
* [Pure-FTPd](12-file-transfer/03-pure-ftpd.md)
* [TFTP](12-file-transfer/04-tftp.md)
* [VBScript: Wget clone](12-file-transfer/05-vbscript-wget-clone.md)

## Misc

* [Bash](13-misc/bash.md)
* [Burp Suite](13-misc/burp-suite.md)
* [Crypto](13-misc/crypto.md)
* [Ebowla](13-misc/ebowla.md)
* [Firefox extensions](13-misc/firefox-extensions.md)
* [Impacket](13-misc/impacket.md)
* [Memory forensics](13-misc/memory-forensics.md)
* [Metasploit Framework (MSF)](13-misc/metasploit-framework.md)
* [MITM](13-misc/mitm.md)
* [Msfvenom](13-misc/msfvenom.md)
* [Pass the Hash (PTH)](13-misc/pass-the-hash.md)
* [PowerShell](13-misc/powershell.md)
* [PowerShell on Linux](13-misc/powershell-linux.md)
* [Wireshark](13-misc/wireshark.md)
* [Wordlists and dictionaries](13-misc/wordlists-dictionaries.md)

## Bug Bounty

* [Platforms](21-bug-bounty/01-platforms.md)
* [Tools](21-bug-bounty/02-tools.md)
