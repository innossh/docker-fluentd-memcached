# docker-fluentd-memcached

a sample docker containers for running Fluentd + Memcached (and Fluentd + MySQL innodb memcached plugin)

## Usage

```sh
$ docker-compose up -d
$ curl http://<DOCKER_HOST>:8888/memcached.test -d 'json={"key":"foo", "value":"bar"}'

# wait a little...

$ telnet <DOCKER_HOST> 11211
Trying <DOCKER_HOST>...
Connected to <DOCKER_HOST>
Escape character is '^]'.
get foo
VALUE foo 1 13
Ibar:ET
END
quit
Connection closed by foreign host.


$ curl http://<DOCKER_HOST>:8888/mysql.test -d 'json={"key":"hoge", "value":"fuga"}'

# wait a little...

$ telnet <DOCKER_HOST> 11222
Trying <DOCKER_HOST>...
Connected to <DOCKER_HOST>
Escape character is '^]'.
get hoge
VALUE hoge 1 14
I"      fuga:ET
END
quit
Connection closed by foreign host.

$ mysql -uroot -h192.168.99.100 -p
Enter password:
...
mysql> select * from test.demo_test;
+------+----------------+------+------+------+
| c1   | c2             | c3   | c4   | c5   |
+------+----------------+------+------+------+
| AA   | HELLO, HELLO   |    8 |    0 |    0 |
| hoge |I"      fuga:ET |    1 |    1 |    0 |
+------+----------------+------+------+------+
2 rows in set (0.00 sec)

mysql> exit
Bye
```
