# Title: Kaba kuvvet koruması
<!-- Position: 2 -->
---
## Kaba kuvvet saldırısı nedir?
Bir saldırganın, çoğu zaman doğru bir şekilde tahmin etme ümidiyle birçok şifreyi veya şifreyi denemesinden oluşur. -Viki.

## Bu nasıl çalışır?
Bludit, bu tür saldırıları hafifletmek için kaba kuvvet koruması sağlar ve varsayılan olarak etkindir.

Oturum açmadaki her başarısızlık için Bludit, kara listeye kimlik doğrulamada başarısız olan kullanıcının IP'sini ekler. Kullanıcı birkaç kez başarısız olduğunda, Bludit bir süre için sorunlu IP'yi engeller ve kullanıcı, engel süresi doluncaya kadar oturum açamaz.

## Sınıf ve nesne
`$Security` olarak adlandırılan bir `Security Object` vardır ve nesnenin sınıfı `/bl-kernel/security.class.php`'dir. Sınıf içindeki değişkenlere bir göz atın.

<pre><code data-language="php">
private $dbFields = array(
    'minutesBlocked'=>5,
    'numberFailuresAllowed'=>10,
    'blackList'=>array()
);
</code></pre>

- `minutesBlocked`: IP'nin engelleneceği dakika miktarı.
- `numberFailuresAllowed`: Engellemenin tetiklenmesi için başarısız deneme sayısı.
- `blackList`: Engellenen IP'lerin listesi.

<div class="note">
<div class="title">Not</div>
Bu değerleri kendi değerleriniz için değiştirebilirsiniz.
</div>
