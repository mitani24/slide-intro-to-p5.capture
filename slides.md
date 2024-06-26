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

# 開発のきっかけ

- 自分自身が p5.js ユーザー
- 作品を SNS にアップするには動画化 (e.g. mp4, gif, webm) が必要
- 品質・手軽さ・汎用性を両立する方法が存在しなかった

<div m="t-4">

| 従来の録画方法                    | 品質 | 手軽さ | 汎用性 |
| ------------------------------ |:------:|:----:|:------:|
| 画面収録ツール                 |   ✕    |  ◯   |   ◯    |
| 画像出力してから ffmpeg で結合 |   ◯    |  ✕   |   ◯    |
| 既存ライブラリ                 |   ◯    |  ◯   |   ✕    |

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

# コンセプト

「超簡単」に「多様なフォーマット」で「フレームレートを落とすことなく」録画できる

- 品質
  - `draw` 関数にフックしてレンダリングされたフレームを記録するため FrameRate-safe
- 手軽さ
  - GUI を提供しスクリプトを読み込むだけで録画機能を追加できる
  - 別途 API も提供しているためコードでも制御できる
- 汎用性
  - 多様なフォーマットを共通の API で使える
  - <img src="/format.png" alt="format table" class="w-96 rounded shadow" />

---

# 反響

- X や Discord で国内外の p5.js ユーザーからポジティブな反応を多数観測
  - 👦 < めっちゃ便利やん！
  - 👧 < 他の人にも勧めるわ！
- GitHub Stars: 🌟200+
  - <img src="https://api.star-history.com/svg?repos=tapioca24/p5.capture" alt="Star History Chart" class="w-80 rounded shadow" />
- [p5js.org](https://p5js.org/) の Libraries セクションに掲載
- 海外のおじさんが寄付くれた

---

# 苦労した点

## 実装の試行錯誤

- [MediaRecorder](https://developer.mozilla.org/ja/docs/Web/API/MediaRecorder) API は FrameRate-safe にできなかった
- ブラウザで使える mp4 エンコーダの実装が少ない

## 設計の試行錯誤

- フォーマットごとに存在する複数のレコーダーを統一的に扱うためのクラス設計
- 録画の状態管理と UI を破綻なく更新する仕組み

## その他

- ドキュメントを作り込む
- リリース後の Issue, PullRequest 対応

<style>
h2 {
  @apply mt-6! mb-2 text-2xl
}
</style>

---

# 開発を通じて感じたこと

- インターネットは価値を届けられる範囲に制限がなくて偉大
- 提供価値を端的に伝えること（つまりコンセプト）がすごく大事
- ユーザーの課題をエレガントに解決することも大事
- 洗練されている感を演出すると人にオススメしたくなる（たぶん）
- 英語得意じゃなくても割となんとかなる
  - [DeepL](https://www.deepl.com/) に頼れば基本問題なかった
- たまに変なユーザーもいるのでヒラリとかわす勇気
- この市場規模だと特に金銭的なメリットはない
- ライブラリ開発は様々な技術を学べる
  - e.g. リサーチ, 設計, テスト, ドキュメンテーション, コミュニティとの関わり
- 情けは人の為ならず
