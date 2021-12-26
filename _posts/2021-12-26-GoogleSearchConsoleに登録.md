---
title: GitHub Pages(Jeykyll)をGoogle Search Consoleに登録
layout: post
---

## 前提
私はGitHub Pagesで[Jekyll/minima](https://github.com/jekyll/minima)を利用しているので、同様な構成な方に向けた記事です。

## サイトマップを作成
jekyllのプラグインを利用してサイトマップを作成するため `_config.yml` に以下を記述。
```
plugins:
- jekyll-sitemap
```

作成されたサイトマップは以下のURLで確認できる。
```
https://{ユーザー名}.github.io/sitemap.xml
```


## gtag(Google analytics)を埋め込む
Google analyticsを仕込んでいることが前提になっているようなので、事前に設定を済ます。

私のようにGitHub Pagesで[Jekyll/minima](https://github.com/jekyll/minima)を利用している場合
`_config.yml` に以下のような記述をする。
```
google_analytics: G-WXXXXXXXXX
```

## Google Search Consoleにアクセス
[https://search.google.com/search-console](https://search.google.com/search-console)にアクセスする。

<br>

サーチコンソールのロゴ下のメニューをクリックし、開いたメニューの中から「プロパティ追加」をクリック。
![俯瞰図](https://i.gyazo.com/dce2b95d46361ad38e873d5e5e9e9291.png)

<br>

URLプレフィックスで自身のページ（`https://{ユーザー名}.github.io`）を入力。続行をクリック。
![追加画面](https://i.gyazo.com/2d834c38eedd04d1d42663f7dcc4a1c0.png)

<br>

登録直後の画面
![登録直後](https://i.gyazo.com/c3ccc8921cac92ce03d4964cc6a78e84.png)

<br>

### サイトマップを登録
左側のメニューから、「インデックス」->「サイトマップ」をクリックする
サイトマップを送信する。
![サイトマップ登録](https://i.gyazo.com/e987cfaa2328b58a5b42d9d070929f48.png)

<br>

サイトマップ送信直後は以下のようになる。
![サイトマップ送信直後](https://i.gyazo.com/eaf2aa36d0e725c9f4a01da5ef6c833f.png)

<br>

あとは待っておけばOK

## 注意
Google Analyticsタグの埋め込みなどは利用しているJeykllテーマによって異なる場合があります。自身の利用しているリモートテーマをしっかりと確認しましょう。

### 参考文献
- [https://netchira.github.io/blog/githubpages/SEOsono1.html](https://netchira.github.io/blog/githubpages/SEOsono1.html)
- [https://developers.google.com/search/docs/beginner/seo-starter-guide](https://developers.google.com/search/docs/beginner/seo-starter-guide)