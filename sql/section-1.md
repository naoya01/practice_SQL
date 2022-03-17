# SQL文の基礎
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

**使用するデータベースを選択する**<br>
use データベース名

**必要なデータを取得する**<br>
selsct * from テーブル名; 

## エラー
select * form users;(スペルミス)
ｓｅｌｅｃｔ * form users;(全角文字)

## エラーしない(大文字、小文字は同じ扱い)
SELECT * FROM USERS;
SELECT * form users;
SElect * form users;
## コメントアウトの種類
「--」
-- select * form users;

「/**/」
/* select * form users; */

## 複数の列を取得
例1)select id, last_name form users;

例2)select
  id,
  last_name
from
  users;

## 列の値に対して演算を行う
select 
  name as 名前,
  price as 価格,
  price * 1.08 as 税込み価格
from
  products;

  ## 条件を指定して値を取得
  select 列1, 列2... from テーブル名 where 条件;

  ### 条件を指定して値を取得の例
  例)値段が9000円以上の商品だけを取得
  select name, price from products where price >= 9000;

  ### 代表的な演算式
  - 「=」等しい
  - 「>」より大きい
  - 「>=」以上
  - 「<」より小さい
  - 「<=」以下
  - 「<>」,「!=」等しくない
  - 「in」ある値が値セット内に含まれているかどうか
  - 「not in」ある値が値セット内に含まれていないかどうか
  - 「is null」値がnull
  - 「is not null」値がnullではない
  - 「like」パターンマッチング(曖昧検索)
  - 「between」値が値の範囲内に含まれているかどうか

#### 例1)　idが1の行を取得
```SQL
select * from products where id = 1;
```
#### 例2)　名前が「商品0003」の行を取得
```SQL
select * from products where name = "商品0003";
```
#### 例3)　priceが1000より大きい行を取得
```SQL
select * from products where price > 1000;
```

#### 例4)　priceが1000より小さい行を取得
```SQL
select * from products where price < 1000;
```
#### 例5)　priceが1000でない行を取得
```SQL
select * from products where price != 1000;
```
```SQL
(select * from products where price <> 1000;)
```
#### 例6)　idが1か2か3の行を取得
```SQL
select * from products where id in(1,2,3);
```

#### 例7)　idが1か2か3でない行を取得
```SQL
select * from products where id not in(1,2,3);
```
#### 例8)　priceがnullではない行を取得
```SQL
select * from products where price is not null;
```

#### 例9)　priceがnullの行を取得
```SQL
select * from products where price is null;
```

#### 例10)　priceが1000から1900の行を取得
```SQL
select * from products where price between 1000 and 1900;
```
```SQL
select * from products where price >=1000 and price >=1900;
```
#### 例10)　価格が1000円または2000円の行を取得
```SQL
select * from products where price = 1000 or price = 2000;
```

## パターンマッチングによる絞り込み
### ワイルドカード文字について
  '%'(パーセント)：0文字以上の任意の文字列<br>
  '_'(アンダースコア)：任意の1文字
  1. '中%'→’中’で始まる文字列
  1. '%中%'→’中’を含む文字列
  1. '%中'→’中’で終わる文字列
  1. '__子'→何かしらの2文字から始まり’子’で終わる文字列

```SQL
select * from users where last_name like '中%';
select * from users where last_name like '%中%';
select * from users where first_name like '%子';
select * from users where first_name like '__子';
```
### 取得件数の制限

select 列, ... from テーブル名 limit[オフセット,]最大取得件数;

#### 10件のみ取得
```SQL
select * from products limit 10;
```
#### 0から取得開始し10件のみ取得
```SQL
select * from products limit 0,10;
```
#### 「中」から始まるものの0番目から取得を開始し100件のみ取得
```SQL
select * from users where last_name like '中%' limit 0,100;
```

### limit句
  select 列名 from テーブル名 where 列名 = 条件 limit = 件数;
```SQL
select id , last_name from users where gender = 1 limit 10;
```