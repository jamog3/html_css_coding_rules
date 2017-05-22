# HTML コーディングルール

## インデント
半角スペース2つ。タブは使用しない

```html
// Good
<ul>
  <li>
    <p>hoge</p>
  </li>
</ul>
```
```html
// Bad
<ul>
    <li>
        <p>hoge</p>
    </li>
</ul>
```

## h1タグ
各ページに必ず1つ

```html
// Good
<section>
  <h1>hoge</h1>
</section>
```
```html
// Bad
<section>
  <h1>hoge</h1>
  <section>
    <h1>huga</h1>
  </section>
</section>
```

## バリデーションチェック
HTML5のコンテンツ・モデルの仕様に沿ったコードを書くため、チェックする<br>※ 下記はほんの一例

```html
// Bad
<section>
  <h1>
    <p>hoge</p>
  </h1>
</section>

<p>
  <a href="#">
    <span>
      <a href="#">hoge</a>
    </span>
  </a>
</p>

<ul>
  <div>
    <li>hoge</li>
  </div>
</ul>
```

## headタグ
以下、サンプル

```html
<head>
  <meta charset="UTF-8">
  <title>タイトル</title>
  <meta name="description" content="概要">
  <meta name="format-detection" content="telephone=no, address=no, email=no">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <link rel="icon" href="/favicon.ico">
  <link rel="apple-touch-icon" href="/images/apple-touch-icon.png">  
  <link rel="stylesheet" href="/style.css">
</head>
```

### その他、必要に応じて下記を追加する

URLの正規化
```
<link rel="canonical" href="正規化したいURL">
```

検索結果など、次ページなどがあるコンテンツ
```
<link rel="prev" href="前のページのURL">
<link rel="next" href="次のページのURL">
```

多言語対応
```
<link rel="alternate" href="日本語ページのURL" hreflang="ja">
<link rel="alternate" href="英語ページのURL" hreflang="en">
```

Twitter
```
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@twitter">
<meta property="twitter:account_id" content="00000000000">
```

Facebook
```
<meta property="fb:admins" content="00000000000">
<meta property="fb:app_id" content="00000000000">
<meta property="article:publisher" content="http://www.facebook.com/00000000000">
<meta property="article:author" content="http://www.facebook.com/00000000000">
<meta property="og:description" content="概要">
<meta property="og:title" content="タイトル">
<meta property="og:url" content="http://hoge.com">
<meta property="og:image" content="/images/ogimage.png">
<meta property="og:type" content="website">
<meta property="og:site_name" content="hoge">
```

## タグの意味(セマンティック)を考えて使用する。SEOも意識する。

例えば、imgタグを使用する場合、その画像に意味があるかを判断。<br>もし、装飾目的の場合は、cssで背景画像として扱う。

ただし、管理画面など、検索エンジンに無縁な場合、SEOは無視してよい。
