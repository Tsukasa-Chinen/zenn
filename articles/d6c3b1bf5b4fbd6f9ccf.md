---
title: "WordPress 5.5のブロックパターン（Gutenberg） が出力するHTML一覧"
emoji: "🕌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ['wordpress', 'gutenberg', 'blockeditor', 'html', 'css']
published: false
---

先日[「WordPress 5.5のブロックエディター（Gutenberg） が出力するHTML一覧」](https://zenn.dev/cocomina/articles/a008986da12a7ef0682d)とゆう記事を書きました。
今度は**単体ブロックではなくブロックパターンが出力するHTML一覧**を記載したいと思います。

## ブロックパターンとは?
WordPress 5.5 で搭載された、単体のブロックの組み合わせを挿入できる新しい機能です。
::: message
単体ブロックを組み合わせてブロックパターンは作られているので出力されるHTMLは単体ブロックとほぼ同じ。
また、文字色や背景色などの設定の可否は内包するブロックに依存します。
:::

# ボタン
ボタンブロックを複数組み合わせたブロックパターンです。

## 2ボタン
塗り潰しとアウトラインのボタンがデフォルトで出力されます。
単体のボタンブロックと違い、style属性などが予め書かれています。
```html
<div class="wp-block-buttons aligncenter">
  <div class="wp-block-button">
    <a class="wp-block-button__link has-text-color has-background" style="border-radius:2px;background-color:#ba0c49;color:#fffffa">塗り潰しボタン</a>
  </div>
  <div class="wp-block-button is-style-outline">
    <a class="wp-block-button__link has-text-color" style="border-radius:2px;color:#ba0c49">アウトラインボタン</a>
  </div>
</div>
```

## 3つのボタン
2ボタンと違い、大きい角丸で背景がグラデーションのボタンが3つ出力されます。
こちらも単体のボタンブロックと違い、style属性などが予め書かれています。
```html
<div class="wp-block-buttons aligncenter">
  <div class="wp-block-button">
    <a class="wp-block-button__link has-text-color has-background" style="border-radius:50px;background:linear-gradient(135deg,rgb(135,9,53) 0%,rgb(179,22,22) 100%);color:#fffffa">セルバンテスについて</a>
  </div>
  <div class="wp-block-button">
    <a class="wp-block-button__link has-text-color has-background" style="border-radius:50px;background:linear-gradient(317deg,rgb(135,9,53) 0%,rgb(179,22,22) 100%);color:#fffffa">お問い合わせ</a>
  </div>
  <div class="wp-block-button">
    <a class="wp-block-button__link has-text-color has-background" style="border-radius:50px;background:linear-gradient(42deg,rgb(135,9,53) 0%,rgb(179,22,22) 100%);color:#fffffa">書名</a>
  </div>
</div>
```
# カラム
カラムブロックを複数組み合わせたブロックパターンです。

## 2カラムのテキスト
**【見出し】と【段落】** を組み合わせたカラムを2つ出力します。
**`カラムブロックと少し違い、「div.wp-block-group」で全体をラップしています。`**
```html
<div class="wp-block-group">
  <div class="wp-block-group__inner-container">
    <h2 class="has-text-color" style="font-size:38px;color:#ba0c49"> 〜 見出しテキスト 〜 </h2>
    <div class="wp-block-columns">
      <div class="wp-block-column">
        <p style="font-size:18px"> 〜 本文 〜</p>
      </div>
      <div class="wp-block-column">
        <p style="font-size:18px"> 〜 本文 〜</p>
      </div>
    </div>
  </div>
</div>
```

## 画像を含む2カラムのテキスト
**【画像】と【段落】** を組み合わせたカラムを2つ出力します。
**`カラムブロックと少し違い、「div.wp-block-group」で全体をラップしています。`**
```html
<div class="wp-block-group">
  <div class="wp-block-group__inner-container">
    <div class="wp-block-columns">
      <div class="wp-block-column">
        <figure class="wp-block-image size-large">
          <img src="https://s.w.org/images/core/5.5/don-quixote-02.jpg" alt=""/>
        </figure>
        <p style="font-size:18px"> 〜 本文 〜</p>
      </div>
      <div class="wp-block-column">
        <figure class="wp-block-image size-large">
          <img src="https://s.w.org/images/core/5.5/don-quixote-04.jpg" alt=""/>
        </figure>
        <p style="font-size:18px"> 〜 本文 〜</p>
      </div>
    </div>
  </div>
</div>
```

## ボタンを含む3カラムのテキスト
**【ボタン】と【段落】** を組み合わせたカラムを3つ出力します。
**`カラムブロックと少し違い、「div.wp-block-group.alignwide」で全体をラップしています。`**
```html
<div class="wp-block-group alignwide">
  <div class="wp-block-group__inner-container">
    <div class="wp-block-columns alignwide">
      <div class="wp-block-column">
        <p>〜 1カラム目のテキスト 〜</p>
        <div class="wp-block-buttons">
          <div class="wp-block-button is-style-outline">
            <a class="wp-block-button__link has-text-color" style="border-radius:50px;color:#ba0c49">〜 ボタン 1 〜</a>
          </div>
        </div>
      </div>
      <div class="wp-block-column">
        <p>〜 2カラム目のテキスト 〜</p>
        <div class="wp-block-buttons">
          <div class="wp-block-button is-style-outline">
            <a class="wp-block-button__link has-text-color" style="border-radius:50px;color:#ba0c49">〜 ボタン 2 〜</a>
          </div>
        </div>
      </div>
      <div class="wp-block-column">
        <p>〜 3カラム目のテキスト 〜</p>
        <div class="wp-block-buttons">
          <div class="wp-block-button is-style-outline">
            <a class="wp-block-button__link has-text-color" style="border-radius:50px;color:#ba0c49">〜 ボタン 3 〜</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```
