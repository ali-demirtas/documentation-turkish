# Title: Bir eklentiyi çevir
<!-- Position: 1 -->
---
Her eklentinin bir `languages` dizini vardır, bu klasörün içinde her dil için farklı sözlük dosyaları oluşturabilirsiniz.

```
/bl-plugins/{PLUGIN_NAME}/languages/
	de_DE.json
	en.json
	es.json
	fr_FR.json
	tr_TR.json
	...
```

<div class="note">
<div class="title">Dosya Kodlaması</div>
Tüm sözlük dosyaları <b>JSON</b> dosyalarıdır ve <b>UTF-8</b> olarak kodlanmaktadır.
</div>

Bu `tr_TR.json` Türkçe bir sözlük örneğidir. `tr_TR.json ` dosyasındaki her satır, soldaki anahtar ve sağdaki değer ile birlikte bir anahtar-değer çiftidir.

```
{
	"plugin-data":
	{
		"name": "Sayfa listesi",
		"description": "Sırayla sayfaların listesini gösterir."
	},

	"home": "Ana sayfa",
	"show-home-link": "Ana sayfa bağlantısı"
}
```

Gördüğünüz gibi `plugin-data` diye bir alanınız var, bu eklentinin adı ve açıklaması vardır ve sonraki alanlar eklenti için `home` ve `show-home-link` ifadeleridir..

Bu bir İspanyolca sözlük örneğidir, dosya `/bl-plugins/{PLUGIN_NAME}/languages/es.json` içinde bulunur.

```
{
	"plugin-data":
	{
		"name": "Listado de paginas",
		"description": "Muestra el listado de paginas en orden."
	},

	"home": "Inicio",
	"show-home-link": "Mostrar link de la pagina de incio"
}
```
