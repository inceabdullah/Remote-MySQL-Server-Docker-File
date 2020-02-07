## Blender MySQL API

**2d image to 3d stl** project has many **Docker Image** that this is one of them. this web application can convert basic image file to 3d stl file that is extluded from your basic 2d picture.

### Setting

This settings are for **Dockerfile** after initilizing. 

**to-do** table is appended by rows by **Quart/Flask** after image file uploading.
**removed** table has info from `to-do` table. This rowmovement is done by **Python API** after completing by **Blender API**. 
**downloaded** table is from `removed` also. After downloading file by link that is sent to client e-mail.

### Remote Connection

After `$ mysql -uroot -p` in `mysql>`



```
create user 'root'@'%' identified by 'password';
grant all privileges on *.* to 'root'@'%' with grant option;
flush privileges;
```


of course.. you should change password with, first:
`mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';`

Listing of users and hosts:
`SELECT host, user FROM mysql.user;`

in default:

```
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| localhost | healthchecker    |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
5 rows in set (0.01 sec)

```

after adding the user `'root'@'%'`:

```
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| %         | root             |
| localhost | healthchecker    |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
6 rows in set (0.00 sec)
```



## Tables and Columns:
|  to-do | removed  | downloaded  |
| ------------ | ------------ | ------------ |
|  ID |  ID | ID  |
|  UNIQUE_ID | UNIQUE_ID  | UNIQUE_ID  |
|  DATE | DATE  | DATE  |
| | DATE_FROM_to-do | DATE_FROM_removed |
| | | DATE_FROM_ro-do |

#### Run

**Build**

`docker build -t mysql1`

`docker run --rm -p3306:3306 -v/root/git/docker/mysql/data:/var/lib/mysql mysql1`
