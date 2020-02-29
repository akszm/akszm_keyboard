# akszm_keyboard
test

#環境
windows10　->　Virtualbox -> ubuntu 16.04 LTS 64bit

仮想環境ってよくわかってないけど、色んなライブラリ(?)を入れたり消したり、
最悪OSごと吹き飛ばしていいから楽ちんな気がする。

#CUI でQMK_firmwareのビルドをする手順　おぼえがき
基本はここ。
http://biacco42.hatenablog.com/entry/2019/08/10/185624

手順通りにやったはずがいっぱいエラーを吐く
1.なんか色々インストールされてない
$ sudo install python-pip
$ pip insatll --upgrade pip
$ sudo apt-get update
$ sudo apt-get install git
$ git clone --recurse-submodules https://github.com/qmk/qmk_firmware.git
$ sudo util/qmk_install.sh

$ lsusb でmeishiのarduino SA が認識されてるか確認
->仮想環境なのでいちいち設定からUSBの許可を出さないとだめ？

https://r7cancer.hatenablog.com/entry/2019/10/18/153458

QMK_Firmwareの書き込みがavrdudeエラーで止まる
→ brew と git がインストールされてない。
$ brew install git
