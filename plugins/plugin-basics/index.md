# Title: Eklenti temelleri
<!-- Position: 1 -->
---
Plugins in Bludit resides in `bl-plugins` folder, and they have a pre-defined structure. Each plugin is an object in Bludit, with differents hooks (methods).

<h2 id="structure">Folder and Files Structure</h2>
This is a mandatory folder structure and files for a plugin.

```
/bl-plugins/{PLUGIN_NAME}/
	languages/en.php
	metadata.json
	plugin.php
```

<h2 id="name-and-description">Name and Description</h2>
The name and description of the plugin is in the JSON file `languages/en.json`.

```
{
	"plugin-data":
	{
		"name": "Merhaba dünya",
		"description": "Yan menüde merhaba dünya yazdırır"
	}
}
```

<h2 id="information">Information</h2>
The information of the plugin is in the JSON file `metadata.json`.

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
The Hello World plugin for Bludit, the below code needs to be in the file `plugin.php`.

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
<div class="title">Download</div>
Download the source code of the plugin <a href="https://github.com/bludit/examples/tree/master/plugins/hello-world">Hello World</a>.
</div>
