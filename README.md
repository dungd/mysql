Nếu gặp lỗi Access denied.... khi tạo database bằng tay thì thao tác như dưới. Thanks
- .env của project
- DB_CONNECTION=mysql
- DB_HOST=laradock_mysql_1 
- DB_PORT=3306
- DB_DATABASE=sekisho  : db được bằng tay trong workbench hoặc heidi
- DB_USERNAME=root      : tài khoản của mysql, nếu đăng nhập heidi bằng tài khoản khác sẽ không được phép tạo schemas (denaid)
- DB_PASSWORD=root      : 

### mysql env/mysql/...

### Copy createdb.sql.example to createdb.sql
- then uncomment then set database name and username to create you need databases

### example: .env MYSQL_USER=appuser and needed db name is myshop_db

-    CREATE DATABASE IF NOT EXISTS `myshop_db` ;
-    GRANT ALL ON `myshop_db`.* TO 'appuser'@'%' ;


### this sql script will auto run when the mysql container starts and the $DATA_PATH_HOST/mysql not found.

### if your $DATA_PATH_HOST/mysql exists and you do not want to delete it, you can run by manual execution:

-     docker-compose exec mysql bash
-     mysql -u root -p < /docker-entrypoint-initdb.d/createdb.sql


### CREATE DATABASE IF NOT EXISTS `dev_db_1` COLLATE 'utf8_general_ci' ;
- GRANT ALL ON `dev_db_1`.* TO 'user'@'%' ;

### CREATE DATABASE IF NOT EXISTS `dev_db_2` COLLATE 'utf8_general_ci' ;
- GRANT ALL ON `dev_db_2`.* TO 'root'@'%' ;

### CREATE DATABASE IF NOT EXISTS `dev_db_3` COLLATE 'utf8_general_ci' ;
- GRANT ALL ON `dev_db_3`.* TO 'default'@'%' ;

- FLUSH PRIVILEGES ;

=> xong rồi thì down, up lại docker và refresh lại heidisql để trải nhiệm.
