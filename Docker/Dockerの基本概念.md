#docker

## イメージ

イメージは、アプリケーションを実行するために必要な全ての要素を含む読み取り専用のテンプレートです。具体的には以下のものが含まれます：

- OSの基本コンポーネント
- アプリケーションのバイナリーとソースコード
- ライブラリーや依存関係
- 設定ファイル
- 環境変数の設定

イメージは「料理のレシピ」に例えることができます。レシピには材料と手順が書かれているものの、それ自体は食べることができないのと同じように、イメージも単独では実行されません。

## コンテナ

コンテナは、イメージの実行中のインスタンスです。以下の特徴があります：

- イメージから作成される動的な実行環境
- 独立した実行空間を持つ
- 書き込み可能なレイヤーを持つ
- 他のコンテナと互いに影響を与えることなく実行可能

先ほどの料理の例えで言えば、コンテナは「レシピを基に実際に作られた料理」にあたります。

## 技術的特徴

### イメージの特徴

- 読み取り専用
- 変更不可（変更する場合は新しいイメージを作成）
- 複数のコンテナで再利用可能

### コンテナの特徴

- 動的な実行環境
- 起動・停止・削除が可能
- ファイルシステムの変更が可能（ただし、コンテナ停止時に失われる）
- 永続的なデータはボリュームを使用して保存

## まとめ

イメージとコンテナは密接に関連していますが、異なる役割を持ちます：

- **イメージ**：アプリケーションの静的な設計図
- **コンテナ**：その設計図を基に実行される動的なインスタンス

この関係を理解することで、Dockerをより効果的に活用することができます。
