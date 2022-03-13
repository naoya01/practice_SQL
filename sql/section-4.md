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

## round