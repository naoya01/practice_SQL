# 集約関数
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

- テーブル orders
  - カラム id, user_id, amount, order_time

## sum 集約関数(合計)
### 2017年1月の合計値を求める
select sum(amount) from orders where order_time >= '2017-01-01 00:00:00' and order_time <= '2017-02-01 00:00:00';

## avg 集約関数(平均)
### 2017年1月の平均値を求める
select avg(price) from products;

## min 集約関数(最小値)
select min(price) from products;

## max 集約関数(最大値)
select max(price) from products;

## nullの扱いについて
  基本的に集約関数いおいては無視される<br>
  10, null, 20 の場合<br>
  => 平均値avg()は15となる<br>
  計算式：(10 + 20) / 2
