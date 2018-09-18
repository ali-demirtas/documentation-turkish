# Title: Örnek: Benim ilk temam
<!-- Position: 2 -->
---
Yeni ve basit bir tema yaratalım, yeni temayı 'Kahve' olarak adlandıracağım.

- `/bl-themes/` klasörünün içinde tema klasörünü oluşturun, `/bl-themes/coffee/`
- `/bl-themes/coffee/` klasörünün içinde `languages` klasörü oluşturun
- `/bl-themes/coffee/languages/` klasörünün içinde `en.json` dosyası oluşturun
- `/bl-themes/coffee/` klasörünün içinde `metadata.json` dosyası oluşturun
- `/bl-themes/coffee/` klasörünün içinde `index.php` dosyası oluşturun

Bir sonraki klasör ve dosya yapısına sahip olacaksınız.

```
/bl-themes/coffee/
	language/en.json
	metadata.json
	index.php
```

Sonraki adımlar dosyaların içeriğini oluşturmaktır. `index.php` ile başlayalım ve aşağıdaki HTML ve PHP kodunu ekleyelim.

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Bludit</title>
</head>
<body>
	<?php foreach ($pages as $page): ?>

	<h1><?php echo $page->title(); ?></h1>
	<div><?php echo $page->content(); ?></div>

	<hr>

	<?php endforeach; ?>
</body>
</html>
```

Temayla ilgili adı ve açıklamayı eklemek için `languages/en.json` adlı dosyayı düzenleyin.

```
{
	"theme-data":
	{
		"name": "Kahve",
		"description": "Bu Bludit için ilk temam."
	}
}
```

Şimdi tema ile ilgili bilgileri tamamlamak için `metadata.json` dosyasını düzenleyin.

```
{
	"author": "Bludit",
	"email": "",
	"website": "",
	"version": "1.0",
	"releaseDate": "2018-02-15",
	"license": "MIT",
	"compatible": "2.0",
	"notes": ""
}
```

Tebrikler, Bludit için ilk temanıza sahipsiniz!
