# Title: Klasör yapısı
<!-- Position: 2 -->
---
Bludit'in klasör yapısı.
```
/bl-content/	<-- Veritabanları ve yüklenen resimler
/bl-kernel/	<-- Bludit'in çekirdeği
/bl-languages/	<-- Dil dosyaları
/bl-plugins/	<-- Eklentiler
/bl-themes/	<-- Temalar
```

## bl-content
Bu klasör çok önemlidir, Bludit tüm dosyalarının yanı sıra veritabanlarını ve görüntüleri burada saklar. Bir güncelleme yapmadan önce, bu klasörün bir yedeğini almanız önerilir.

```
/bl-content/

	databases/
		plugins/		<-- Veritabanı: eklentiler
		pages.php		<-- Veritabanı: sayfalar
		security.php	        <-- Veritabanı: kara liste, kaba kuvvet koruması, diğerleri
		site.php		<-- Veritabanı: site değişkenleri, isim, açıklama, slogan, diğerleri
		tags.php		<-- Veritabanı: etiketler
		users.php		<-- Veritabanı: kullanıcılar

	pages/				<-- İçerik: sayfalar
		about/index.txt
		food/index.txt

	tmp/				<-- Geçici dosyalar
	uploads/			<-- Yüklenen dosyalar
		profiles/		<-- Profil resimleri
		thumbnails/		<-- Küçük resimler
		photo1.jpg
		photo2.png
```

## bl-kernel
Bu klasör Bludit'in çekirdeğini içerir.

## bl-languages
Bu klasör tüm dil dosyalarını içerir, her dosya UTF-8 olarak kodlanmış bir JSON belgesidir.

```
/bl-languages/
	bg_BG.json
	cs_CZ.json
	de_CH.json
	tr_TR.json
	en.json
	es.json
	...
```

## bl-plugins
Bu klasör tüm eklentileri içerir, yeni eklentileri indirebilir ve buraya yükleyebilirsiniz.

```
/bl-plugins/
	about/
	disqus/
	rss/
	sitemap/
	simplemde/
	...
```

## bl-themes
Bu klasör tüm temaları içerir, yeni temalar indirebilir ve buraya yükleyebilirsiniz.

```
/bl-themes/
	clean-blog/
	kernel-panic/
	...
```
