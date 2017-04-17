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

## タグの意味(セマンティック)を考えて使用する。SEOも意識する。

例えば、imgタグを使用する場合、その画像に意味があるかを判断。<br>もし、装飾目的の場合は、cssで背景画像として扱う。

ただし、管理画面など、検索エンジンに無縁な場合、SEOは無視してよい。
