# Title: Nginx
<!-- Position: 1 -->
---
Bludit, [Nginx](https://nginx.org/en/) destekler ve bir Web sunucusu için önerilen bir seçenektir.

Bludit, tüm istekleri ve yanıtları ele alan kendi `router` sahiptir. Fikir, tüm istekleri `index.php` dosyasına yönlendirmektir.

Hususlar:
- Web sunucusu, PHP-FPM'yi CGI Process Manager olarak kullanıyor.
- PHP-FPM `unix:/run/php/php-fpm.sock` üzerinde Unix soketinde dinliyor.

## HTTP kurulumu
Bludit için yeni bir sunucu bloğu kurmak için, `/etc/nginx/conf.d/bludit.conf` içinde yapılandırmayla yeni bir dosya oluşturun. Bu dizin GNU / Linux'un diğer dağıtımlarında farklı olabilir. Ubuntu'da `/etc/nginx/sites-enabled/bludit.conf` olabilir. Güvenlik nedeniyle, `/bl-content/databases`, `/bl-content/pages` ve `/bl-content/temp` klasörlerine erişimi yasaklamayı unutmayın. Aksi takdirde, kullanıcıların bu yerlerin içindeki bazı dosyalara doğrudan erişimi vardır.

```
server {
	listen 80;
	server_name example.com;
	root /www/bludit;
	index index.php;

	access_log /var/log/nginx/example.log;
	error_log /var/log/nginx/example.log;

	location ~ \.(jpg|jpeg|gif|png|css|js|ico|svg|eot|ttf|woff|woff2|otf)$ {
		access_log        off;
		expires           30d;
	}

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php-fpm.sock;
		fastcgi_index   index.php;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}

	location ^~ /bl-content/tmp/ { deny all; } 
	location ^~ /bl-content/pages/ { deny all; } 
	location ^~ /bl-content/databases/ { deny all; } 
}
```

## HTTPS kurulumu
HTTPS yapılandırmasının bazı ekstra yapılandırmaları ve elbette SSL sertifikası vardır. Ücretsiz bir sertifika almak için [LetsEncrypt] (https://letsencrypt.org) kullanmanızı öneririz.

Sunucu bloğu bu konfigürasyona sahiptir ve isteği HTTP'den HTTPS'ye yönlendirmek için fazladan bir blok ekliyoruz.

```
server {
	listen 443 ssl;
	server_name example.com;
	root /www/bludit;
	index index.php;

	access_log /var/log/nginx/example.log;
	error_log /var/log/nginx/example.log;

	ssl_certificate         /etc/letsencrypt/live/example.com/fullchain.pem;
	ssl_certificate_key     /etc/letsencrypt/live/example.com/privkey.pem;
	ssl_dhparam             /etc/ssl/certs/dhparam.pem;

	ssl_session_cache       shared:SSL:50m;
	ssl_session_timeout     10m;

	ssl_prefer_server_ciphers	on;
	ssl_stapling			on;
	ssl_stapling_verify		on;
	ssl_protocols			TLSv1.1 TLSv1.2;
	ssl_ciphers			"ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";

	add_header Strict-Transport-Security "max-age=31557600; includeSubDomains";

	location ~ \.(jpg|jpeg|gif|png|css|js|ico|svg|eot|ttf|woff|woff2|otf)$ {
		access_log        off;
		expires           30d;
	}

	location ~ \.php$ {
		fastcgi_pass    unix:/var/run/php-fpm/php-fpm.sock;
		fastcgi_index   index.php;
		include         fastcgi.conf;
		fastcgi_param   HTTPS on;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}

	location ^~ /bl-content/tmp/ { deny all; } 
	location ^~ /bl-content/pages/ { deny all; } 
	location ^~ /bl-content/databases/ { deny all; } 
}

# Redirect from HTTP to HTTPS
server {
	listen 80;
	server_name example.com;
	return 301 https://example.com$request_uri;
}
```

