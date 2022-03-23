# テーブルの結合
データベース mydb<br>
- テーブル users
  - カラム id, first_name, last_name, gender, birthday, prefecture_id

- テーブル products
  - カラム id, name, price

- テーブル orders
  - カラム id, user_id, amount, order_time

- テーブル access_log
  - カラム id, user_id, request_path, request_time, request_mouth

  ## テーブルの正規化
    テーブルを分けて情報の重複をなくしていく作業<br>


  ### テーブルを正規化するメリット
  1. データの管理か容易になる
  1. データ容量の削減
  => 特別な意図がなければ、テーブルは正規化する。<br>
  (特別な意図の例)システムパフォーマンスの向上のため

  ## テーブルの統合
    テーブル同士をある条件で結合することにより、正規化なしの状態を作りだすこと

    ### 主キー(Primary key, PK)
    一つの行を特定できる列のこと

    ### 外部キー(Foreign key, FK)
    他のテーブルとの関連付けに使う列のこと
    外部キーは関連付けされた先のテーブルでは主キーになる

  ## リレーションシップの種類
  1対多
  多対多(中間テーブルが必要)
  1対1

  ## 内部結合
    ``` SQL
    select
      テーブル名1,列名,
      テーブル名2,列名...
    from
      テーブル名1
    inner join
      テーブル名2
    on テーブル名1.列名 = テーブル名2.列名;
    ```

    ``` SQL
    select
      users.id,
      users.last_name,
      users.first_name,
      prefectures.name
    from
      users
    inner join
      prefectures
    on users.prefecture_id = prefectures.id;
    ```

  ## inner join + where
    ``` SQL
    select
      テーブル名1,列名,
      テーブル名2,列名...
    from
      テーブル名1
    inner join
      テーブル名2
    on テーブル名1.列名 = テーブル名2.列名
    where
      絞り込み条件;
    ```

    ``` SQL
    select
      users.id,
      users.last_name,
      users.first_name,
      prefectures.name
    from
      users
    inner join
      prefectures
    on users.prefecture_id = prefectures.id
    where users.gender = 2;
    ```

    ## 記述順序

    1. select 取得行(カラム)の指定
    1. from 対象テーブルの指定
    1. 結合処理
    1. where 絞り込み条件の指定
    1. group by グループ化の条件を指定
    1. having グループ化した後の絞り込み条件を指定
    1. order by 並び替え条件を指定
    1. LIMIT 取得する行数の制限

  ```SQL
    select 
	 orders.id,
     orders.order_time,
     orders.amount,
     users.id,
     users.last_name,
     users.first_name
    from orders
    inner join
      users
    on orders.user_id = users.id
    where
		  users.prefecture_id = 13
      and orders.order_time >= '2017-01-01 00:00:00'
		  and orders.order_time < '2017-02-01 00:00:00'
  ```

  
  ## 外部結合
  - 片方のテーブルが全て出力される、テーブルの統合
  - 外部結合は欠落のあるデータを取り扱う結合

    構文
    ``` SQL
    select
      テーブル名1,列名,
      テーブル名2,列名...
    from
      テーブル名1
    outer join
      テーブル名2
    on テーブル名1.列名 = テーブル名2.列名;
    ```