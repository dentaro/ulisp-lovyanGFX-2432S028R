# ulisp-lovyanGFX-2432S028R
ulisp-lovyanGFX-2432S028R


https://lang-ship.com/blog/work/esp32-2432s028r-1/

こちらで紹介されているデバイス（2.8インチタッチパネル付きESP32-2432S028R）で、

uLisp（マイクロLisp)を遊ぶためのArduinoスケッチです。

2432S028R.hのピンアサイン設定を変えればM5stackなどでも動くと思います。


使い方

別途LovyanGFXライブラリが必要です。

普通にArduinoでコンパイルする。

シリアルを9600で繋ぐ

Arduinoのシリアルで以下を送る（NewLineモードで）

●uLisp（マイクロLisp)

まずdefunで利用する関数名と実行関数を登録する（１、２）

１、RGB計算関数

(defun rgb (r g b)
  (logior (ash (logand r #xf8) 8) (ash (logand g #xfc) 3) (ash b -3)))

２、描画関数plot（中で1の関数を使っている）

(defun plot ()
(draw-rect 0 0 100 100 (rgb 0 255 0))
)

３、実行する(2で登録したplotが実行される、rgbのように引数が必要な時もある）

(plot)

４、2のplot部分を色々と書き換えて楽しむ。サンプルはこちらの本家サイトにあります。

http://www.ulisp.com/show?2YRM

以上です！

--
・コード内容の覚えがきを書いておきます。
12行目～
コンパイルオプションです。
使いたい機能のコメントアウトを外して下さい。、

// #define resetautorun
 #define printfreespace//プリント関連？
// #define printgcs
// #define sdcardsupport //SDカード //http://www.ulisp.com/show?207M
 #define gfxsupport    //LovyanGFX
// #define lisplibrary
// #define lineeditor
// #define vt100
