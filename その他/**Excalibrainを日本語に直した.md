**Excalibrainの描画ファイルパス**

△ このファイルはプラグインによって上書きされます。スクリプトを停止してグラフに変更を加えた場合は、ファイル名を変更して編集内容を保持する必要があります。なぜなら、次にExcaliBrainを起動したときに、編集内容が自動生成されたExcaliBrainグラフによって上書きされるからです。

**インデックスの更新頻度**

ExcaliBrainは、作業ペインを切り替えるたびにインデックスを更新します。これは、前回のインデックス更新以降にVault内のファイルが変更された場合に対応するためです。

したがって、この設定は、マークダウンエディタで入力しているとき（ファイルやペインを切り替えていないとき）にのみ関連し、入力中にExcaliBrainがグラフを更新し続けるようにしたい場合にのみ有効です。バックグラウンドでの頻繁なインデックス更新はリソースを大量に消費する可能性があるため、インデックス更新の時間間隔を長くするオプションがあります。これにより、システムのオーバーヘッドを削減できます。

**オントロジー**

オントロジーは、ExcaliBrainの心臓部です。これは、ナレッジグラフのコンテキストであり、グラフ内の異なるノード間の関係を整理および定義するためのシステムを指します。これにより、「作成者」や「章」などの特定のDataviewフィールドに関連付けることで、接続に意味を追加できます。これらのフィールドは、ノードがグラフ上で互いにどのように配置されるかに影響します。このアプローチにより、情報がより構造化され、意味のある形で表現されるため、Vault内のマークダウンドキュメント内の概念の相互接続を理解しやすくなります。

グラフ内のリンクを定義するために使用するフィールド名をコンマ（,）で区切って入力します。

マークダウンエディタで新しいフィールド（例：「Consits of::」）を入力し、コマンドパレットのアクションのいずれかを呼び出してDataviewフィールドをオントロジーに追加するか、コンテキストメニューを開くことで、オンザフライでオントロジーにフィールドを追加することもできます。


各項目を日本語に訳すと、以下のようになります。

- **Parents (親)**: inception, North, origin, Parent, parent domain, Parents, source, u, up
    - 起源、北、原点、親、親ドメイン、ソース、上 など、上位概念や起源を表すフィールド
- **Children (子)**: Child, Children, contributes to, d, down, leads to, nurtures, South
    - 子、貢献する、下、導く、育む、南 など、下位概念や結果を表すフィールド
- **Left-Side Friends (左側の友達)**: advantages, alternatives, Friend, Friends, j, Jump, Jumps, pros, similar, supports
    - 利点、代替案、友達、ジャンプ、賛成、類似、サポート など、類似概念や肯定的な関連を表すフィールド
- **Right-Side Friends (右側の友達)**: cons, disadvantages, missing, opposes
    - 欠点、反対、不足、反対する など、反対概念や否定的な関連を表すフィールド
- **Previous (Friends) (前の友達)**: Before, Prev, Previous, w, West
    - 前、西 など、時間的または空間的に前の概念を表すフィールド
- **Next (Friends) (次の友達)**: After, e, East, n, Next
    - 後、東、次 など、時間的または空間的に次の概念を表すフィールド
- **Hidden (非表示)**: hidden
    - グラフに表示したくないDataviewまたはYAMLフィールド

これらの設定は、Obsidianのノート間の関係をグラフで表示する際に、どのように表示するかを定義するものです。例えば、「Parent」というフィールドを持つノートは、グラフの上位に配置され、「Child」というフィールドを持つノートは、下位に配置されます。

このように、フィールド名を設定することで、ノート間の関係を視覚的に表現し、より深く理解することができます。

**Excluded (除外)**

- DataviewまたはYAMLフィールドで、オントロジーに使用されないもの。これらのフィールドは、マークダウンエディタのオントロジーサジェスターに表示されず、未割り当てリストにも表示されません。
    - `excalidraw-border-color`、`excalidraw-css`、`excalidraw-default-mode`、`excalidraw-export-dark`、`excalidraw-export-pngscale`、`excalidraw-export-svgpadding`、`excalidraw-export-transparent`、`excalidraw-font`、`excalidraw-font-color`、`excalidraw-link-brackets`、`excalidraw-link-prefix`、`excalidraw-linkbutton-opacity`、`excalidraw-onload-script`、`excalidraw-plugin`、`excalidraw-url-prefix`、`kanban-plugin`  、`tags`

**Unassigned (未割り当て)**

- Vault内のフィールドで、除外されておらず、定義されたオントロジーの一部でもないもの。

**Infer all implicit relationships as Friend (すべての暗黙的な関係を「友達」として推測)**

- **トグルオン:**ドキュメント内のすべての暗黙的なリンクは「友達」と解釈されます。
- **トグルオフ:**以下のロジックが使用されます。
    - 前方リンクは「子」として推測されます。
    - 後方リンクは「親」として推測されます。
    - ファイルが相互にリンクしている場合は、「友達」です。

**Reverse infer logic (推測ロジックを反転)**

- **トグルオン:**後方リンクを子として、前方リンクを親として扱います。
- **トグルオフ:**後方リンクを親として、前方リンクを子として扱います。

**Inverse arrow direction (矢印の方向を反転)**

- **トグルオン:**リンク方向と反対方向に矢印を表示します。
- **トグルオフ:**リンク方向と同じ方向に矢印を表示します。

**Ontology Suggester (オントロジーサジェスター)**

- マークダウンエディタでオントロジーサジェスターを有効にします。有効にすると、段落の先頭にトリガーシーケンスを入力すると、上記で定義したオントロジーフィールドを一覧表示するサジェスターがアクティブになります。

**Character sequence to trigger generic suggester (汎用サジェスターをトリガーする文字シーケンス)**

- 方向に関係なく、すべてのオントロジーフィールドを含む汎用サジェスターをトリガーします。
    - `:::`

**Character sequence to trigger parent suggester (親サジェスターをトリガーする文字シーケンス)**

```
* `::p`
```

**Character sequence to trigger child suggester (子サジェスターをトリガーする文字シーケンス)**

```
* `::c`
```

これらの設定項目は、Excalibrainがノートの関係をどのように解釈し、グラフに表示するかを細かく制御するためのものです。

**Character sequence to trigger left-side friend suggester (左側の友達サジェスターをトリガーする文字シーケンス)**

- `::l`

**Character sequence to trigger right-side friend suggester (右側の友達サジェスターをトリガーする文字シーケンス)**

- `::r`

**Character sequence to trigger previous (friend) suggester (前の友達サジェスターをトリガーする文字シーケンス)**

- `::e`

**Character sequence to trigger next (friend) suggester (次の友達サジェスターをトリガーする文字シーケンス)**

- `::n`

**Mid-sentence dataview field suggester trigger (文中のDataviewフィールドサジェスターのトリガー)**

- 文中にフィールドを追加することができます。2つの形式があります。
    - `We met at [location:: [[XYZ restaurant]]] with [candidate:: [[John Doe]]]`
    - `We met at (location:: [[XYZ restaurant]]) with (candidate:: [[John Doe]])`
- このトリガーを例えば `(` に設定すると、文中の任意の場所で `(` と入力するとサジェスターがアクティブになります（上記のデフォルトの汎用サジェスターのトリガーの組み合わせ `:::` を使用している場合）。
- インラインフィールドの詳細はこちらをご覧ください: [DataView Help](https://blacksmithgu.github.io/obsidian-dataview/data-annotation/)

**Add selected field with BOLD (選択したフィールドを太字で追加)**

- 選択したフィールドを太字でテキストに追加します。つまり、`(**field name**::)` と入力すると `(**field name**::)` になります。

**Behavior (動作)**

**Synchronize navigation on Embed toggle (埋め込みの切り替え時にナビゲーションを同期)**

- **トグルオン:**「<> 中央のノードを埋め込みフレームとして表示」ボタンを切り替えると、ExcaliBrainは自動的にナビゲーションの同期をオンにします。
- **トグルオフ:**「<> 中央のノードを埋め込みフレームとして表示」ボタンを切り替えても、ExcaliBrainは自動的にナビゲーションの同期をオンにしません。

**Filepaths to exclude (除外するファイルパス)**

- インデックスから除外するファイルパスのカンマ区切りリストを入力します。

**Javascript for rendering node names (ノード名を描画するためのJavascript)**

ノードのタイトルを描画するためのJavascriptコードです。必要ない場合は、このフィールドを空のままにしてください。

関数定義: `customNodeLabel: (dvPage: Literal, defaultName:string) => string`

スクリプトでは、`dvPage` 変数でDataviewページオブジェクトを参照できます。また、`defaultName` 変数でデフォルトのページ名（ファイル名またはエイリアス）を参照できます。

次の式構文を使用します。

`dvPage['field 1'] ?? defaultName` - この例では、「field 1」の値が表示されます（使用可能な場合）。それ以外の場合は、`defaultName` が表示されます。

△ コード行はそのまま実行されます。適切な例外処理を追加してください。 `defaultName` とDataviewフィールド名に加えて、任意のJavascript関数（例: `defaultName.toLowerCase()`）と `dvPage` オブジェクトに表示される任意の値（例: `dvPage.file.path` など）も自由に使用できます。

Dataviewページオブジェクトを調べるには、開発者コンソールを開き、次のコードを入力します。

`DataviewAPI.page('拡張子を含む完全なファイルパス')`

タイトルフィールドの値が表示されます（使用可能な場合）。それ以外の場合は、ファイル名が表示され、その後に状態が表示されます（使用可能な場合）。

`dvPage.title ?? defaultName + (dvPage.state ? ' - ' + dvPage.state : '')`

**Display (表示)**

**Compact view (コンパクトビュー)**

子ノードと親ノードに表示される列の最大数を設定することで、グラフの幅を制御します。

- **トグルオン:**子の列の最大数は3、親の列の最大数は2です。
- **トグルオフ:**子の列の最大数は5、親の列の最大数は3です。

**Compacting factor (圧縮係数)**

数値が高いほど、グラフはコンパクトになります。数値が低いほど、グラフは広がります。

**Minimum center-friend distance (最小中央-友達距離)**

中央のノードと友達ノードの間の最小距離。数値が高いほど、友達は親から離れ、リンクオントロジーラベルのスペースが増えます。

**Display full tag name (完全なタグ名を表示)**

- **トグルオン:**完全なタグ名が表示されます（例: `#reading/books/sci-fi`）。
- **トグルオフ:**タグの現在のセクションが表示されます。上記のタグを想定すると、タグ階層を移動するときに、グラフにはそれぞれ `#reading`、`#books`、`#sci-fi` のみが表示されます。

**Character sequence to trigger left-side friend suggester (左側の友達サジェスターをトリガーする文字シーケンス)**

- `::l` ：ノート内で「::l」と入力すると、左側の友達関係にあるノートを候補として表示するサジェスターが起動します。

**Character sequence to trigger right-side friend suggester (右側の友達サジェスターをトリガーする文字シーケンス)**

- `::r` ：ノート内で「::r」と入力すると、右側の友達関係にあるノートを候補として表示するサジェスターが起動します。

**Character sequence to trigger previous (friend) suggester (前の友達サジェスターをトリガーする文字シーケンス)**

- `::e` ：ノート内で「::e」と入力すると、前の友達関係にあるノートを候補として表示するサジェスターが起動します。

**Character sequence to trigger next (friend) suggester (次の友達サジェスターをトリガーする文字シーケンス)**

- `::n` ：ノート内で「::n」と入力すると、次の友達関係にあるノートを候補として表示するサジェスターが起動します。

**Mid-sentence dataview field suggester trigger (文中のDataviewフィールドサジェスターのトリガー)**

- 文中にDataviewフィールドを挿入するためのトリガーを設定します。
- 例えば `(` を設定した場合、文中で `(` と入力すると、フィールド名を入力するためのサジェスターが起動します。
- 2つの形式でフィールドを挿入できます。
    - `We met at [location:: [[XYZ restaurant]]] with [candidate:: [[John Doe]]]`
    - `We met at (location:: [[XYZ restaurant]]) with (candidate:: [[John Doe]])`
- デフォルトでは `:::` が設定されています。

**Add selected field with BOLD (選択したフィールドを太字で追加)**

- サジェスターからフィールドを選択した際に、太字で挿入するかどうかを設定します。
- トグルをオンにすると、`field name` は `(**field name**)` として挿入されます。

**Behavior (動作)**

**Synchronize navigation on Embed toggle (埋め込みの切り替え時にナビゲーションを同期)**

- グラフの中央に表示されているノートを、埋め込み表示に切り替えるボタンを押した際の動作を設定します。
- トグルをオンにすると、埋め込み表示に切り替えた際に、自動的にナビゲーションの同期がオンになります。
- トグルをオフにすると、埋め込み表示に切り替えても、ナビゲーションの同期は自動的にはオンになりません。

**Filepaths to exclude (除外するファイルパス)**

- Excalibrainのインデックスから除外したいファイルのパスを指定します。
- 複数のファイルパスを指定する場合は、カンマで区切ります。

これらの設定項目は、Excalibrainを使ってノート間の関係をグラフで表示する際に、どのように表示するか、どのように操作するかを細かくカスタマイズするためのものです。

**Styling (スタイル)**

スタイルは順番に適用されます。

1. ベースノードスタイル
2. 推測ノードスタイル (ノードが推測される場合にのみ適用)
3. 仮想ノードスタイル (ノードが仮想の場合にのみ適用)
4. 中央ノードスタイル (ノードが中央にある場合にのみ適用)
5. 兄弟ノードスタイル (ノードが兄弟の場合にのみ適用)
6. 添付ノードスタイル (ノードが添付ファイルの場合にのみ適用)
7. オプションのタグベースのスタイル

ベースノードスタイルのすべての属性を指定する必要があります。他のすべてのスタイルは、部分的な定義を持つことができます。例えば、プレフィックスを追加し、タグベースのスタイルでベースノードの背景色を上書きし、推測ノードスタイルでフォントの色を上書きし、仮想ノードスタイルで境界線のストロークスタイルを点線に設定することができます。

**Canvas color (キャンバスの色)**

- **color:** キャンバスの背景色を設定します。
- **opacity:** キャンバスの背景色の不透明度を設定します。

**Formatted tags (フォーマットされたタグ)**

タグに基づいてノードに特別な書式設定ルールを指定できます。ノートに複数のタグがあり、「ノートタイプ::」が定義されていない場合は、指定と一致する最初のページが使用されます。

- タグ名は `#` で始まり、不完全な場合があります。つまり、`#book` は `#books`、`#book/fiction` などと一致します。
- タグ名は **大文字と小文字が区別されます**。
- ここにタグのコンマ区切りリストを入力し、ドロップダウンリストから選択して書式設定を変更します。

**Note style tag field (ノートスタイルタグフィールド)**

ページのスタイルを設定するためのプライマリタグを指定するDataviewフィールド。このタグはベーススタイルとして使用されます。ページ上の他のタグにもスタイルが定義されていて、それらのスタイル定義にプレフィックス文字が含まれている場合、それらのプレフィックスもノートタイトルに追加されます。

**Display all tags styles (すべてのタグスタイルを表示)**

ノートに含まれるすべてのタグのタグプレフィックスを表示します。

これらの設定項目は、Excalibrainで生成されるグラフの見た目を細かくカスタマイズするためのものです。ノードの色、形、サイズなどを、タグやノードの種類に応じて変更することができます。

[[Drawing 2024-09-29 21.51.10.md]]

