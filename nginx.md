# nginx

### command
```shell
nginx version: nginx/1.10.3 (Ubuntu)
Usage: nginx [-?hvVtTq] [-s signal] [-c filename] [-p prefix] [-g directives]

Options:
  -?,-h         : this help
  -v            : show version and exit
  -V            : show version and configure options then exit
  -t            : test configuration and exit
  -T            : test configuration, dump it and exit
  -q            : suppress non-error messages during configuration testing
  -s signal     : send signal to a master process: stop, quit, reopen, reload
  -p prefix     : set prefix path (default: /usr/share/nginx/)
  -c filename   : set configuration file (default: /etc/nginx/nginx.conf)
  -g directives : set global directives out of configuration file
```

### reload config

`$ nginx -s reload`

[nginx的启动、停止、重载配置、验证配置](https://www.cnblogs.com/sea-stream/p/10201195.html)

### IP

```conf
location / {
    allow 123.34.12.123;
    allow 11.22.33.1/100;
    deny  all;
}
```

[Nginx配置IP白名单和黑名单](https://www.cnblogs.com/xiaozong/p/5683638.html)


### Forbidden access files with specified extension

```conf
location ~* \.(ini|docx|txt|doc)$ { 
     deny all;
} 
location ~* \.html$ {
     deny all;
}
```

### Nginx 502 with Codeigniter

Finally found is pho-fpm version error.

```conf
location ~ \.php$ {
     # ...
     fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
     # ...
}
```

### Enable conf

`$ ln -s /etc/nginx/sites-available/example.com.conf /etc/nginx/sites-enabled/example.com.conf`

### Nginx configure https

[Nginx 服务器证书安装](https://cloud.tencent.com/document/product/400/35244)


### 413 Request Entity Too Large

`/etc/nginx/nginx.conf`:
```conf
client_max_body_size 20m;
```

`php.ini`:
```ini
upload_max_filesize = 20M
post_max_size = 20M
```

- [nginx 出现413 Request Entity Too Large问题的解决方法](https://blog.csdn.net/fdipzone/article/details/45544497)

### Refs

- [Nginx实现URL重写](https://www.cnblogs.com/dalaoyang/p/10264919.html)
- [Ubuntu 18.04系统用Nginx替换Apache的方法](https://www.laozuo.org/14171.html)
- [How to Install Nginx, PHP 7.3 (LEMP stack) on Ubuntu 18.04 | Google Cloud](https://www.cloudbooklet.com/how-to-install-nginx-php-7-3-lemp-stack-on-ubuntu-18-04-google-cloud/)
- [Nginx - Codeigniter](https://www.nginx.com/resources/wiki/start/topics/recipes/codeigniter/)
- [How to Install Nginx with PHP-FPM on Ubuntu 18.04 LTS](https://tecadmin.net/install-nginx-php-fpm-ubuntu-18-04/)