# throttleとdebounce

めちゃくちゃ便利だけど、いざ使おうと思うとThrottleとDebouceという言葉が出てこないので、忘れないようにメモ。

両方共イベントを間引くメソッド。

LodashなどのJSライブラリで実装されている。

## Throttle

一定時間の間イベントを１度しか発火しないようにする。

##  Debouce

終わったらイベントを発火する。
最後のイベントから一定時間たったら発火する。


## 実装について

Lodashはいろいろはいったライブラリだが、
ライブラリ入れなくても簡単に実装できるから、ちょっとしたプログラムなら自前で書いてもいいと思う。

https://www.npmjs.com/package/throttle-debounce

Throttle Debouceだけのパッケージもあるので、それを使ってもいいかも。
