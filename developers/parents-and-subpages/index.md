# Title: Üst ve alt sayfalar
<!-- Position: 7 -->
---
<div class="note">
Aşağıdaki kodlar Bludit > v2.3'te çalışır
</div>

## Bir sayfanın alt sayfaları olup olmadığını kontrol edin (alt sayfalar)

```
<?php
	// The variable $page is an Page-Object
	if ($page->hasChildren())) {
		echo 'Bu sayfada alt sayfa var';
	} else {
		echo 'Bu sayfada alt sayfa yok';
	}
?>
```

## Bir sayfanın tüm alt sayfalarını listele

```
<?php
	// The variable $page is an Page-Object
	$children = $page->children();

	// Each child is a Page-Object
	foreach ($children as $child) {
		echo $child->title();
	}
?>
```

## Bir sayfanın alt sayfa olup olmadığını kontrol edin (üst sayfa var)

```
<?php
	// The variable $page is an Page-Object
	if ($page->isChild())) {
		echo 'Bu bir alt sayfadır';
	} else {
		echo 'Bu bir alt sayfa değildir';
	}
?>
```

## Ana sayfanın başlığını alt sayfadan yazdır
Bir sayfanın bir alt sayfası varsa, ana sayfanın yöntemlerini  `parentMethod()` yöntemiyle çağırabilirsiniz.

```
<?php
	// The variable $page is an Page-Object
	if ($page->isChild())) {
		echo 'Ana sayfanın başlığı: ' . $page->parentMethod('title');
	} else {
		echo 'Sayfa, alt sayfa değil';
	}
?>
```

## Gezinme çubuğu yazdır
Bir üst sayfa alt sayfa sahibi olabilir veya olmayabilir.

```
<?php
	// Üst sayfaların listesini al
	$parents = buildParentPages();

	foreach ($parents as $parent) {
		echo $parent->title();

		// Sayfanın alt sayfa olup olmadığını kontrol edin
		if ($parent->hasChildren()) {
			// Get the list of children
			$children = $parent->children();

			foreach ($children as $child) {
				echo " > " . $child->title();
			}
		}
	}
?>
```
