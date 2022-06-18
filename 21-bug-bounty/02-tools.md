# Tools

Highly inspired by [The Bug Hunter’s Methodology Jason Haddix @jhaddix](https://youtu.be/gIz_yn0Uvb8).

## Seeds/Roots

* crt.sh [crt.sh | Certificate Search](https://crt.sh)
* [Shodan Search Engine](https://www.shodan.io)
* [Home - Censys](https://censys.io)

### ASN Enumeratiom

* bgp.he.net
* Asnlookup
* Metabigor

### Reverse WHOIS

* whoxy.com
* DOMLink

### Ad/Analytics Relationships

* [builtwith.com](https://builtwith.com) (also available as Firefox addon)
* getrelationship.py

### Google-Fu

* Copyright text
* Terms of service text
* Privacy policy test

## Subs

### Linked and JS Discovery

* Burp Suite Pro (or ZAP Proxy?)
* GoSpider
* hakrawler
* Subdomainizer
* subscraper

### Subdomain Scraping

```
site:twitch-tv -www.twicht.tv
```

```
site:twitch-tv -www.twicht.tv -watch.twitch.tv
```

* Amass `amass enum ...`
* Subfinder v2
* github-subdomains.py
* github-search (unstable -> run multiple times)
* shosubgo
* Cloud Ranges (scan all AWS, Azure, etc. check SSL certs for "target")
* Sublist3r [GitHub - aboul3la/Sublist3r: Fast subdomains enumeration tool for penetration testers](https://github.com/aboul3la/Sublist3r)

### Subdomain Bruting

* Massdns
* Amass
`amass enum -brute -d twitch.tv -src`
* aisdnsbrute
* shuffleDNS
* altdns
* Knockpy [GitHub - guelfoweb/knock at knock4](https://github.com/guelfoweb/knock/tree/knock4)
* HostileSubBrutforcer [GitHub - nahamsec/HostileSubBruteforcer](https://github.com/nahamsec/HostileSubBruteforcer)

#### Wordlists

* all.txt
* AssetNote -> commonspeak2

## Favicon Analysis

* favfreak

## Port Analysis

* Nmap
* masscan (faster than Nmap)
* dnmasscan
* Brutespray

## GitHub Dorking

* github-search 

## Screenshotting 

* Aquatone 
* Eyewitness
* httpscreenshot
* WitnessMe

## Subdomain takeover 

* can-i-take-over-xyz
* Nuclei
* SubOver

## Automation++

* interlace
* Tools by TomNomNom (eg httpprobe, mage)

## Frameworks

### S-Tier

* [AssetNote](https://assetnote.io)
* [SpiderFoot](https://www.spiderfoot.net)
* [Project Discovery Framework](https://projectdiscovery.io)
* [Jaeles (scanner)](https://github.com/jaeles-project/jaeles)
* [Osmedeus](https://github.com/j3ssie/Osmedeus)
* [HunterSuite.io](https://huntersuite.io)
* Bunty.offensiveai.com (paid)
* [reNgine](https://github.com/yogeshojha/rengine)
* Scout (paid)

### A-Tier

* [Findomain Monitoring Service](https://github.com/Edu4rdSHL/findomain)
* [Rock-ON (A One-Shoot Killer)](https://github.com/SilverPoision/Rock-ON)
* [Automated Reconnaissance Pipeline](https://github.com/epi052/recon-pipeline)

### B-Tier

* [LazyRecon](https://github.com/capt-meelo/LazyRecon)
* [Automated-Scanner](https://github.com/phspade/Automated-Scanner)
* [OneForAll](https://github.com/shmilylty/OneForAll)
* [Chomp Scan](https://github.com/SolomonSklash/chomp-scan)
* [domained [archived]](https://github.com/TypeError/domained)
* [Sudomy](https://github.com/Screetsec/Sudomy)
* [Gorecon - lightweight Reconnaissance Tool [NO LONGER MAINTAINED]](https://github.com/devanshbatham/Gorecon)
* [TugaRecon](https://github.com/LordNeoStark/tugarecon)
* [Photon](https://github.com/s0md3v/photon)

### C-Tier

* [bountyRecon](https://github.com/AdmiralGaust/bountyRecon)
* [recon](https://github.com/offhourscoding/recon)
* [Recon-tools](https://github.com/Sambal0x/Recon-tools)
* [AutoRecon](https://github.com/JoshuaMart/AutoRecon)
* [Hunter](https://github.com/yourbuddy25/Hunter)
* [ultimate_recon.sh](https://github.com/venom26/recon/blob/master/ultimate_recon.sh)
* [st8out.sh](https://gist.github.com/dwisiswant0/5f647e3d406b5e984e6d69d3538968cd)

# MISC (to be cleaned up)

* WebScarab
* Recon-ng
* GitRob
* [CyberChef](https://gchq.github.io/CyberChef/)
* OnlineHashCrack.com
* idb 
* Wireshark
* Bucket Finder
* Race the Web
* Google Dorks
* JD GUI
* Mobile Security Framework 
* Ysoserial
