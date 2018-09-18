# Title: Bir temayı çevir
<!-- Position: 2 -->
---
Her temanın bir `languages` dizini vardır, bu klasörün içinde her dil için farklı sözlük dosyaları oluşturabilirsiniz.

```
/bl-themes/{THEME_NAME}/languages/
	de_DE.json
	en.json
	es.json
	fr_FR.json
	tr_TR.json
	...
```

<div class="note">
<div class="title">Dosya Kodlaması</div>
Tüm sözlük dosyaları <b>JSON</b> dosyasıdır ve <b>UTF-8</b> ile kodlanır.
</div>

Bu bir Türkçe sözlük örneğidir `tr_TR.json`. `tr_TR.json` dosyasındaki her satır, soldaki anahtar ve sağdaki değere sahip bir anahtar-değer çiftidir.

```
{
	"theme-data":
	{
		"name": "Temiz",
		"description": "Basit ve temiz, Pure.css çerçevesine göre."
	}
}
```

Görebildiğiniz gibi, `theme-data` diye adlandırılan bir alanınız var, bunun temanın adı ve açıklaması var.

Bu bir İspanyolca sözlük örneğidir, dosya `/bl-themes/{THEME_NAME}/languages/es.json` içinde bulunur.

```
{
	"theme-data":
	{
		"name": "Pure",
		"description": "Simple y minimalista, basado en el framework Pure.css."
	}
}
```
