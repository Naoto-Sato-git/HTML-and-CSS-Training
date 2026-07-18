# Webサイト作成手順のメモ
## その1：ファイルとフォルダの作成
index.html:Webサイトの骨組みを書くファイル
<br>assetsフォルダ:
<br> - cssフォルダ:CSSファイルを格納するフォルダ
<br> -- sanitize.css:初期設定の平地化
<br> -- style.css:Webサイトの見た目をいじるファイル
<br> - imagesフォルダ:画像関係
<br> - jsフォルダ:JavaScripts関連
<br> -- app.js:
<br> - videosフォルダ:映像関連

## その2：動作確認と設定
CSSファイルとHTMLファイルをリンクさせる
```html
<link rel="stylesheet" href="./assets/css/sanitize.css">
<link rel="stylesheet" href="./assets/css/style.css">
```
javaScriptsはスタイルに直接影響しないのでbodyの最後(読み込みの優先度が低い)
```html
<body>
    
    <p>Hello World</p>

    <script src="./assets/js/script.js"></script>
</body>
```
CSSファイルにも簡単な指示を書いて実行
```css
@charset "utf-8";

p{
    color:red;
}
```
問題なく動作したら、フォントを決定する
<br>https://fonts.google.com/?preview.layout=grid

## その3：作り始める
### 使うタグ
```html
<figure>
    <img src="" alt="">
    <figcaption>
        <h2>What can we do?</h2>
        <p>
            text
        </p>
    </figcaption>
</figure>
```
・figureタグ：画像とそれを説明するためのタグ
<br>imgタグの部分で画像や図、ソースコードなどを入れる
<br>画像が表示されなかった場合に、代わりのテキストを表示するのがalt属性
<br>widthとheightで画像の横幅と高さを設定することも可能
<br>・figcaptionタグ：図・画像の説明のテキストを入れておく部分
<br>ダミー画像：https://dummyimage.com/
・dlタグ：データの見出しとコンテンツを紐づける
<br>ダミーアイコン：https://www.flaticon.com/

### 使うプロパティ
```css
.about{
    margin:0;
    display: flex;
}
```
・display:flexプロパティ：特定のタグの子要素を横並びにできる
<br>チートシート：https://www.webcreatorbox.com/blog/css-flexbox-cheat-sheet
```css
.grid{
    margin:0;
    padding:0;
    display:flex;
    align-items:center;
    justify-content:center;
}
```
・slign-items:center：display:flexがつく要素を中央揃えにする。