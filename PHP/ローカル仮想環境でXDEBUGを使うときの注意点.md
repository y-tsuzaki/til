# ローカル仮想環境でXDEBUGを使うときの注意点

ある構成のとき、ホストマシンのVSCodeとゲストマシンのXDEBUGが接続できなかったのでメモ。

## 構成

```
ホストマシン （ブラウザ
↓
↓（ゲストの80ポートを8080ポートにマッピング）
↓
ゲストマシン（HTTPサーバ）
```

## 設定内容

/etc/httpd/conf/httpd.conf
```
    php_value session.auto_start 0
    php_value xdebug.remote_autostart 1
    php_value xdebug.remote_enable 1
    php_value xdebug.remote_host XX.XX.XX.XX
    php_value xdebug.remote_connect_back 1
 ```
 
`remote_host`でホストマシンのIPを指定しているが、
`remote_connect_back`を有効にしてしまっていた。

`remote_connect_back`は、HTTPリクエストの送信元IPに対して、XDEBUGが接続を行う設定だ。

ホストマシンはポートフォワードで、ゲストマシンの８０ポートにアクセスしてるため、
XDEBUGは、`remote_host XX.XX.XX.XX`を無視して、`localhost`に接続を試みる。
XDEBUGにとっての`localhost`はゲストマシンのことなので、ホストマシンのVSCodeとゲストマシンのXDEBUGは疎通できなかった。

## 結論
ポーフォフォワードでHTTPサーバにアクセスしてる場合は、
`remote_connect_back`を無効にする。
