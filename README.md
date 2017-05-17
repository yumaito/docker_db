# docker_db

さくっとMySQLとかPostgreSQLとかRedisとか試してみたいときに使う用
手元の環境を汚さずに使いたいとき用
fluentd入れたのは特に理由はない

Usage

[https://docs.docker.com/](https://docs.docker.com/) からDockerをダウンロード&インストール

```sh
$ git clone git@github.com:yumaito/docker_db.git
$ cd docker_db
$ docker-compose up
```

```sh
$ docker-compose ps
Name                     Command               State                        Ports
-------------------------------------------------------------------------------------------------------------
docker_fluentd_1    /bin/sh -c exec fluentd -c ...   Up      0.0.0.0:24224->24224/tcp, 0.0.0.0:5140->5140/tcp
docker_mysql_1      docker-entrypoint.sh mysqld      Up      0.0.0.0:3306->3306/tcp
docker_postgres_1   /docker-entrypoint.sh postgres   Up      0.0.0.0:5432->5432/tcp
docker_redis_1      docker-entrypoint.sh redis ...   Up      0.0.0.0:6379->6379/tcp docker-compose ps
```

それぞれhostとportを指定すれば繋げられます

* MySQL

```sh
$ mysql -uroot -h 0.0.0.0 -P 3306
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.6.36-log MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

* PostgreSQL

```sh
$ psql -h 0.0.0.0 -p 5432 -U postgres
psql (9.6.2, server 8.4.22)
Type "help" for help.

postgres=#
```

* Redis

```sh
$ redis-cli -h 0.0.0.0 -p 6379
0.0.0.0:6379>
```
