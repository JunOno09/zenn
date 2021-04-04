# HTML
## hタグ Heading(見出し) 1~6まで
## pタグ　paragraph 段落 本文などで使う、改行される <br>も
## 入れ子構造　タグの中にタグを入れる
## inputタグ ユーザーに動作を促す　メールの入力など　
- type属性 指定した先で何を入力するか決まる email,checkboxなど
- name属性 必須属性 textフィールドの名前（オリジナル）
- インプットは終了タグなし 挟むものがないため

## buttonタグ
- type属性の指定で役割が変わる
1. type="submit" …… フォーム入力内容を送信するサブミットボタン（初期値）
2. type="reset" …… フォーム入力内容をリセットするリセットボタン
3. type="button" …… 何もしない汎用的な押しボタン

## HTMLの宣言
```
<!DOCTYPE html>
```
- 上記でHTML5の宣言になる
```
<html>
  <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width">
     <title>タイトル</title>
  </head>
    <body>
      本文
    </body>
</html>
```
- headタグのmetaは文字のコード（文字化けしないように使う）
- viewportで端末の幅を指定


## divタグ
- ディヴィジョン　領域を表す
# CSS
## インラインスタイルシート
- 一つのタグの中に記述すること
```
 <h1 style="font-size: 24px; margin: 50px;"  >入会申込み</h1>
 ```

## span
- 改行されないので、一部の要素に適用できる
 ## 内部参照
 - headタグに記述する
 - styleタグの中にセレクターを指定し、記述
 ``` 
 <head>
<style>
 p {
   font-size: 14px;
 }
</style>
 </head>
 ```

### brタグ
- ブレイク　改行の役割
 ## 外部参照
 - CSSのページを作る
 - ポイントに寄って使い分けるのが大切
 - 適用される優先順位（同じ要素）は降順

 ## リセットCSS
 -  デフォルトでCSSが効いているので、無効にする
 - sanitize.cssを検索し、下部のダウンロードをし、リンクを貼る

 ## 効果
 -  border-radius 角が丸くなる
- box-shadow 影が出る

### セレクター
- クラス属性をセレクターにする際は.をつける。




