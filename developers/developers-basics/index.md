# Title: Geliştiricilerin temelleri
<!-- Position: 1 -->
---
Mevcut değişkenlerinizden ortam değişkenlerini kontrol etmeye başlayalım. Yönetici panelinize geliştiricinizin `https://example.com/admin/developers` alanına gidin, bu bölüm menüden gizlenmiştir.

PHP konfigürasyonunuz, `$_SERVER` gibi çevre değişkenleri, yüklenen eklentiler, kurulu olan yerel ayarlar, Bludit sabitleri ve bazı Nesneler özellikleri gibi bazı bilgileri görebilirsiniz.

## Yönetici paneli için dosya yükleme akışı
Bunlar, bazı kullanıcılar yönetici paneline gittiğinde yüklenen dosyalardır.

```
index.php
	bl-kernel/boot/init.php
	bl-kernel/boot/admin.php
		bl-kernel/boot/rules/60.plugins.php
		bl-kernel/boot/rules/69.pages.php
		bl-kernel/boot/rules/99.header.php
		bl-kernel/boot/rules/99.paginator.php
		bl-kernel/boot/rules/99.themes.php
		bl-kernel/boot/rules/99.security.php
		bl-kernel/admin/themes/default/init.php
		bl-kernel/admin/controllers/{CONTROLLER}.php
		bl-kernel/admin/themes/default/index.php
			bl-kernel/admin/controllers/{VIEW}.php
```

## Site için dosya yükleme akışı
Bunlar, bazı kullanıcılar siteye gittiğinde yüklenen dosyalardır.

```
index.php
	bl-kernel/boot/init.php
	bl-kernel/boot/site.php
		bl-kernel/boot/rules/60.plugins.php
		bl-kernel/boot/rules/69.pages.php
		bl-kernel/boot/rules/99.header.php
		bl-kernel/boot/rules/99.paginator.php
		bl-kernel/boot/rules/99.themes.php
		bl-kernel/boot/rules/99.security.php
		bl-themes/{THEME_NAME}/init.php
		bl-themes/{THEME_NAME}/index.php
```

## Ortam değişkenleri ve sabitler
Bludit, önceden tanımlanmış bazı yapılandırmalarla farklı ortam değişkenleri ve sabitler sağlar.

- [bl-kernel/boot/init.php](https://github.com/bludit/bludit/blob/master/bl-kernel/boot/init.php)
- [bl-kernel/boot/variables.php](https://github.com/bludit/bludit/blob/master/bl-kernel/boot/variables.php)

Tanımlanan ortam değişkenlerini görebileceğiniz başka bir yer ise `bl-kernel/boot/rules/` kurallarına dayanır, örneğin, `content` ve `pages` ilgili değişkenler [bl-kernel/boot/rules/69.pages.php] ile tanımlanır.(https://github.com/bludit/bludit/blob/master/bl-kernel/boot/rules/69.pages.php)
