# toru1231.tamulab.jp

プレーリーカードのリンク先として公開する、田村 とおる (Toru TAMURA) のプロフィールページ。

公開URL: https://toru1231.tamulab.jp

## ファイル構成

| ファイル | 役割 |
|---|---|
| `index.html` | プロフィール本体（HTML マークアップ） |
| `css/style.css` | プロフィールページのスタイル定義 |
| `image/favicon.png` | サイトの favicon / apple-touch-icon（180×180 PNG） |
| `image/tamulab.png` | プロフィール用 tamulab.jp アイコン（240×240 PNG） |
| `image/facebook.jpg` | プロフィール用 Facebook 写真（240×240 JPEG） |
| `image/ogp.jpg` | OGP（SNS プレビュー）用カバー画像（851×315 JPEG） |
| `CNAME` | GitHub Pages のカスタムドメイン設定（`toru1231.tamulab.jp`） |
| `.nojekyll` | GitHub Pages の Jekyll 処理を無効化（プレーン HTML をそのまま配信） |
| `README.md` | 本ファイル |

## ローカル確認

```sh
cd toru1231.tamulab.jp
python3 -m http.server 8000
# → http://localhost:8000 をブラウザで開く
```

スマートフォン幅（DevTools で 375px 程度）でレイアウトが崩れていないか、ダークモードでも読みやすいかも確認推奨。

## GitHub Pages へのデプロイ

1. **リポジトリを作成**: GitHub で `torut.github.io` という名前のリポジトリを新規作成（ユーザーサイト方式が手軽）

2. **初回プッシュ**:
   ```sh
   git init
   git add .
   git commit -m "Initial profile page"
   git branch -M main
   git remote add origin git@github.com:torut/torut.github.io.git
   git push -u origin main
   ```

3. **GitHub Pages を有効化**: リポジトリの **Settings → Pages** で:
   - Source: `Deploy from a branch`
   - Branch: `main` / `/ (root)` → Save
   - Custom domain に `toru1231.tamulab.jp` を入力し Save（`CNAME` が既にコミットされていれば自動認識）

4. **DNS を設定**（`tamulab.jp` のネームサーバー側）:
   | 種別 | ホスト | 値 |
   |---|---|---|
   | CNAME | `toru1231` | `torut.github.io.` |

5. DNS 反映後（数分〜数十分）、GitHub Pages の **Enforce HTTPS** を ON。

6. `https://toru1231.tamulab.jp` でアクセス確認 + X などにリンクを貼って OGP プレビュー確認。

## 差し替えメモ

`index.html` 内に `<!-- TODO: -->` コメントで明示。

- 自己紹介文 (`<p class="bio">`) … 仮文なので本人の文章へ
- 追加 SNS（Zenn / note / connpass など）が出てきたら `<ul class="sns">` にリンクを追加
- favicon は暫定で GitHub アバターを流用 → 必要なら独自のものを用意して `<link rel="icon">` を差し替え
