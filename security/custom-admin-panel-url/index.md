# Title: Özel yönetici paneli URL'si
<!-- Position: 3 -->
---
Bludit, varsayılan olarak yönetici panelini `/admin` bağlamında sunar.

`/bl-kernel/boot/variables.php` dosyasını düzenleyerek değiştirebilirsiniz.`ADMIN_URI_FILTER` sabitini kendi değerinizle değiştirin.

<pre><code data-language="php">define('ADMIN_URI_FILTER', 'admin');</code></pre>
