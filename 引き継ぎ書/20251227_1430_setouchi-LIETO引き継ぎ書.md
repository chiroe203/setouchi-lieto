# setouchi LIETO ウェブサイト 引き継ぎ書

## プロジェクト概要

| 項目 | 内容 |
|------|------|
| プロジェクト名 | setouchi LIETO（セトウチ リエット） |
| 種類 | 柑橘農園のウェブサイト |
| 所在地 | 愛媛県今治市・大三島（しまなみ海道中間地点） |
| ドメイン | setouchi-lieto.com |
| 技術 | 静的HTML（シングルページ、タブ切り替え） |
| デプロイ先 | Vercel（GitHub連携） |

### 「LIETO」の意味
イタリア語で「楽しい」「陽気」という意味。

---

## 公開URL

| 種類 | URL |
|------|-----|
| 本番サイト | https://setouchi-lieto.com |
| 本番サイト（www） | https://www.setouchi-lieto.com |
| Vercel URL | https://setouchi-lieto.vercel.app |
| GitHubリポジトリ | https://github.com/chiroe203/setouchi-lieto |

---

## 完了した作業（2025/12/27）

### 1. GitHubリポジトリ作成・プッシュ
- リポジトリ名: `setouchi-lieto`
- ユーザー名: `chiroe203`
- HTMLファイルと画像をすべてアップロード完了

### 2. Vercelデプロイ
- GitHubと連携して自動デプロイ設定完了
- Framework Preset: Other（静的HTML）

### 3. カスタムドメイン設定
- ドメイン管理: さくらインターネット
- DNS設定を変更してVercelに向けた

| エントリ名 | タイプ | 値 |
|-----------|--------|-----|
| @ | A | 216.198.79.1 |
| www | CNAME | 3a44315211381d95.vercel-dns-017.com. |

### 4. Google Search Console
- 所有権確認完了（TXTレコードで認証）
- プロパティ: setouchi-lieto.com

### 5. Google Analytics
- 測定ID: **G-4876N30XET**
- index.htmlにトラッキングコード追加済み

---

## サイト構成

### ナビゲーション
- **ホーム** - メインコンテンツ
- **ご購入** - ポケットマルシェへのリンク
- **お知らせ** - Facebook埋め込み
- **SNSアイコン** - Facebook・Instagram（ナビバー右側）

### ホームページ構成
1. **ヒーロースライダー** - 3枚の画像が自動切り替え
2. **About Us** - 農園紹介文
3. **柑橘セクション** - 4品種（モーダル付き）
4. **加工品セクション** - 2品目（モーダル付き）
5. **フッター** - SNSリンク

### ご購入ページ
- ポケットマルシェへのリンクボタン
- URL: https://poke-m.com/producers/265442

### お知らせページ
- Facebook Page Plugin埋め込み
- Facebookページへの直接リンク

---

## SNSリンク

| プラットフォーム | URL |
|-----------------|-----|
| Facebook | https://www.facebook.com/setouchi.LIETO/ |
| Instagram | https://www.instagram.com/setouchi.lieto/ |

---

## ファイル構成

```
setouchi LIETO/
├── index.html          ← メインHTMLファイル（Google Analytics追加済み）
└── images/
    ├── favicon.png     ← ブラウザタブアイコン
    ├── logo.png        ← ナビゲーションロゴ
    │
    │── [ヒーロースライダー]
    ├── hero-1.jpg
    ├── hero-2.jpg
    ├── hero-3.jpg
    │
    │── [柑橘カード用]
    ├── madonna.jpg
    ├── harehime.jpg
    ├── himekoharu-kanpei.jpg
    ├── others.jpg
    │
    │── [柑橘モーダルスライダー用]
    ├── madonna-1.jpg
    ├── madonna-2.jpg
    ├── madonna-3.jpg
    ├── harehime-1.jpg
    ├── harehime-2.jpg
    ├── himekoharu-kanpei-1.jpg
    ├── himekoharu-kanpei-2.jpg
    ├── others-1.jpg
    ├── others-2.jpg
    │
    │── [加工品カード用]
    ├── juice.jpg
    ├── honey.jpg
    │
    │── [加工品モーダルスライダー用]
    ├── juice-1.jpg
    ├── juice-2.jpg
    ├── honey-1.jpg
    └── honey-2.jpg
```

---

## サイト更新方法

### ファイルを変更した場合

```bash
cd ~/Desktop/setouchi\ LIETO
git add .
git commit -m "変更内容のメモ"
git push
```

これだけでVercelが自動的に再デプロイします（1〜2分で反映）。

### コミットメッセージの例
- `"画像を更新"`
- `"ヒーロー画像を差し替え"`
- `"まどんなの説明文を修正"`
- `"新商品を追加"`

---

## ローカルでのプレビュー方法

```bash
# フォルダに移動
cd ~/Desktop/setouchi\ LIETO

# 簡易サーバー起動
npx serve

# ブラウザで開く
# http://localhost:3000
```

---

## 管理画面リンク

| サービス | URL |
|---------|-----|
| GitHub | https://github.com/chiroe203/setouchi-lieto |
| Vercel | https://vercel.com/ |
| Google Analytics | https://analytics.google.com/ |
| Google Search Console | https://search.google.com/search-console |
| さくらインターネット | https://secure.sakura.ad.jp/menu/domain/ |

---

## カラーパレット

| 変数名 | カラーコード | 用途 |
|--------|-------------|------|
| `--olive-dark` | #6B7B3D | フッター背景、文字色 |
| `--olive-medium` | #8A9B5C | サブカラー |
| `--olive-light` | #C5D4A8 | 背景アクセント |
| `--orange-citrus` | #E8A832 | メインアクセント |
| `--orange-pale` | #FFF8E8 | 背景色（柑橘セクション） |
| `--cream` | #FDFAF5 | ベース背景色 |
| `--text-dark` | #4A5530 | テキスト（濃） |
| `--text-light` | #6B7B5D | テキスト（薄） |

---

## 画像について

### 注意点
- HEICファイルは**変換が必要**（ファイル名変更だけでは不可）
- Macのプレビューで「ファイル」→「書き出す」→「JPEG」で変換
- 推奨サイズ: 1600〜2000px幅、200〜500KB

---

## 削除・非表示にした要素

- **所在地セクション**: 住所の公表をしないため全削除
- **フッター住所**: 同上の理由で削除
- **ご購入ページのメール案内文**: 削除
- **栽培へのこだわりセクション**: シンプルにするため未実装

---

## 作成日
2025年12月27日

## ファイル保存場所
`~/Desktop/setouchi LIETO/`
