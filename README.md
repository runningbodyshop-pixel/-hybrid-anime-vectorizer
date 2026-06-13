# Hybrid Anime Vectorizer

スマホで使える、アニメ絵向けのハイブリッドSVG化サイトです。

- 背景処理
- 白フチ対策
- VTracerで色面化
- Potraceで線画化
- 合成してハイブリッドSVGを出力

---

## 1. ZIPをダウンロードして解凍
このプロジェクト一式をダウンロードして解凍します。

---

## 2. GitHub にアップロード

### 2-1. GitHubアカウントを作る
まだ無ければ https://github.com/ でアカウントを作成します。

### 2-2. 新しいリポジトリを作る
1. GitHubにログイン
2. 右上の `+` → `New repository`
3. Repository name に `hybrid-anime-vectorizer` などを入力
4. `Public` を選択
5. `Create repository`

### 2-3. ファイルをアップロード
スマホでもPCでもOKです。

#### スマホでやる場合
1. 作成したリポジトリ画面を開く
2. `Add file` → `Upload files`
3. 解凍したフォルダの中身を全部アップロード
4. 下の `Commit changes` を押す

**アップロードするもの**
- `app/` フォルダ
- `requirements.txt`
- `Dockerfile`
- `render.yaml`
- `.dockerignore`
- `README.md`

---

## 3. Render にデプロイ

### 3-1. Renderアカウントを作る
https://render.com/ にアクセスしてアカウントを作成します。

おすすめは **GitHubでログイン** です。

### 3-2. New Web Service を作る
1. Renderにログイン
2. `New +` を押す
3. `Web Service` を選ぶ
4. GitHub連携を許可する
5. さっき作った `hybrid-anime-vectorizer` リポジトリを選ぶ

### 3-3. 設定
だいたい自動で読み取られますが、もし聞かれたら以下を設定します。

- **Name**: 好きな名前
- **Runtime**: Docker
- **Branch**: `main`
- **Region**: 近い場所でOK
- **Plan**: Free でOK

`Create Web Service` を押します。

---

## 4. デプロイ完了を待つ
数分待つとビルドが進みます。

成功すると、RenderがURLを発行します。例:

- `https://hybrid-anime-vectorizer.onrender.com`

そのURLを開けばサイトが使えます。

---

## 5. サイトの使い方
1. 画像をアップロード
2. プリセットを選ぶ
   - `軽量`: 速さ優先
   - `標準`: バランス
   - `高品質`: 細部優先
3. 必要なら
   - `外側の白/薄灰背景を透明化`
   - `白フチ対策`
   をONのまま使う
4. `SVG化する` を押す
5. 出力をダウンロード

おすすめは **ハイブリッドSVG** です。

---

## 6. もしデプロイで失敗したら
Renderの画面にエラーが出ます。
その場合は、

- Renderのエラー画面のスクショ
- Build Log の最後のほう

をこのチャットに貼ってください。原因を見て直します。

---

## 7. 今回の構成
- **FastAPI**: サイト本体
- **Pillow / NumPy**: 前処理
- **VTracer**: 色面のトレース
- **Potrace**: 線画のトレース
- **Docker**: Renderで安定動作させるため

---

## 8. 補足
この版は **落ちにくさ重視の最初の完成版** です。
今後、必要なら次を追加できます。

- GT7向け自動分割
- 15KB制限向け分割出力
- 線の太さ調整
- 色数調整
- underpaint / overlap 対策
- ジョブキュー方式でさらに安定化
