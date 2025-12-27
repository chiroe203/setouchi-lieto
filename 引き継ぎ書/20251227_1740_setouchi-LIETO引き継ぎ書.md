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

## 完了した作業（2025/12/27 17:40）

### 1. About Usセクションのレスポンシブ改行対応

スマホとPCで異なる改行位置を設定できるようにした。

#### 追加したCSS
```css
/* スマホ用改行（PCでは無視） */
.br-sp {
  display: none;
}

@media (max-width: 768px) {
  .br-sp {
    display: inline;
  }
}
```

#### 使い方
- `<br>` → PC・スマホ両方で改行
- `<br class="br-sp">` → スマホでのみ改行（PCでは無視）

#### 設定した改行位置

**スマホ表示：**
```
瀬戸内海にある大三島に
setouchi LIETO はあります

広島県尾道市と
愛媛県今治市を結ぶ、
サイクリングロードとしても有名な
『しまなみ海道』の
ちょうど中間地点に位置しています

瀬戸内は温暖で
年間を通し降水量が少なく
柑橘栽培に適した気候です

LIETO（リエット）は
「楽しい」「陽気」などの
意味があります
瀬戸内海の穏やかな潮風と
太陽をたくさん浴びた
フレッシュな柑橘と
楽しくなるような気持ちも込めて
お届けします
```

**PC表示：**
```
瀬戸内海にある大三島にsetouchi LIETO はあります

広島県尾道市と愛媛県今治市を結ぶ、
サイクリングロードとしても有名な
『しまなみ海道』の
ちょうど中間地点に位置しています

瀬戸内は温暖で年間を通し降水量が少なく
柑橘栽培に適した気候です

LIETO（リエット）は「楽しい」「陽気」などの意味があります
瀬戸内海の穏やかな潮風と太陽をたくさん浴びた
フレッシュな柑橘と
楽しくなるような気持ちも込めてお届けします
```

### 2. モーダルスライダーのCSS修正

まどんなの3枚目画像が表示されない問題に対応してCSSを修正。

```css
.modal-slide {
  min-width: 100%;
  width: 100%;
  height: 100%;
  flex-shrink: 0;  /* 追加：スライドが縮小されないように */
}

.modal-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;  /* 追加：余計な余白を防止 */
}
```

### 3. madonna-3.jpgの画像形式修正

**問題**: ファイル名は`.jpg`だったが、中身がHEIC形式（iPhoneの写真形式）のままだった。ブラウザはHEIC形式を直接表示できないため、画像が読み込めなかった。

**解決**: Macのプレビュー.appで「ファイル」→「書き出す」→「JPEG」で正しく変換。

---

## 画像について（重要な注意点）

### HEIC→JPEG変換の確認方法

ターミナルで以下のコマンドを実行すると、ファイルの実際の形式がわかる：

```bash
file images/ファイル名.jpg
```

- 正しいJPEG: `JPEG image data`と表示される
- 問題あり: `ISO Media, HEIF Image`と表示される（HEICのまま）

### 正しい変換手順（Mac）

1. 画像をプレビュー.appで開く
2. メニューの「ファイル」→「書き出す...」
3. フォーマットを「JPEG」に選択
4. 「保存」をクリック

**注意**: Finderでファイル名を`.heic`から`.jpg`に変更しただけでは、中身は変換されない！

---

## Git操作の注意点

### GitHub上でファイルを削除した後にpushする場合

GitHub上で直接ファイルを削除すると、ローカルとリモートの履歴がずれてエラーになる。

```
error: failed to push some refs to 'https://github.com/...'
hint: Updates were rejected because the remote contains work that you do not have locally.
```

**解決方法:**
```bash
git pull                    # リモートの変更を取り込む
git add ファイル名           # ファイルを追加
git commit -m "メッセージ"
git push
```

---

## サイト更新方法

### 通常の更新手順

```bash
cd ~/Desktop/setouchi\ LIETO
git add .
git commit -m "変更内容のメモ"
git push
```

Vercelが自動的に再デプロイ（1〜2分で反映）。

---

## ファイル構成

```
setouchi LIETO/
├── index.html          ← メインHTMLファイル（Google Analytics追加済み）
└── images/
    ├── favicon.png
    ├── logo.png
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
    ├── madonna-3.jpg   ← JPEG形式に変換済み
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

## 管理画面リンク

| サービス | URL |
|---------|-----|
| GitHub | https://github.com/chiroe203/setouchi-lieto |
| Vercel | https://vercel.com/ |
| Google Analytics | https://analytics.google.com/ |
| Google Search Console | https://search.google.com/search-console |
| さくらインターネット | https://secure.sakura.ad.jp/menu/domain/ |

---

## SNSリンク

| プラットフォーム | URL |
|-----------------|-----|
| Facebook | https://www.facebook.com/setouchi.LIETO/ |
| Instagram | https://www.instagram.com/setouchi.lieto/ |

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

## 作成日
2025年12月27日 17:40

## ファイル保存場所
`~/Desktop/setouchi LIETO/`
