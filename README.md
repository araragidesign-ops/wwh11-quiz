# この9人は、誰でしょう？ ｜ Wako's Music Holiday Concert Vol.11

フライヤーの集合写真に登場する9人の「作曲家」を当てるクイズアプリです。
HTMLファイル1枚（`index.html`）と画像1枚（`photo.jpg`）だけで動く、
サーバー不要の静的サイトなので、GitHub Pages にそのまま公開できます。

## ファイル構成

```
composer-quiz/
├── index.html   ← ページ本体（HTML/CSS/JSをすべて内蔵）
└── photo.jpg    ← クイズに使う集合写真（フライヤーからトリミング済み）
```

## GitHub Pages での公開手順

### 1. GitHubにリポジトリを作る
1. https://github.com にログインし、右上の「＋」→「New repository」をクリック
2. Repository name を決める（例：`composer-quiz`）
3. Public を選択（GitHub Pages の無料利用には Public 推奨）
4. 「Create repository」をクリック

### 2. ファイルをアップロードする
1. 作成したリポジトリのページで「Add file」→「Upload files」をクリック
2. `index.html` と `photo.jpg` の2つをドラッグ＆ドロップ
3. 下部の「Commit changes」をクリックしてアップロードを確定

（Gitコマンドに慣れている場合は、以下でも可）
```bash
git init
git add index.html photo.jpg
git commit -m "composer quiz"
git branch -M main
git remote add origin https://github.com/【ユーザー名】/composer-quiz.git
git push -u origin main
```

### 3. GitHub Pages を有効にする
1. リポジトリの「Settings」タブを開く
2. 左メニューの「Pages」をクリック
3. 「Build and deployment」の「Source」を **Deploy from a branch** に設定
4. 「Branch」を **main** ／ フォルダを **/(root)** にして「Save」

### 4. 公開URLを確認する
数十秒〜数分待つと、ページ上部に公開URLが表示されます。形式は：

```
https://【ユーザー名】.github.io/【リポジトリ名】/
```

例：`https://wako-music.github.io/composer-quiz/`

このURLをそのままチラシやSNSでシェアできます。

## アプリの機能

- 写真の①〜⑨の番号ピン（顔にかからないよう胸元に配置）をクリックすると、対応する回答欄にジャンプ
- 各回答欄に「ヒント」ボタン。押すと、その人物の見分け方が表示される
- 同じ作曲家は1回しか選べない（重複を自動でブロック）
- 「採点する」を押すと**別画面**に切り替わり、採点結果を表示
- **全問正解すると**「おめでとうございます！受付でこのページをお見せください」と認定枠を表示
- 結果画面の下部で、写真に写っていない10人目（スッペ）を種明かし

## 中身を編集したいとき

すべて `index.html` の `<script>` 内で完結しています。

- **答え・作曲家名・曲名を変える** → `const composers = [...]` と `const positions = [...]`
  （`correct` の値が正解の作曲家 `id`）
- **ヒントの文面を変える** → `positions` の各 `hint` を書き換え
- **番号ピンの位置を微調整する** → `positions` の `x` / `y`
  （写真の左端・上端からのパーセント。指揮者のピンは `conductor`）
- **全問正解時のメッセージを変える** → `perfectBox` を組み立てている箇所
- **写真を差し替える** → `photo.jpg` を置き換え、必要に応じてピン位置を再調整

## ローカルで確認したいとき

`index.html` をブラウザでそのまま開くだけで動作します（インターネット接続時はGoogleフォントを読み込みます）。
