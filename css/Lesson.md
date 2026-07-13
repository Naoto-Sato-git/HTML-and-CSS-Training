# CSSの基礎について
## ➀ CSSの記法(3種類)
### スタイルタグを使う
```html
<style>
    body {
        background-color: red;
    }
</style>
```
htmlタグであるstyleタグの中にCSSを書く記法。
<br>フレームワークによっては使うこともあるが、一般的には使われない。

### インラインCSS
```html
<p style="color:red; font-weight:bold;">Text</p>
```
styleをインラインで定義して使う方法。
<br>この記法もほぼ使わない。

### リンクタグを使ってCSSファイルを読み込む
```html
<link rel="stylesheet" href="./style.css">
```
最も一般的な記法

## ➁ CSSのルール
基本的にCSSはセレクター、プロパティ、プロパティの値で構成されている。
```css
p {
    color: red;
}
```
・セレクター：どのHTMLに対してCSSを当てるか(例:p)
<br>・プロパティと値：たくさんの種類がある。(例:color:red (redが値))

## ➂ プロパティの紹介
```css
div {margin-bottom: 200px;}
```
間隔を設定するプロパティ
<br>margin-leftやright、topもある
```css
p {
    color: red;
    background-color: skyblue;
    font-weight: bold;
    font-size: 80px;
}
```
色、背景色、文字の書式と大きさを決定するプロパティ
```css
div {
    width: 100px;
    height: 100px;
    background-color: orange;
}
```
縦幅、横幅を調整できる
<br>プロパティ一覧：https://www.tagindex.com/stylesheet/properties/
<br>16進数カラーコード：https://www.colordic.org/
```css
width: calc(100% - 50px);
```
calc関数:値が違うもの同士で演算できる(%とpxなど)
```css
background-image: url("./png/haikei.png");
```
url関数：urlの画像が表示される。
```css
transform: translate(-100px, 30px);
```
translate関数：X軸とY軸を指定して要素を動かす。
<br>transform：関数を設定して要素を変化させるプロパティ。
```css
transform: translate(-100px, 30px) rotate(45deg) skew(70deg);
```
rotate関数：要素を回転させる関数
<br>skew関数：要素をゆがめる関数
<br>このように、プロパティには数字だけでなく、関数も入れることができる。

## ➃ セレクタの紹介
・id/classセレクタ
<br>1つのファイルでidは1度だけ、classは複数回使える。
<br>要素のラベル付けのような機能

### 疑似セレクタ
```css
a:hover {
    color: red;
}
```
・:hover
<br>マウスカーソルをのせた時だけスタイルをあてる

### 子セレクタ/子孫セレクタ
親セレクタの中に入っているセレクタ
```css
.parent p{
    color:red;
}
```
parentクラスにネストされてるpタグだけに割り当てられる状態。
```css
.parent > p{
    color:green;
}
```
親セレクタの直下にある子セレクタにのみ反映される。

## ➄ まとめて編集
```html
<div class="abc">Text</div>
<div class="def xyz">Text</div>
<div class="def">Text</div>
```
```css
.abc,
.def {
    width:30px;
    height:30px;
    background-color:#000;
    margin:10px;
}

.def.xyz{
    background-color:green;
}

div.def{
    background-color:red;
}
```
「クラス,クラス」で複数クラスを同時に編集
<br>「.クラス.クラス」で特定のクラスの子クラスのみに適用
<br>「セレクタ.クラス」でセレクタに属するクラスにのみ適用
```css
.def + a{
    font-size:30px;
}
```
defクラスの要素の次にaセレクタがある場合に適用