---
title: Neumorphismサンプル
layout: post
---

## Sandbox



## ポイント

### SVG化した文字に陰影をつける

cssではこのようにすると綺麗に抜ける。
```css
svg {
  filter: drop-shadow(3px 3px 3px #fff)
    drop-shadow(-3px -3px 1px rgba(0, 0, 0, 0.15));
}
```
html上では、適宜fillやstrokeを設定する。

[https://danmarshall.github.io/google-font-to-svg-path/](https://danmarshall.github.io/google-font-to-svg-path/)（[GitHubリポジトリ](https://github.com/danmarshall/google-font-to-svg-path)）を使って文字を事前にSVG化しておく。

npmパッケージで似たものを提供している人もいる[https://github.com/shrhdk/text-to-svg](https://github.com/shrhdk/text-to-svg)