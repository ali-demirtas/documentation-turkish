# Title: İçerik > Sabit Sayfalar
<!-- Position: 4 -->
---
Bludit'in iki tür içeriği vardır, **sayfalar** ve **sabit sayfalar**.

- **Sayfalar**, **Ayarlar > Gelişmiş > Sırala** ile tanımlanmış ayarlara göre sıralanır,  varsayılan olarak tarihe göre sıralanmıştır.
- **Sabit sayfalar** her zaman pozisyona göre sıralanır.

Bu bölümde, **sabit sayfalar** ile çalışmak için bazı kod parçacıkları göstereceğiz.

## Tüm sabit sayfaları göster
Kolay yolu işlevi kullanıyor `buildStaticPages()`

```
<?php
	// Each static page is an Page-Object
	$staticPages = buildStaticPages();

	foreach ($staticPages as $page) {
		echo $page->title();
	}
?>
```

Or you can use the the object `$dbPages` to get the database of keys of the static pages and build the pages.

```
<?php
	// Get the keys of the static pages
	$staticPages = $dbPages->getStaticDB();

	// Foreach page key build the page and print the title
	foreach ($staticPages as $pageKey) {
		// buildPage function returns a Page-Object
		$page = buildPage($pageKey);

		echo $page->title();
	}
?>
```
