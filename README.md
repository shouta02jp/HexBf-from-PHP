# HexBF from php
Brainf*ckを元に作った自作言語をPHPで作成したものです。
## 仕組み
* アドレスは二つのみ。
* 一桁目が、16進数の上位ビット。
* 二桁目が、16進数の下位ビット。
* 初期指定アドレスは二桁目。
* []のネスト数は最大8(超えると、overflowとなり、処理を中断する)。
## 操作
Brainf*ckと操作はほぼ同じです。

|入力|説明| 
:----:| ----
|+|指定アドレス値をインクリメント|
|-|指定アドレス値をデクリメント|
|<|指定アドレスを一桁左にずらす|
|>|指定アドレスを一桁右にずらす|
|.|全体の値をASCIIコードで文字列に変換し、出力|
|[|指定アドレス値が0出ない場合、]まで実行|
|]|指定アドレス値が0だった場合、]に戻る|:

* <,>をしたとき、指定アドレスはループするようになっています。

例）```<<+```の値は、0x01<br>
　　```>+```の値は、0x10となります。
## 初期値
* 指定アドレスは、下位ビットです。
* アドレス値は、上位下位ともに0(0x00)です。
## 例
入力
```
++++++++<++++.>---.+++++++..+++.---------------<--.+++>+++++++.++++++++<-.+>-------------.++++++++++<-.>--------.---<--..
```
出力
```
HELLO WORLD!!
```
## 現時点(2018/07/19)でのバグ
* **[]** のネストが最大で8個までとなっていること。
## 2018/06/22でのバグ
* **[]** の処理がアドレス全体の値で適応となり、```[-]```をすると強制的に初期値(0x00)となります。
* 0x08(\b)は、非対応となっています。
