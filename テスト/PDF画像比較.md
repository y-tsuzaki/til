# PDF画像比較

PDFを画像に変換し、それに差分があるかチェックするシェルスクリプト。

imagemagickが必要

WindowsではWSL (Windows Subsystem for Linux)でも動く

beforeとafterディレクトリ直下にそれぞれ同名のPDFを入れる
あとはシェルを動かすと
outputディレクトリに画像が書き出され、
標準出力でOK、NGが表示される。

複数ページのPDFにも対応している。


## ファイルの配置

```
before/ a.pdf
        b.pdf
      
after/  a.pdf
        b.pdf
        
pdfdiff.sh
```

## コード
```sh
#!/bin/bash

readonly BEFORE_DIR="before"
readonly AFTER_DIR="after"
readonly OUTPUT_DIR="output"
readonly IM_DENSITY="-density 200"

function convert_to_image() {
    local path=$1
    local output_dir=$2

    mkdir -p $output_dir
    convert -quiet $IM_DENSITY -alpha off $path $output_dir/image.png
    echo $(ls -1 $output_dir/*.png | wc -l)
}

function compare_pdf() {
    local pdf=$1
    local img1_dir=$OUTPUT_DIR/$pdf/before
    local img2_dir=$OUTPUT_DIR/$pdf/after
    local diff_dir=$OUTPUT_DIR/$pdf/diff
    mkdir -p $diff_dir

    local count1=$(convert_to_image $BEFORE_DIR/$pdf $img1_dir)
    local count2=$(convert_to_image $AFTER_DIR/$pdf $img2_dir)
    if [ $count1 -ne $count2 ]; then
        echo "$pdf: NG"
        return
    fi

    for path in $img1_dir/*.png; do
        png=$(basename $path)
        composite -quiet -compose difference $img1_dir/$png $img2_dir/$png $diff_dir/$png
        result=$(identify -format "%[mean]" $diff_dir/$png)
        if [ "$result" = "0" ]; then
            echo "$pdf/$png: OK"
        else
            echo "$pdf/$png: NG"
        fi
    done
}

for path in $BEFORE_DIR/*.pdf; do
    pdf=$(basename $path)
    compare_pdf $pdf
done
```

## 参考（コピペ元）
https://qiita.com/oohira/items/184dbbe7c631e8c335a1
