- 環境　
  - ホスト Windows10
  - ゲスト Centos/7
  - `Vagrant 2.0.4`
  
`vagrant ssh`で

```
vagrant@127.0.0.1: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
```


参考：https://github.com/hashicorp/vagrant/issues/9831

```
powershell を起動する
$Env:VAGRANT_PREFER_SYSTEM_BIN += 0
vagrant ssh
``` 
