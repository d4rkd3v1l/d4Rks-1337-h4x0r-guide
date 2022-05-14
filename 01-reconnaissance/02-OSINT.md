# OSINT

## Sites

* [OSINT Framework](https://osintframework.com)

## Google Dorking

* [Sans Cheatsheet](https://www.sans.org/posters/google-hacking-and-defense-cheat-sheet)
* [sundowndev Cheatsheet](https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06)

## Mail

Query domain records
```bash
nslookup -type=any <domain>
```

```bash
dig <domain> any
```

### SPF (Sender Policy Framework)

> Sender Policy Framework (SPF) is an email authentication method designed to detect forging sender addresses during the delivery of the email.[2] SPF alone, though, is limited to detecting a forged sender claim in the envelope of the email, which is used when the mail gets bounced.[2] Only in combination with DMARC can it be used to detect the forging of the visible sender in emails (email spoofing[3]), a technique often used in phishing and email spam. 
> 
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Sender_Policy_Framework)

Query domain, check `TXT` record.  

```
"v=spf1 ip4:192.0.2.0/24 ip4:198.51.100.123 a -all"
```  

### MARC (Domain-based Message Authentication, Reporting and Conformance)

> DMARC (Domain-based Message Authentication, Reporting and Conformance) is an email authentication protocol. It is designed to give email domain owners the ability to protect their domain from unauthorized use, commonly known as email spoofing. The purpose and primary outcome of implementing DMARC is to protect a domain from being used in business email compromise attacks, phishing emails, email scams and other cyber threat activities.  
> 
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/DMARC)

Query `_dmarc.<domain>`, check  `TXT` record.  
```
"v=DMARC1;p=none;sp=quarantine;pct=100;rua=mailto:dmarcreports@example.com;"
```
