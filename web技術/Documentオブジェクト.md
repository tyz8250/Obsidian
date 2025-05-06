#DOM #HTML 


DOM（Document Object Model）は、HTMLやXML文書をプログラムから操作するための標準的なインターフェースです。特に、DOMの中で「Document」は、ウェブページ全体を表すオブジェクトであり、ページ内のすべての要素にアクセスし、操作するための基盤となります。

家（Document）
├── 1階（html要素）
  │   ├── リビング（body要素）
  │    │          ├── テーブル（div要素）
  │    │          ├── ソファ（p要素）
  │    │          └── テレビ（img要素）
  │   └── 玄関（head要素）

```html
<!DOCTYPE html>
<html>              <!-- 1階 -->
    <head>          <!-- 玄関 -->
        <title>私の家</title>
    </head>
    <body>          <!-- リビング -->
        <div>       <!-- テーブル -->
            <p>こんにちは</p>   <!-- ソファ -->
            <img src="photo.jpg"> <!-- テレビ -->
        </div>
    </body>
</html>
```

```Javascript
// 家全体（Document）から特定の要素を探す
const sofa = document.querySelector('p');
const tv = document.querySelector('img');

// 新しい家具（要素）を追加する
const newChair = document.createElement('div');
document.body.appendChild(newChair);
```
## Documentオブジェクトの役割

Documentオブジェクトは、ウェブページの構造をツリー形式で表現します。このツリーは、各要素（例えば、`<div>`、`<p>`、`<a>`など）がノードとして表され、親子関係を持っています。これにより、プログラマーは特定の要素を簡単に取得したり、変更したりすることができます。

例えば、JavaScriptを使用して、特定のIDを持つ要素を取得するには、`document.getElementById('elementId')`メソッドを使用します。このメソッドは、指定したIDを持つ要素を返します。

## Documentオブジェクトの主なメソッド

Documentオブジェクトには、さまざまなメソッドが用意されています。以下はその一部です：

- `getElementById(id)`：指定したIDを持つ要素を取得します。
- `getElementsByClassName(className)`：指定したクラス名を持つすべての要素を取得します。
- `getElementsByTagName(tagName)`：指定したタグ名を持つすべての要素を取得します。
- `querySelector(selector)`：CSSセレクタを使用して、最初に一致する要素を取得します。
- `createElement(tagName)`：新しい要素を作成します。

## Documentオブジェクトの重要性

Documentオブジェクトは、ウェブ開発において非常に重要な役割を果たします。これを理解することで、動的なウェブページを作成し、ユーザーの操作に応じて内容を変更することが可能になります。たとえば、ボタンをクリックしたときに特定のテキストを表示したり、フォームの入力内容を検証したりすることができます[1](https://udemy.benesse.co.jp/development/dom.html "udemy.benesse.co.jp")[2](https://zenn.dev/goldsaya/articles/aa705596b4a598 "zenn.dev")[3](https://developer.mozilla.org/ja/docs/Web/API/Document_Object_Model/Introduction "developer.mozilla.org")[4](https://www.youtube.com/watch?v=puaJhJ-HTUo "youtube.com")[5](https://note.com/skipla/n/nb65a0bb4c24c "note.com")。

---

Documentオブジェクトは、HTML文書の構造を表現するだけでなく、文書全体に対する操作を可能にします。具体的には、DOMツリーのルートノードとして機能し、すべての他のノード（要素、属性、テキストなど）へのアクセスを提供します。

また、Documentオブジェクトには、以下のような重要なプロパティもあります：

- `document.title`：現在の文書のタイトルを取得または設定します。
- `document.body`：文書の`<body>`要素を取得します。
- `document.head`：文書の`<head>`要素を取得します。

これらのプロパティを使用することで、ページのタイトルを変更したり、ボディの内容を直接操作したりすることができます。たとえば、`document.title = '新しいタイトル';`とすることで、ページのタイトルを変更できます。

さらに、Documentオブジェクトは、イベントリスナーを追加するためのメソッドも提供しています。これにより、ユーザーの操作に応じて動的に反応することが可能です。例えば、`document.addEventListener('click', function() { /* 処理 */ });`のようにして、クリックイベントに対する処理を定義できます。