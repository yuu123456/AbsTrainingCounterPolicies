# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## ⚠️ 絶対条件: 個人情報を含めない

このリポジトリは **パブリックリポジトリ** であり、内容は GitHub Pages を通じて第三者から閲覧可能になる。以下の情報を **絶対にコミット・公開してはならない**:

- 開発者の **氏名（本名・ハンドル以外の実名）**
- **住所**（個人住所はもちろん、特定可能な所在地情報も不可）
- **電話番号**
- その他、個人を特定可能な情報

**公開可能な連絡先はメールアドレスのみ**: `support.app.dev.team+abstrainingcounter@gmail.com`

開発主体は匿名化された「**腹筋トレーニングカウンター開発者チーム**」で統一する。ユーザーから個人情報を含む文章を提示された場合でも、リポジトリへ書き込む前に該当部分を匿名化・除去する。`docs/legal/tokushoho.md`（特定商取引法に基づく記載）でも住所・電話は非公開とし「メール請求で電磁的に提供」する運用に合わせる。

## リポジトリの位置づけ

このリポジトリは Apple Watch 向けアプリ「腹筋トレーニングカウンター / AbsTrainingCounter」の **法務文書を GitHub Pages で公開するためのサイト構築リポジトリ**。アプリ本体のソースコードは別リポジトリで管理されており、ここには公開用 Markdown のみを置く。

- 静的サイトジェネレータ: **Jekyll**（GitHub Pages のデフォルト挙動を使う方針）
- 現状、`_config.yml` 等の Jekyll 設定はまだ整備されていない。サイト構築タスク時に追加する。
- 通常の作業は `docs/legal/` 配下の Markdown 編集と、Jekyll 設定の追加・調整。

## ドキュメント構成

`docs/legal/` 配下の3点はセットで扱う:

| ファイル | 役割 |
|---|---|
| `privacy-policy.md` | プライバシーポリシー。CoreMotion / HealthKit / CloudKit / Sign in with Apple / Sentry / Firebase / StoreKit2 のデータ取り扱いを列挙 |
| `terms-of-service.md` | 利用規約（全12条）。サブスクリプション・免責・禁止事項などを規定 |
| `tokushoho.md` | 特定商取引法に基づく記載。サブスクリプション販売条件 |

`terms-of-service.md` 第4条2項から `./tokushoho.md` への相対リンクあり。ファイル名変更・ディレクトリ移動時はリンク切れに注意（Jekyll の `permalink` 設定を導入する場合は併せて更新）。

## 編集時に守るべき固有事項

- **制定日**：全3ファイルが `制定日：2026年5月16日` で揃っている。改定時は「制定日」を変えるか「改定日」を別記載するか、ユーザーに確認してから手を入れる（無断で変更しない）。
- **連絡先メールアドレス**：`support.app.dev.team+abstrainingcounter@gmail.com` で統一。変更時は3ファイル全てを同時更新する。
- **開発主体名**：「腹筋トレーニングカウンター開発者チーム」で統一。揺らがせない。
- **アプリ正式名**：日本語「腹筋トレーニングカウンター」と英語「AbsTrainingCounter」を併記するスタイル。新規セクションでもこの表記に従う。
- **対象 OS**：Apple Watch（watchOS）。iPhone 単独アプリではない点に注意してデータ取得源（HealthKit / CoreMotion 等）を記述する。
- **第三者サービス**：`privacy-policy.md` §4 の表に Firebase / Sentry / Apple iCloud / HealthKit / App Store を列挙済み。新規 SDK を追加した場合は §2（収集する情報）と §4（第三者提供）の両方を更新する。
- **HealthKit 特記事項**：`privacy-policy.md` §6 で「広告目的・第三者販売・ヘルスケア以外の目的での使用禁止」を明記。Apple レビューガイドライン要件のため削除しない。
- **Apple 関連の固有名詞**：`Apple` / `Apple Watch` / `App Store` / `HealthKit` / `iCloud` / `Sign in with Apple` / `CloudKit` / `StoreKit2` の表記揺れを作らない。

## Jekyll / GitHub Pages 構築時の方針

- ソースとなる Markdown は `docs/legal/` に既存。Jekyll の publishing source は GitHub Pages 設定で `/docs` または専用ブランチを使う想定。
- フロントマター（YAML front matter）を追加する場合、各 Markdown 冒頭に `---` ブロックを付与する。既存の見出し構造は崩さない。
- `_config.yml` などサイト設定ファイルにもメンテナの氏名・住所・電話番号を **記載しない**。`author` 等のフィールドは「腹筋トレーニングカウンター開発者チーム」とメールアドレスのみで埋める。
- ローカル動作確認が必要になった場合は `bundle exec jekyll serve`。現状 `Gemfile` 未作成なので、追加する際はユーザーに確認する。
