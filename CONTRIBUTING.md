### Php
- `docker exec -it php bash`
- set git name `git config --global user.name "<Your-Full-Name>"`
- set git email `git config --global user.email "<your-email-address>"`
- `cd /srv/www`
- clone code `git clone https://github.com/yves-chevallier/chevallier.io.git .`

### MYSQL
- In a bash `docker exec -it mysql bash`
- In the mysql container
  - `mysql -u root -p` (no password)
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
  
  ### Access
  - `127.0.0.1:8080`