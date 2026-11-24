# PowerDesign Store - Vercelへの公開手順

このドキュメントでは、PowerDesign StoreサイトをVercel.appで公開するための手順を説明します。

## 📋 必要なもの

- GitHubアカウント
- Vercelアカウント
- Gitコマンドライン（またはGitHub Desktop）

## 🚀 デプロイ手順

### ステップ1: GitHubリポジトリを作成

1. [GitHub](https://github.com)にログイン
2. 「New repository」をクリック
3. リポジトリ名を入力：`powerdesign-store`
4. 説明（任意）：`PowerDesign - iPhone and Apple product skins`
5. 「Public」を選択（公開サイトのため）
6. 「Create repository」をクリック

### ステップ2: ローカルからGitHubにアップロード

ターミナルで以下のコマンドを実行：

```bash
# p_design_webディレクトリに移動
cd ~/Desktop/PowerDesign/p_design_web

# Gitリポジトリを初期化（まだなら）
git init

# すべてのファイルをステージング
git add .

# 最初のコミット
git commit -m "Initial commit: PowerDesign Store modern redesign"

# メインブランチの名前変更（古い環境の場合）
git branch -M main

# リモートリポジトリを追加
# 下記のURLを、あなたのGitHubリポジトリのURLに置き換えてください
git remote add origin https://github.com/YOUR_USERNAME/powerdesign-store.git

# GitHubにプッシュ
git push -u origin main
```

### ステップ3: Vercelにデプロイ

#### 方法A: Vercelウェブサイトから

1. [Vercel](https://vercel.com)にログイン（またはGitHubアカウントで新規登録）
2. 「New Project」をクリック
3. 「Import Git Repository」を選択
4. GitHubアカウントを接続
5. 「powerdesign-store」リポジトリを選択
6. インポート設定：
   - **Framework Preset**: 「Other」を選択
   - **Root Directory**: `p_design_web`に設定（リポジトリ構造による）
   - **Build Command**: 空欄（静的サイトの場合）
   - **Output Directory**: 空欄
7. 「Deploy」をクリック

#### 方法B: Vercel CLIから

```bash
# Vercel CLIのインストール（初回のみ）
npm install -g vercel

# p_design_webディレクトリに移動
cd ~/Desktop/PowerDesign/p_design_web

# Vercelにデプロイ
vercel --prod
```

### ステップ4: カスタムドメイン設定（オプション）

1. Vercelダッシュボードのプロジェクトを開く
2. 「Settings」→「Domains」
3. 「Add Domain」をクリック
4. ドメイン名を入力
5. DNS設定に従って、ドメインプロバイダー側で設定

## 📝 ファイル構造

```
p_design_web/
├── index_new.html         # メインページ（UTF-8、モダンHTML5）
├── styles.css             # レスポンシブスタイルシート
├── vercel.json            # Vercel設定ファイル
├── .gitignore             # Git除外ファイル
│
├── iPhone4/               # iPhone4関連ファイル
│   ├── carbon.jpg
│   ├── iPhone4Color_image.jpg
│   ├── top.jpg
│   ├── fake/
│   │   └── *.jpg
│   └── ...
│
├── iPhone3G/              # iPhone3G関連ファイル
│   └── ...
│
├── PRADAPhone/            # PRADAPhone関連ファイル
│   └── ...
│
├── MacBooAir/             # MacBook Air関連ファイル
│   └── ...
│
├── MacBookPro/            # MacBook Pro関連ファイル
│   └── ...
│
├── PSP/                   # PSP関連ファイル
│   └── ...
│
├── Windows/               # Windows関連ファイル
│   └── ...
│
├── card_image/            # 支払い方法のロゴ
│   └── *.gif
│
└── gazou/                 # その他の画像
    └── *.gif
```

## 🔄 更新・変更方法

サイトを更新したい場合：

```bash
# p_design_webディレクトリで
cd ~/Desktop/PowerDesign/p_design_web

# ファイルを編集

# 変更をステージング
git add .

# コミット
git commit -m "変更内容の説明"

# GitHubにプッシュ
git push

# Vercelが自動的にデプロイします（数秒～数分）
```

## 🎨 デザインの改善点

新しい版では以下の改善が施されています：

✅ **モダンHTML5** - セマンティックなタグ構造  
✅ **UTF-8エンコーディング** - 文字化けなし  
✅ **レスポンシブデザイン** - スマートフォン・タブレット対応  
✅ **改善されたUX** - ホバーエフェクト、スムーズなスクロール  
✅ **アクセシビリティ** - 適切なAlt属性、セマンティックマークアップ  
✅ **パフォーマンス** - 最適化されたCSSスタイル  
✅ **ダークモード対応** - ユーザーの設定に応じて自動切り替え  

## ⚠️ 注意事項

1. **外部リンク**: 一部の外部リンク（bodymask.cart.fc2.com など）は、公開時に有効かどうか確認してください
2. **アクセスカウンター**: 旧式のカウンター機能は削除されています
3. **古いHTMLファイル**: `index.html`（元のShift_JIS版）は`index_new.html`に置き換わります

## 🆘 トラブルシューティング

### デプロイに失敗する
- GitHubリポジトリが公開されているか確認
- ファイル数が大きすぎないか確認（Vercel無料プランの制限）

### 画像が表示されない
- 相対パスが正しいか確認
- ファイル名の大文字・小文字を確認（特にMacでは重要）

### CSSが反映されない
- ブラウザキャッシュをクリア（Ctrl+Shift+Delete）
- Vercelの再デプロイを待つ

## 📞 サポート

- Vercel Documentation: https://vercel.com/docs
- GitHub Help: https://docs.github.com
- 問題が解決しない場合は、メールでお問い合わせください: renkon555@gmail.com

---

**作成日**: 2026年11月24日  
**最終更新**: 2026年11月24日
