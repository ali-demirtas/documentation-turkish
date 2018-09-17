# Başlık: Sayfa listesi isteme
<!-- Position: 2 -->
---
Bludit API, belirli bir sayfa listesi istemek için özellik sağlar.

API'nin tüm isteği `API Token` ihtiyaç duyar, eklenti ayarlarında belirteci bulabilirsiniz.

<h2 id="request">İstek</h2>

- Son nokta: `/api/pages`
- Yöntem: `GET`
- Parametreler: `token`

<h2 id="response">Yanıt</h2>

- HTTP Kodu: `200`
- İçerik Türü: `application/json`
- İçerik

```
{
	"status": "0",
	"message": "Sayfaların listesi, öge miktarı: 15",
	"data": [
		{
			"key": "the-dog",
			"title": "Köpek",
			"content": "Sayfanın içeriği",
			"description": "Sayfanın açıklaması",
			"date": "2017-08-24 22:00:00",
			"permalink": "http:\/\/example.com\/the-dog"
		},
		{
			....
		}
	]
}
```

<h2 id="curl-example">CURL komut örneği</h2>
Komut satırı üzerinden komut istemiyle yapılan bir isteğin bir örneği.

```
$ curl -vvv \
	-X GET \
	-G "https://example.com/api/pages" \
	-d "token=80a09ba055b73f68e3c9e7c9ea12b432"

> GET /api/pages?token=80a09ba055b73f68e3c9e7c9ea12b432 HTTP/1.1
> Host: example.com
> User-Agent: curl/7.54.0
> Accept: */*

< HTTP/1.1 200 OK
< Date: Sun, 27 Aug 2017 18:58:25 GMT
< Set-Cookie: Bludit-KEY=3de3df692e83b9cbbf5d31de385110bb; path=/; HttpOnly
< Expires: Thu, 19 Nov 1981 08:52:00 GMT
< Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
< Pragma: no-cache
< Access-Control-Allow-Origin: *
< Content-Length: 50731
< Content-Type: application/json

{
        "status": "0",
        "message": "Sayfaların listesi, öge miktarı: 15",
        "data": [
		{
                        "key": "the-dog",
                        "title": "Köpek",
                        "content": "Sayfanın içeriği",
                        "description": "Sayfanın açıklaması",
                        "date": "2017-08-24 22:00:00",
                        "permalink": "http:\/\/example.com\/the-dog"
                },
                {
                        ....
                }
        ]
}
```

<h2 id="ajax-example">Javascript: jQuery ile AJAX</h2>
Javascript kütüphanesi ile AJAX talebi örneği [jQuery](https://api.jquery.com/jQuery.ajax/).

```
$.ajax({
	url: "https://example.com/api/pages",
	method: "GET",
	data: "token=80a09ba055b73f68e3c9e7c9ea12b432",
	dataType: 'json',
	success: function(json) {
		console.log(json);
	}
});
```

<div class="note">
<div class="title">İndir</div>
Örnekte kaynak kodunu <a href="https://github.com/bludit/examples/tree/master/api/ajax-request-list-of-pages">jQuery</a> olarak indir.
</div>
