# 集約関数
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

- テーブル orders
  - カラム id, user_id, amount, order_time

- テーブル access_log
  - カラム id, user_id, request_path, request_time, request_mouth
## sum 集約関数(合計)
### 2017年1月の合計値を求める
select sum(amount) from orders where order_time >= '2017-01-01 00:00:00' and order_time <= '2017-02-01 00:00:00';

## avg 集約関数(平均)
### 2017年1月の平均値を求める
```SQL
select avg(price) from products;
```
## min 集約関数(最小値)
```SQL
select min(price) from products;
```
## max 集約関数(最大値)
```SQL
select max(price) from products;
```
## nullの扱いについて
  基本的に集約関数いおいては無視される<br>
  10, null, 20 の場合<br>
  => 平均値avg()は15となる<br>
  計算式：(10 + 20) / 2

## count 集約関数(対象の行数を数える)
```SQL
select count(*) from users;
select count(*) from users where gender = 2;
```
## count(distinct expr) 集約関数(ある数を重複を排除した数を数える)
```SQL
select 
	count(distinct user_id) 
from 
	access_logs 
where 
	request_month = '2017-01-01';
```
  ## group by 集約関数(グループ単位で集計する)
  ### 都道府県別のユーザーの数を集計
```SQL
  select prefecture_id,count(*) from users group by prefecture_id;
```
  ### 期間ごとに集計する
```SQL
  select 
      request_month,
      count(distinct user_id)
  from 
      access_logs 
  where 
      request_month >= '2017-01-01' and request_month <= '2018-01-01' 
  group by
    request_month;
```

  ### 期間ごとに集計し、さらに絞り込む
  select 
    列1,...
  from 
    テーブル名
  where 
    条件式 
  group by
    列1,...
  having
    条件式;<br><br>
```SQL
  select
      request_month,
      count(distinct user_id)
  from 
      access_logs 
  where 
      request_month >= '2017-01-01' and request_month <= '2018-01-01' 
  group by
    request_month
  having 
    count(distinct user_id) >= 630;
```
  ### 記述順序
  1. select：取得行(カラム)の指定
  1. from：対象テーブルの指定
  1. where：絞り込み条件の指定
  1. group by：グループ化の条件を指定
  1. having：グループ化した後に絞り込み条件の指定
  1. order by：並び替え条件を指定
  1. limit：取得する行すうを制限

  ### 記述順序
  1. from：対象テーブルの指定
  1. where：絞り込み条件の指定
  1. group by：グループ化の条件を指定
  1. having：グループ化した後に絞り込み条件の指定
  1. select：取得行(カラム)の指定
  1. order by：並び替え条件を指定
  1. limit：取得する行すうを制限