## NavHost：Composeのナビゲーションの舞台裏を支える縁の下の力持ち！

### NavHostってなに？

Jetpack Composeで画面遷移を実現する際に、 **NavHost** は欠かせない存在です。例えるなら、**アプリの中に作られた小さな劇場**のようなもの。

- **舞台（画面）を用意**:
    
    - `composable` という命令を使って、アプリの中に複数の「舞台」（画面）を用意します。
    - 各舞台には、それぞれ名前（ルート）をつけます。（例： "home", "settings" など）
- **観客（NavController）を案内**:
    
    - `NavController` という案内役が、観客（ユーザー）をどの舞台に案内するかを決めます。
    - `NavController` は、`NavHost` に「どの舞台を見たいか」を伝えます。
- **舞台を切り替える**:
    
    - `NavController` の指示に従って、`NavHost` は適切な「舞台」（画面）に切り替えます。
    - 観客は、まるで別の場所へ移動したかのように、スムーズに次の画面を見ることができます。

### 具体的なコード例

Kotlin

```
@Composable
fun MyScreen() {
    val navController = rememberNavController() // 案内役（NavController）を作る

    NavHost(navController = navController, startDestination = "home") { // 劇場（NavHost）を作る
        composable("home") { HomeScreen() } // "home" という名前の舞台（HomeScreen）を用意
        composable("settings") { SettingsScreen() } // "settings" という名前の舞台（SettingsScreen）を用意
    }
}
```

コードは[注意](/faq#coding)してご使用ください。

### ポイント

- **NavHostは一つだけ**: アプリの中に `NavHost` は基本的に一つだけ作ります。これが全ての画面遷移を管理する劇場となります。
- **composableで舞台を用意**: `composable` を使って、`NavHost` の中に複数の画面（Composable関数）を登録します。
- **NavControllerが案内役**: `NavController` を使って、どの画面に遷移するかを `NavHost` に指示します。
- **startDestinationで最初の舞台を決める**: `startDestination` で、アプリ起動時に最初に表示する画面のルートを指定します。

### まとめ

- `NavHost` は、Jetpack Compose での画面遷移を管理するための重要なコンポーネントです。
- `NavHost` は、アプリ内の複数の画面（Composable）を管理し、`NavController` の指示に従って画面を切り替えます。
- `composable` 関数を使って、各画面のルートと、そのルートに対応する Composable 関数を `NavHost` に登録します。
- `startDestination` で、アプリ起動時に最初に表示する画面のルートを指定します。

### さらに詳しく

- **ネストされたナビゲーション**: 複数の `NavHost` をネストして、より複雑なナビゲーション構造を構築できます。
- **BottomNavigationとの連携**: `BottomNavigation` と `NavController` を組み合わせて使うことで、画面下部にタブナビゲーションを実装できます。

これらの詳細については、公式ドキュメントや他の学習資料を参照してください。

これで `NavHost` について少しは理解できたでしょうか？