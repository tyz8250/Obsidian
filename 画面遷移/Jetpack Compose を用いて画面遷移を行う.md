
## 目的
アプリのHOME画面から設定画面に移動するためのプログラムを作成する。

## 前提
HOME画面は作成しており、ヘッダーに設定ボタンを配置していること。

## 手順

build.gradle(:app) ファイルに依存関係を追加
```kotlin
implementation("androidx.navigation:navigation-compose:2.5.3") // 最新の安定版バージョンを使用してください``` 
