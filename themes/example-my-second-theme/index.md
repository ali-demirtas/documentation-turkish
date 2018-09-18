# Title: Örnek: Benim ikinci temam
<!-- Position: 3 -->
---
İkinci örnek, CSS, Javascript ekleyerek ve eklentiler için destek dahil ederek Bludit için bir temayı nasıl oluşturabileceğinizi gösterir.

Bir sonraki tema `Mars` olarak adlandırılır.

Eğer öğretici ile ilgilenmiyorsanız, kaynak kodunu indirebilirsiniz <a href="https://github.com/bludit/examples/tree/master/themes/mars">Mars Teması</a>.

<h2 id="folder-structure">1. Klasör yapısı</h2>

`/bl-themes/` klasörünün içinde temanın klasörünü oluşturun, `/bl-themes/mars/`

Ardından, dilleri, css ve js klasörlerini oluşturun:
- `/bl-themes/mars/`klasörünün içinde `languages` klasörü oluşturun.
- `/bl-themes/mars/`klasörünün içinde `css` klasörü oluşturun.
- `/bl-themes/mars/`klasörünün içinde `js` klasörü oluşturun.

```
/bl-themes/mars/
	css/
	js/
	language/
```

<h2 id="name-and-information">2. İsim ve bilgi</h2>

Tema bilgisi içeren bir dosya oluşturun. Bir sonraki dosya, JSON koduyla kök tema klasöründe `metadata.json` dosyası olacak:

```
{
	"author": "Bludit",
	"email": "",
	"website": "",
	"version": "1.0",
	"releaseDate": "2018-02-14",
	"license": "MIT",
	"compatible": "2.0, 2.1, 2.2, 2.3",
	"notes": ""
}
```

Temanın adı ve açıklaması ile başka bir dosya oluşturun. Sonra, JSON koduyla `/bl-themes/mars/ anguages/` klasöründe `en.json` adlı bir dosya oluşturun:

```
{
	"theme-data":
	{
		"name": "Mars",
		"description": "Bu Bludit için ikinci temam."
	}
}
```
<h2 id="index">3. Index.php</h2>

`index.php` adlı dosya üzerinde çalışalım. Sonra, HTML koduyla `/bl-themes/mars/` dizinindeki dosyayı oluşturun:

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
</head>
<body>

</body>
</html>
```

<h2 id="css-files">4. CSS dosyaları</h2>

Bazı CSS dosyaları ekle:
- Helper nesnesini kullanma `Theme::css()`
- HTML etiketini kullanma `<link href=".." rel="stylesheet" type="text/css" />`

Bu durumda CSS dosyasını `/bl-themes/mars/css/style.css` eklemek için Helper'ı kullanacağız. Helper ile mutlak yolu belirtmenize gerek yoktur.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>
</head>
<body>

</body>
</html>
```

<h2 id="javascript-files">5. Javascript dosyaları</h2>

Bazı Javascript dosyaları ekle:
- Helper nesnesini kullanma `Theme::javascript()`
- HTML etiketini kullanma `<script>...</script>`

Bu durumda Javascript dosyasını `/bl-themes/mars/js/jquery.min.js` eklemek için Helper'ı kullanacağız. Helper ile mutlak yolu belirtmenize gerek yoktur.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>
</head>
<body>

</body>
</html>
```

<h2 id="plugin-support">6. Eklenti desteği ekleme</h2>

Eklentiler için destek ekleyin, helper'ı kullanabilirsiniz: `Theme::plugins()`

Site için eklenti kancaları:
- `siteHead`, `<head>...</head>` için kod döndüren tüm eklentileri içerir.
- `siteBodyBegin`, başlangıçta `<body>...</body>` için kod döndüren tüm eklentileri içerir, hoş geldiniz başlığı veya üst kısım için bazı araç çubuğu olabilir.
- `siteBodyEnd`,  javascript kodu gibi alt kısımda `<body>...</body>` için kod döndüren tüm eklentileri içerir.
```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Kancalı eklentileri yükle siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<!-- İşte bütün HTML kodları -->

	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="site-title-and-slogan">7. Site başlığı ve sloganı</h2>

Başlık ve sloganı almak için Site-Object kullanabilirsiniz.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Kancalı eklentileri yükle siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="where-am-i">8. Neredeyim</h2>

Şimdi sitenin içeriği ile çalışalım.

Kullanıcının sitede hangi sayfada gezindiğini bulmak için `$WHERE_AM_I` değişkenini kullanın. Örneğin, kullanıcı bir sayfa izliyorsa, değişkenin değeri `page`, dizgesine sahiptir ve kullanıcı ana sayfayı (ana sayfa) izliyorsa değişkenin değeri `home` olacaktır.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Kancalı eklentileri yükle siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
	<p>Kullanıcı belirli bir sayfayı izliyor</p>

	<?php elseif ($WHERE_AM_I=='home'): ?>
	<p>Kullanıcı ana sayfayı izliyor</p>

	<?php endif ?>

	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="main-content">9. Ana içerik</h2>

Kullanıcı ana sayfada ise, Bludit yayınlanmış tüm sayfalarda global bir dizi `$pages` üretir, her sayfa bir `Page Object` nesnesidir.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Kancalı eklentileri yükle siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
	<p>Kullanıcı belirli bir sayfayı izliyor</p>

	<?php elseif ($WHERE_AM_I=='home'): ?>
		<?php foreach ($pages as $page): ?>
		<h3><?php echo $page->title(); ?></h3>
		<?php endforeach ?>

	<?php endif ?>

	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

Kullanıcı belirli bir sayfayı izliyorsa, Bludit genel bir Page-Object `$page`, sayfası oluşturur, bu örnekte başlığı ve içeriği yazdıracağız.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Kancalı eklentileri yükle siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
		<h3><?php echo $page->title(); ?></h3>

	<?php elseif ($WHERE_AM_I=='home'): ?>
		<?php foreach ($pages as $page): ?>
		<h3><?php echo $page->title(); ?></h3>
		<?php endforeach ?>

	<?php endif ?>

	<!-- Kancalı eklentileri yükle siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<div class="note">
<div class="title">İndir</div>
Temanın kaynak kodunu indirin: <a href="https://github.com/bludit/examples/tree/master/themes/mars">Mars</a>.
</div>
