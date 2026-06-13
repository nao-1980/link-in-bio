# Link in bio

シンプルな Link in bio（プロフィール＋リンク集）ページです。ビルド不要の素の HTML/CSS/JS で、GitHub Pages で公開できます。

## 公開URL

デプロイ後、以下でアクセスできます（`<ユーザー名>` は自分の GitHub アカウント名）：

```
https://<ユーザー名>.github.io/link-in-bio/
```

## 編集方法

すべて [`index.html`](index.html) 内で完結します。

| 変更したいもの | 編集箇所 |
| --- | --- |
| 名前 | `<h1 class="name">Your Name</h1>` |
| 一言紹介 | `<p class="bio">…</p>` |
| アイコン画像 | `assets/avatar.svg` を自分の画像（正方形推奨）に差し替え。別名にした場合は `<img class="avatar" src="...">` の src も変更 |
| 各SNSのリンク | 各 `<a class="link" href="#" …>` の `href="#"` を実際のURLに変更 |
| メールアドレス | `href="mailto:your@email.com"` を自分のアドレスに変更 |
| タイトル/OGP | `<head>` 内の `<title>` と `og:*` メタタグ |

リンクの追加・削除は `<nav class="links">` 内の `<a class="link">…</a>` ブロックを複製・削除するだけです。

## ローカルで確認

```bash
cd link-in-bio
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

## デプロイ（GitHub Pages）

1. このリポジトリを GitHub に push
2. GitHub のリポジトリ → **Settings** → **Pages**
3. **Source** を `Deploy from a branch`、Branch を `main` / `/ (root)` に設定して Save
4. 数十秒後、上記の公開URLで表示されます
