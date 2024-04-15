---
theme: seriph
background: https://cover.sli.dev
title: p5.js の作品を録画するライブラリを作った話
class: text-center
highlighter: shiki
transition: slide-left
mdc: true
export:
  dark: true
---

# p5.js の作品を録画するライブラリを作った話

2024-04-25 社内 LT 大会

<p class="absolute bottom-10 right-10 font-700">
  mitani24
</p>

---

# [p5.js](https://p5js.org/) とは

- クリエイティブコーディングのための JavaScript ライブラリ
- プログラムを使ったビジュアルアートを簡単に制作できる

<iframe m="t-4" height="350" style="width: 100%;" scrolling="no" title="simple p5.js sketch" src="https://codepen.io/tapioca24/embed/jORpPwY?default-tab=js%2Cresult&editable=true&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/tapioca24/pen/jORpPwY">
  simple p5.js sketch</a> by tapioca24 (<a href="https://codepen.io/tapioca24">@tapioca24</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

# [p5.js](https://p5js.org/) とは

[OpenProcessing](https://openprocessing.org/) 等でいろいろなクリエイターの作品が公開されている

![openprocessing](openprocessing.png)

---

# なぜライブラリを作ろうと思ったか

- 自分自身が p5.js ユーザー
- 作品を YouTube, X, Instagram 等でシェアするには動画化 (e.g. mp4, gif, webm) が必要
- 手軽さ・品質・汎用性を両立する方法が存在しなかった
- 最初は「自分のため」に開発していたが途中から「みんなのため」へピボットした

<div m="t-4">

| 録画方法                       | 手軽さ | 品質 | 汎用性 |
| ------------------------------ |:------:|:----:|:------:|
| 画面収録ツール                 |   ◯    |  ✕   |   ◯    |
| 画像出力してから ffmpeg で結合 |   ✕    |  ◯   |   ◯    |
| 既存ライブラリ                 |   △    |  ◯   |   ✕    |

</div>

---
layout: fact
---

# [p5.capture](https://github.com/tapioca24/p5.capture) 爆誕


---

# Demo

<iframe height="420" style="width: 100%;" scrolling="no" title="simple p5.js sketch rec" src="https://codepen.io/tapioca24/embed/abxjdJV?default-tab=js%2Cresult&editable=true&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/tapioca24/pen/abxjdJV">
  simple p5.js sketch rec</a> by tapioca24 (<a href="https://codepen.io/tapioca24">@tapioca24</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

# 特長

- 手軽さ
  - GUI を提供しスクリプトを読み込むだけで録画機能を追加できる
- 品質
  - `draw` 関数にフックしてレンダリングされたフレームを記録するため FrameRate-safe
- 汎用性
  - 多様なフォーマットを共通の API で使える
  - ![format](format.png){width=340px}

---

# 反響

- X や Discord で国内外のユーザーから好意的な反応を多数観測
  - 👦 < めっちゃ便利やん！
  - 👧 < わいクリエイティブコーディングの講師やねんけど生徒に勧めるわ！
- GitHub Stars: 198
  - ![Star History Chart](https://api.star-history.com/svg?repos=tapioca24/p5.capture){width=350px}
- [p5js.org](https://p5js.org/) の Libraries セクションに掲載
- 海外のおじさんが寄付くれた

---

# 苦労した点

- 実装の試行錯誤
  - [MediaRecorder](https://developer.mozilla.org/ja/docs/Web/API/MediaRecorder) API は FrameRate-safe にならなかった
  - ブラウザで使える mp4 エンコーダの実装が少ない
- 設計の試行錯誤
  - 異なるフォーマットを統一的に扱うためのクラス設計
  - 録画の状態管理と UI を破綻なく更新する仕組み
- 型定義のないライブラリ
- README の体裁を整える
- リリース後の Issue, PullRequest, DM 対応

---

# 開発を通じて学んだこと

- ニッチな分野は課題がたくさん
  - 小さいライブラリでも解決できる
- 最初から完璧なものはできない
  - 試行錯誤・改善を繰り返す
- 課題に対して筋の良い解を提示できればちゃんと価値を届けられる
  - インターネットの恩恵は偉大
- ライブラリ開発は様々な技術を学べる
  - 設計
  - テスト
  - ドキュメンテーション
  - コミュニティとの関わり
- 「自分のため」をはみ出して「人のため」を目指すのは意外と割に合う
