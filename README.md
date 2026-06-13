# Link in bio

シンプルな Link in bio（プロフィール＋リンク集）ページです。ビルド不要の素の HTML/CSS/JS で、GitHub Pages で公開できます。
カスタマイズの方法は2通りあります。

- **コードを書かずに作る** → ジェネレーター（[`generator.html`](generator.html)）でフォーム入力 → 自分用のページHTMLをダウンロード
- **コードで直接編集** → [`index.html`](index.html) 内の設定ブロック（`CONFIG`）を書き換える

## ジェネレーター（おすすめ・誰でも使える）

ログイン不要・無料。フォームに入力するとプレビューが更新され、「ダウンロード」で完成した `index.html` が手に入ります。
**入力データはどこにも保存されません**（すべてブラウザ内で完結）。

```
https://<ユーザー名>.github.io/link-in-bio/generator.html
```

1. 上記URLを開く
2. 名前・一言・アイコン・背景・デザイン・リンクを入力（プレビューでその場確認）
3. 「📥 ページをダウンロード」で `index.html` を保存
4. その `index.html` を GitHub Pages や Netlify などにアップすれば公開完了

> 他の人にも使ってもらう場合は、この generator.html のURLを共有するだけ。各自がダウンロードして自分の好きな場所で公開できます。

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

  theme: {                            // デザイン（見た目）の設定
    accent: "#6d5efc",               // アクセントカラー
    font: "sans",                     // フォント
    buttonStyle: "card",             // ボタンの種類
    buttonRadius: 14,                 // ボタンの角丸
    avatarShape: "circle",           // アイコンの形
  },

  links: [
    { icon: "x",         label: "X (Twitter)", url: "https://x.com/yourname" },
    { icon: "instagram", label: "Instagram",   url: "https://instagram.com/yourname" },
    { icon: "email",     label: "メール",        url: "mailto:your@email.com" },
  ],

  music: "",                          // 好きな曲のURL（Spotify等）。空欄なら非表示
  gallery: [],                        // 写真ギャラリー（画像URLの配列）。2列で表示

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

### デザインの変更（`theme`）

コードを書かずに、`theme` の値を変えるだけで見た目を自由に調整できます。

| 設定 | 選べる値 | 内容 |
| --- | --- | --- |
| `accent` | 任意の色（例 `"#ff5a8a"`） | アクセント色（ホバー枠・solid塗り・glass縁取り） |
| `font` | `"sans"` / `"rounded"` / `"serif"` / `"mono"` | フォントの雰囲気（標準・丸ゴシック・明朝・等幅） |
| `buttonStyle` | `"card"` / `"outline"` / `"solid"` / `"glass"` | 白カード / 枠線のみ / アクセント塗り / すりガラス |
| `buttonRadius` | 数値(px) | `0`=四角 / `14`=標準 / `999`=カプセル型 |
| `avatarShape` | `"circle"` / `"rounded"` / `"square"` | アイコンの形（丸 / 角丸 / 四角） |

**組み合わせ例：**
- シンプル：`buttonStyle:"card"`, `font:"sans"`, `avatarShape:"circle"`
- ポップ：`buttonStyle:"solid"`, `accent:"#ff5a8a"`, `buttonRadius:999`, `font:"rounded"`
- 写真背景に映える：`buttonStyle:"glass"`, `textColor:"#ffffff"`（背景画像と併用）
- 上品：`buttonStyle:"outline"`, `font:"serif"`

> `buttonStyle:"glass"` や白文字は、暗い背景・写真背景と組み合わせると映えます（`textColor` も合わせて調整）。

### 好きな曲を埋め込む（`music`）

`music` に曲のURLを貼ると、プレイヤーが表示されます（空欄なら非表示）。対応サービス：

- **Spotify**（曲・アルバム・プレイリスト）例：`"https://open.spotify.com/track/..."`
- **YouTube** 例：`"https://youtu.be/..."`
- **Apple Music** 例：`"https://music.apple.com/jp/album/..."`
- **SoundCloud** 例：`"https://soundcloud.com/.../..."`

曲ページの「共有」からURLをコピーして貼り付けるだけ。サービスは自動判定されます。

### 写真ギャラリー（`gallery`）

`gallery` に画像URLを並べると、2列のグリッドで写真が表示されます（空配列なら非表示）。

```js
gallery: [
  "assets/photo1.jpg",
  "https://example.com/photo2.jpg",
],
```

ジェネレーターでは「写真をアップロード」で複数画像を選ぶか、画像URLを貼って追加できます（アップした写真はHTMLに埋め込まれます。枚数が多いとファイルが大きくなる点に注意）。

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
