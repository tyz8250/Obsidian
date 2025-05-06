#docker
## Docker runの裏側で起きていること
- Look for that image locally in iimage cache, doesn't find anything
- Then looks in remote image repository(defauits to Docker Hub)
- Downloads the latest version(nginx:latest by default)
- Creates new container based on that image and prepares to start
- Open up port 80 on host and fowards to post 80 in container
- Gives it a vertual IP on a private network inside docker engine
- Starts container by using the CMD in the image Dockerfile
## 概要

`docker run`コマンドを実行すると、Dockerは以下の7つのステップを自動的に実行します。各ステップを詳しく見ていきましょう。

## 詳細なステップ解説

### 1. ローカルイメージの確認

- まず、指定されたイメージがローカル環境にあるか確認します
- これは、以前にダウンロードして保存されているイメージを再利用するためです

### 2. リモートリポジトリの検索

- ローカルに見つからない場合、Docker Hubを検索します
- Docker Hubは、Dockerの公式イメージ保管庫です

### 3. イメージのダウンロード

- 最新バージョン（例：nginx:latest）をダウンロードします
- ダウンロード進捗状況が画面に表示されます

### 4. コンテナの作成準備

- ダウンロードしたイメージを基に、新しいコンテナを作成します
- 実行環境の初期設定を行います

### 5. ポートの設定

- ホストマシンのポート（例：80番）を開きます
- コンテナ内の対応するポートへの転送設定を行います

### 6. ネットワークの設定

- コンテナ用の仮想IPアドレスを割り当てます
- Dockerの内部ネットワークに接続します

### 7. コンテナの起動

- Dockerfileに記述された起動コマンド（CMD）を実行します
- アプリケーションが起動します

## 実行例

```bash
CopyCopyCopyCopyCopyCopy# Nginxコンテナを起動する例
docker run -d -p 80:80 nginx

# コンテナの状態確認
docker ps
```

## 重要なポイント

1. 自動化されたプロセス
    
    - 全ての手順が自動的に実行されます
    - エラーが発生した場合は、そのステップで停止します
2. 効率的な実行
    
    - ローカルにイメージがある場合、ダウンロードはスキップされます
    - 複数のコンテナで同じイメージを共有できます
3. カスタマイズ可能
    
    - ポート番号の変更が可能です
    - 環境変数の設定ができます
    - ボリュームのマウントが可能です