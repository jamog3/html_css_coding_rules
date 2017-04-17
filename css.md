# CSS コーディングルール

## ID、タグでcssを指定しない
classのみで指定する
```scss
// Good
.hoge {
}
```
```scss
// Bad
#hoge {
}

p {
}
```

## classについて
基本的にはBEMをベースとする<br>
参考：[BEMによるフロントエンドの設計 - 基本概念とルール | CodeGrid](https://app.codegrid.net/entry/bem-basic-1)

### B/E/Mの要素はそれぞれ、最大1回までの使用とする
```scss
// Good
.block {
}

.block__element--modifier {
}
```
```scss
// Bad
.block__element__element {
}
```

### 命名規則はlower chain case
小文字のみ、単語と単語の間にはハイフン
```scss
// Good
.cascading-style-sheets {
}
```
```scss
// Bad
.cascading_style_sheets {
}

.cascadingStyleSheets {
}
```

###タグ名をそのままclass名にしない
```scss
// Good
.text {
}
```
```scss
// Bad
.div {
}

.p {
}
```

### 単語を省略しない
```scss
// Good
.title {
}

.text {
}

.button {
}

.wrapper {
}

.inner {
}
```
```scss
// Bad
.ttl {
}

.txt {
}

.btn {
}

.wrap {
}

.inr {
}
```

### 表記ゆれを減らす
+ 押せる箇所 `link, button`など -> `link`
+ 要素を囲った箇所 `box, block`など -> `box`

などなど。。

### プロパティの順序
CSScombを使用し整形する<br>参考：[ルールはこんな感じ](https://gist.github.com/jamog3/c12e044f051b22a30e1e)

## Sass
+ `style.sass`はincludeのみの記述とする
+ BEMのBの単位でcssのファイルを分割する
+ 変数は`partial/_variables.sass`に集約する

## 色指定
+ 色は直接指定せず、名前を付けて変数にする
+ 命名規則は色名をそのまま使わず、セマンティックなものにする
+ 色のルールを事前にデザイナーなどに確認する
```scss
// Good
.hoge {
  color: $base-text;
}

```
```scss
// Bad
.hoge {
  color: #000;
  background: $white;
}
```

## 余白
+ 余白のルールを事前にデザイナーなどに確認する
++ 原則、margin-bottomで頑張る
+++ デザイン次第ではその限りではない

## メディアクエリ
+ 数値は変数で管理
+ 1ヶ所にまとめたりせず、各要素に記述していく
++ そのままだと記述量が増えるのでgulpの[css-mqpacker](https://www.npmjs.com/package/css-mqpacker)などを使い、まとめる
```scss
// Good
.hoge {
  width: 1000px;
  @media screen and (max-width: $sp-width) {
    width: 100%;
  }
}

```
```scss
// Bad
.hoge {
  width: 1000px;
}
/* ~~~ */
@media screen and (max-width: $sp-width) {
  .hoge {
    width: 100%;
  }
}
```

## ベンダープレフィックス
どの要素がどのブラウザならベンダープレフィックスなしでも動くかなんて把握してられないので、<br>可能な限り[autoprefixer](https://www.npmjs.com/package/autoprefixer)に任せる
```scss
// Good
.hoge {
  transform: scale(1);
}

```
```scss
// Bad
.hoge {
  -webkit-transform: scale(1);
  -ms-transform: scale(1);
  -o-transform: scale(1);
  transform: scale(1);
}
```

## その他のプレフィックス
### .js-hoge
+ jsで参照する場合に使用。このclass名にはcssを当てない。

### .is-hoge
+ jsやサーバ側で操作する箇所における状態の変化
+ BEMのMを使用すると汎用性が下がるため

## !important
よほどのことがない限り、使用禁止

## 値の上書き
includeやメディアクエリを使用した際に値を上書く場合、不必要な箇所まで指定しない
```scss
// Good
.hoge {
  margin: 0 100px 50px;
  @media screen and (max-width: $sp-width) {
    margin-left: auto;
    margin-right: auto;
  }
}
```
```scss
// Bad
.hoge {
  margin: 0 100px 50px;
  @media screen and (max-width: $sp-width) {
    margin: 0 auto 50px;
  }
}
```

## マルチクラス
基本的に使用禁止
```scss
// Good
.foo {
}
.bar {
}
```
```scss
// Bad
.foo .bar {
}
```



