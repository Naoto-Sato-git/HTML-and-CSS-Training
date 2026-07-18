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
```css
<li class="grid-item">
    <dl class="feature">
        <dt class="feature-headline">1.Great Service</dt>
        <dd class="feature-img">
            <img src="./assets/images/png/004-new-features.png" width="100" height="100" alt="Great Service">
        </dd>
        <dd class="feature-description">Text</dd>
    </dl>
</li>
```
・dlタグ：データの見出しとコンテンツを紐づける
<br>ダミーアイコン：https://www.flaticon.com/
```css
<article>
    <a href="#" class="card-link">
        <span class="card-label">New</span>
        <img class="card-image" src="https://dummyimage.com/200x100/000/fff" alt="thumbnail">
        <div class="card-info">
            <time datetime="2022-01-01" class="card-time">2022.01.01</time>
            <h1 class="card-headline">Text</h1>
            <p class="card-description">Text</p>
        </div>
    </a>
</article>
```
・articleタグ：一固まりで完結するコンテンツを作るときに使う
<br>・timeタグ：時間を表す記述の意味を理解させる。(datetimeという属性を持つ)
```html
<form class="form" action="">
    <table class="form-table">
        <tr>
            <th>Menu</th>
            <td>
                <select name="" id="">
                    <option value="menu-1">Menu 1</option>
                    <option value="menu-2">Menu 2</option>
                    <option value="menu-3">Menu 3</option>
                </select>
            </td>
        </tr>
    </table>
</form>
```
・formタグ：ボタンを押してフォームを送るようなインタラクティブな要素を扱う時に、バックエンドとの連携がしやすくなる
<br>・trタグ：table rowの略で入力1行分
<br>・thタグ：table headlineで入力の見出し
<br>・tdタグ：table dataで項目を表す
<br>・selectタグ：プルダウンメニューが出る
<br>・optionタグ：メニューの中の項目
<br>属性のvalueを設定することで、項目選択時にバックエンド側にはvalueの記述を送る
```html
<tr>
    <th>
        <label for="Name">
            Name
        </label>
    </th>
    <td>
        <input type="text" id="Name">
    </td>
</tr>
```
・inputタグ：文字を入力するフィールド
<br>labelとidを設定することで、見出しをクリックしても入力動作に移れる
```html
<tr>
    <th>Gender</th>
    <td>
        <label>
            <input type="radio" name="gender" value="male">Male
        </label>
        <label>
            <input type="radio" name="gender" value="femail">Femail
        </label>
        <label>
            <input type="radio" name="gender" value="other">Other
        </label>
    </td>
</tr>
```
inputタグのtypeをradioにすることで選択形式にできる
<br>各要素のnameをgenderに統一することで、単一選択形式にできる
<br>radioをcheckboxにすると複数選択形式の選択様式になる
```html
<textarea cols="30" rows="10"></textarea>
```
・textareaタグ：複数行入力できる
```html
<button type="submit">Submit</button>
```
・buttonタグ：押すことで何かしらのアクションを起こす
```html
<aside  class="works">
    <img src="https://dummyimage.com/150x80/ccc/fff" alt="logo">
</aside>
```
・asideタグ：メインコンテンツの補間をするために使うタグ
```html
<footer class="footer">

    <figure class="footer-map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3240.8254544793112!2d139.76255968885494!3d35.6812996!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x60188bfbd89f700b%3A0x277c49ba34ed38!2z5p2x5Lqs6aeF!5e0!3m2!1sja!2sjp!4v1784359636882!5m2!1sja!2sjp" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="strict-origin-when-cross-origin"></iframe>
    
        <figcaption class="footer-mapinfo">
            <div class="footer-maplogo">
                BugFix Inc.
            </div>
            <address class="footer-mapaddress">
                〒100-0000 東京都千代田区丸の内１－１－１<br/>
                <a href="https://maps.app.goo.gl/VgQk2zMhNMmGcVNf7" target="_blank">Google Map</a>
            </address>
        </figcaption>
    </figure>
</footer>
```
・footerタグ：フッターを作るためだけのタグ
<br>・iframeタグ：外部のWebサイトを埋め込む
```html
<hr class="footer-line" />
<small>Copyright</small>
```
・hrタグ：ラインを作ることができるタグ
<br>・smallタグ：コピーライトを作るためだけのタグ
```html
<div class="hero">
    <strong>Hello World!</strong>
    <div class="hero-particles"></div>
    <video autoplay loop muted preload>
        <source src="./assets/video/hero2.mp4" type="video/mp4">
    </video>
</div>
```
・strongタグ：強調表示(1ファイルで1,2回使うのが良い)
<br>・videoタグ：動画用タグ
<br>属性はautoplayが自動再生、loopはループ再生、mutedはミュート(消音)、preloadはHTMLが読み込まれたら即座にMP4の読み込みを開始する
```html
<nav class="header-nav">
    <ul class="header-navlist">
        <ii class="header-navitem">
            <a href="#">About</a>
        </ii>
    </ul>
</nav>
```
navタグ：主要なナビゲーションメニューを囲むタグ


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
・align-items:center：display:flexがつく要素を中央揃えにする。
```css
.card-link{
    color:#333;
    text-decoration:none;
    position: relative;
    display:block;
}
.card-label{
    position:absolute;
    left:0;
    top:0;
    background-color: #999;
    color:#fff;
    display:block;
    padding:5px 10px;
    font-size:12px;
}
```
・positionプロパティ
<br>親要素にrelative、子要素にabsoluteをつけると、relativeの中で自由に動かすことができる
```css
transition:background-color.25s;
```
・transitionプロパティ：プロパティが変化するまでの時間を設定(アニメーションを作るときに便利)
```css
.avator{
    display:flex;
    flex-direction: row-reverse;
    align-items:center;
    justify-content:start;
    padding: 10px;
}
```
・flex-direction：順番を反転させる
<br>例：htmlのdlタグでは「イメージ名⇒画像」の順に記述するのがルールだが、画像の次に名前を表示したい場合、CSS側で順番を反転する
<br>・justify-content：属性がstartなら、左寄せ
```css
.avator-image{
    margin:0;
    border-radius: 50%;
    overflow:hidden;
}
```
・border-radius：角を丸くする
<br>・overflow：border-radiusではみ出た部分を隠す(=描画しない)
```css
box-shadow: 5px 5px 0 #bbb;
```
・box-shadow：影をつける
<br>属性は(x方向にはみ出る度合い、y方向にはみ出る度合い、影の濃さ、色)
```css
label, input, textarea, select, button{
    cursor:pointer;
}
```
特定の場所(入力欄や記事の選択時)でカーソルを指にする場合は、属性をpointerにする
```css
.hero > strong{
    position: absolute;
    z-index: 2;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 120px;
    color:#fff;
    font-weight: bold;
    display: block;
    width: 100%;
    text-align: center;
}
.hero > video {
    z-index: 1;
    position: absolute;
    width: auto;
    height: 120%;
}
```
・z-index：インデックスの大きいタグが優先的に表示される。
```css
.header{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 15px;
    position: fixed;
    z-index: 10;
    top: 0;
    left: 0;
}
```
・justify-content: space-between：要素が左右の端に寄る
<br>・position: fixedで他の要素に関わらず、位置が固定される。

## その4：Java Scripts
Java Scriotsを使うなら、公開されているライブラリプラグインを使うのが良い
<br>https://github.com/VincentGarreau/particles.js/
<br>ものによるが、サーバー環境を用意して実行しないと動かないことがあるので注意

## その5：ホスティング
サーバー上にあげて、だれでも閲覧可能にすること
<br>今回はnetlifyを使う
<br>url:https://www.netlify.com/

## 補足
### 画像ファイルの形式の違い
・jpg：細かい色の表現が得意(複数種類の色を使うならjpg)
<br>・png：細かい色の表現は不得意だが、JPEGよりも軽い
<br>・gif：背景の透過とアニメーションが使えるが、画質が荒く、容量も大きい
<br>・svg：ベクターファイル(拡大縮小しても画像の解像度が一定のもの)をHTMLに変換したもの。文字情報なので軽い+Javascriotで動かせる。
<br>url:https://worldvectorlogo.com/logo/svg-6

### アイコン画像の生成サイト
url:https://realfavicongenerator.net/