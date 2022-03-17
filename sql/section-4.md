# 関数と演算式
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

- テーブル orders
  - カラム id, user_id, amount, order_time

- テーブル access_log
  - カラム id, user_id, request_path, request_time, request_mouth
### 足し算
  select 10 + 3;<br>
=>13
### 引き算
  select 10 - 3;<br>
=>7
### 掛け算
  select 10 * 3;<br>
=>30
### 割り算
  select 10 / 3;<br>
=>3.333
### 余り
  select 10 % 3;<br>
=>1
## nullを含む計算の注意点

### 足し算
  select 10 + null;<br>
=>null
### 引き算
  select 10 - null;<br>
=>null
### 掛け算
  select 10 * null;<br>
=>null
### 割り算
  select 10 / null;<br>
=>null
### 余り
  select 10 % null;<br>
=>null

## 絶対値
### 10の絶対値
select abs(10);<br>
=>10
### 10の絶対値
select abs(-10);<br>
=>10
### 10の絶対値
select abs(0);<br>
=>0

## round関数(四捨五入)
round(対象の数値,丸めの桁数)<br>
丸めの桁数に0を指定すると、少数第1位で四捨五入　round(10.555,0)<br>
=>11<br><br>

丸めの桁数に0を指定すると、少数第1位で四捨五入　round(10.555,1)<br>
=>10.6<br><br>

丸めの桁数に0を指定すると、少数第1位で四捨五入　round(10.555,2)<br>
=>10.56<br><br>

少数第1位で四捨五入<br>
select id,name,round(price * 1.08,0) from products;<br><br>

少数第1位で四捨五入<br>
select id,name,round(price * 1.08,1) from products;<br><br>

## 文字列演算
concat(文字列1,文字列2,文字列3,)<br>

select concat(last_name,'',first_name,'さん') from users;

### メルマガ用のリスト作成
select concat(last_name,'さん'), email from users where gender = 2;

## 日付の計算
### 主な日付と時刻の関数や演算子
- 現在の日付：current_date
  - select current_date();<br>
  => 2022-03-16
- 現在の時刻：current_timestamp
  - select current_timestamp();<br>
    => 2022-03-16 10:46:08
- n日後の日付：d + n
  - select current_date() + 3;<br>
  => 20220319
- n日前の日付：d - n
  - select current_date() - 3;<br>
  => 20220313
- x時間後の時刻：interval 'x hour'
  - select current_time() + interval 6 hour;<br>
  => 16:52:02
- x時間前の時刻：- interval 'x hour'
  - select current_time() - interval 6 hour;<br>
  => 04:52:54
- extract：日付や時刻の特定の部分(年や月)までを取り出す
  - ordersテーブルから注文日時(order_timeカラム)が、2017年01月のレコードを取得する
    - select * from orders where extract(year_month from order_time) = 201701;

  - ordersテーブルから注文日時(order_timeカラム)が、2017年のレコードを取得する
      - select * from orders where extract(year from order_time) = 2017;

  - ordersテーブルから注文日時(order_timeカラム)が、1月のレコードを取得する
```SQL
select * from orders where extract(month from order_time) = 1;
```