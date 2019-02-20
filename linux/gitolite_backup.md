# gitolite backup

gitoliteのバックアップ方法。


### はじめに

以下のリポジトリを使う。
```
https://github.com/wmanley/gitolite-backup
```

`git clone --bare`してくれるツール。


### 使い方

事前にgitoliteのバックアップ対象のリポジトリに、
バックアップ用のユーザを作成しアクセスできるようにしておく。

```
./gitolite-backup.sh gitolite_server_hostname
```

./reposディレクトリにリポジトリがクローンされる。

引数にSSHの接続ホスト名を入れる。
ポート番号や秘密鍵を指定する際は、`~/.ssh/config`にあらかじめ登録しておく。

そのままだとうまく動かない。

リポジトリの名前の後ろにcr(\r）がついてしまっているようだったので、
以下の変更を行う。

https://github.com/y-tsuzaki/gitolite-backup/commit/e2a652a0d7945e7f7c07e761c4e43f974bb1650f

実行した日付が保存されるため、同日に複数回実行すると終了ステータスが１となるので注意すること。
