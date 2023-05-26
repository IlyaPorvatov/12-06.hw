# Домашнее задание к занятию «Репликация и масштабирование. Часть 1» - `Илья Порватов`

### Задание 1

На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

*Ответить в свободной форме.*

Основное различие в том, что при мастер-мастер можем писать и читать на оба мастера, а при мастер-слейв пишем на мастер читать можем с обеих, но обычно со слейв. 

Конфигурация мастер-мастер опасна при нарушении репликации - понять где верные данные будет сложно, восстановление  данных очень трудозатратно. 

------

### Задание 2

Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

<img src="/img/master_slave_status.png" alt="master_slave_status" style="zoom:75%;" />

<img src="/img/master_slave_test.png" alt="master_slave_test" style="zoom:75%;" />

**host mysql1** <u>mysqld.cnf</u> 

```ini
[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
log-error       = /var/log/mysql/error.log

bind-address=0.0.0.0
server-id=1
log_bin=/var/log/mysql/mybin.log
```

**host mysql1** <u>mysqld.cnf</u> 

```ini
[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
log-error       = /var/log/mysql/error.log

bind-address=0.0.0.0
server-id=2
log_bin=/var/log/mysql/mybin.log
```
