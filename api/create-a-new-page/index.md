# Title: Bir sayfa oluştur
<!-- Position: 4 -->
---
Bludit API, yeni bir sayfa oluşturmak için özellikler sağlar.

API'ye yönelik tüm talepler `API Token` ihtiyaç duyar, eklentiyi eklentinin ayarlarında bulabilirsiniz.

API'nın içerik yazma isteğinin tamamı bir `Authorization Token` sağlamak için gereklidir. Bu tür bir jetonu almak için **ADMINISTRATOR** rolüne sahip bir kullanıcıya ihtiyacınız var. `Authorization Token` burada bulunur: **Yönetici paneli > Yönet > Kullanıcılar > {Username} > Kullanıcıyı düzenle > Authentication Token > Token**.

<h2 id="request">İstek</h2>

- Son nokta: `/api/pages`
- Methot: `POST`
- İçerik Türü: `application/json`
- İçerik

```
{
	"token": "24a8857ed78a8c89a91c99afd503afa7",
	"authentication": "193569a9d341624e967486efb3d36d75",
	"title": "Köpeğim",
	"content": "Bu sayfanın içeriği, Markdown kodunu ve HTML kodunu destekler."
}
```

<h2 id="response">Yanıt</h2>

- HTTP Kodu: `200`
- İçerik Türü: `application/json`
- İçerik

```
{
	"status": "0",
	"message": "Sayfa oluşturuldu.",
	"data": {
		"key": "my-dog"
	}
}
```

<h2 id="curl-example">CURL komut örneği</h2>
Komut satırı üzerinden `curl` komutu ile yeni bir sayfa nasıl oluşturulacağını gösteren bir örnek. `data.json` dosyası yeni bir sayfa oluşturmak için gereken temel verilere sahiptir.

Dosya `data.json`

```
{
	"token": "24a8857ed78a8c89a91c99afd503afa7",
	"authentication": "193569a9d341624e967486efb3d36d75",
	"title": "Köpeğim",
	"content": "Bu sayfanın içeriği, Markdown kodunu ve HTML kodunu destekler."
}
```

Komutu çalıştırın ve `data.json` dosyasını ekleyin

```
$ curl -vvv \
	-X POST \
	-H "Content-Type: application/json" \
	-d @data.json \
	"https://example.com/api/pages"

> POST /api/pages HTTP/1.1
> Host: example.com
> User-Agent: curl/7.54.0
> Accept: */*
> Content-Type: application/json

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
	"message": "Sayfa oluşturuldu.",
	"data": {
		"key": "my-dog"
	}
}
```
