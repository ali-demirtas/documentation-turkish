# Title: İçerik > Sayfalar
<!-- Position: 3 -->
---
Bludit'in iki tür içeriği vardır, **sayfalar** ve **sabit sayfalar**.

- **Sayfalar**, **Ayarlar > Gelişmiş > Sırala** ile tanımlanmış ayarlara göre sıralanır,  varsayılan olarak tarihe göre sıralanmıştır.
- **Sabit sayfalar** her zaman pozisyona göre sıralanır.

Bu bölümde, **sayfalar** ile çalışmak için bazı kod parçacıkları göstereceğiz.

## En son 5 sayfayı listeleme
Bu kod parçacığı, yayınlanan en son 5 sayfanın `başlaığını` yazdırır.
```
<?php
	// Paginator sayfa numarası, ilk sayfa 1
	$pageNumber = 1;
	// Geri ögeler için sayfa miktarı
	$amountOfItems = 5;
	// Sadece yayınlanmış durumdaki sayfaları alın
	$onlyPublished = true;
	// Sayfaların anahtar listesini alın
	$pages = $dbPages->getList($pageNumber, $amountOfItems, $onlyPublished);

	foreach ($pages as $pageKey) {
		// buildPage function returns a Page-Object
		$page = buildPage($pageKey);

		echo $page->title();
	}
?>
```

## Tüm sayfaları listele
Bu kod pasajı, sistemdeki tüm sayfaların `başlığını` yayınlanan durumla birlikte yazdırır.

```
<?php
	// Paginator sayfa numarası, ilk sayfa 1
	$pageNumber = 1;
	// -1 değeri, sistemdeki tüm sayfaları döndürmek için Bludit'e söyler.
	$amountOfItems = -1;
	// Sadece yayınlanmış durumdaki sayfaları alın
	$onlyPublished = true;
	// Sayfaların anahtar listesini alın
	$pages = $dbPages->getList($pageNumber, $amountOfItems, $onlyPublished);

	foreach ($pages as $pageKey) {
		// buildPage function returns a Page-Object
		$page = buildPage($pageKey);

		echo $page->title();
	}
?>
```

## Alt sayfalarla çalışma
Bludit bir alt sayfa seviyesini destekler.

Alt sayfalarla düzgün bir şekilde çalışmak için sıralama filtresini `position` olarak ayarlamanız gerekir.

Bu konuya ait bir bölüm oluşturuyoruz: [Üst sayfalar ve alt sayfalar](https://docs.bludit.com/en/developers/parents-and-children)
