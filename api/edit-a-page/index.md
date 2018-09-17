# Title: Bir sayfa düzenle
<!-- Position: 5 -->
---
Bludit API, yeni bir sayfayı düzenlemek için özellikler sağlar.

API'ye yönelik tüm talepler `API Token` ihtiyaç duyar, eklentiyi eklentinin ayarlarında bulabilirsiniz.

API'nın içerik yazma isteğinin tamamı bir `Authorization Token` sağlamak için gereklidir. Bu tür bir jetonu almak için **ADMINISTRATOR** rolüne sahip bir kullanıcıya ihtiyacınız var. `Authorization Token` burada bulunur: **Yönetici paneli > Yönet > Kullanıcılar > {Username} > Kullanıcıyı düzenle > Authentication Token > Token**.

<h2 id="request">İstek</h2>

- Son nokta: `/api/pages/{key}`
- Yöntem: `PUT`
- İçerik Türü: `application/json`
- İçerik

```
{
	"token": "24a8857ed78a8c89a91c99afd503afa7",
	"authentication": "193569a9d341624e967486efb3d36d75",
	"title": "My edited dog",
	"content": "Content of the page here, support Markdown code and HTML code."
}
```

<h2 id="response">Yanıt</h2>

- HTTP Kodu: `200`
- İçerik Türü: `application/json`
- İçerik

```
{
	"status": "0",
	"message": "Sayfa düzenlendi.",
	"data": {
		"key": "my-dog"
	}
}
```
