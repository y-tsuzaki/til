## メンテナンス中にするためのhtaccess

```
#---------------------------------------------------
# Maintenance
#---------------------------------------------------
ErrorDocument 503 /mainte.html

<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteCond %{REQUEST_URI} !=/maintenance.html
  RewriteCond %{REMOTE_ADDR} !=XXX.XXX.XXX.XXX
  RewriteRule ^.*$ - [R=503,L]
</IfModule>
```
