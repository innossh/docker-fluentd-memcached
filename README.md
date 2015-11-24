# docker-fluentd-memcached

a sample docker containers for running Fluentd + Memcached

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
```
