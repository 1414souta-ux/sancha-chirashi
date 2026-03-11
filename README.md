# 🛒 SMART CART — 買い物最適化エージェント

三軒茶屋・太子堂エリアの**5スーパー横断**で価格比較・レシピ提案・コスパスコアを自動生成するPWAアプリです。

[![Deploy to GitHub Pages](https://github.com/YOUR_USERNAME/smart-cart/actions/workflows/deploy.yml/badge.svg)](https://github.com/YOUR_USERNAME/smart-cart/actions/workflows/deploy.yml)

---

## 🏪 対象店舗

| # | 店舗名 | 営業時間 | 強み |
|---|--------|----------|------|
| 1 | ベルクス 太子堂 | 9:00–22:00 | 安さ重視・特売品豊富 |
| 2 | ダイエー 三軒茶屋 | 10:00–22:00 | 品揃え豊富・ポイント還元 |
| 3 | サミット 下馬店 | 9:00–24:00 | 深夜営業・PB充実 |
| 4 | 西友 三軒茶屋 | 24時間 | EDLP戦略・日用品も豊富 |
| 5 | オオゼキ 三軒茶屋店 | 9:00–21:00 | 鮮魚・精肉が強み |

---

## ✨ 機能

- **🔍 買い物リスト分析** — 食材を入力すると5店舗の価格比較を瞬時に生成
- **📊 コスパスコア** — AIが100点満点で各店舗をスコアリング（バーグラフ + 王冠表示）
- **💴 価格比較テーブル** — 最安値（緑）・最高値（赤）でハイライト
- **📄 チラシ画像解析** — PNG/JPGのチラシをVision AIが自動解析
- **🍳 レシピ提案** — 予算・食材条件から最安購入先付きレシピを生成
- **⚡ クイックアクション** — 特売チェック・今日のレシピ等をワンクリック
- **📱 PWA対応** — ホーム画面追加・オフラインUI・ショートカット対応

---

## 🚀 セットアップ

### 1. リポジトリをクローン

```bash
git clone https://github.com/YOUR_USERNAME/smart-cart.git
cd smart-cart
```

### 2. APIキーを設定

`config.js` を作成します（`.gitignore` 済み、コミットされません）：

```js
// config.js
window.ANTHROPIC_API_KEY = 'sk-ant-...your-key...';
```

APIキーは [Anthropic Console](https://console.anthropic.com) から取得してください。

### 3. ローカルで起動

```bash
# Python 3
python3 -m http.server 8000

# または Node.js
npx serve .
```

ブラウザで `http://localhost:8000` を開きます。

---

## 🌐 GitHub Pages へのデプロイ

### 自動デプロイ（推奨）

1. GitHubリポジトリの **Settings → Pages** を開く
2. Source を **GitHub Actions** に設定
3. `main` ブランチにプッシュすると自動デプロイされます

```bash
git add .
git commit -m "feat: initial deploy"
git push origin main
```

数分後に `https://YOUR_USERNAME.github.io/smart-cart/` で公開されます。

### ⚠️ CORS に関する注意

GitHub Pages から Anthropic API を直接呼び出す場合、**CORSエラーが発生する可能性**があります。

**解決策（推奨）**: Cloudflare Workers や Vercel Edge Functions を使ったAPIプロキシを設置し、`index.html` のAPIエンドポイントをプロキシURLに変更してください。

claude.ai の Artifact 環境では認証が自動処理されるため問題ありません。

---

## 📁 ファイル構成

```
smart-cart/
├── index.html                  # メインアプリ（HTML/CSS/JS一体型）
├── manifest.json               # PWA設定
├── sw.js                       # Service Worker（キャッシュ戦略）
├── config.js                   # APIキー設定（.gitignore済み）
├── icons/
│   ├── icon-192x192.png        # PWAアイコン（Android/Chrome）
│   ├── icon-512x512.png        # PWAアイコン（スプラッシュ）
│   └── apple-touch-icon.png    # iOSホーム画面アイコン
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions自動デプロイ
├── .gitignore
└── README.md
```

---

## 🛠 技術スタック

| 要素 | 技術 |
|------|------|
| フロントエンド | Vanilla HTML / CSS / JavaScript（依存ライブラリなし） |
| AI | Anthropic Claude API（claude-sonnet-4-20250514） |
| Vision | Claude Vision API（チラシ画像解析） |
| ホスティング | GitHub Pages（静的・HTTPS） |
| PWA | Service Worker + Web App Manifest |
| CI/CD | GitHub Actions |

---

## 📋 使い方

1. サイドバーの入力欄に食材・商品名を入力（例：`鶏もも肉・豆腐・キャベツ`）
2. 「AIで分析する」ボタンをクリック（または `Ctrl+Enter`）
3. コスパスコア・価格比較・分析結果が表示される
4. チラシ画像をアップロードすると特売情報も考慮した分析が可能

---

## 🗺 今後の拡張予定

- [ ] APIプロキシ（Cloudflare Workers）によるCORS解消
- [ ] 価格履歴データベース（IndexedDB）
- [ ] 週間買い物プラン自動生成
- [ ] プッシュ通知（特売開始案内）
- [ ] お気に入り商品登録

---

## 📄 ライセンス

MIT License — 個人・商用問わず自由に使用可能

---

*設計書バージョン 1.0.0 (2026-03-10) に基づいて実装*
