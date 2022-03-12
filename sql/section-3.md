# データの並び替え(order by)
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

- テーブル orders
  - カラム id, user_id, amount, order_time

- テーブル access_log
  - カラム id, user_id, request_path, request_time, request_mouth
## 構文
 order by 列名や式　並び順,..

## 商品が高い順
 select * from products order by price desc;

## 商品が高い順
select * from products order by price asc;

## 複数のデータの並び替え
select * from products order by price desc,id asc ;<br>

select * from users order by birthday asc, prefecture_id asc;