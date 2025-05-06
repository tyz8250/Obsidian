#docker 

## 目的

開発・テスト用の3つのコンテナ（Nginx、Apache、MySQL）を簡単に起動・管理・破棄できる環境を構築します。

## 基本要件

- デタッチモード（-d）での実行が必須 [[デタッチモードについて]]
- コンテナ名の明示的な指定（[[Dockerコンテナの名前指定（--name）について]]）
- 異なるポートでの実行 ([[Dockerの - pオプションについて]])
- アプリケーションデータの設定は不要

## コンテナ構成

| サービス   | コンテナ名       | ポート設定     | 用途      |
| ------ | ----------- | --------- | ------- |
| Nginx  | test-nginx  | 80:80     | Webプロキシ |
| Apache | test-apache | 8080:80   | Webサーバー |
| MySQL  | test-mysql  | 3306:3306 | データベース  |

## セットアップ手順

### 1. コンテナの起動

```bash
# Nginxの起動
docker run -d --name test-nginx -p 80:80 nginx

# Apacheの起動
docker run -d --name test-apache -p 8080:80 httpd

# MySQLの起動（ランダムパスワード使用）
docker run -d --name test-mysql \
  -p 3306:3306 \
  -e MYSQL_RANDOM_ROOT_PASSWORD=yes \
  mysql
```

### 2. 起動確認とパスワード取得

```bash
# コンテナの状態確認
docker ps

# MySQLのパスワード確認
docker logs test-mysql | grep GENERATED
```

### 3. 環境の破棄

```bash
# コンテナの停止
docker stop test-nginx test-apache test-mysql

# コンテナの削除
docker rm test-nginx test-apache test-mysql

# 確認
docker ps -a
```

## 管理用コマンド集

### 基本操作

```bash
# 実行中のコンテナ確認
docker ps

# 全コンテナ確認（停止中含む）
docker ps -a

# 個別のログ確認
docker logs [コンテナ名]

# システムクリーンアップ
docker system prune
```

## トラブルシューティング

### よくある問題と解決方法

1. ポート競合

```bash
CopyCopyCopyCopyCopyCopyCopyCopy# 別のポートを指定して再起動
docker run -d --name test-nginx -p 8000:80 nginx
```

2. コンテナ起動エラー

```bash
CopyCopyCopyCopyCopyCopyCopyCopy# ログの確認
docker logs [コンテナ名]

# コンテナの状態確認
docker inspect [コンテナ名]
```

## 注意事項

1. **環境変数の利用**

- テスト環境では環境変数で簡単に設定可能
- 本番環境では適切なセキュリティ設定が必要

2. **リソース管理**

- 不要なコンテナは速やかに削除
- 定期的なシステムクリーンアップを推奨

3. **セキュリティ**

- テスト環境専用の設定であることを認識
- MySQLのパスワードは適切に管理

## 補足情報

- コンテナ名は任意に変更可能
- ポート番号は環境に応じて調整
- 本番環境では永続化とセキュリティ設定が必要

このガイドに従うことで、開発・テスト用の3コンテナ環境を効率的に管理できます。必要に応じて環境を作成・破棄し、開発作業を円滑に進めることができます。