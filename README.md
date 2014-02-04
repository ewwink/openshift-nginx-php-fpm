# OpenShift Nginx 1.5.9 (with headers More Module) PHP-FPM 5.4 Cartridge
This cartridge serves static content using nginx web server, passing requests to .php files down to php-fpm.

Place your static files inside www/static dir, commit and push.
Place your php files inside php/ dir, commit and push.
###Content

 - **Nginx 1.5.9**
 - **Headers More Nginx module 0.25** (ngx_headers_more) - Set and clear input and output headers... more than "add"!
 - **PHP-FPM 5.4**
 - **PCRE 8.34**

### Usage

```bash
$ rhc app create phpfpm https://reflector-getupcloud.getup.io/reflect?github=ewwink/openshift-nginx-php-fpm
$ cd phpfpm
$ echo '<?php phpinfo(); ?>' > php/info.php
$ echo 'Hello World' >> www/static/hello.html
$ git add .
$ git commit -m 'Testing'
$ git push
```

### User-defined configuration

Place your nginx .conf files inside config/nginx.d/. It will be include()ed from "http" scope.
Place your php-fpm .conf files inside config/php-fpm.d/. It will be include()ed from main php-fpm.conf file.

###Nginx Build Info
this nginx built with the following command
```
./configure --prefix=/tmp/nginx-rhel --user=nginx --group=nginx \
--with-http_realip_module --with-http_ssl_module \
--with-http_gzip_static_module --with-http_stub_status_module \
--add-module=contrib/headers-more-nginx-module-0.25 --with-pcre=contrib/pcre-8.34
```

while original repo
```
./configure --prefix=/usr/share/nginx --sbin-path=/usr/sbin/nginx \
--conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log \
	--http-log-path=/var/log/nginx/access.log \
	--http-client-body-temp-path=/var/lib/nginx/tmp/client_body \
	--http-proxy-temp-path=/var/lib/nginx/tmp/proxy \
	--http-fastcgi-temp-path=/var/lib/nginx/tmp/fastcgi \
	--http-uwsgi-temp-path=/var/lib/nginx/tmp/uwsgi \
	--http-scgi-temp-path=/var/lib/nginx/tmp/scgi \
	--pid-path=/var/run/nginx.pid --lock-path=/var/lock/subsys/nginx \
	--user=nginx --group=nginx --with-file-aio --without-ipv6 \
	--with-http_ssl_module --with-http_realip_module \
	--with-http_addition_module --with-http_xslt_module \
	--with-http_image_filter_module --with-http_geoip_module
	--with-http_sub_module --with-http_dav_module --with-http_flv_module \
	--with-http_mp4_module --with-http_gzip_static_module \
	--with-http_random_index_module	--with-http_secure_link_module \
	--with-http_degradation_module --with-http_stub_status_module \
	--with-http_perl_module --with-mail --with-mail_ssl_module \
	--with-debug --with-cc-opt='-O2 -g -pipe \
	-Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector \
	--param=ssp-buffer-size=4 -m64 -mtune=generic' \
	--with-ld-opt=-Wl,-E
```
####Credit
this repo forked from https://github.com/getupcloud/openshift-nginx-php-fpm

----------
####About me
This is part of prpagerank.com [Check Pagerank](http://www.prpagerank.com) project