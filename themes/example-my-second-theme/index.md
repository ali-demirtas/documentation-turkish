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

<h2 id="where-am-i">8. Where Am I</h2>
Now let's work with the content of the site.

To locate what page the user is browsing on the site use the variable `$WHERE_AM_I`. For example, if the user is watching a page the value of the variable has the string `page`, and if the user is watching the main page (home page) the value of the variable is going to be `home`.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Load plugins with the hook siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Load plugins with the hook siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
	<p>The user is watching a particular page</p>

	<?php elseif ($WHERE_AM_I=='home'): ?>
	<p>The user is watching the homepage</p>

	<?php endif ?>

	<!-- Load plugins with the hook siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<h2 id="main-content">9. Main Content</h2>
If the user is in the home page, Bludit generates a global array `$pages` with all the published pages, each page is a `Page Object`.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Load plugins with the hook siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Load plugins with the hook siteBodyBegin -->
	<?php Theme::plugins('siteBodyBegin') ?>

	<h1><?php echo $site->title() ?></h1>
	<h2><?php echo $site->slogan() ?></h2>

	<?php if ($WHERE_AM_I=='page'): ?>
	<p>The user is watching a particular page</p>

	<?php elseif ($WHERE_AM_I=='home'): ?>
		<?php foreach ($pages as $page): ?>
		<h3><?php echo $page->title(); ?></h3>
		<?php endforeach ?>

	<?php endif ?>

	<!-- Load plugins with the hook siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

If the user is watching a particular page, Bludit generates a global Page-Object `$page`, in this example, we are going to print the title and the content.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">

	<!-- CSS -->
	<?php echo Theme::css('css/style.css') ?>

	<!-- Javascript -->
	<?php echo Theme::javascript('js/jquery.min.js') ?>

	<!-- Load plugins with the hook siteHead -->
	<?php Theme::plugins('siteHead') ?>
</head>
<body>
	<!-- Load plugins with the hook siteBodyBegin -->
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

	<!-- Load plugins with the hook siteBodyBegin -->
	<?php Theme::plugins('siteBodyEnd') ?>
</body>
</html>
```

<div class="note">
<div class="title">Download</div>
Download the source code of the theme <a href="https://github.com/bludit/examples/tree/master/themes/mars">Mars</a>.
</div>
