#python #json
Pythonでは、`json`モジュールを使用してJSONファイルを読み込むことができます。以下にその基本的な手順を示します。

## JSONファイルの準備

まず、読み込むJSONファイルを用意します。例えば、次のような内容の`data.json`というファイルを考えます：

```json
{
    "name": "山田太郎",
    "age": 30,
    "city": "東京"
}
```

## Pythonコードでの読み込み

次に、Pythonコードを使ってこのファイルを読み込みます。以下はその手順です：

1. `json`モジュールをインポートします。
2. `open()`関数を使用してファイルを開きます。
3. `json.load()`メソッドでファイルの内容を読み込みます。

### サンプルコード

```python
import json

# JSONファイルを開く
with open('data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# データを表示する
print(data)
```

このコードでは、ファイルを読み込み、内容をPythonの辞書として`data`に格納し、コンソールに出力します。

## 重要なポイント

- **ファイルのエンコーディング**：UTF-8を指定することで、日本語などの非ASCII文字に対応できます。
- **エラーハンドリング**：ファイルが存在しない場合や、フォーマットが不正な場合に備えて、エラーハンドリングを追加することを考慮するといいでしょう。例えば、`try-except`文を使って読み込み処理を囲むことができます。

### エラーハンドリングの例

```python
try:
    with open('data.json', 'r', encoding='utf-8') as f:
        data = json.load(f)
        print(data)
except FileNotFoundError:
    print('ファイルが見つかりません。')
except json.JSONDecodeError:
    print('JSONデータの読み込みに失敗しました。')
```

このようにして、PythonでJSONファイルを受け取る処理を簡単に実装できます。

ファイルを開く際には、`with open()`文を使うことでファイルを自動的に閉じることができ、リソース管理が向上します。また、JSONデータが正しく読み込まれた場合は、辞書形式としてアクセスしやすくなる他、特定のキーの値に直接アクセスすることが可能です。

さらに、JSONファイルから読み込んだデータを利用して処理を行う例として、特定の情報を抽出したり、データを更新したりする方法も考慮することが大切です。以下に、読み込んだデータに対して特定の処理を行う例を示します。

### 特定のキーにアクセスする例

```python
print(data['name'])  # 出力: 山田太郎
print(data['age'])   # 出力: 30
```

### データの更新

```python
data['age'] = 31  # 年齢を更新

# 更新した内容を再びJSONファイルに書き込む
with open('data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f, ensure_ascii=False, indent=4)
```

このように、JSONの読み込みだけでなく、その後のデータ処理やファイルへの書き込みも簡単に行えます。加えて、`json.dump()`メソッドの`ensure_ascii=False`引数を使うことで、日本語などの非ASCII文字をそのまま保存することができるため、見やすさに配慮したフォーマットで出力できます。