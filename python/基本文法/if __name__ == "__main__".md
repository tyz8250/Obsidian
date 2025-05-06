
#python 
このスクリプトが直接実行時のみ、以下のコードを実行する。
他のスクリプトから呼び出された場合は、実行しない。

```python
def main():
    # コマンドライン引数の確認
    if len(sys.argv) != 3: #引数が3以外のとき
        print("使用方法: python convert_to_html.py 入力ファイルパス 出力ファイルパス")
        sys.exit(1) #異常終了

    input_path = sys.argv[1]
    output_path = sys.argv[2]

    # マークダウンをHTMLに変換
    convert_markdown_to_html(input_path, output_path)

if __name__ == "__main__": #もしこのプログラムが直接読まれていれば、以下の部分を実行する。
    main()
```