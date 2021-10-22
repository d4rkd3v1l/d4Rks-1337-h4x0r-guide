# Wordlists / dictionaries

## Related

[Passwords & credentials](/03-exploitation/02-passwords/04-passwords-credentials.md)

## Wordlists

```bash
/usr/share/wordlists/
```

## Password Lists

### rockyou

[rockyou.txt](http://downloads.skullsecurity.org/passwords/rockyou.txt.bz2)  
Compromise from 2009 from a social game and advertising website  

### msf

```bash
/usr/share/metasploit-framework/data/wordlists
```

### crackstation-human-only

[crackstation-human-only](http://download.g0tmi1k.com/wordlists/large/crackstation-human-only.txt.gz)  
Real human passwords leaked from various website databases.  

### m3g0tr0n_Passwords_WordList_CLEANED

[m3g0tr0n_Passwords_WordList_CLEANED](http://wordbook.xyz/download/big/m3g9tr0n_Passwords_WordList_CLEANED.zip)  
List of 122 Million Passwords

## SecLists

> SecLists is the security tester’s companion. It’s a collection of multiple types of lists used during security assessments, collected in one place. List types include usernames, passwords, URLs, sensitive data patterns, fuzzing payloads, web shells, and many more.  
[GitHub - danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)

Search for default creds (e.g. for tomcat)
```bash
find /usr/share/seclists | grep -i tomcat`
```
