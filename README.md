# AbsTrainingCounterPolicies

「腹筋トレーニングカウンター / AbsTrainingCounter」の法務文書を、GitHub Pages（Jekyll）で公開するためのリポジトリです。

公開サイト: [https://yuu123456.github.io/AbsTrainingCounterPolicies/](https://yuu123456.github.io/AbsTrainingCounterPolicies/)

## このリポジトリの役割

- 利用規約、プライバシーポリシー、特定商取引法に基づく記載を公開する
- バージョン付き URL（`document_type + version + lang`）で法務文書を管理する
- Jekyll レイアウト・include・スタイルで法務ページの共通 UI を提供する

## ディレクトリ構成（抜粋）

```text
docs/
  _config.yml                 # サイト設定（url/baseurl, languages, plugins）
  _layouts/
    default.html              # 共通レイアウト
    legal.html                # 法務ページ用レイアウト
  _includes/
    version-notice.html       # バージョン表示
    lang-switcher.html        # 言語切替
  assets/css/style.css        # 共通スタイル
  index.md                    # 法務文書ハブ
  privacy/v1/{ja,en}/index.md
  terms/v1/{ja,en}/index.md
  tokushoho/v1/ja/index.md    # 現状、日本語のみ
```

## ローカルセットアップ

前提:

- Ruby 3.0 以上
- Bundler

```bash
bundle install
```

## ビルド / プレビュー

```bash
# サイト全体をビルド
bundle exec jekyll build --source docs --config docs/_config.yml

# ローカルプレビュー起動
bundle exec jekyll serve --source docs --config docs/_config.yml
```

プレビュー例:

- [http://127.0.0.1:4000/AbsTrainingCounterPolicies/privacy/v1/ja/](http://127.0.0.1:4000/AbsTrainingCounterPolicies/privacy/v1/ja/)
- [http://127.0.0.1:4000/AbsTrainingCounterPolicies/terms/v1/ja/](http://127.0.0.1:4000/AbsTrainingCounterPolicies/terms/v1/ja/)
- [http://127.0.0.1:4000/AbsTrainingCounterPolicies/tokushoho/v1/ja/](http://127.0.0.1:4000/AbsTrainingCounterPolicies/tokushoho/v1/ja/)

## GitHub Pages で公開する手順

1. 変更を `main` ブランチへ push する。
2. リポジトリの **Settings > Pages** で、公開元を次のように設定する。
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/docs**
3. push 後、GitHub Pages が自動で再ビルド・再公開する（反映まで数十秒〜数分）。
4. 下記の公開リンクへアクセスして表示を確認する。

## 編集時の運用ルール

- 個人情報（氏名・住所・電話番号）を記載しない
- 公開連絡先は `support.app.dev.team+abstrainingcounter@gmail.com` のみ
- 開発主体名は「腹筋トレーニングカウンター開発者チーム」で統一
- アプリ名は「腹筋トレーニングカウンター / AbsTrainingCounter」の併記を維持
- 法務ページの front matter は以下を揃える
  - `layout`, `permalink`, `lang`, `document_type`, `version`, `effective_date`, `title`
- バージョン・制定日・連絡先を更新する際は、関連するハブ/入口/各法務文書を同時更新して不整合を防ぐ
- 文書間参照は Jekyll の `{% link ... %}` 形式を使う

## 主要ページ

- ハブ（ja）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/](https://yuu123456.github.io/AbsTrainingCounterPolicies/)
- 利用規約（v1 ja）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/terms/v1/ja/](https://yuu123456.github.io/AbsTrainingCounterPolicies/terms/v1/ja/)
- 利用規約（v1 en）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/terms/v1/en/](https://yuu123456.github.io/AbsTrainingCounterPolicies/terms/v1/en/)
- プライバシーポリシー（v1 ja）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/privacy/v1/ja/](https://yuu123456.github.io/AbsTrainingCounterPolicies/privacy/v1/ja/)
- プライバシーポリシー（v1 en）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/privacy/v1/en/](https://yuu123456.github.io/AbsTrainingCounterPolicies/privacy/v1/en/)
- 特定商取引法に基づく記載（v1 ja のみ）: [https://yuu123456.github.io/AbsTrainingCounterPolicies/tokushoho/v1/ja/](https://yuu123456.github.io/AbsTrainingCounterPolicies/tokushoho/v1/ja/)
