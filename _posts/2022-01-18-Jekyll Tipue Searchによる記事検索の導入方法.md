---
title: Jekyll Tipue Searchによる記事検索の導入方法
layout: post
categories: tech
---

Github Pagesで手軽にブログを作成する際に第一候補となるであろうStatic Site Generator「Jekyll」に自作ブログ内検索を手軽に導入する方法について記述します。

![完成イメージ図](https://gyazo.com/9f18a04650fb3bfaef972a88a25a00f2.png)


### 準備するもの
- すでに公開設定などを済ませたJekyll製ブログ
### 手順
1. 以下に示すソースコード（./assets）をダウンロードします。

[ソースコード(d4b5df7).zip](https://github.com/jekylltools/jekyll-tipue-search/archive/refs/heads/master.zip)

>[公式GitHubリポジトリ](https://github.com/jekylltools/jekyll-tipue-search)は2017年8月23日より新規コミットがないので、以下に直接zipのリンクを掲載しています。

<br>

2. 解凍し、自身のブログのソースコードにassetsフォルダの中身を丸ごとコピーします。

![image1](https://i.gyazo.com/e8456b0e9178d920970dcc32c088b62a.png)
![image2](https://i.gyazo.com/b1c5d6ca798cf6851b5b17db17b09e8e.png)

3. 利用しているテーマでheadタグを規定している部分に以下のソースコードを追記する。
   - 筆者の環境だと[minima](https://github.com/jekyll/minima)を利用しているので、`_includes/custom-head.html`が本手順の作業対象になります。


```html
{% if page.tipue_search_active or layout.tipue_search_active %}
<link rel="stylesheet" href="{{ "/assets/tipuesearch/css/normalize.css" | relative_url }}">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script src="{{ "/assets/tipuesearch/tipuesearch_content.js" | relative_url }}"></script>
<link rel="stylesheet" href="{{ "/assets/tipuesearch/css/tipuesearch.css" | relative_url }}">
<script src="{{ "/assets/tipuesearch/tipuesearch_set.js" | relative_url }}"></script>
<script src="{{ "/assets/tipuesearch/tipuesearch.min.js" | relative_url }}"></script>
{% endif %}
```
![image3](https://i.gyazo.com/a75a11a735f7db802a1f1eaccabebad3.png)

4. 以下に示すコードを`search.html`としてコピペし、画像のように配置します。
   - [minima](https://github.com/jekyll/minima)であれば、統一感を持たせるためにファイル名`search.md`とするのが綺麗な気がするので、私は`search.md`としています。

```html
---
title: Search
description: "Search this site"
layout: page
permalink: /search
tipue_search_active: true
exclude_from_search: true
---

<form action="{{ page.url | relative_url }}" class="tipue_form">
  <div class="tipue_search_left"><img src="{{ "/assets/tipuesearch/search.png" | relative_url }}" class="tipue_search_icon"></div>
  <div class="tipue_search_right"><input type="text" name="q" id="tipue_search_input" pattern=".{3,}" title="At least 3 characters" required></div>
  <div style="clear: both;"></div>
</form>

<div id="tipue_search_content"></div>

<script>
$(document).ready(function() {
  $('#tipue_search_input').tipuesearch();
});
</script>
```
![image4](https://gyazo.com/e83c01861fea2707147a8970e8f31784.png)


5. あとは`_config.yml`をいじるなりしてヘッダー部分にパーマリンクを設置したり、CSSを少し変えてみたり、ビルド、デプロイをすれば完了です。
   - よろしければ[筆者の公開リポジトリ](https://github.com/ikmnjrd/ikmnjrd.github.io)を参考にしてみてください。

完成です。

![完成](https://i.gyazo.com/82a80325376d64d4e4560fc0b924881f.png)