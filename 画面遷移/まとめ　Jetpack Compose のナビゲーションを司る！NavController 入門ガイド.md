
### はじめに

この記事では、Jetpack Compose での画面遷移をスムーズに行うための重要なコンポーネント、`NavController` について解説します。初心者の方にも分かりやすいように、基本的な使い方から実際のコード例、そしてよくある質問までを網羅しています。

### 目次

1. NavController とは？
2. NavController の基本的な使い方
3. 画面遷移の実装
4. データの受け渡し
5. よくある質問
6. まとめ

### 1. NavController とは？

`NavController` は、Jetpack Compose のナビゲーションシステムの中核を担うコンポーネントです。アプリ内の様々な画面（Composable）間の遷移を管理し、ユーザーが画面を移動したり戻ったりする操作をスムーズに処理します。

- **画面遷移の制御**: `navigate()` 関数を使って、指定した画面に遷移できます。
- **履歴管理**: ユーザーが訪れた画面の履歴を保持し、戻るボタンの動作などを自動的に処理します。
- **データの受け渡し**: 画面間でデータを受け渡すことができます。

### 2. NavController の基本的な使い方

`NavController` を使用するには、まず `androidx.navigation:navigation-compose` 依存関係をプロジェクトに追加する必要があります。

Kotlin

```
implementation("androidx.navigation:navigation-compose:2.5.3") // 最新の安定版バージョンを使用してください
```

次に、[[`NavHost` ]]コンポーネントと [`rememberNavController` ]()関数を使って、`NavController` を作成し、ナビゲーションのルートを定義します。

Kotlin

```
@Composable
fun MyScreen() {
    val navController = rememberNavController() // NavControllerを作成

    NavHost(navController = navController, startDestination = "home") {
        // ... 画面の定義
    }
}
```


- `rememberNavController()`: `NavController` を作成します。
- `NavHost`: ナビゲーションのルートを定義します。
    - `navController`: 先ほど作成した `NavController` を渡します。
	    - `startDestination`: アプリ起動時の初期画面のルートを指定します。

### 3. 画面遷移の実装

`composable` 関数を使って、各画面のルートと、そのルートに対応する Composable 関数を定義します。

Kotlin

```
NavHost(navController = navController, startDestination = "home") {
    composable("home") { HomeScreen() }
    composable("settings") { SettingsScreen() }
}
```

コードは[注意](/faq#coding)してご使用ください。

画面遷移を行うには、`navController.navigate(route)` を使用します。  

[

1. wolfia.com

](https://wolfia.com/?ref=theresanaiforthat)

[

wolfia.com

](https://wolfia.com/?ref=theresanaiforthat)

Kotlin

```
IconButton(onClick = { navController.navigate("settings") }) {
    // ...
}
```

コードは[注意](/faq#coding)してご使用ください。

### 4. データの受け渡し

画面間でデータを受け渡すには、`navController.navigate()` の引数にデータを含めることができます。

Kotlin

```
navController.navigate("detail/$itemId")
```

コードは[注意](/faq#coding)してご使用ください。

遷移先の画面では、`NavBackStackEntry.arguments` からデータを取得できます。

Kotlin

```
@Composable
fun DetailScreen(navBackStackEntry: NavBackStackEntry) {
    val itemId = navBackStackEntry.arguments?.getString("itemId")
    // ...
}
```

コードは[注意](/faq#coding)してご使用ください。

### 5. よくある質問

- **Q: 戻るボタンの処理はどうすればいいですか？**
    
    - A: `NavController` は自動的に戻るボタンの動作を処理します。明示的に戻る場合は、`navController.popBackStack()` を使用します。
- **Q: Bottom Navigation と一緒に使うにはどうすればいいですか？**
    
    - A: `BottomNavigation` コンポーネントと `NavController` を組み合わせて使用します。公式ドキュメントの Bottom Navigation [無効な URL を削除しました] を参照してください。
- **Q: より複雑なナビゲーションパターンを実装したい場合はどうすればいいですか？**
    
    - A: Nested Navigation を使用することで、複数の `NavHost` をネストして、より複雑なナビゲーション構造を構築できます。

### 6. まとめ

この記事では、Jetpack Compose の `NavController` について解説しました。`NavController` を使うことで、画面遷移をシンプルかつ柔軟に実装できます。ぜひ、あなたのアプリ開発に役立ててください。

**参考サイト**

- [Navigation with Compose | Jetpack Compose - Android Developers](https://developer.android.com/jetpack/compose/navigation)
- [ComposeでNavigationを実装する #Android - Qiita](https://qiita.com/shxun6934/items/5301b69a85df98e30983)

**補足**

- この記事は、Jetpack Compose のナビゲーションの基本を解説したものです。より高度なナビゲーションパターンや、他のナビゲーション関連コンポーネントについては、公式ドキュメントなどを参照してください。
- Jetpack Compose のナビゲーション機能は、今後も進化していく可能性があります。最新の情報に常に注意を払いましょう。