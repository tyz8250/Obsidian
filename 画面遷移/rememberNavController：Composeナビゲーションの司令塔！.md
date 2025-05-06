

### rememberNavController とは？

`rememberNavController` は、Jetpack Compose でナビゲーションを制御するための **`NavController`** を作成する関数です。

- **NavController を生成**: `rememberNavController()` を呼び出すと、 `NavController` オブジェクトが生成されます。
- **状態の保持**: `remember` を使用しているため、コンポジションが再実行されても `NavController` の状態（現在の画面、バックスタックなど）が保持されます。
- **画面遷移の制御**: 生成された `NavController` は、 `navigate()` や `popBackStack()` などの関数を使用して、画面遷移を制御するために使用されます。

### 使い方

1. `rememberNavController()` を呼び出して `NavController` を作成します。

Kotlin

```
val navController = rememberNavController()
```

コードは[注意](/faq#coding)してご使用ください。

2. `NavHost` に `navController` を渡します。

Kotlin

```
NavHost(navController = navController, startDestination = "home") {
    // ... 画面の定義
}
```

コードは[注意](/faq#coding)してご使用ください。

3. 画面遷移を行う際に `navController` を使用します。

Kotlin

```
Button(onClick = { navController.navigate("settings") }) {
    Text("設定画面へ")
}
```

コードは[注意](/faq#coding)してご使用ください。

### ポイント

- `rememberNavController()` は、Composable 関数内で呼び出す必要があります。
- `NavController` は、状態ホイスティングの原則に従って、最上位の Composable 関数で定義し、下位の Composable 関数に渡すことが推奨されます。
- `NavController` を使用することで、画面遷移だけでなく、画面間でのデータの受け渡しや、深いリンクへの対応なども行えます。

### まとめ

- `rememberNavController` は、Jetpack Compose でナビゲーションを制御するための `NavController` を作成する関数です。
- `remember` を使用しているため、コンポジションが再実行されても `NavController` の状態が保持されます。
- `NavController` を使用することで、画面遷移をシンプルかつ柔軟に実装できます。