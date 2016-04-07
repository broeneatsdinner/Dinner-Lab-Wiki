To find the user's current hostnames and encrypted password:
```
SELECT user, host, password FROM mysql.user WHERE user = 'username' ORDER BY host ASC;
```
Then, to grant all privileges to that user:
```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' 
IDENTIFIED BY PASSWORD 'encrypted_password' 
WITH GRANT OPTION;
```