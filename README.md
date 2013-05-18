FirefoxOS のキーボードで手書き認識をしてみる実験.

とは言っても、
全部を FirefoxOS 上でやるのは大変そうなので、
1台の PC 上で FirefoxOS Simulator と認識用のサーバーを動かして、
socket.io 経由でやりとりさせるという形態となります.

## Requirements

* [FirefoxOS Simulator](https://people.mozilla.com/~myk/r2d2b2g/)
* [node-jim](https://github.com/hankei6km/node-jim)

## Installation

PC 上で FirefoxOS Simulator を動かせるようにしたあと、
[日本語入力を有効にする \[Firefox OS\]](http://iizukak.github.io/2013/03/10/japanese_ime__firefox_os.html)
などを参考に、FirefoxOS の `settings.gaiamobile.org` の `application.zip` に含まれる
`index.html` を書き換えて日本語キーボードを有効にします.
(かな漢字変換をしないなら辞書ファイルは作らなくても動きます)

その後、このリポジトリに含まれてる `index.html` と `*.js` および `*.css` を
`keyboard.gaiamobile.org` の `application.zip` の対応するディレクトリへコピーします.

## Handwriting

FirefoxOS Simulator が稼働している PC 上で node-jim を開始します.
(node-jim は手書き認識の機能しか使わないので、
かな漢字変換用の設定は行わなくても動きます)

その後、FirefoxOS Simulator 上で日本語キーボードを表示し、
未変換の入力がない状態でキーボード左下の `大小` キーをタップすると、
入力パッドが開き(画面上側の白くなった部分に)手書きで文字を入力できます.

認識の結果から、
ひらがなを選択した場合は通常のキーボードのように変換用の文字として扱われ、
その他の文字の場合は直接入力されます.

なにも入力されていない状態で `大小` をキーをタップすることで、
入力パッドが閉じます.

## Device

あまり真面目に調べてないのですが、
入力はマウスイベントのみでタッチイベントとか考慮してない作りなので、
実機ではたぶん動かないんじゃないかなと思います.

## Hack

FirefoxOS のキーボードの Hack は、
[Adding cursor swipe to the Firefox OS keyboard](https://hacks.mozilla.org/2013/03/adding-cursor-swipe-to-the-firefox-os-keyboard/)
とかが参考になるのでないかと.

## License

Copyright (c) 2013 hankei6km (MIT License)

詳細は LICENSE ファイルを参照.  
