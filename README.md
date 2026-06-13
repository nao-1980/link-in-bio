# Link in bio

シンプルな Link in bio（プロフィール＋リンク集）ページです。ビルド不要の素の HTML/CSS/JS で、GitHub Pages で公開できます。
**`index.html` 内の設定ブロック（`CONFIG`）を書き換えるだけ**で、誰でも自分用にカスタマイズできます。

## 公開URL

```
https://<ユーザー名>.github.io/link-in-bio/
```

（例：このリポジトリでは https://nao-1980.github.io/link-in-bio/ ）

## カスタマイズ方法

[`index.html`](index.html) の中ほどにある「▼ここだけ編集すればOK」の `CONFIG` を編集します。

```js
const CONFIG = {
  name: "Your Name",                 // 名前
  bio: "ここに一言紹介が入ります。",   // 一言紹介
  avatar: "assets/avatar.svg",        // アイコン画像（正方形推奨。URLでも可）

  background: "#f7f8fa",              // 背景（色 / グラデーション / 画像）
  textColor: "#1a1a1a",              // 名前・一言・フッターの文字色
  overlay: "",                        // 画像背景の重ね色（任意）

  links: [
    { icon: "x",         label: "X (Twitter)", url: "https://x.com/yourname" },
    { icon: "instagram", label: "Instagram",   url: "https://instagram.com/yourname" },
    { icon: "email",     label: "メール",        url: "mailto:your@email.com" },
  ],

  footer: "Your Name",                // フッターの名前（© 年 は自動）
};
```

### リンクの追加・削除

- **削除**：不要な `{ icon: ..., label: ..., url: ... },` の行を**丸ごと消す**だけ
- **追加**：行を**複製**して `label` と `url` を変えるだけ（順番は上から表示順）
- **メール**：`url` を `"mailto:アドレス"` にすると別タブで開かずメーラーが起動します

### 使えるアイコン（`icon:` の値）

`x` / `instagram` / `youtube` / `tiktok` / `email` / `website` / `line` / `facebook` / `github` / `note` / `threads`

> 一覧にない名前を指定した場合は、自動で汎用（地球儀）アイコンが表示されます。

### 背景の変更

`CONFIG.background` に次のいずれかを指定します。

| やりたいこと | 書き方 |
| --- | --- |
| 単色 | `background: "#ffeef5"`（`"white"` などの色名もOK） |
| グラデーション | `background: "linear-gradient(135deg, #a18cd1, #fbc2eb)"` |
| 画像を背景に | `background: "assets/bg.jpg"`（`.jpg/.png/.webp/.gif/.svg` は自動で画像背景になり、画面全体に `cover` 表示） |

**画像を使う手順**：使いたい画像（例 `bg.jpg`）を `assets/` フォルダに入れ、`background: "assets/bg.jpg"` と書くだけ。外部URL（`https://.../bg.jpg`）も指定できます。

**暗い背景・写真背景のとき**：
- 文字が見えにくければ `textColor: "#ffffff"`（白文字）にする
- さらに読みやすくしたいときは `overlay` に重ね色を指定
  - 背景を暗くする：`overlay: "rgba(0,0,0,0.35)"`
  - 背景を明るくする：`overlay: "rgba(255,255,255,0.45)"`
  - 不要なら `overlay: ""`（空）

> リンクボタンは常に白カードなので、背景を変えてもボタン内の文字は読みやすいままです。

### アイコン画像（プロフィール）

`assets/avatar.svg` を自分の画像に差し替えます。別名・別形式（.png / .jpg）にした場合は `CONFIG.avatar` のパスも合わせて変更してください。外部URL（例：画像ホスティングのURL）も指定できます。

## ローカルで確認

```bash
cd link-in-bio
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

## デプロイ（GitHub Pages）

初回はリポジトリ作成と Pages 有効化が必要です（このリポジトリは設定済み）。
以後は編集して push するだけで、数十秒後に公開URLへ自動反映されます。

```bash
git add -A
git commit -m "update"
git push
```

新しく自分のリポジトリで公開する場合：
1. GitHub に push
2. リポジトリ → **Settings** → **Pages**
3. **Source** を `Deploy from a branch`、Branch を `main` / `/ (root)` にして Save
