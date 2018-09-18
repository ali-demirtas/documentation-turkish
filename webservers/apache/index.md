# Title: Apache
<!-- Position: 1 -->
---
Bludit sistemi otomatik olarak yapılandırmayı deneyin, kurulumla ilgili herhangi bir sorununuz yoksa sonraki adımları izlemeniz gerekmez.

Apache web sunucusu, yeniden düzenleme kuralları gibi bazı yapılandırmaları saklamak için `.htaccess` dosyasını kullanır. `.htaccess` dosyası gizli bir dosyadır.

- Bludit'i kök dizine yüklerseniz, `RewriteBase /` satırını kaldırmanız gerekir.

- Bludit'i bir alt dizine, örneğin, `bludit` dizinine yüklerseniz, `RewriteBase /bludit/` için `RewriteBase /` ifadesini kaldırmanız ve değiştirmeniz gerekir.

Dosya: `.htaccess`

```
AddDefaultCharset UTF-8

<IfModule mod_rewrite.c>

# Yeniden yazma kurallarını etkinleştir
RewriteEngine on

# Temel dizin
#RewriteBase /

# .Txt dosyalarına doğrudan erişimi engelle
RewriteRule ^bl-content/(.*)\.txt$ - [R=404,L]

# Tüm URL işlemleri index.php tarafından
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*) index.php [PT,L]

</IfModule>
```



