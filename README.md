
# nextpaint version 0.5

###概要

nextpaint は無料で使えるFlashのお絵かきツールです。
機能はシンプルで最低限の機能のみサポートします。

主な機能
-色、透明度、ペンサイズを選んでフリーハンドで描画
-スポイント機能
-サーバへ画像保存
-無制限アンドゥ
-画像初期化
-パラメータで画像サイズの指定

###動作サンプル
http://spicky.net/sample1/paint/1956/

###設置について

ウェブサーバの任意の場所に nextpaint.swf を置いて、任意のウェブページに
以下のタグを記述してください。Flash対応のブラウザで閲覧すると nextpaint が
表示されます。

----------------------------------------------------------------------
```
<object type="application/x-shockwave-flash" 
 data="nextpaint.swf" width="776" height="500" >
  <param name="movie" value="nextpaint.swf" />
  <param name="FlashVars" value="imageWidth=640&imageHeight=480" />
</object>
```
----------------------------------------------------------------------


■パラメータについて

FlashVars を記述することで nextpaint にパラメータを渡すことができます。
パラメータは以下のように & 区切りで キー=値 で記述します。
```
<param name="FlashVars" value="imageWidth=640&imageHeight=480" />
```
imageWidth:
お絵かきできる画像の横サイズ

imageHeight:
お絵かきできる画像の縦サイズ

uploadurl:
画像のアップロード先のURLを記述します。URLはURLエンコードを
行った文字列を記述してください。
指定がなかった場合、サーバへ保存ボタンが無効になります。

以下の例では、画像サイズは 320×480、
画像をアップロードするURLは http://www.example.com/upload.php と
なります。

----------------------------------------------------------------------
```
<object type="application/x-shockwave-flash"
data="nextpaint.swf" width="456" height="500" >
  <param name="movie" value="nextpaint.swf" />
  <param name="FlashVars" value="imageWidth=320&imageHeight=480&uploadurl=http%3A%2F%2Fwww.example.com%2Fupload.php"
/>
</object>
```
----------------------------------------------------------------------

なお、Flash自体の縦横サイズは 画像の横サイズ + 126、画像の縦サイズ + 20 
とすると綺麗な表示になります。


■サーバへ画像保存について

サーバへ保存ボタンをクリックすると、パラメータで指定したアップロードURLに
POSTします。
以下はPHPで受信してPNGファイルを生成するサンプルです。

----------------------------------------------------------------------
```
<?php

$png = file_get_contents("php://input");

$filename = './a.png'; // a.png には書き込み権限が必要

$fp = fopen($filename, 'wb');
fwrite($fp, $png);
fclose($fp);

?>
```
----------------------------------------------------------------------

#ライセンスについて

MIT ライセンスで配布します。
再配布・修正したファイルの再配布が可能です。

MIT License
http://www.opensource.org/licenses/mit-license.php

Flashの中にある「(C) tokita」のコピーライト表示、URLの表示は
削除して構いません。


アイコンについて以下の通り
```
Fugue Icons
============================================================
Copyright (C) 2009 Yusuke Kamiyamane. All rights reserved.
The icons are licensed under a Creative Commons Attribution
3.0 license. <http://creativecommons.org/licenses/by/3.0/>
------------------------------------------------------------
If you can't or don't want to place link back, please
purchase a royalty-free license. <http://www.pinvoke.com/>
```

copyright(c)2009 Masahiko Tokita http://tokita.net/ 


