# ビュー
  ## create view
  構文<br>
  create view ビュー名 (<ビューの列名1>,<ビューの列名2>,...)<br>
  as<br>
  <select文>

  ```SQL
  create view prefecutr_user_counts(name,count)
    as
    select
      p.name name,
      count(*) count
    from
      users u
    inner join
      prefectures p
      on u.prefecture_id = p.id
    group by
      u.prefecture_id;
  ```

  ```SQL
    select
      name,
        count
    from
      prefecutr_user_counts;
  ```

  ### ビューの定義で、order by 句は使えない

  ## ビューの削除
  ```SQL
    drop view prefecutr_user_counts;
  ```

  ## サブクエリ
  ```SQL
    select 
      id,
        last_name,
        first_name
    from
      users
    where id not in(    
    select 
      user_id
    from
      orders
    where
      order_time >= '2017-12-01 00:00:00'
        and order_time < '2018-12-01 00:00:00')
  ```


  ```SQL
    select
      *
    from
      products
    where
      price > (
    select 
      avg(price)
    from
      products)
    order by
      price desc, id asc;
  ```