# データの更新
構文
``` SQL
  insert into
    テーブル名(列1, 列2, 列3,...)
  values
    テーブル名(列1, 列2, 列3,...);
```

``` SQL
  insert into products(name, price) values('新商品A',1000);
  select * from products;  (確認コード)
```

## 1列レコードを追加する
``` SQL
  insert products values(1007, '新商品B', 2000);
  select * from products;  (確認コード)
```

## 行を複数個追加する
``` SQL
  insert products(name,price) 
  values
    ('新商品C',3000),
      ('新商品D',4000),
      ('新商品E',5000);
  select * from products;
```

## レコードの更新
``` SQL
  set aql_safe_update = 0;
  update products set price = proce * 0.9;
```

## 行の削除
構文
``` SQL
  dekete from テーブル名 [where 削除条件];
```

``` SQL
    delete from products_categories;
```

## 条件を指定して行の削除
``` SQL
    delete from products where id = 1001;
```


