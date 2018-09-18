# Title: İçerik > Sabit Sayfalar
<!-- Position: 4 -->
---
Bludit'in iki tür içeriği vardır, **sayfalar** ve **sabit sayfalar**.

- **Sayfalar**, **Ayarlar > Gelişmiş > Sırala** ile tanımlanmış ayarlara göre sıralanır,  varsayılan olarak tarihe göre sıralanmıştır.
- **Sabit sayfalar** her zaman pozisyona göre sıralanır.

Bu bölümde, **sabit sayfalar** ile çalışmak için bazı kod parçacıkları göstereceğiz.

## Tüm sabit sayfaları göster
Kolay yolu `buildStaticPages()` nesnesini kullanmaktır.

```
<?php
	// Her sabit sayfa Page-Object nesnesidir
	$staticPages = buildStaticPages();

	foreach ($staticPages as $page) {
		echo $page->title();
	}
?>
```

Ya da sabit sayfaların anahtarlarının veritabanını almak ve sayfaları oluşturmak için `$dbPages` nesnesini kullanabilirsiniz.

```
<?php
	// Sabit sayfaların anahtarlarını al
	$staticPages = $dbPages->getStaticDB();

	// Foreach sayfası tuşu sayfayı oluşturun ve başlığı yazdırın
	foreach ($staticPages as $pageKey) {
		// buildPage işlevi bir Page-Object döndürür
		$page = buildPage($pageKey);

		echo $page->title();
	}
?>
```
