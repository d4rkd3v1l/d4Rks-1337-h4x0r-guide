# Drupal

> Drupal is a free and open-source web content management system written in PHP and distributed under the GNU General Public License. Drupal provides a back-end framework for at least 13% of the top 10,000 websites worldwide – ranging from personal blogs to corporate, political, and government sites. Wikipedia
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Drupal)</cite>

## droopescan

A plugin-based scanner that aids security researchers in identifying issues with several CMSs, mainly Drupal & Silverstripe.  
[GitHub - droope/droopescan](https://github.com/droope/droopescan)

```bash
droopescan scan drupal -u <ip>
```

Search for creds
```bash
./sites/default/settings | grep -i pass
```

## Interesting files

[Web Security Geeks - The Security Blog: Pentesting CMS : Wordpress Joomla Drupal](https://www.websecgeeks.com/2015/11/pentesting-cms-wordpress-joomla-drupal.html)
```
Default files: “CHANGELOG.txt”, “UPGRADE.txt”, “README.txt”
Configuration file location: [examplesitefortesting.com]/sites/default/settings.php
Plugin location: [examplesitefortesting.com]/?q=[pluginname]
```

## Authenticated

Activate php filter plugin to allow php code execution in posts
