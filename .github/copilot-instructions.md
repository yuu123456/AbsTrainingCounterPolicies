# このリポジトリ向け Copilot Instructions

## ビルド・テスト・Lint コマンド

実行ディレクトリはリポジトリルート。現在の依存関係では Ruby 3.0+ が必要です。

| 作業 | コマンド |
|---|---|
| gem のインストール | `bundle install` |
| サイト全体をビルド | `bundle exec jekyll build --source docs --config docs/_config.yml` |
| ローカルプレビュー起動 | `bundle exec jekyll serve --source docs --config docs/_config.yml` |
| 単一ドキュメント確認 | `bundle exec jekyll serve --source docs --config docs/_config.yml` 実行後に `/privacy/v1/ja/` など対象パスを確認 |

このリポジトリには、専用の自動テストランナーや lint 設定は現在ありません。

## 高レベルアーキテクチャ

- このリポジトリは、Apple Watch 向けアプリ **腹筋トレーニングカウンター / AbsTrainingCounter** の法務文書を GitHub Pages で公開する Jekyll サイトです（アプリ本体コードは含みません）。
- 公開ソースは `docs/` 配下で、コンテンツと表示ロジックを同居させています。
  - `docs/_config.yml`: `url` / `baseurl`、対応言語（`ja`, `en`）、プラグイン定義
  - `docs/_layouts/default.html`: 共通レイアウト
  - `docs/_layouts/legal.html`: 法務ページ用レイアウト（バージョン表示 + 言語切替 + 本文）
  - `docs/_includes/version-notice.html` / `docs/_includes/lang-switcher.html`: 法務ページ共通 UI 部品
  - `docs/assets/css/style.css`: ハブページ・法務ページ共通スタイル
- 法務文書は `document_type + version + lang` で URL/ファイルを切っています。
  - `docs/privacy/v1/{ja,en}/index.md`
  - `docs/terms/v1/{ja,en}/index.md`
  - `docs/tokushoho/v1/ja/index.md`
- `docs/privacy/index.md` や `docs/privacy/v1/index.md` などの入口ページは、最新版の日本語版へリダイレクトする役割です。
- `docs/index.md` は法務文書ハブとして、現在の正式版リンクを集約します。

## このコードベース固有の重要規約

- 個人情報（実名・住所・電話番号）はコミットしない。公開連絡先は `support.app.dev.team+abstrainingcounter@gmail.com` のみ。
- 開発主体名は `腹筋トレーニングカウンター開発者チーム` で統一する。
- アプリ名は `腹筋トレーニングカウンター / AbsTrainingCounter` の併記スタイルを維持する。
- 法務ページの front matter は `layout`, `permalink`, `lang`, `document_type`, `version`, `effective_date`, `title` を揃える。
- バージョン・制定日・連絡先などを更新する場合、関連ファイル（ハブ、リダイレクト、各法務文書）を同時に更新して不整合を出さない。
- 文書間参照は Jekyll の `{% link ... %}` 形式を維持する（例: `{% link tokushoho/v1/ja/index.md %}`）。
- `tokushoho` は現状日本語のみが正本で、英語未提供時の切替制御は `_includes/lang-switcher.html` に実装されている。
- プライバシーポリシーで外部サービスを追加・変更する場合は、「収集する情報」と「第三者へのデータ提供」の両セクションを必ず同期更新する。
