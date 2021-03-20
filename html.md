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




