# Title: Kategoriler
<!-- Position: 5 -->
---
Kategorilerle çalışmak için kod parçacığı.

<div class="note">
Varsayılan olarak, kategoriler veritabanı alfasayısal olarak sıralanır.
</div>

## Tüm kategorileri listele

```
<?php
	$categories = getCategories();

	foreach ($categories as $category) {
		// Each category is an Category-Object
		echo 'Kategori adı: '	. $category->name();
		echo 'Kategori anahtarı: ' 	. $category->key();
		echo 'Kategori bağlantısı: ' 	. $category->permalink();
		echo 'Kategorideki sayfaların sayısı: ' . count($category->pages());
	}
?>
```

## Yalnızca sayfaları olan kategorileri listeleme

```
<?php
	$categories = getCategories();

	foreach ($categories as $category) {
		// Each category is an Category-Object
		if (count($category->pages())>0) {
			echo 'Kategori adı: '	. $category->name();
			echo 'Kategori anahtarı: ' 	. $category->key();
			echo 'Kategori bağlantısı: ' 	. $category->permalink();
		}
	}
?>
```

## Kategoriyle ilgili tüm kategorileri ve sayfaları listeleyin

```
<?php
	$categories = getCategories();

	foreach ($categories as $category) {
		// Each category is an Category-Object
		echo 'Kategori adı: ' . $category->name();

		// The method $category->pages() returns all the pages keys releated to the category
		foreach ($category->pages() as $pageKey) {
			// buildPage function returns a Page-Object
			$page = buildPage($pageKey);

			echo '- Sayfa adı: ' . $page->title();
		}
	}
?>
```

## Kategori ile ilgili tüm sayfaları listeleme

```
<?php
        // Kategori anahtarı
        $categoryKey = 'example';

		// The category is an Category-Object
        $category = getCategory($categoryKey);

        // Kategori adını yazdır
        echo 'Kategori adı: ' . $category->name();

        // "example" kategorisiyle ilgili sayfaların başlıklarını yazdır
        foreach ($category->pages() as $pageKey) {
			// buildPage function returns a Page-Object
			$page = buildPage($pageKey);

			echo $page->title();
        }
?>
```

## Etkin kategoriyi al

```
<?php
	// Kullanıcının bir kategoriye göz atıp atmadığını kontrol edin
	if ($WHERE_AM_I=='category') {
		// Kategori anahtarını URL'den alın
		$categoryKey = $Url->slug();

		// Kategori adını kategori anahtarından alın
		$categoryName = $dbCategories->getName($categoryKey);

		// Kategori adını yazdır
		echo $categoryName;
	}
?>
```
