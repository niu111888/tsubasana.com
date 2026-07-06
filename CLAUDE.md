# tsubasana.com — 大原翼の個人サイト

3言語対応（日本語・英語・中国語）の1ページ静的サイト。ビルド不要（素のHTML/CSS/JS）。

## 構成

| ファイル | 役割 |
|---|---|
| `index.html` | サイト本体。文章は `data-i18n` 属性 + `content/*.json` から動的に読み込み（HTML内の日本語はフォールバック） |
| `style.css` | ライラック配色・明朝/セリフ体・アニメーション多め |
| `content/ja.json` `en.json` `zh.json` | 各言語の全文章（キーは3ファイル完全一致必須） |
| `content/site.json` | メール・SNSリンク、ピアノ動画（YouTube URL or mp4）、旅の写真リスト |
| `.pages.yml` | Pages CMS（app.pagescms.org）の管理画面定義 |
| `assets/` | CMSからアップロードされる画像・動画の置き場 |

## デプロイ

- GitHub リポジトリ: `niu111888/tsubasana.com`（アカウント: niu111888）
- `main` に push → GitHub Pages が自動公開（1〜2分）
- 独自ドメイン: `tsubasana.com`（お名前.comで取得、ネームサーバー 01〜04.dnsv.jp、AレコードでGitHub Pagesに向けている。`CNAME` ファイルがカスタムドメイン設定）

## コンテンツ更新の流れ（コードを触らない編集）

https://app.pagescms.org に GitHub（niu111888）でログイン → リポジトリを選ぶ → 日本語ラベルのフォームで編集 → 保存＝自動コミット → サイトに自動反映。どのPC・スマホのブラウザからでも可能（ローカル環境不要）。

## ローカルプレビュー

```
python3 -m http.server 8642
```
（`.claude/launch.json` に `site` として定義済み。fetch を使うので file:// では動かない）

## 変更時のルール

- **個人情報は載せない**: 電話・住所・生年月日・勤務先の社名・具体的な運用金額はサイトに書かない（本人の希望）
- **文章キーを追加するときは4点セット**: `index.html` の `data-i18n` + `ja.json` + `en.json` + `zh.json` + `.pages.yml` のフィールド定義を必ず揃える
- CMS入力値は `safeHtml()` でエスケープされる。HTMLタグは `<br>`（と `<br class="sp-only">`）のみ許可
- `@media (prefers-reduced-motion: reduce)` ブロックは **style.css の末尾に置く**（同詳細度のベースルールに勝つため。移動させないこと）
- 検証は `python3 -m http.server` + ブラウザで。プレビュー環境によっては IntersectionObserver の発火がスクリーンショット時のみになるが実ブラウザでは正常
