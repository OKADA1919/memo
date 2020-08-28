# Aviator Connectorを使ってUSBケーブルを自作する。

Webで「aviator connector usb cable」と検索すると、下のような画像がヒットする。けど、USBケーブルなんてダイソーにでも行けば100円程度で十分使えるモノが手に入るじゃない。いやいや、黒や白のつまらない材料で出来たケーブルなんて使っても面白くないし。せっかくなら自分好みの部品や配色のケーブルが使いたい！ってことで自作のハードルもそんなに高くないので作ってみることにした。
![aviator connector](https://github.com/OKADA1919/memo/blob/images/2020-08-26%20223421.png?raw=true)

## 必要な材料
- **USBコネクター(type-A / mini-B 共にオス)**  
自分の環境に合ったコネクタを用意する。今回は下記リンクの部品を用意した。  
[type-A](http://akizukidenshi.com/catalog/g/gC-07664/)/[mini-B](https://www.mouser.jp/ProductDetail/TE-Connectivity/1734205-1?qs=o4qE4s2E%252BcwHLCQYxSm%252B8w%3D%3D)
- **アビエイターコネクター**  
ケーブルの間に取り付ける部品。こいつを脱着すればわざわざパソコンの裏面まで手を伸ばさなくて良くなるし、何よりカッコイイ。もとは通信ケーブルの中継につかわれている部品で汎用性が高く、内部にあるピンの数によってはLANにもUSBにも音響系にも何でも使えるのが特徴。  
※日本国内では、「PLT コネクタ」という名称で販売されているらしい。  
[PLT コネクタ](https://jp.misumi-ec.com/vona2/detail/110500032770/)
- **4芯ケーブル**  
シールド部分をアースにすれば、3芯でも良い。私はオヤイデ電気で買った。4芯シールド線1.5mで259円。
- **熱収縮チューブ**  
10mm、6mm径など、コネクターの種類に合わせて選ぶ。色は白黒以外に赤黄青とかもある。
- **グルーガン**  
コネクタとケーブルの半田付けをした箇所を補強する。必須じゃないけどあると便利。ダイソーのやつで良いかな。200円だし。
- **パラコード**  
Amazonとか登山用品店とかで売ってる。秋葉原のレプマート東京アキバ店でも売ってた。実物見れるし良いかも。私はレプマートにて1382円で買った。30mもある。  
[Amazon](https://www.amazon.co.jp/gp/product/B075D9JTPF/ref=oh_aui_search_detailpage?ie=UTF8&th=1&psc=1)/[レプマート](https://repmart.jp/user_data/repmart-tokyo-akiba.php)
## 製作手順
### 1.ケーブルとパラコードを準備する  
パラコード は、伸び縮みするのでケーブルの長さ＋１０センチくらい余裕を持った長さがあると安心。ケーブルは長ければ長いほどパラコードは余分に長いものを用意した方が良いかも。ケーブルの先端は熱収縮チューブで保護してると入れやすいかも。これは必須じゃない。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable1.jpeg?raw=true)
### 2.パラコードの中にある白いの糸を抜いてケールブに差し込んでいく  
パラコードは押し入れようとする力で縮んでいくので、仕上げに先端を掴んでパラコードを伸ばすと良いかも。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable2.jpeg?raw=true)
### 3.ケーブル完成！！
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable3.jpeg?raw=true)
### 4.USB-Aコネクタを付ける  
色の箇所に電線をハンダ付けしていく。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable15.jpeg?raw=true)  
まずは予備ハンダ。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable4.jpeg?raw=true)  
こんな感じ。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable5.jpeg?raw=true)  
キャップをはめる。シールド戦はキャップに巻きつけるくらいでいいかも。  
あんまりはみ出てると熱収縮チューブした時に見た目が悪くなるので注意。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable6.jpeg?raw=true)  
### 5.USB Mini-Bコネクタを付ける  
USB-Aと同じ色の線を同じ箇所にハンダ付けしていく。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable7.jpeg?raw=true)  
わかりづらいけどこんな感じ。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable8.jpeg?raw=true)  
キャップはめて完成。
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable9.jpeg?raw=true)   
良い感じ！  
![photo](https://github.com/OKADA1919/memo/blob/images/usbcable10.jpeg?raw=true)  
コネクタを保護するために、熱収縮チューブをはめてく。今回は6mmの物を使ったがUSB-Aコネクタは幅が広いのでラジオペンチなどで広げていく。ラジオペンチの跡が残っても熱収縮すれば消えるので気にしない。  
伸ばしたやつとノーマルなやつ。長さ3cmにした。  
ライターで炙って完成！！きれい！
