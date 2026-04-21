# Architec Grain — Official Website

> 言葉にならない課題を、形にする。

Architec Grain合同会社のオフィシャルサイト（1ページ構成）。

## 構成

```
/
├── index.html          メインページ（ロゴは Base64 埋め込みで自己完結）
├── robots.txt          クローラー設定（AIクローラー全許可）
├── sitemap.xml         サイトマップ（要ドメイン後編集）
├── README.md           このファイル
└── assets/
    └── logo/           元のロゴファイル（将来の再編集用に保管）
```

`index.html` は単体で動作します。ブラウザで直接開いても、ロゴは正常に表示されます。

## ブランドカラー

| 用途 | 色 | コード |
|---|---|---|
| ベース | 和紙白 | `#f5f1e8` |
| プライマリ | 濃墨グレー | `#2a2a2a` |
| アクセント | 朱 | `#d94f2c` |

朱は全体の 3-5% のみ。本文テキストには使用しない。

## 公開手順

### ステップ 1: GitHub Pages で暫定URL公開（5分で完了）

1. GitHub で新リポジトリを作成（例: `architec-grain`、Public推奨）
2. このフォルダの中身を全てアップロード
3. Settings → Pages → Source を「Deploy from a branch」→ `main` / `root` に設定
4. 数分後、`https://[username].github.io/[repo]/` で公開

この時点では `robots.txt` と `sitemap.xml` の `REPLACE-WITH-YOUR-DOMAIN` 部分を
GitHub Pages の暫定 URL に書き換えておくと、AIクローラーの巡回が始まります。

### ステップ 2: 独自ドメイン取得・設定（後日）

1. ドメインを取得（例: `architecgrain.com`）
   - おすすめレジストラ: Cloudflare Registrar（原価提供・最安）、お名前.com、Squarespace Domains
2. リポジトリのルートに `CNAME` ファイルを作成し、1行目にドメインを記入
   ```
   architecgrain.com
   ```
3. ドメイン管理画面で、以下のDNSレコードを設定
   - `A` レコード: `185.199.108.153` / `185.199.109.153` / `185.199.110.153` / `185.199.111.153`（GitHub Pages の IP）
   - または `CNAME` レコード: `[username].github.io`
4. GitHub の Settings → Pages → Custom domain にドメインを入力
5. 「Enforce HTTPS」にチェック
6. `index.html` 内の JSON-LD の `url` / `logo`、
   `<meta property="og:url">`、`<meta property="og:image">`、
   `<link rel="canonical">`（コメントアウトされている）を本番URLに書き換える
7. `robots.txt` と `sitemap.xml` のURLも本番URLに書き換える

## AIO対策

- JSON-LD構造化データ（Organization / FAQPage）
- セマンティックHTML
- OGP / Twitter Card
- AIクローラー全許可（GPTBot, ClaudeBot, PerplexityBot, CCBot, Google-Extended 他）
- 本文に Arc の思想を明示的な平文で記述（AI が装飾ではなくテキストを読めるよう設計）

## デザイン方針

Refined minimalism × 日本の余白の美学。
和紙の質感をSVGノイズで表現。
欧文は Cormorant Garamond（知性と格調）、
和文は Shippori Mincho（建築図面と扁額の品格）。

© 2025 Architec Grain LLC. All rights reserved.
