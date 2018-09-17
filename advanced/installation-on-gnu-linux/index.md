# Title: GNU/Linux üzerine Kurulum
<!-- Position: 5 -->
---
Tüm örnekler, Nginx Web Sunucusu ile kutu yüklemesinin dışında. Diğer dağıtımlar için adımlarınız varsa, bunu [forum](https://forum.bludit.org) üzerinde yayınlayabilir ya da sadece bu sayfayı Github'da düzenleyin, sayfanın sonunda bağlantı ile bir düğme bulabilirsiniz.

### İçerik
1. [Ubuntu 16.04 üzerinde kurulum](#ubuntu)
2. [Centos 7 / RedHat 7 üzerinde kurulum](#centos)

---

## <a id="ubuntu"></a> Ubuntu 16.04 LTS üzerinde kurulum

Hususlar:
- PHP-FPM, `www-data` kullanıcı adı altında çalışıyor.
- PHP-FPM, `unix:/run/php/php7.0-fpm.sock` üzerinde Unix soketinde dinliyor.
- Nginx, `www-data` kullanıcı adı altında çalışıyor.
- Başka bir web sunucusu yüklemediniz.
- Bu, üretim ortamları için daha fazla okuyan temel bir yapılandırmadır.

Nginx Web sunucusu, PHP ve bazı araçları yükleyin.
```
$ sudo apt install -y nginx php-fpm php-dom php-mbstring php-cli php-gd php-opcache unzip wget
```

Nginx yapılandırın.
```
$ sudo rm -f /etc/nginx/sites-enabled/*
```

Sanal sunucu bloğu ile yeni bir dosya ekle `/etc/nginx/conf.d/bludit.conf`
```
server {
	listen 80;
	server_name _;
	root /www/bludit;
	index index.php;

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php7.0-fpm.sock;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}
}
```

Bludit'in son sürümünü indirin ve genişletin.
```
$ mkdir /www
$ cd /www
$ wget https://s3.amazonaws.com/bludit-s3/bludit-builds/bludit_latest.zip
$ unzip bludit_latest.zip
$ sudo chown -R www-data:www-data /www
```

Yeni yapılandırmaları yüklemek için hizmetleri yeniden başlatın.
```
$ sudo service php7.0-fpm restart
$ sudo service nginx restart
```

Tarayıcınızı açın ve http://localhost adresine gidin, yükleme işlemini tamamlayın.

---

## <a id="centos"></a> Centos 7 / Red Hat 7 üzerinde kurulum

Hususlar:
- PHP-FPM, `nginx` kullanıcı adı altında çalışıyor.
- PHP-FPM, `unix:/run/php/php-fpm.sock` üzerinde Unix soketinde dinliyor.
- Nginx, `nginx` kullanıcı adı altında çalışıyor.
- Başka bir web sunucusu yüklemediniz.
- Bu, üretim ortamları için daha fazla okuyan temel bir yapılandırmadır.

```
$ sudo yum install -y epel-release
```

Nginx Web sunucusu, PHP ve bazı araçları yükleyin.
```
$ yum install -y nginx php-fpm php-cli php-dom php-mbstring php-zip php-gd
```

Nginx'i yapılandırın, sanal sunucu bloğuyla yeni bir dosya ekleyin `/etc/nginx/conf.d/bludit.conf`
```
server {
	listen 80;
	server_name _;
	root /www/bludit;
	index index.php;

	location ~ \.php$ {
		fastcgi_pass    unix:/run/php/php7.0-fpm.sock;
		include         fastcgi.conf;
	}

	location / {
		try_files $uri $uri/ /index.php?$args;
	}
}
```

Bludit'in son sürümünü indirin ve genişletin.
```
$ mkdir /www
$ cd /www
$ wget https://s3.amazonaws.com/bludit-s3/bludit-builds/bludit_latest.zip
$ unzip bludit_latest.zip
$ sudo chown -R nginx:nginx /www
```

Yeni yapılandırmaları yüklemek için hizmetleri yeniden başlatın.
```
$ sudo systemctl php-fpm restart
$ sudo systemctl nginx restart
```

Tarayıcınızı açın ve http://localhost adresine gidin, yükleme işlemini tamamlayın.
