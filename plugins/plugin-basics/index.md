# Title: Eklenti temelleri
<!-- Position: 1 -->
---
Bludit'teki eklentiler, `bl-plugins` klasöründe bulunur ve önceden tanımlanmış bir yapıya sahiptir. Her eklenti, farklı kancalarla (yöntemlerle) Bludit'teki bir nesnedir.

<h2 id="structure">Klasör ve Dosya Yapısı</h2>
Bu bir zorunlu klasör yapısı ve bir eklenti için dosyaları.

```
/bl-plugins/{PLUGIN_NAME}/
	languages/en.php
	metadata.json
	plugin.php
```

<h2 id="name-and-description">İsim ve Tanım</h2>
Eklentinin adı ve açıklaması JSON dosyasında `languages/en.json` bulunur.

```
{
	"plugin-data":
	{
		"name": "Merhaba dünya",
		"description": "Yan menüde merhaba dünya yazdırır"
	}
}
```

<h2 id="information">Bilgi</h2>
Eklentinin bilgileri JSON dosyasında `metadata.json` bulunur.

```
{
	"author": "Bludit",
	"email": "",
	"website": "https://plugins.bludit.com",
	"version": "1.0",
	"releaseDate": "2018-02-15",
	"license": "MIT",
	"compatible": "2.0, 2.1, 2.2, 2.3",
	"notes": ""
}
```

<h2 id="hello-world">Merhaba dünya</h2>
Bludit için Merhaba dünya eklentisi, aşağıdaki kodun `plugin.php` dosyasında olması gerekiyor.

```
<?php
	class pluginHello extends Plugin {
		public function siteSidebar() {
			echo 'Merhaba dünya';
		}
	}
?>
```

<div class="note">
<div class="title">İndir</div>
Eklentinin kaynak kodunu indir <a href="https://github.com/bludit/examples/tree/master/plugins/hello-world">Merhaba dünya</a>.
</div>
