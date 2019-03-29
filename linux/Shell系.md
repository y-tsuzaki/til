## ファイル名に現在日時を付ける

```
echo > ./$(date +%y%m%d).txt
```

## ブレース展開

file -> file.bk　にする
```
mv file{,bk}
```

file1 ~ file10　という連番ファイルを作る
```
touch file{1..10}
```

他にもいろいろできるので、暇なときに見る。
https://qiita.com/laikuaut/items/642aa329a8d214a2cccb

