# OpenShift Nginx 1.5.9 (with headers More Module) PHP-FPM 5.4 Cartridge
This cartridge serves static content using nginx web server, passing requests to .php files down to php-fpm.

Place your static files inside www/static dir, commit and push.
Place your php files inside php/ dir, commit and push.
###Content

 - **Nginx 1.5.9**
 - **Headers More Nginx module 0.25** (ngx_headers_more) - Set and clear input and output headers... more than "add"!
 - **PHP-FPM 5.4**

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

####Credit
this repo forked from https://github.com/getupcloud/openshift-nginx-php-fpm

####About me
This is part of prpagerank.com [Check Pagerank](http://www.prpagerank.com) project