# BrownSugar Flex ビルドガイド

![][bs_flex]

BrownSugar Flex のビルドガイドです  
組み立ての前に一通り目を通しておいてください

## 事前準備

以下のリストを参考に、必要な部品や機材を確認してください

### 内容物

数量の `()` 内の数字は、数量に含まれる予備の数です

|部品|数量|
|:--|--:|
|PCB - Base|2|
|PCB - Row0|2|
|PCB - Row1|2|
|PCB - Row5|2|
|PCB - Row6A|2|
|PCB - Row6B|2|
|PCB - Pad|2|
|Kailh Choc キーソケット|134|
|ダイオード|134|
|USB Micro オス|24|
|USB Micro オス シールド|24|
|USB Micro メス|20|
|フルカラーLED (YS-SK6812MINI-E)|5(1)|
|TRRSジャック|2|
|タクトスイッチ|2|
|ピンソケット 4pin|2|
|ピンヘッダ 4pin|2|
|3.5mm スペーサー|42|
|7mm スペーサー|4|
|M2 3mm ねじ|100(8)|

### 別途必要な部品

部品の例としてリンクを張ってあります  
すべて、[遊舎工房][yusha]さんや[TALP KEYBOARD][talp]さんで揃えることができます

|部品|数量|
|:--|--:|
|[Kailh Choc V1 キースイッチ][choc_switch]|134|
|[Kailh Choc V1 対応キーキャップ][choc_keycap]|134|
|[Pro Micro 5V/16MHz][pro_micro]|2|
|[ピンヘッダ or コンスルー 12pin][pinheader]|4|
|[TRRS ケーブル][trrs_cable]|1|

### 必要な機材

* [はんだごて][soldering_iron]
* [はんだ][solder]
* [はんだ Φ0.3][solder0.3]
* [テスター][tester]
* [エポキシ系接着剤][cemedine]
* やすり（棒やすり推奨）
* マスキングテープ
* フラックス
* フラックス除去剤

## 組み立て

部品の確認や機材の用意ができたら、組み立てに入ります

### PCB の切り離し

BrownSugar Flex は PCB サンドイッチというマウント方法を採用しています  
各 PCB は `トッププレート` `基板` `ボトムプレート` が繋がった状態で届きます  
これらを切り離しましょう

![][cut_out_pcb]

この部分を折ると簡単に切り離せます

![][pcb_edge]

切り離したら、折りしろとして残った部分をやすりで削り、平らにならします

また、この時点で端面を黒いマーカーなどで塗ると見栄えが良くなります

![][cut_out]

### 部品の実装

PCB の切り離しが終わったら、部品の実装を行います

#### 裏面の部品の実装

これから部品の実装を行う面が裏面（スイッチを取り付ける面と反対）になるので、左右に気を付けてください

##### USB オスの実装

まずはコネクタにシールドを取り付けます

![][shield]

![][cut_out_shield]

シールドを折り取ります

![][usb1]
![][usb2]
![][usb3]
![][usb4]

`カチッ` と音がなるまで押し込みます  
ものによっては鳴らないこともありますが、シールドがコネクタの爪に引っかかっていれば問題ありません

![][usb_taped]

次にマスキングテープで基板に固定します

固定したらはんだ(Φ0.3)を使ってはんだ付けしていきます  
フラックスを塗布したほうがいいでしょう

##### USB メスの実装

![][usb_female_taped]

オスと同様にマスキングテープで基板に固定して、はんだ付けしていきます  
これも、フラックスを塗布したほうがいいでしょう

![][usb_female_soldered]

端子のはんだ付けが終わったら、固定用の足もはんだ付けします

##### 導通確認

USB コネクタを実装したら、導通確認をします  
まずは、各基板を接続します  
このとき、USB コネクタを持って差し込んでください  
最悪折れます  
なお、 `Row6A` `Row6B` はどちらか一方しか接続できないので、どちらかを先に固定まで行い、もう一方を改めて導通確認から行います

**<font color="red">これ以降、コネクタを固定するまで抜かないようにしてください</font>**

画像内で各色の丸で示したパッドがそれぞれ導通しているか確認してください

###### 右手 Row

![][check_right_row]

以下の四角で囲われている部分で導通していなかった場合、四角と同じ色の丸で囲われている USB コネクタのはんだ付けを確認してください

![][check_right_row_error]

###### 右手 Col

![][check_right_col]

以下の四角で囲われている部分で導通していなかった場合、四角と同じ色の丸で囲われている USB コネクタのはんだ付けを確認してください

![][check_right_col_error]

###### 左手 Row

![][check_left_row]

以下の四角で囲われている部分で導通していなかった場合、四角と同じ色の丸で囲われている USB コネクタのはんだ付けを確認してください

![][check_left_row_error]

###### 左手 Col

![][check_left_col]

以下の四角で囲われている部分で導通していなかった場合、四角と同じ色の丸で囲われている USB コネクタのはんだ付けを確認してください

![][check_left_col_error]

##### USB コネクタの固定

導通確認で問題なければ、コネクタを固定します

![][glued_front]

まずは表側をエポキシ系接着剤で固定します

![][glued_back1]
![][glued_back2]

表側が終わったら裏側からも固定します

完全硬化するまで一度放置しましょう

硬化したら、抜いても問題ありません

##### ダイオードの実装

ダイオードを実装します  
USB コネクタを実装した面に実装します  
基板に印刷されている方向に合わせて実装してください

##### Kailh Choc ソケットの実装

ソケットを実装します  
USB コネクタを実装した面に実装します  
基板に印刷されている形に合わせて実装してください

#### 表面の実装

基板をひっくり返し、表面に部品を実装していきます  
写真を参考にはんだ付けしてください

##### 右手側

![][right_front]

##### 左手側

![][left_front]

##### ジャンパのブリッジ

見えているジャンパ4つをブリッジします

##### その他部品の実装

表側にして、ピンソケット、TRRSジャック、タクトスイッチを実装します

#### シールドの実装

##### YS-SK6812MINI-E の実装

![][led_orientation]

方向に注意して実装します  
あまり長い時間はんだごてを当てると、熱によって内部の IC が破壊されるので気を付けましょう  
温度にもよりますが、おおむね5秒以内なら大丈夫だと思います

##### ピンヘッダの実装

なるべく傾きがないように実装します

### 組み立て

部品の実装が終わったら、ねじ止めをして組み立てます

### ファームウェアの書き込み

#### 準備

1. [QMK のドキュメント][qmk]を参考に環境を構築します
1. [ここ][qmk_firmware_koktoh]からリポジトリをクローンします

```
git clone -b dev/bs_flex --depth 1 https://github.com/koktoh/qmk_firmware_koktoh
```

#### 書き込み

先ほどクローンしたファームウェアのディレクトリ内で以下のコマンドを実行してください

```
qmk flash -kb bs_flex -km default
```

左右の Pro Micro に対して行ってください

以上で終了です  
お疲れ様でした

## 問い合わせ

組み立てについてわからないことがあれば、[私のツイッター][twitter]や、このリポジトリの issue に書き込んでください


[//]:# (links)
[yusha]:https://shop.yushakobo.jp/
[talp]:https://talpkeyboard.stores.jp/
[choc_switch]:https://shop.yushakobo.jp/collections/kailh/products/pg1350
[choc_keycap]:https://shop.yushakobo.jp/collections/choc/products/mbk-choc-low-profile-keycaps
[pro_micro]:https://shop.yushakobo.jp/collections/controller-board/products/promicro-spring-pinheader
[pinheader]:https://shop.yushakobo.jp/collections/keyboard-parts/products/a01mc-00
[trrs_cable]:https://shop.yushakobo.jp/collections/accessory/products/trrs_cable
[soldering_iron]:https://www.amazon.co.jp/dp/B006MQD7M4/
[solder]:https://www.amazon.co.jp/dp/B001PR1L32/
[solder0.3]:https://www.amazon.co.jp/dp/B000W9IORU/
[tester]:https://akizukidenshi.com/catalog/g/gM-01287/
[cemedine]:https://www.amazon.co.jp/dp/B000TGAR3K/
[qmk]:https://docs.qmk.fm/#/ja/
[qmk_firmware_koktoh]:https://github.com/koktoh/qmk_firmware_koktoh
[twitter]:https://twitter.com/KokToH_kuro

[//]:# (imgs)
[bs_flex]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/bs_flex.jpg
[cut_out_pcb]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/cut_out_pcb.png
[pcb_edge]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/pcb_edge.png
[cut_out]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/cut_out.jpg
[shield]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/shield.png
[cut_out_shield]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/cut_out_shield.jpg
[usb1]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb1.jpg
[usb2]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb2.jpg
[usb3]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb3.png
[usb4]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb4.jpg
[usb_taped]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb_taped.jpg
[usb_female_taped]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb_female_taped.jpg
[usb_female_soldered]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb_female_soldered.jpg
[check_right_row]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_right_row.png
[check_right_col]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_right_col.png
[check_left_row]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_left_row.png
[check_left_col]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_left_col.png
[check_right_row_error]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_right_row_error.png
[check_right_col_error]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_right_col_error.png
[check_left_row_error]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_left_row_error.png
[check_left_col_error]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/check_left_col_error.png
[glued_front]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/glued_front.jpg
[glued_back1]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/glued_back1.jpg
[glued_back2]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/glued_back2.jpg
[usb_soldered_left_back]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb_soldered_left_back.jpg
[usb_soldered_right_back]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/usb_soldered_right_back.jpg
[right_front]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/right_front.jpg
[left_front]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/left_front.jpg
[led_orientation]:https://github.com/koktoh/bs_flex_build_guide/blob/img/img/led_orientation.png
