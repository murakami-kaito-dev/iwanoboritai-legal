# iwanoboritai-legal

ボルダリングジム検索・ボル活記録サービス「イワノボリタイ」（iOS アプリ・Web 版）の
利用規約・プライバシーポリシーを GitHub Pages で公開するためのリポジトリ。

- 公開 URL: https://murakami-kaito-dev.github.io/iwanoboritai-legal/
  - 利用規約 `/terms/`、プライバシーポリシー `/privacy/`（アプリ・Web 版からリンクされているため **パスは変えない**）
- `main` への push で自動公開される。変更はブランチ → PR → レビュー後にマージする。

## 構成

| ファイル | 役割 |
|---|---|
| `_config.yml` | サイト設定。導線 URL（`app_store_url` / `web_url`）と連絡先はここだけを直せば全ページに反映される |
| `_layouts/legal.html` | 自前レイアウト（ヘッダー・題・最終更新日・要点サマリ・フッター）。Jekyll プラグイン不使用 |
| `assets/legal.css` | スタイル。Web 版 `webapp/DESIGN.md` の「Rock & Chalk」トークンに準拠したダーク単一テーマ |
| `index.md` | ハブ（両文書へのカード・改訂履歴の概要・問い合わせ） |
| `terms.md` / `privacy.md` | 本文。front matter の `updated`（最終更新日）と `summary`（要点サマリの箇条書き）をレイアウトが描く |

### 本文の書き方

- 各条は `## N. 見出し {#terms-N}` / `{#privacy-N}` のように **固定 ID** を付ける（`#terms-4` で条を直接指せる）。
- 目次は本文冒頭の `<nav class="toc">` に手書き（条を増減したら目次と改訂履歴も更新する）。
- 相互参照は `{{ '/privacy/' | relative_url }}#privacy-6` の形で書く。
- 条文を実質的に変えたら、`updated` を更新し、末尾の「改訂履歴」表に 1 行足す。

## ローカルプレビュー

GitHub Pages は `main` しかビルドしないため、ブランチの確認はローカルで行う。

```bash
bundle install            # 初回のみ（github-pages gem。Ruby が必要）
bundle exec jekyll serve  # http://localhost:4000/iwanoboritai-legal/
```
