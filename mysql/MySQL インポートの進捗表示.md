# MySQL インポートの進捗表示.md

pvコマンドを使う。

pv : https://linux.die.net/man/1/pv

```
pv IMPORTDATA.sql | mysql -uUSERNAME -p DATABASE
Enter password: 
630MiB 0:06:51 [ 716KiB/s] [=============>                          ] 14% ETA 0:39:37
```

## 参考

https://qiita.com/hiroq/items/efd8c3580c9c9457c869
