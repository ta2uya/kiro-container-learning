# Kiro Container Learning

Amazon Kiroと一緒にDockerとAWS ECS Fargateを学んだ3日間の記録

## 概要

このリポジトリは、AWSインフラエンジニアがコンテナ技術を学ぶために、Amazon Kiroを活用しながら実践した学習プロジェクトの成果物です。

### 学習内容
- Docker基礎（コンテナとは、仮想マシンとの違い）
- Dockerfileの作成とイメージビルド
- Amazon ECRへのイメージ管理
- Amazon ECS Fargateでのコンテナ実行
- AWS環境でのネットワーキング設定

### 期間
2025年1月8日〜1月22日（左記の中で約3日間の実作業）

---

## プロジェクト構成
```
kiro-container-learning/
├── README.md                    # このファイル
├── docs/                        # 学習記録
│   ├── kiro-chat-log.md        # Kiroとの対話記録
│   └── learning-notes.md       # 学習メモと振り返り
├── webapp/                      # Webアプリケーション
│   ├── index.html              # サンプルHTML
│   └── Dockerfile              # コンテナイメージ定義
└── screenshots/                 # スクリーンショット
    ├── day1/                   # Day 1: Docker基礎
    ├── day2/                   # Day 2: ECRへpush
    └── day3/                   # Day 3: ECS Fargate実行
```

---

## 学習の流れ

### Day 1: コンテナ基礎理解
- Kiroに「コンテナとは何か」から質問
- Docker Desktopインストール
- Nginxコンテナの起動確認

**学んだこと:**
- コンテナと仮想マシンの違い
- Dockerの基本コマンド

**躓いたポイント:**
- Docker Desktopのメモリ消費（8GB環境での設定判断）

### Day 2: Dockerイメージ作成とECR
- 簡単なWebアプリ（HTML）を作成
- Dockerfileを作成してイメージビルド
- Amazon ECRへpush

**学んだこと:**
- Dockerfileの書き方
- ECRとDocker Desktopの関係性
- ビルド、デプロイ、リリースの違い

**躓いたポイント:**
- HTMLの文字化け（charset指定忘れ）
- 「ECRってAWSのサービスなのに、なぜローカルでDockerが必要？」問題

### Day 3: ECS Fargateで実行
- VPC、サブネット、セキュリティグループ設定
- ECSクラスター、タスク定義、サービス作成
- インターネット公開成功

**学んだこと:**
- ECSの構成要素（クラスター、タスク定義、サービス）
- Fargateのサーバーレス実行
- セキュリティグループの重要性

**躓いたポイント:**
- サービスリンクロールエラー
- イメージタグ不一致（v1 vs latest）
- セキュリティグループ設定ミス
- 文字化け再発（再ビルド・再pushの必要性）

---

## 使用技術

### ローカル環境
- Windows 11
- Docker Desktop
- AWS CLI

### AWS環境
- Amazon ECR
- Amazon ECS (Fargate)
- Amazon VPC
- CloudWatch Logs

### 学習支援ツール
- Amazon Kiro

---

## 成果物

### デプロイされたWebアプリ
簡単なHTML（🐳 Kiro学習プロジェクト）をNginxコンテナでホスティング

### 学習記録
- [Kiroとの対話記録](./docs/kiro-chat-log.md)
- [学習メモと振り返り](./docs/learning-notes.md)

---

## セットアップ手順

### ローカルでの実行
```bash
# リポジトリのクローン
git clone https://github.com/ta2uya/kiro-container-learning.git
cd kiro-container-learning/webapp

# Dockerイメージのビルド
docker build -t kiro-webapp:latest .

# コンテナの起動
docker run -d -p 8080:80 kiro-webapp:latest

# ブラウザでアクセス
# http://localhost:8080
```

### AWS ECS Fargateへのデプロイ

詳細な手順は [学習記録](./docs/learning-notes.md) を参照してください。

---

## 学びのポイント

### 1. Kiroの活用方法
- 基礎的な質問から段階的に理解を深められる
- エラーメッセージをそのまま投げても的確に解決
- 「なぜ？」を繰り返すことで本質的な理解が進む

### 2. インフラエンジニアとしての気づき
- AWSコンソールのUIは頻繁に変わる（手順書との差異に注意）
- 「何を実現したいか」を理解していれば対応できる
- トラブルシュートの経験が最も価値のある学び

### 3. コンテナ技術の理解
- コンテナ = アプリケーションとその依存関係のパッケージ
- ECR = クラウドの倉庫、Docker Desktop = ローカルの工場
- ビルド → push → デプロイの一連の流れの重要性

---

## 関連記事

- [Zenn記事](リンク予定)（執筆予定）
- [次回: Lambda編](リンク予定)（学習予定）

---

## ライセンス

MIT License

---

## Author

[@ta2uya](https://github.com/ta2uya)
