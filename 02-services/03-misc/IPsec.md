# IPsec

> **Internet Protocol Security (IPsec)** is a secure network protocol suite that authenticates and encrypts the  packets of data to provide secure encrypted communication between two computers over an Internet Protocol network. It is used in virtual private networks (VPNs).  

## ike-scan

The IKE Scanner - Discover and fingerprint IKE hosts (IPsec VPN Servers)
[GitHub - royhills/ike-scan](https://github.com/royhills/ike-scan)

```bash
ike-scan -A -M <ip>
```
-> `-2` to check for ikev2

## Strongswan

IPsec VPN for Linux, Android, FreeBSD, Mac OS X, Windows
[strongSwan](https://www.strongswan.org)

```bash
apt install strongswan
```

### configure

/etc/ipsec.secrets

-> Add line `<target-ip> %any: PSK "<PSK>"`

/etc/ipsec.conf
```
conn Conceal
	type=transport
	keyexchange=ikev1
	left=<local-ip>
	leftprotoport=tcp
	right=<target-ip>
	rightprotoport=tcp
	authby=psk
	esp=3des-sha1
	ike=3des-sha1-modp1024
	ikelifetime=8h
	auto=start
```

Run
```bash
ipsec start --nofork
```

[VPN — IPsec — Troubleshooting IPsec VPNs | pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/vpn/ipsec/ipsec-troubleshooting.html)
* add `fragmentation=yes` to `/etc/ipsec.conf`
* reduce mtu zize `ifconfig tun0 mtu 1000`
