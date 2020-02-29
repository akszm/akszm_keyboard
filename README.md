# akszm_keyboard
test
改行をどうするかすらわからないワロタ

# 環境
windows10　->　Virtualbox -> ubuntu 16.04 LTS 64bit

仮想環境ってよくわかってないけど、色んなライブラリ(?)を入れたり消したり、
最悪OSごと吹き飛ばしていいから楽ちんな気がする。

# CUI でQMK_firmwareのビルドをする手順　おぼえがき
基本はここ。
http://biacco42.hatenablog.com/entry/2019/08/10/185624

？？？手順通りにやったはずがいっぱいエラーを吐く
->なんか色々インストールされてない。以下、入れた順に。
$ sudo install python-pip
$ pip insatll --upgrade pip
$ sudo apt-get update
$ sudo apt-get install git
$ git clone --recurse-submodules https://github.com/qmk/qmk_firmware.git
$ sudo util/qmk_install.sh
$ lsusb でmeishi2のarduino SA が認識されてるか確認
　->仮想環境なのでいちいち設定からUSBの許可を出さないとだめ？
qmk_firmware\lib\lufaをDLしてlufaディレクトリに展開　cf.　後述　2.
　->2. なぜかわからないがqmk_firmware\lib\lufa以下のフォルダがない
　　ref.「lufaがなんたら」って書いてある
　　https://r7cancer.hatenablog.com/entry/2019/10/18/153458

$ brew apt install linuxbrew-wrapper
$ brew uninstall --force avr-gcc
$ brew update
$ brew install avr-gcc@7
$ git -C "$(brew --repo homebrew/core" fetch --unshallow
$ brew install avrdude
　->時間かかる(10-20min?)
$brew install git

いまここ

？？？FF14をやるとき、logicoolG600でNumキー入力がバグる。なんだろう。
NumLockがかかっている？？？
->かかってた。NumLockLockでとりあえず対処
