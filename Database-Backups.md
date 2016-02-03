```
mysql> show master status;
+------------------+----------+------------------------------------------------------------------------------+------------------+
| File             | Position | Binlog_Do_DB                                                                 | Binlog_Ignore_DB |
+------------------+----------+------------------------------------------------------------------------------+------------------+
| mysql-bin.000300 |    96787 | blogdi5_wo509,dinnerlab_development,dinnerlab_production,dinnerlab_warehouse |                  |
+------------------+----------+------------------------------------------------------------------------------+------------------+
1 row in set (0.00 sec)

USE blogdi5_wo509; FLUSH TABLES WITH READ LOCK; USE dinnerlab_development; FLUSH TABLES WITH READ LOCK; USE dinnerlab_production; FLUSH TABLES WITH READ LOCK; USE dinnerlab_warehouse; FLUSH TABLES WITH READ LOCK; 

mysqldump -u root -p blogdi5_wo509 > blogdi5_wo509.sql
mysqldump -u root -p dinnerlab_development > dinnerlab_development.sql
mysqldump -u root -p dinnerlab_production > dinnerlab_production.sql
mysqldump -u root -p dinnerlab_warehouse > dinnerlab_warehouse.sql

USE blogdi5_wo509; UNLOCK TABLES; USE dinnerlab_development; UNLOCK TABLES; USE dinnerlab_production; UNLOCK TABLES; USE dinnerlab_warehouse; UNLOCK TABLES; 

scp blogdi5_wo509.sql root@104.237.134.115:/root
scp dinnerlab_development.sql root@104.237.134.115:/root
scp dinnerlab_production.sql root@104.237.134.115:/root
scp dinnerlab_warehouse.sql root@104.237.134.115:/root

CHANGE MASTER TO MASTER_HOST='104.200.21.220',MASTER_USER='user',MASTER_PASSWORD='password',MASTER_LOG_FILE='mysql-bin.000300', MASTER_LOG_POS=96787;

```