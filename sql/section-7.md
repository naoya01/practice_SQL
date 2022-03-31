# 条件によって値を変更する（分岐）
構文<br>
``` SQL
  case
    when 条件式1 then 値1 　・・・条件式1がtrueならば値１
    [when 条件式2 then 値2]　・・・条件式2がtrueならば値2
    [else 値3]　・・・どれにも当てはまらないなら値3
  end
  []は省略可
```

``` SQL
  select
    u.id as user_id,
      count(*) as num,
      case
      when count(*) >= 5 then 'A'
          when count(*) >= 2 then 'B'
          else 'C'
      end as user_lank
  from
    users  u
  inner join
    orders o
  on u.id = o.user_id
  group by u.id
  order by user_lank asc;
```

## 取得値nullを0に置き換える
``` SQL
  select
    p.id,
      p.name,
      case
      when sum(product_qty) >= 20 then 'A'
          when sum(product_qty) >= 10 then 'B'
          else 'C'
      end as lank,
      sum(product_qty)
  from
    products p
  left join
    order_details od
  on p.id = od.product_id
  group by p.id
  order by lank;
```