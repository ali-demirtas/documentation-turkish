# Title: Eklentiler
<!-- Position: 10 -->
---
Eklentiyle çalışmak için kod parçacıkları.

## Eklenti etkinleştirme

```
<?php
	// Eklentinin sınıf adı
	$className = 'pluginAbout';

	activatePlugin($className);
?>
```

## Eklenti devre dışı bırakma

```
<?php
	// Eklentinin sınıf adı
	$className = 'pluginAbout';

	deactivatePlugin($className);
?>
```

## Bir eklentinin etkin olup olmadığını kontrol edin (etkin)

```
<?php
	// Eklentinin sınıf adı
	$className = 'pluginAbout';

	if (pluginActivated($className)) {
		echo 'About eklentisi etkinleştirildi';
	} else {
		echo 'About eklentisi devre dışı bırakıldı';
	}
?>
```

## Bir eklenti al
Bu işlev bir [Plugin-Object] (https://github.com/bludit/bludit/blob/master/bl-kernel/abstract/plugin.class.php) döndürür.

Eklentinin etkinleştirilmesi gerekir, aksi halde `getPlugin()` işlevi `false` işlevine döner.

```
<?php
	// Eklentinin sınıf adı
	$className = 'pluginAbout';

	// Get the Plugin-Object
	$plugin = getPlugin($className);

	// Eklenti etiketini yazdır
	echo $plugin->label();
	
	// Eklentinin kancasını siteSidebar çalıştırın ve yazdırın
	echo $plugin->siteSidebar();
?>
```
