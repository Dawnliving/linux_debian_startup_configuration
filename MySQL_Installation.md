# Debian MySQL Installation

## Configure APT repository

```shell
wget https://repo.mysql.com//mysql-apt-config_0.8.33-1_all.deb
```

```shell
sudo dpkg -i mysql-apt-config_0.8.33-1_all.deb
```

```shell
sudo apt update
```

## Install MySQL

```shell
sudo apt-get install mysql-server
```

## Configure MySQL

```shell
mysql -uroot -p
```

enter root password

```sql
use mysql;
```

```sql
select User,host from user;
```

allow remote access

```sql
update user set host='%' where User = 'root';
```

refresh privilege, without restart mysql service

```sql
flush privileges;
```

create new user(based on demand, in this case to keep user same as system user debian) 

please change 'password' as you want

```sql
create user 'debian'@'%' identified by "password";
```

grant privileges to new user, in this case, grant all privileges, you can grant different privileges to different users based on your needs.

```sql
grant all privileges on *.* to 'debian'@'%';
```

refresh privilege, without restart mysql service

```sql
flush privileges;
```

