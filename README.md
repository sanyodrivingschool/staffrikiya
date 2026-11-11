# 三陽自動車学校 SNS流入LP（GitHub Pages）

## ファイル構成

```
index.html   … LP本体（CSS・JSも1ファイルに入っています）
images/      … 写真・OGP画像を入れるフォルダ（今は空）
.nojekyll    … GitHub PagesでJekyll処理をさせないための空ファイル
README.md    … このファイル
```

## 公開手順

1. GitHubで新しいリポジトリを作る（例：`sanyo-lp`、Public）
2. このフォルダの中身をすべてアップロードする（`.nojekyll` も忘れずに）
   - ブラウザなら「Add file → Upload files」にドラッグ＆ドロップ
   - コマンドなら：
     ```
     git init
     git add .
     git commit -m "first commit"
     git branch -M main
     git remote add origin https://github.com/<ユーザー名>/sanyo-lp.git
     git push -u origin main
     ```
3. リポジトリの **Settings → Pages** を開く
4. **Source：Deploy from a branch**、**Branch：main / (root)** を選んで Save
5. 1〜2分後に `https://<ユーザー名>.github.io/sanyo-lp/` で公開されます

## URLの使い分け

| 用途 | URL |
|---|---|
| 学生向けPR投稿 | `https://<ユーザー名>.github.io/sanyo-lp/` |
| 保護者向けPR投稿 | `https://<ユーザー名>.github.io/sanyo-lp/?t=parent` |

`?t=parent` を付けると、ファーストビューの見出しが保護者向けに切り替わります。
計測用に `&utm_source=instagram&utm_content=投稿ID&rep=営業ID` を足しても表示は変わりません。

## 写真の差し替え（HTMLの編集は不要）

`images/` フォルダに、下の名前で写真をアップロードするだけで表示されます。
写真がない枠は「写真差し替え」の表示のまま残ります。

| 枠 | ファイル名 | サイズの目安 |
|---|---|---|
| ファーストビューの学生 | `fv.webp` | 720×960（縦長） |
| 施設：4車線コース | `about-1.webp` | 1080×1080 |
| 施設：教習車 | `about-2.webp` | 1080×1080 |
| 施設：ロビー・待合 | `about-3.webp` | 1080×1080 |
| 施設：指導員 | `about-4.webp` | 1080×1080 |
| 先輩の声 1〜2人目（卒業生） | `voice-1.webp` `voice-2.webp` | 240×240 |
| 先輩の声 3人目（保護者） | `voice-3.webp` | 240×240 |
| 上熊本駅校の外観 | `access-kamikumamoto.webp` | 960×560 |
| 熊本駅田崎校の外観 | `access-tasaki.webp` | 960×560 |
| SNSシェア画像 | `ogp.png` | 1200×630 |

- `.webp` が無いときは、同じ名前の `.jpg` を探します（例：`fv.jpg`）。スマホの写真をそのまま入れてもOKです。ただし拡張子は小文字の `.jpg` にしてください（`.JPG` `.jpeg` は読みません）。
- 写真は枠に合わせて自動で切り抜かれます（中央基準）。
- 入れ替えるときは、同じ名前でアップロードし直すと上書きされます。
- 反映されないときは、ブラウザの再読み込み（キャッシュ）を試してください。

### GitHubでのアップロード手順
1. リポジトリの `images` フォルダを開く
2. 「Add file → Upload files」に写真をドラッグ＆ドロップ
3. 下の「Commit changes」を押す → 1〜2分でLPに反映

## 公開前に差し替えるもの（テキスト）

`index.html` 内の [ ] の部分です。

- OGP画像のURL：`<head>` の `og:image` を、公開後の絶対URLに書き換え
- 学生料金の総額、11月キャンペーンの内容と期限、送迎バスの運行エリア
- 先輩の声（掲載許諾を取ったもの）
- 「卒業生事故率の低さ 熊本市内No.1」の根拠（フッターの注記欄）
- FAQの友達紹介・グループ特典

## 計測（任意）

`<head>` 内のコメント位置に、既存のGoogle Tag Manager（GTM-P2TM5Z6）のタグを貼ると、
LINEボタン・電話タップなどをGTM側でイベント計測できます。
