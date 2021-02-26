# php 学習
## phpとは
 - web開発でよく使用されるスプリクト言語

 - htmlに埋め込むことができる  
 -<?php >が開始タグ,?>が閉じタグ
 -例
 ```
 <p>
  <?php echo "php"; ?>入門
  </p>
```
- 開始タグを省略できる <? でOK
終了タグを省略できるが、省略すると、以降全てがphpの扱いになる

-phpのコメントの書き方は//でOK
複数行になるときは/** で開始、*/で終了
-文字列は.を使えば連結できる
```

<? echo "php"."入門"; ?>
```

## 変数について
- 変数とは値を入れておく箱
- 変数=値で定義
- 変数の先頭には$マークを付ける
```
$tenp =1; //変数tenpに１を代入
echo $tenp; //１が出る
```
- 変数を上書きできる
- 変数で足し算・連結できる
```
$foo = 'php';
$fooo = '入門';
echo $foo.$fooo;
//php入門と出力
```
- 変数はくり返し使える
```
$program = "php";
echo $program."入門";
echo $program."初回";
```
~1/29

## 変数展開
- 文字列に変数を埋め込むこと
- 注意点は"で囲うこと
```
<?php
$i = 1;
$x = "php";
echo "第{$i}回{$x}入門講座";
?>
//　第１回php入門講座と出力される
```

## 値の解析
var_dumpを使うと値の解析ができる
```
<?php 
var_dump(6);
var_dump('6');
?>
```
int(6)  数値で値は６という意味

string(1) "6"と出力される　文字列で、１文字、６は値を表す
- int型(数値)やstiring型(文字列)のような値の種類のことを型という

## 比較演算子
- 比較をするときは==とする（rubyと同じ）
```
<?php
var_dump(1 == 1);
var_dump(1 == 2);
?>
/**
bool(true)  
bool(false)と出力される

tureの場合
a == b 等しいか
a < b aはbより大きいか
a <=b aはb以上か（１<=１の場合ture)
a > b aはbより小さいか
a >= b a以下か (1 >= 1の場合ture)
a != b aはbと異なるか
!a aではない
```
- rubyに似ているので、記述だけ理解する
- bool型(ture/falseの２択)

### 厳密な比較
- 型の比較を行うときは===とする
```
<?php 
var_dump(1 == '1');
var_dump(1 === '1');
/**
bool(true)
bool(false)
*/
?>
```

## if文の書き方

```
<?php 
if(条件式) {
  tureの場合の処理;
}
?>
<?php
 if(条件式){
   tureの場合の処理;
 } else {
   falseの場合の処理;
 }
?>

<?php
 if（条件式）{
   tureの場合の処理;
 } elseif(条件式2) {
   false1の処理;
 } else {
   false2の処理;
 }
?>
```


```
<?php
$score = 77;
if($score >= 80) {
  // 80点の処理
  echo "合格点です";
} elseif($score >= 70) {
  //70~79点の処理
  echo "惜しい";
  それ以外（〜69点の処理）
 } else {
  echo "頑張りましょう";
}
?>
```

### 条件式の組み合わせ
```
// AND条件 &&を使うときはどちらもtureならtureになる、それ以外はfalse
<?php
$a = 2
1 <= $a && $a <= 10
?>

// OR条件 ||によって組み合わせ,どちらか1つでもtureならture,それ以外はfalse

<?php
$a = 2
1 <= $a || $a <= 10
?>

```
~1/30

- if文のネスト
```
<?php
$sex = "男";
$age = 30;
if($sex == "男") {
    if (35 <= $age && $age < 50) {
        echo "中年おじさんです";
    } elseif ($age <=34) {
        echo 'まだ若い';
    } else {
        echo "おじいさん";
    }
} else {
    echo "女性です";
}
?>
//まだ若いと出力される
```

## 配列
```
//からの配列
[];
array();
//文字列の配列
["php","python",ruby"];
//数値の配列
[1,3,5];
```
### インデクス
```
<?php
$arr = ["php","python",ruby"];
$arr[0]; //"php"
$arr[1]; //"python"
$arr[2]; //"ruby"
?>
```
- 0から数えていく、数字のことをインデクスという
- 配列に格納した値のことを要素という

### 連想配列
- インデクス番号で管理せず、名前をつけて管理
```
//配列
<?php
$arr = ["php", "ruby"];
echo $arr[0];
// phpと出力
?>

// 連想配列
<?php
$arr = ["key1" => "php", "key2" => "ruby"];
echo $arr["key1"]; 
//phpと出力
?>
```
- =>を使うことで、名前を指定できる、上だったら,phpはkey1という名前という意味
- 名前のことをキーと言う

```
//配列の中に配列、多次元配列
[[1],[2]];
//配列の中に連想配列
[[key1 = 1]];
//連想配列の中に配列
[key1 = [1]];
```

~1/31

## echo と　printの違い

### 役割
- echo 1つ以上の文字列を出力する
- print 文字列を出力する

### 使い方
```
/echoの場合
<?php
echo "こんにちは";
?>
/こんにちはと出力

/ printの場合
<?php
print("こんにちは);
?>
/こんにちはと出力
```
- echoとprintは関数ではなく,言語構造なので、()は使用しなくてもいい。()を使っても表示される

### 違い
- printは単一の引数のみ受付け、常に１を返す

```
<?php
if (print '') {
    print 'OK';
} else {
    print 'NG';
}
 ?>
 //OKと出力

 <?php
 if (echo '') {
    echo 'OK';
 } else {
    echo 'NG';
 ?>

//echoは返り値がないため,エラーが起きる
```

- echoは文字列を連結するとき","が使える
```
<?php
echo 'A','B'; // カンマ使用 → 出力結果 AB
echo 'A'.'B'; // ドット使用 → 出力結果 AB

print 'A'.'B'; // ドット使用 → 出力結果 AB
// print 'A','B'; // printでカンマを使って複数の文字列を出力しようとするとエラーになる
?>

```

### エメット
```
html 5 
# なんか出てくる
```

### gem
- buluma rails cssを手軽にできる　便利そう

https://github.com/joshuajansen/bulma-rails







