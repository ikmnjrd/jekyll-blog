# README
## 概要
GitHub Pages(jekyll)をズボラに利用したブログです。
ローカルでの環境構築はせずにポイポイと.mdを投げていく。


## 利用しているもの
* jekyllリモートテーマ[minima](https://github.com/jekyll/minima)
* [Jekyll Tipue Search](https://github.com/jekylltools/jekyll-tipue-search)


## 運用
`/_posts/` マークダウン形式で記事を格納

`/_includes/` オリジナルテーマのhtmlをオーバーライドしたい時に適宜使用

`_draft` 下書きの記事の接頭辞

### 記事内で画像を使う
スクリーンショット的なものであればGyazoを利用する。
1. gyazoでスクリーショットを撮影。自動的にブラウザが開く
2. アドレスバーの`https://gyazo.com/XXXX`をコピー
3. `https://i.gyazo.com/XXXX.png`を記事中に指定

### 記事のfront matter
以下のようにカテゴリーを設定する場合はtech、もしくはideaを設定する。
Zennに移行しやすいように合わせている。[参考](https://zenn.dev/tech-or-idea)
```
---
title: Macでオンライン会議を文字起こし
layout: post
---
```