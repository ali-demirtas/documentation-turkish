# Title: API Giriş
<!-- Position: 1 -->
---
Bludit API (Uygulama Programlama Arayüzü), Bludit ile kolay entegrasyon sağlamak için bir eklentidir. Bu eklentiyle, yalnızca bir HTTP isteği ile veri tabanından veri alabilir veya güncelleyebilirsiniz.

<h2 id="installation">Kurulum</h2>
Bludit önceden yüklenmiş eklenti API ile birlikte gelir, sadece onu etkinleştirmeniz gerekir.

**Yönetici paneli > Eklentiler > API > Etkinleştir** git.

<h2 id="url">URL</h2>
API'nin URL'si:

```
{protocol}://{domain}/api/{endpoint}
````

Örnek:

```
https://example.com/api/pages
```

<h2 id="endpoints">Son Noktalar ve Yöntemler</h2>

Son nokta		  | Yöntem 	| Açıklama
--------------|---------|-----------------------------------------------|
/pages 			  | GET 		| Sayfaların bir listesini içeren bir dizi döndürür		|
/pages/{key}	| GET		  | Sayfa anahtarıyla filtrelenen bir sayfa döndürür	|
/pages			  | POST		| Yeni sayfa oluştur				|
/pages/{key}  | PUT		  | Bir sayfayı düzenle			|
/pages/{key}  | DELETE	| Bir sayfayı sil				|

<h2 id="inputs">Yöntem Girdileri</h2>

Anahtar         | Tür 		| Açıklama
----------------|---------|-----------------------------------------------|
token 		      | string 	| API belirteci					|
authentication	| string	| Kimlik doğrulama kullanıcı belirteci		|
limit		        | integer	| Döndürülecek sayfaları sınırlamak için bir numara  		|

<h2 id="http-response">HTTP Yanıt</h2>

Yanıt biçimi `JSON` şeklindedir, JSON nesnesinden bir anahtar listesi.

| Anahtar	| Tür 		| Açıklama 					|
----------|---------|-----------------------------------------------|
| message	| string	| Yürütme hakkında küçük bir mesaj döndürür	|
| data 		| array		| Son nokta için yanıtın içeriği	|

Farklı yanıtlar için HTTP Kodunu kontrol edebilirsiniz.
