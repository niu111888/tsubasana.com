# tsubasana.com

大原翼の個人サイト（日本語・英語・中国語対応）。GitHub Pages でホスティングしています。

- 公開URL: https://tsubasana.com
- リポジトリ: https://github.com/niu111888/tsubasana.com
- `main` ブランチにプッシュすると1〜2分で自動公開されます

## しくみ

- `index.html` / `style.css` — サイト本体（1ページ構成、3言語切り替え）
- `content/ja.json` / `en.json` / `zh.json` — 各言語の文章。ここを書き換えるとサイトの文章が変わります
- `content/site.json` — メール・SNSリンク、ピアノ動画、旅の写真の設定
- `assets/` — 写真や動画のアップロード先
- `.pages.yml` — CMS（Pages CMS）の管理画面設定

## ✏️ ふだんの編集（CMS — どのPC・スマホからでもOK）

コードやこのフォルダは不要です。ブラウザだけで編集できます。

1. <https://app.pagescms.org> を開く
2. **Sign in with GitHub** でログイン（`niu111888` アカウント）
3. 初回のみ：Pages CMS のGitHubアプリをインストール（対象は `tsubasana.com` リポジトリだけでOK）
4. リポジトリ `tsubasana.com` を開き、左メニューから編集
   - **サイト設定（動画・写真・連絡先）** — ピアノ動画のYouTube URL、旅の写真、メール・Instagram・X
   - **文章（日本語）／（英語）／（中文）** — キャッチコピーから資格まで全文章
5. 保存＝自動コミット。1〜2分でサイトに反映されます

### よくある編集
- **ピアノ動画を載せる** — サイト設定 →「ピアノ動画」→ YouTubeのURLを貼るだけ
- **旅の写真を追加** — サイト設定 →「旅の写真」→ 写真をアップロード＋キャプション入力
- **連絡先を設定** — メール / Instagram / X を入力（空欄のボタンは自動で非表示）

## 💻 別のパソコンで作業する（デザイン・コードを触る場合）

必要なもの: `git`（macOSなら最初から入っています）。プッシュするなら GitHub CLI（`gh`）か GitHub へのログイン。

```bash
# 1. プロジェクトを取得（このフォルダをコピーしてもOK）
git clone https://github.com/niu111888/tsubasana.com.git kojinn
cd kojinn

# 2. ローカルで表示確認（ビルド不要）
python3 -m http.server 8642
# → ブラウザで http://localhost:8642 を開く

# 3. 変更を公開
git add -A && git commit -m "変更内容" && git push
```

## 🌐 ドメイン設定メモ（お名前.com）

- ネームサーバー: `01.dnsv.jp` 〜 `04.dnsv.jp`（お名前.comのDNSレコード設定用）
- DNSレコード: Aレコード4件（`185.199.108.153` 〜 `185.199.111.153`）＋ `www` CNAME → `niu111888.github.io`
- SSL証明書はGitHubが自動発行・自動更新（無料）
