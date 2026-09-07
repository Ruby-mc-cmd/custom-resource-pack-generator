# [Custom Resource Pack Generator](https://ruby-mc-cmd.github.io/custom-resource-pack-generator/)

Blockbenchで作った `.bbmodel`、PNGテクスチャ、音声ファイルをドラッグ&ドロップするだけで、Minecraft用のカスタムリソースパック（zip）を作れるブラウザツールです。サーバー不要・単一HTMLファイルで完結しています。

**デモ:** このリポジトリでGitHub Pagesを有効にすると、`https://<ユーザー名>.github.io/<リポジトリ名>/` で公開されます。

## できること

- **3Dモデル（`.bbmodel`）** → カスタムアイテムのモデルとして自動変換（UV・回転・アニメーション対応）
- **PNGテクスチャ** → 平面の2Dアイテムとして登録。縦横比2以上の画像は自動でアニメーションテクスチャと判定
- **音声ファイル（mp3/wav/m4a/flacなど）** → 自動でOgg Vorbisに変換してカスタムサウンドとして登録
- 複数ファイルをまとめて1つのパックに
- 新規作成、または既存のリソースパックへの追加（zipを読み込んで中身を保ったままアイテム追加）
- 対象Minecraftバージョンを選択（`misode/mcmeta`から最新のバージョン一覧を取得し、`pack_format`/`min_format`/`max_format`を自動で適切な書き方に）
- ベースアイテムの検索候補（バニラアイテム一覧から検索、ブロックは実際のブロックモデルを3D描画したアイコン付き）
- パックアイコン・パック名・説明文の設定
- `/give`・`/playsound`コマンドのプレビュー

## 使い方

1. 上記のGitHub PagesのURLを開く（またはこのリポジトリの `index.html` を直接ブラウザで開く）
2. 「作成方法」で新規作成 or 既存パックへの追加を選ぶ
3. 対象バージョンを選ぶ
4. `.bbmodel` / PNG / 音声ファイルをドロップ
5. 必要に応じてベースアイテムなどを設定し、「リソースパックをダウンロード」

すべての処理はブラウザ内で完結しており、アップロード先のサーバーはありません。

## 技術的な補足

- 3Dアイテムのモデル変換、ブロックアイコンの3D描画には [deepslate](https://github.com/misode/deepslate)（misode氏によるMinecraftレンダリングライブラリ）を使用
- 音声のOgg Vorbis変換には [vorbis-encoder-js](https://github.com/higuma/ogg-vorbis-encoder-js) を使用
- バージョン一覧・アイテム一覧・ブロックモデル/テクスチャの取得には [misode/mcmeta](https://github.com/misode/mcmeta) を使用

## ライセンス

MIT License（`LICENSE`ファイル参照）。同梱しているライブラリ（deepslate, vorbis-encoder-js, JSZip, Three.js, gl-matrix）はそれぞれのライセンスに従います。
