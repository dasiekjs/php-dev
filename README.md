Simple PHP 7.4 container

NOT INCLUDED WEBSERVER (use f.ex nginx from example folder)
Use this image as php service - link it into your container and use port 9000

installed things:
- iconv 
- gettext 
- intl 
- xml 
- soap 
- opcache 
- pdo 
- pdo_mysql 
- mysqli 
- pdo_pgsql 
- curl 
- zip 
- gd
- pgsql
- mcrypt
- xdebug
- mongodb
- composer


build

```
docker build . -t name
```

example usage with nginx in `example folder`
