# SQL文の基礎
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name

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

  ## 条件を指定して値を取得
  例)値段が9000円以上の商品だけを取得
  select name, price from products where price >= 9000;