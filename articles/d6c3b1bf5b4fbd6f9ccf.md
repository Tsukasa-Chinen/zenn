---
title: "WordPress 5.5のブロックパターン（Gutenberg） が出力するHTML一覧"
emoji: "🦄"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ['wordpress', 'gutenberg', 'blockeditor', 'html', 'css']
published: true
---

![Gutenbergのロゴ画像](https://storage.googleapis.com/zenn-user-upload/j2dex2bfwfn24iqyf4dsrqopo6mb)
こんにちは。
先日[「WordPress 5.5のブロックエディター（Gutenberg） が出力するHTML一覧」](https://zenn.dev/cocomina/articles/a008986da12a7ef0682d)とゆう初めてので記事を**Zenn**で書きました（Zenn使いやすくて気に入ってます）

さて、今回は**単体ブロックではなくブロックパターンが出力するHTML一覧**を書きたいと思います。

## ブロックパターンとは?
WordPress 5.5 で搭載された、予め用意された単体のブロックの組み合わせで作られた様々なレイアウトを挿入できる新しい機能です。
::: message
単体ブロックを組み合わせてブロックパターンは作られているので出力されるHTMLは単体ブロックとほぼ同じ。文字色や背景色などの設定の可否はパターン内のブロックによって変わります。
:::

::: message alert
WordPress 5.5を対象に調べてますが今後のアップデートによっては変わってるかもしれません。
:::

# ボタン
ボタンブロックを複数組み合わせたブロックパターンです。

## 2ボタン
塗り潰しとアウトラインのボタンがデフォルトで出力されます。
**`単体のボタンブロックと違い、style属性などが予め書かれています。`**
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
**`単体のボタンブロックと違い、style属性などが予め書かれています。`**
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
# ギャラリー
**【ギャラリーブロック】** と少し違って、figure.wp-block-galleryに.alignwideが追加されている。
```html
<figure class="wp-block-gallery alignwide columns-2 is-cropped">
  <ul class="blocks-gallery-grid">
    <li class="blocks-gallery-item">
      <figure>
        <img src="https://s.w.org/images/core/5.5/don-quixote-05.jpg" alt=""/>
      　// キャプションがある場合はここにfigcaptionを出力
        <figcaption class="blocks-gallery-item__caption"> 〜 </figcaption>
      </figure>
    </li>
    <li class="blocks-gallery-item">
      <figure><img src="https://s.w.org/images/core/5.5/don-quixote-01.jpg" alt=""/></figure>
      　// キャプションがある場合はここにfigcaptionを出力
        <figcaption class="blocks-gallery-item__caption"> 〜 </figcaption>
    </li>
  </ul>
　// キャプションがある場合はここにfigcaptionを出力
  <figcaption class="blocks-gallery-caption"> 〜 </figcaption>
</figure>
```

# ヘッダー
**カバーブロックをベースにしたブロックパターンです。**
個人的にファーストビューなどに設置するのを予想しているのかインパクトが強いのが特徴的だと思います。

## 見出しを含む大きなヘッダー
**【背景画像】と【段落】** を組み合わせたHTMLを出力します。
見出しを含むとありますがデフォルトだとテキストは`p > strong` でマークアップされています。
**`カバーブロックと少し違い、CSSで予め装飾されています。`**
```html
<div class="wp-block-cover alignwide has-background-dim-20 has-background-dim is-position-center-center" style="background-image:url(https://s.w.org/images/core/5.5/don-quixote-06.jpg);background-position:40% 26%;min-height:375px">
  <div class="wp-block-cover__inner-container">
    <p class="has-text-align-center has-text-color" style="line-height:1.1;font-size:74px;color:#fffffa">
      <strong> 〜 見出しテキスト 〜 </strong>
    </p>
  </div>
</div>
```

## 見出しとボタンを含む大きなヘッダー
**【背景画像】【段落】【ボタン】【カラム】【スペーサー】** などを組み合わせたHTMLを出力します。
見出しを含むとありますがデフォルトだとテキストは`p > strong` でマークアップされています。
**`こちらもCSSで予め装飾されています。`**
```html
<div class="wp-block-cover alignwide has-background-dim has-background-gradient is-position-center-center" style="background:linear-gradient(135deg,rgb(249,72,72) 1%,rgb(179,22,22) 100%);min-height:575px">
  <div class="wp-block-cover__inner-container">
    <div class="wp-block-columns alignwide">
      <div class="wp-block-column" style="flex-basis:12%">
        <div style="height:100px" aria-hidden="true" class="wp-block-spacer"></div>
      </div>
      <div class="wp-block-column">
        <div style="height:100px" aria-hidden="true" class="wp-block-spacer"></div>
        <p class="has-text-align-left has-text-color" style="line-height:1.2;font-size:68px;color:#fffffa">
          <strong>汝は見た</strong>
          <br>
          <strong>まだ何もありません</strong>
        </p>
        <div class="wp-block-buttons">
          <div class="wp-block-button">
            <a class="wp-block-button__link has-text-color has-background" style="border-radius:3px;background-color:#fffffa;color:#00000a">今すぐ読む</a>
          </div>
        </div>
        <div style="height:100px" aria-hidden="true" class="wp-block-spacer"></div>
      </div>
      <div class="wp-block-column" style="flex-basis:12%">
        <div style="height:100px" aria-hidden="true" class="wp-block-spacer"></div>
      </div>
    </div>
  </div>
</div>
```

# テキスト

## 見出しと段落
**見出しの下に本文** といったよくあるレイアウトのブロックパターンです。
```html
<div class="wp-block-group">
  <div class="wp-block-group__inner-container">
    <h2 class="has-large-font-size">
      <span style="color:#ba0c49" class="has-inline-color">
        <strong>2</strong>.
      </span>
      <br>才知あふれる郷士ドン・キホーテの最初の旅立ち
    </h2>
    <p> 〜 本文テキスト 〜 </p>
  </div>
</div>
```

## 引用
**画像の下に引用** 本の末尾にあるような著者プロフィールみたいなレイアウト。
```html
<div class="wp-block-group">
  <div class="wp-block-group__inner-container"></div>
</div>
<div class="wp-block-group">
  <div class="wp-block-group__inner-container">
    <div class="wp-block-image is-style-rounded">
      <figure class="aligncenter size-large is-resized">
        <img loading="lazy" src="https://s.w.org/images/core/5.5/don-quixote-03.jpg" alt="" width="164" height="164"/>
      </figure>
    </div>
    <blockquote class="wp-block-quote has-text-align-center is-style-large">
      <p>「友よ、サンチョ。向こうに30だか40だかの大きな巨人が見えるか ? 私は彼らと戦い、殺すつもりだ」</p>
      <cite>— ドン・キホーテ</cite>
    </blockquote>
    <hr class="wp-block-separator is-style-dots"/>
  </div>
</div>
```

以上になります。
これらが、WordPress 5.5で追加された**ブロックパターン** になります。
当然ですが、どれもブロックを組み合わせて作られたものばかりなので、ブロックエディター の可能性を感じますね`（もうクラシックエディターには戻れない）`

今後WordPressのアップデートに伴い、パターンは増減する可能性もありますが、それに合わせてこの記事も添削していきたいと思います。



