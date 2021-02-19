### Code
- `https://github.com/heig-vd-tin/heig-quiz`

### Installation
- If is not possible to execute `initphp.sh`. You need to change permission
(`chmod`) for the file in the folder `./php/config`. Config files are share with docker volume.

### Php
- `docker exec -it php bash`
- set git name `git config --global user.name "<Your-Full-Name>"`
- set git email `git config --global user.email "<your-email-address>"`
- `cd /srv/www`
- clone code 
  - `git init`
  - `git remote add origin https://github.com/yves-chevallier/chevallier.io.git`
  - `git pull`

- `composer intall`
- `npm install`
- `npm run dev`

#### Migration
- `php artisan migrate:fresh --seed`

#### Permission
- Dev solution : Change permission for folder `www/storage/` `chmod -R a+w storage/`

### MYSQL

- Copy config into `mysql` container : `docker cp ./mysql/my.cnf mysql:/etc/mysql/conf.d/`

- In a bash `docker exec -it mysql bash`
- In the mysql container
  - `mysql -u root -p` (no password) or secret
  - Show user `select Host,User from mysql.user;`
  - `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'secret';`
  - `CREATE USER 'laravel'@'%' IDENTIFIED WITH mysql_native_password BY 'secret';`
  - `GRANT ALL PRIVILEGES ON *.* TO 'laravel'@'%';`
  - `FLUSH PRIVILEGES;`
  - `SHOW VARIABLES like 'lowe%';`
    ```bash
    +------------------------+-------+
    | Variable_name          | Value |
    +------------------------+-------+
    | lower_case_table_names | 1     |
    +------------------------+-------+
    ```
  
### Web
- In a bash `docker exec -it web bash`
- Into the container
  - `cd  /etc/apache2/sites-available`
  - `a2ensite quiz.conf`
  - `service apache2 reload`


  ### Access
  - `127.0.0.1:8080`

  ### Command
  - VM : `http://10.193.81.49/`
  - Autologin : `http://<server>:8080/debug/login/1`