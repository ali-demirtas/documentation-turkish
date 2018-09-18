# Title: Etiketler
<!-- Position: 6 -->
---
Etiketlerle çalışmak için kod parçacıkları.

<div class="note">
Bu kodlar Bludit > v2.1'de çalışır.
</div>

<div class="note">
Varsayılan olarak, etiketlerin veritabanı alfasayısal olarak sıralanır.
</div>

## Tüm etiketleri listele
```
<?php
	$tags = getTags();

	foreach ($tags as $tag) {
		echo 'Etiket adı: '	. $tag->name();
		echo 'Etiket anahtarı: ' . $tag->key();
		echo 'Etiket bağlantısı: ' . $tag->permalink();
		echo 'Sayfaların miktarını etiketle: ' . count($tag->pages());
	}
?>
```
