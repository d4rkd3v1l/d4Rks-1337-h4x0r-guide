# UDP 161: SNMP

> Simple Network Management Protocol is an Internet Standard protocol for collecting and organizing information about managed devices on IP networks and for modifying that information to change device behavior.  
> Typically, SNMP agents listen on UDP port 161, asynchronous traps are received on port 162.  
>
> --<cite>[Wikipedia](https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol)</cite>

## Nmap

```bash
nmap -sU --open -p 161 <ip>
```

## Management information Base (MiB)

[IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/ssw_aix_53/eos/eos.htm)  

--- | ---
1.3.6.1.2.1.25.1.6.0 | System Processes 
1.3.6.1.2.1.25.4.2.1.2 | Running Programs 
1.3.6.1.2.1.25.4.2.1.4 | Processes Path 
1.3.6.1.2.1.25.2.3.1.4 | Storage Units 
1.3.6.1.2.1.25.6.3.1.2 | Software Name 
1.3.6.1.4.1.77.1.2.25 | User Accounts 
1.3.6.1.2.1.6.13.1.3 | TCP Local Ports

Community strings  
[fuzzdb/wordlist-common-snmp-community-strings.txt at master · fuzzdb-project/fuzzdb · GitHub](https://github.com/fuzzdb-project/fuzzdb/blob/master/wordlists-misc/wordlist-common-snmp-community-strings.txt)  

[GitHub - trailofbits/onesixtyone: Fast SNMP Scanner](https://github.com/trailofbits/onesixtyone)
```bash
onesixtyone -c <community-strings-file> -i <ips>
```

## SNMPWalk

```bash
snmpwalk -c public -v1 <ip>
```

Using mib-values
```bash
snmpwalk -c public -v1 <ip> 1.3.6.1.2.1.25.4.2.1.2
```

### Make MiBs readable

```bash
apt install snmp-mibs-downloader
```

Comment out `mibs:` line in `/etc/snmp/snmp.conf`

```bash
snmpwalk -c public -v2c <ip>
```

## snmp-check

```bash
snmp-check <ip>
```

## Other tools

* snmpenum
