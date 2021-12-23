# Crypto

## Decrypt file

### Find cipher used for encryption

```bash
ciphers.lst
```

```
-aes-256-cbc
-aes-128-cbc
-aes-256-ecb
-aes-128-ecb
-aes-256-ofb
-aes-128-ofb
-rc4
-rc4-cbc
-aria-128-cbc
-des
```

Generate files of various lengths (in steps of 8)
```bash
for i in $(seq 0 8 176); do python -c "print 'A'*$i" > $i; done
```

Generate encrypted files with various ciphers if various length
```bash
for cipher in $(cat ciphers.lst); do
	for length in $(ls | grep ^[0-9]); do
		openssl enc $cipher -e -in $length -out $length$cipher.enc -k Whatever
	done
done
```

Check which of those match the length of the encrypted file
```bash
ls *.enc | xargs wc -c | grep '176 '
```

Crack it^^
```bash
bruteforce-salted-openssl -t 10 -f <wordlist> -c aes-256-cbc -d sha256 <encrypted-file>
```

Decrypt the file
```bash
openssl enc -aes-256-cbc -d -in <encrypted-file> -out <decrypted-file> -k <password>
```
