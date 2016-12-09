# Pebbleのサーバーが万が一明日落ちた場合
PebbleがFitbitに買収された模様．現在存在するPebbleは当面動くようで，Pebbleもクラウドに依存しないようにする予定とのこと．

しかしPebbleが万が一クラウドに依存しないシステムを作るのを諦めてしまったまま，サーバーがダウンしたら公式のアプリは使えなくなるかもしれない．

そのようなことが起きた場合はどうするかを自分のためにメモ.

もっと良い方法があったら教えてくださいお願いしますm(__)m

** ここに書かれていることを実行して何が起きても自己責任で！！！！　**

たとえPebbleが壊れてもサポートがどうなるのかわからないし，，，，，


## TL;DR
- Androidスマートフォンを使っている場合
	- Pebbleのファームウェアとウォッチフェイスとアプリのバックアップを取り，GagetBridgeを使う．
- iosスマートフォンを使っている場合
	- iosデバイス持ってない

## Androidの場合
### Pebbleファームウェアのバックアップを取る
PebbleのファームウェアはPebble社が管理しているサーバーだと思われるので，バックアップをとっておいた方がいいと思う．

2016/12/09現在はver4.3が最新だが，不安定なので，ver4.2のバックアップをおすすめする．

Pebble Time
https://pebblefw.s3.amazonaws.com/pebble/snowy_dvt/release-v3.8/pbz/Pebble-4.2-snowy_dvt.pbz

Pebble Time Steel
https://pebblefw.s3.amazonaws.com/pebble/snowy_s3/release-v3.8/pbz/Pebble-4.2-snowy_s3.pbz

Pebble Time Round
https://pebblefw.s3.amazonaws.com/pebble/spalding/release-v3.8/pbz/Pebble-4.2-spalding.pbz

Pebble 2
https://pebblefw.s3.amazonaws.com/pebble/silk/release-v3.8/pbz/Pebble-4.2-silk.pbz

ダウンロードしたpbzファイルがファームウェアです．

### アプリやウォッチフェイスのバックアップを取る
公式サーバーがダウンするということは今まで使っていた [https://apps.getpebble.com/](https://apps.getpebble.com/)　が使えなくなる可能性がある．

そのためアプリやウォッチフェイスのpbwファイルのバックアップをとっておく必要がある．
[https://apps.getpebble.com/](https://apps.getpebble.com/) にアクセスし，バックアップしたいアプリ・フェイスのページのURLの末尾に以下のクエリを追加．
```
?dev_settings=true
```
もし，すでにクエリがついていたら以下を追加
```
&dev_settings=true
```
こんな感じになるはず↓
```
https://apps.getpebble.com/en_US/application/*******************?dev_settings=true
```
追加するとアプリ・フェイスのページの下部にDOWNLOAD PBWという項目が増えるので，そこをクリックしてpbwファイルをダウンロード．

参考HP
- ひとりぶろぐ Pebble Watchのアプリストアapps.getpebble.comからパッケージファイルPBWをダウンロードする方法 2016年12月9日アクセス [http://hitoriblog.com/?p=40386](http://hitoriblog.com/?p=40386)

### 日本語フォントファイルのバックアップを取る
日本語フォントを配布している方のサーバーはPebble社のサーバーとは関係ないと思うので，バックアップを取る必要は無いと思いますが，一応．

各種サイトから```*.pbl```をダウンロードしておく．

以下G+コミュにまとめられていた日本語フォントを配っているサイト一覧

1. Kuroさん
http://blog.kuro.ro/pebble-time-chinese-japanese-language-pack/

2. EKESTE.NETさん
http://www.ekesete.net/log/?p=8183

3. minoru chikamuneさん
https://drive.google.com/folderview?id=0B3XsaTcJZ4A3fmNWUVFmTEpzb2lHODkwR0t4ajU2SjlHSktEYVhZdzhXLTJhdjhzZ0Y1OHc#

4. Polyfusia Suguruさん
https://github.com/polyfusia/pebble-japanese-custom-font

5. Cryingneko さん (サイト再開されました！）
http://wh.to/pebble/wiki.php?%E6%97%A5%E6%9C%AC%E8%AA%9E%E8%A8%80%E8%AA%9E%E3%83%91%E3%83%83%E3%82%AF#.ViRQAq0w_tQ

6. あおしまさん
http://d.hatena.ne.jp/aoshimak/touch/20160728

7. Kazuki Negoroさん
https://drive.google.com/file/d/0B3X8ZuIm6h02SENnSTdtbXRuUUE/view

有料だけれど好みの日本語フォントパックを作成できるサイト

1. Cryignekoさんによる言語パック製作所
http://wh.to/pebble/lab_jp.php#.VjbLea377tQ

2. Firmmaker Club　のサイト
http://firmmaker.club/


### gadgetbridgeを使う
#### gadgetbridgeとは
オープンソースプロジェクトでベンダーのクローズドなアプリやクラウドを使わずにMibandやPebbleを使うことを目的として開発されているAndroidアプリ．

GitHubにて複数人にて開発されている．

[https://github.com/Freeyourgadget/Gadgetbridge](https://github.com/Freeyourgadget/Gadgetbridge)

Pebbleにおいて以下の機能が使えると書いてある(かなり適当に訳してるので間違ってたらすみません)．

- 電話の通知と表示
- 電話をした時の表示
- 電話を受けるか切るかの選択
- SMSの通知
- K-9 Mailの通知
- 一般的なアプリの通知
- 16個までの定型文返信
- 各通知をアクションメニューから削除，ミュート，定型文返信
- 全ての通知を削除する機能
- 音楽の再生情報の表示(アーティスト，アルバム，トラック)
- 音楽のコントロール(再生，停止，次，前，音量上，音量下)
- インストールされているアプリやフェイスを一覧表示・アンインストール
- ウォッチフェイスやアプリのインストール(.pbw)
- pebbleファームウェアのインストール(.pbz)
- ランゲージパックのインストール(.pbl)
- Pebbleの画面のスクショを取る
- PebbleKitのサポート
- ヘルス情報をpebble health,misfit,morpheuzから取得（実験的）
- ウォッチフェイスやアプリの設定(実験的)

#### gadgetbridgeのインストール
オープンソースなアプリ限定なアプリストア（ストアと言っても有料のアプリはない）Fdroidからインストール可能．

Fdroidは以下のURLからapkファイルをダウンロードしてスマホにインストール．（設定→セキュリティ→提供元不明のアプリをチェックする必要あり）

[https://f-droid.org/](https://f-droid.org/)

Fdroidでgadgetbridgeで検索をかければあるはず．

installボタンを押してgadgetbridgeをインストール．

#### pebbleをgadgetbridgeと接続
gadgetbridgeのwikiに英語で書いてある．

[https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Getting-Started](https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Getting-Started)

適当に訳すと

1. AndroidのBluetooth設定でPebbleとペアリングを行う．ただしLEのついてない方で．
2. GadgetBridgeを起動して，自分のPebbleをタップする．
3. 初期化されたと表示される

gadgetbridgeとつなぐ前に先にPebbleをファクトリーリセットしたほうがいいかもしれない．

#### gadgetbridgeの設定
gadgetbridgeを起動して右上の…をタップし，設定を開ける．

ここで通知の設定や，音楽アプリの設定，アクティビティトラッカーの設定などが行える．

#### pebbleのファームウェアのインストール
gadgetbridgeを使ってファームウェアをアップデート（ダウングレードも？）可能．

gadgetbridge wiki 
[https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Firmware-updates](https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Firmware-updates)

#### 言語パックのインストール
言語パックは同時に1つのみpebbleに対してインストールできる．

gadgetbridge wiki
[https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Language-Packs](https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Language-Packs)

#### ウォッチフェイスやアプリのインストール
gadgetbridgeにてアプリやフェイスをインストール可能

バックアップをとった``` *.pbw ``` ファイルをファイルブラウザなどでタップし，gadgetbridgeで開くとインストール画面が開く．

gadgetbridge wiki
[https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Watchfaces](https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Watchfaces)

#### ウォッチフェイスやアプリの設定
疑問：設定画面のサーバーってやっぱりPebble社が管理してるのですかね？→G+コミュの方に答えていただきました．ありがとうございます．
> Kenji Irie (にく)
> アプリやウォッチフェースの(スマホ上での)設定画面は各提供元が持っているはずです。
> 自作のウォッチフェースの場合はgithub pagesでホストしたりしてました。

gadgetbridgeのホーム画面から自分のPebbleをタップすることにより，アプリ管理画面が開く．

ここにインストールされているアプリやフェイス一覧が表示されている．

アプリやフェイスの設定を行いたい場合はアプリやフェイスを***ロングタップ***することにより設定画面を開くことが可能である．

この機能はまだ実験的であり不安定とのこと．

自分が試した限り特に問題は起きなかった．

gadgetbridge wiki
[https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Watchfaces](https://github.com/Freeyourgadget/Gadgetbridge/wiki/Pebble-Watchfaces)

## iOSの場合
iosデバイス持ってないのでよくわからない

