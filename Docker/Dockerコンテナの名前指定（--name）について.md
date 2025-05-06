#docker 
## 基本概念

`--name`オプションは、Dockerコンテナに明示的に名前を付けるための機能です。これにより、コンテナの識別と管理が容易になります。

### 基本構文

```bash
docker run --name [コンテナ名] [その他のオプション] [イメージ名]
```

## 使用例

### 基本的な例

```bash
# Nginxコンテナを起動
docker run -d --name my-web nginx

# MySQLコンテナを起動
docker run -d --name db-server \
  -e MYSQL_ROOT_PASSWORD=mypassword \
  mysql
```

### 実践的な例

```bash
# 開発環境用Webサーバー
docker run -d --name dev-web -p 8080:80 nginx

# テスト環境用データベース
docker run -d --name test-db \
  -e MYSQL_ROOT_PASSWORD=test123 \
  mysql
```

## 命名規則とベストプラクティス

### 使用可能な文字

- 小文字（a-z）
- 大文字（A-Z）
- 数字（0-9）
- 特殊文字（ハイフン[-]、アンダースコア[_]）

### 推奨される命名パターン

```bash
# 環境-サービス-役割
dev-web-nginx
prod-db-mysql

# プロジェクト-機能-環境
myapp-auth-dev
myapp-api-prod
```