# apache-tomcat-docker-sample

- docker sample 
- apache(mod_jk) => tomcat => servlet

## dependencies

- virtualbox
- docker
- docker-machine
- docker-compose >= 1.6.0

must use docker-compose >= 1.6.0. because we use version 2 of the Compose file format.

see: https://blog.docker.com/2016/02/compose-1-6/

## how to use

```
$ docker-machine create --driver virtualbox apache-tomcat-docker-sample
```

```
$ eval "$(docker-machine env apache-tomcat-docker-sample)"
$ docker-compose up
```

```
$ mvn clean package
```

then, access browser

- http://{ip}/

ip is

```
$ docker-machine ip apache-tomcat-docker-sample
```

## tips

```
$ docker exec -it httpd-container /bin/bash
$ docker exec -it tomcat-container /bin/bash
```
