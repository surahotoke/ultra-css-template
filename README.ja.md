# ultra-css-template

[English version here](README.md)

最新の CSS 機能だけでロジックを組む作品集・テンプレート。JS は index.html の onload 1行のみ（コンポーネントの読み込みと複製のためのローダ）で、コンポーネントのロジック——状態管理・データ取得・描画——はすべて CSS が担う。

**Live demo:** https://ultra-css-template.surahotoke.workers.dev/

## 動作環境
デスクトップ版の最新 Chrome 前提（Chrome 150+ 推奨）。iPhone の Chrome は WebKit ベースのため非対応。`@function` / `if()` / `::column::scroll-marker` / Anchor Positioning / `text-fit` / scroll-triggered animations（`timeline-trigger` / `animation-trigger`）など、出荷直後の機能を積極的に使用している。

## コンポーネント（components/）

| コンポーネント | 説明 |
| --- | --- |
| api-source | css-api の SVG レスポンスを scroll-timeline 化する受信機 |
| column-generator-demo | column-generator 機構のカスタマイズ例 |
| dice-cube | スクロールで回転する 3D サイコロ |
| digital-clock | css-api の時刻を受信して進み続けるデジタル時計 |
| duplicator-slot | enter キーで要素を複製できる入力スロット |
| function-render | `@function` で定義した数式のグラフ描画 |
| macbook-keyboard | counter-style だけで組んだ MacBook キーボード |
| offset-colorful-css | offset-path 上の粒子が「CSS」の字を描くロゴ演出（画面内に入ると発火） |
| todo-item / todo-list | フィルター付き TODO リスト |
| weather-display | css-api の天気データを受信して表示 |

## ライブラリ（lib/）

- **api-getter** — css-api が SVG の寸法にエンコードした値を、scroll-timeline とアニメーションだけでデコードする機構。HTTP ステータスの取得（`--api-status()`）や成否分岐（`--api-ok()`）も CSS 関数で提供
- **column-generator** — `columns` と `::column::scroll-marker` を使い、1 つの要素から大量の描画要素を生成する機構。mapping / navigate の各モードで、要素へのインデックス・クラス・ロール付与や 2 次元配置に対応
- **duplicator-layout** — contenteditable 領域内で duplicator-slot を複製起点として機能させるためのレイアウト機構

## 埋め込み（embeds/）

- **comment** — css-api と連携した掲示板 UI。フォーム POST・名前変更（Popover + Anchor Positioning）・一覧表示（SVG-as-img）

## 構成

```
components/  Web Components として読み込まれる HTML（<style> + マークアップ）
lib/         コンポーネント横断で使う CSS 機構
property/    @property 登録（アニメーション対象のカスタムプロパティ）
embeds/      iframe 埋め込み用の独立ページ
utility.css  汎用 CSS 関数（--random, --get-bit など）
```

## JS なし版（no-js.html）

`index.html` は onload 1行のローダで各コンポーネントを fetch し shadow root に流し込む方式だが、`no-js.html` はその展開後の状態を丸ごと静的に書き出した版。各コンポーネントの shadow root を `<template shadowrootmode="open">`（Declarative Shadow DOM）としてインラインに展開しているため、JS を一切使わず動作する——ブラウザで JavaScript を無効化しても動く。

**Live demo (no-JS):** https://ultra-css-template.surahotoke.workers.dev/no-js

ローダがない分、それに依存する機能は調整・除外している。`count` による複製が使えないため `offset-colorful-css` は粒子の `<div>` を10個手書きし、`todo-list` はカスタム要素の正規登録が必須なため除外している。

## 関連

- [css-api](https://github.com/surahotoke/css-api) — このテンプレートが利用するデータ供給 API

## License
MIT
