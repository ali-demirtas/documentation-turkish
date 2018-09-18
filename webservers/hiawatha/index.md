# Title: Hiawatha
<!-- Position: 2 -->
<!-- Date: 2017-08-22 22:00:00 -->
---
Bludit, Hiawatha web sunucusunu destekler, aşağıdaki yeniden yazma kuralını kullanabilirsiniz:

```
UrlToolkit {
    ToolkitID = bludit
    RequestURI exists Return
    Match [^?]*(\?.*)? Rewrite /index.php$1
}
```
