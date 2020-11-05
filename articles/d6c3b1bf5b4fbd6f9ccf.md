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
単体ブロックを組み合わせてブロックパターンは作られているので出力されるHTMLは単体ブロックとほぼ同じです。
:::

# ■ ボタン
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