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