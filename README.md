# akszm_keyboard
test
改行をどうするかすらわからないワロタ

# 20/03/02

# 環境
windows10　->　Virtualbox -> ubuntu 18.04 LTS 64bit
                                    ^
最新のubuntu　LTS版に変更

最新の公式サイトの記述に従っていくこと。
https://docs.qmk.fm/#/ja/
qiitaは情報が遅れている場合もあるので気をつける。

# ハマったポイント
make meishi2:default:avrdude
でハマった。以下を参照して解決。
https://qiita.com/zuk2y/items/efed106dad430430060b

パスを通すときに、参照したサイトそれぞれでフォルダ名が細々違った
export NRFSDK15_ROOT=~/nRF_SDK_v15.0.0
                          ^    ^　　　　~~~~~~~~~
あと.bashrc(?)に書き込みたいけどうまく行かないので、
terminalを立ち上げるたびに上のexport文を入力する必要あり

# 別件；
コンスルーが半抜けになってた。直接は関係ないが、今後気をつけること。

# BLE版もコンパイルできた
ただし、tmk_core/protocol/nrf/matrix.c でエラーを吐いた。
行564-573をコメントアウトしたらなんか通ったが、これはやったらいけないやつな気がする。

以下、エラーはいたときのログ
Compiling: tmk_core/protocol/nrf/matrix.c                                                          tmk_core/protocol/nrf/matrix.c: In function 'ble_nus_on_disconnect':
tmk_core/protocol/nrf/matrix.c:567:11: error: array subscript is above array bounds [-Werror=array-bounds]
     matrix[i + matrix_offset] = 0;
     ~~~~~~^~~~~~~~~~~~~~~~~~~
tmk_core/protocol/nrf/matrix.c:567:11: error: array subscript is above array bounds [-Werror=array-bounds]
cc1: all warnings being treated as errors
 [ERRORS]





# 20/03/01
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
