# UDEMY講座のメモ

```
<?php
print('phpを勉強中です！');
?>
```
- printの部分をファンクション（関数）という,ファンクションは機能という意味で、phpの機能名を書くみたいなニュアンス
- ファンクションの後には必ず()があり、中にパラメーター（引数、上記で言う'phpを勉強中です！'）を書くことができる
- ファンクションによって定義されているパラメーターを書く *リファレンスを確認する

## エスケープシーケンス
1. 非英数字の前に記述する場合で、続く文字が表す特別な意味を取り去る
2. 非表示文字〔制御コードなど〕を パターン中に目に見える形で記述するための方法

## 算術演算子

```
+ //足し算
- //引き算
* //掛け算
/ //割算
% //剰余算 (あまりの数)
```

### 日付を表示
- dateを使用
```
//ローカルの日付/時刻を書式化する
date ( string $format , int|null $timestamp = null ) : string

// format 引数で表示される内容が変わる
d 日, 01〜31 
D 曜日、３文字 Mon,Friなど
l 曜日、Monday
s 秒数, 00~59
たくさんある
```

#### タイムゾーンの変更の仕方
MANP/bin/php/phpのバージョン/conf/php.ini
```
[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
date.timezone = "Asia/Tokyo"
```
- date.timezone = "Asia/Tokyo"のところがヨーロッパの時間帯になっているので上記に修正
MANPの場合は;を消さないと反映されない

- dateメソッドで使用
```

<?php
date_default_timezone_set('Asia/Tokyo');
print(date('G時 i分 s秒'));
?>
```
画面に表示するにはechoかprintで組み合わせる
dateは時間は取得するけど、文字は出力できないため

- 文字列を入れる場合
```
<?php
print("現在は".date(G時1分s秒)."です");
?>
```
- .で連結することで表示される

- オブジェクトをつかって時刻を表示する
Datetimeを使用（classっぽい）
```
<?php
$today = new Datetime();
print($today) ->format('G時i分s秒');
?>

// ->　アロー演算子という
 左辺から右辺を取り出す
 上記なら$todayから時刻を取り出している
```

### 変数
- $マークを使う
1. 英単語
2. 英語
3. _数字
4. 日本語
- 記号やスペースは使えない
- 先頭が数字は使えない
- 基本的にはすべて小文字

#### 代入
- 記憶させたいのを=の次に書く
- 表示させる場合は$変数名などで使用
- 変数を""で囲うと変数の中身が表示される

## 繰り返し処理
- while文
```
初期化処理
while (繰り返す条件) {
  繰り返したい処理
  更新処理
}
```
- １から365を表示する記述
```
<?php
$i = 1;
print($1);
while($i <= 365){
  print($i . "\n");
  $i= $i + 1 ;
}
?>
```
// \nで改行

- for文
```
for(初期化処理; 繰り返す条件; 更新処理){
  繰り返したい処理
}
```

例
```
for ($i=1; $i<=365; $i++) {
  print($i. "\n");
}
```

### 再代入
```
$i = $i + 1;
Si += 1;
$i++; インクリメント(increment=加算)

$i = $i - 1;
$i -= 1;
$i--; デクリメント(decrement=減算) 
```

## 1年のカレンダーを表示させるプログラム
### dateメソッド
```
<?php 
print(date('n/j(D)));
?>
// 2/14(Sun)と表示される（作成日）
```
### timestump（デフォルト）
```
print(time());
//1613308334と表示
// 1970/01/01が1秒のスタートで現在の秒数で表示

```

- timeを活用して明日を表示する
```
print(date('n/j'(D),time( + 60 * 60 * 24)));
// 2/15(Mon)と表示される
// 今日の日付に 60秒*60分*24時間をかけることで明日を表示する
```

### strtotimeファンクション
- string to timestumpの略、記述されたtimestumpを表示する
```
print(strtime('1990/03/09'));
// 636908400と表示(自分の誕生日）

print(date('n/j'(D),strtotime(+'2day')));
// 2/16(Tue)と表示

```

- for文を活用した記述
```
<?php

for($i=1; $i<=365; $i++){
  print(date('n/j(D)',strtotime('+'.$i.'day')));
  print"\n";
}
?>
```
- 上記をリファクタリング
```
<?php
for($i=1;$i<=365; $i++){
  $date= strtotime('+'.$i.'day');
  print(date('n/j(D)',$date));
  print"\n";
}
?>
```
- :とendfor; :とendwhile;
```
<?php
for($i=1;$i<=365; $i++):
  $date= strtotime('+'.$i.'day');
  print(date('n/j(D)',$date));
  print"\n";
endfor;
?>

//{}の代わりに:とendfor;で囲う（for分の場合,
while文であれば,:とforwhile;になる
```

# カレンダーを作るプログラム(日本語の曜日,配列を利用していく)
- dateファンクション w
1. 数字で曜日を表す
- 0 日曜日
- 1 月曜日
- 2 火曜日
- 3 水曜日
- 4 木曜日
- 5 金曜日
- 6 土曜日

### 配列の作り方
```
$変数名 = [];
// []をブラケットという
// ,で区切る
// 配列を表示するにはindex(添字(目次みたいな意味))が必要
// 配列の中身は変数なども表示できる
$week_day = ['日','月','火','水','木','金','土'];
print(week_day[date('w')]); 
```

## 連想配列
- indexを自由に割り振れる,順番が関係ない配列を取り出す
```
<?php
$fruits=['apple'=>'りんご','grape'=>'ぶどう','lemon'=>'レモン'];
print($fruits['grape']);
//ぶどうと表示される
//appleの部分がindex,りんごの部分が値
```
?>

### foreach
- 配列を反復処理するのに便利,配列とオブジェクトのみ使用可能

1. foreach (iterable_expression as $value)
```
$fruits = [
  'apple'=> 'りんご',
  'grape'=> 'ぶどう',
  'lemon'=> 'レモン',
];

foreach($fruits as $valuse) {
  print($valuse."\n");
};
//りんご　ぶどう　レモンと表示
```

2. foreach (iterable_expression as $key => $value)
```
$fruits = [
  'apple'=> 'りんご',
  'grape'=> 'ぶどう',
  'lemon'=> 'レモン',
];

foreach($fruits as $key => $value){
  print($key.":".$value);
};
// apple:りんごgrape:ぶどうlemon:レモンと表示
// keyとvalueの部分は自分で命名できる
```


## if文
- 文字列の条件
```
$s = 'あいうえお';
if($s) {
  print('sはからではありません');
} else {
  print(sはからです);
}

// 文字列 変数に中身があればture,空ならfalse
```

- 数字の条件
```
$s = 0;
if($s) {
  print('sは0ではありません');
} else {
  print('sは0です');
}
// 数字は 0以上はture,0はfalse
```

- 否定
```
$s = 0;
if(!$s) {
  print('sは0ではありません');
} else {
  print('sは0です');
}
// 条件が反転する、数字は 0以上はfalse,0はture
```

## 小数点の計算
- 切り捨て
```
print(floor(100 / 3000 * 100));

// 3と出力(3.3333...なので切り捨てた結果)
```

- 切り上げ
```
print(ceil(100 / 3000 * 100));
// 4と出力
```

- 四捨五入
```
print(round(100 / 3000 * 100,2));

//3.33と出力、第2パラメーターの数字で少数第何位まで出力されるか決まる
```

## 書式を整える
```
//sprintfファンクション

<?
$date= sprintf('%04d年 %02d月 %02d日',2021,2,21);
print($date); 
?>

// 真ん中の数字で桁数を指定
// 0で補う、半角スペースも可能
// d 数字　書式をチェックしてくれる
// %でパラメーターの数が変わる,上記だと3つあるので3つパラメーターがいる
```

### ファイルの読み込み・書き込み

#### ファイルの書き込み,file_put_contensを使用
```
<?php
$success = file_put_contents('../../news_data/news.txt','2021-02-21 HPをリニューアルしたよ');
if ($success){
  print('成功');
} else {
  print('失敗');
}
?>
```
- 上記の場合だと変数successにプログラムを入れる、new_dataディレクトリにnews.txtを作成し,文を記述するところまで

#### ファイルの読み込み file_get_contensを使用
```
$news = file_get_contents('../../news_data/news.txt');
print($news);
```
- 変数newsにプログラムを入れる、その変数をprintで記述する

####  readfileで読み込み
```
 readfile('../../news_data/news.txt');
 ```
 - 中身を確認するだけならば, readfileが便利、読み込む中身が変わるならば,file_get_contensで変数を代入したほうが良さそう

 ### ファイルに内容を追記する

 ```
 <?php
  $news = file_get_contents('../../news_data/news.txt');
  $news .= '2021-02-24 ニュースを追記';
  file_put_contents('../../news_data/news.txt',$news);
  print($news);
 
 // .=は文字列連結、+=みたいなイメージ
 // 上記は降順に表記される

 //上に表記させる場合
 $news = '2021-02-24 ニュースを追記'.$news;とすると上に出る
 ?>

```
## XMLの情報を読み込む
### XML
- 拡張できるマークアップ言語(HTMLの親分みたいらしい)
```
<?php
$xmlTree = simplexml_load_file('https://h2o-space.com/feed/');
foreach ($xmlTree->channel->item as $item):
?>
・<a href="<?php print($item->link); ?>"><?php print($item->title); ?></a>
<?php endforeach; ?>
?>
```

##  JSONの読み込み
- Javascript object notation (javascriptのオブジェクトとして使える表記法)
- 記述量が少ない（XMLはタグでくぐるがJSONは:のため）
- 各データの中身が見える

### json_decode
- JSON文字列をデコードする

```
<?php
$file =file_get_contents('https://h2o-space.com/feed/json/'); 
$json = json_decode($file);
foreach ($json -> items as $item):
?> 
・ <a href="<?php print($item -> url); ?> "><?php print($item -> title); ?> </a>
<?php
endforeach;
?>
```

## フォームから入力した内容を取得する
### フォームを作成
- ディレクトリ内にindex.htmlを作成
```
<form action="submit.php" method="get">
  <label for="my_name">お名前：</label>
  <input type="text" id="my_name" name="my_name" maxlength="255" value="" >
  <input type="submit" value="送信する">
</form>
```

## HTTPメソッド　GET POST
- ディレクトリ内にsubmit.phpを作成

```
print(html_specialchars($_REQUEST['my_name'],ENT_QUOUTE));
```
- ['my_name']でフォーム属性を指定
- htmlspecialcharsを使用することで、htmlをエンティティする（セキュリティ）
1. １つ目のファンクションで何を、２つ目のファンクションでどのように
2. 基本的には第２パラメータはENT_QUOTEを使用
3. $_REQUESTはhtmlのフォーム属性がGETでもPOSTでも受け取れる、しかしPOSTで送るべき内容（パスワード）もGETに乗せて送られるため、属性がわかっている場合は合わせる

### radio,チェックボックス
- textフィールドと違ってvalue属性のデータが送られる
```
#index.html  
<form action="submit.php" method="POST">
  <p>
    性別：
    <input type="radio" name="gender" value="male">男性
    ／
    <input type="radio" name="gender" value="female">女性
  </p>
  <input type="submit" value="送信する">
</form>
```

```
#submit.php
<?php print(htmlspecialchars($_POST["gender"],ENT_QUOTES)); ?>
```

- 上記の場合,男性を指定したらmale,女性を選択したらfemaleが表示される

## 複数選択可能なチェックボックス、リストボックスの値を取得.



























