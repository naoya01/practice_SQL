# データベース構造の操作

## データベースの作成
構文
``` SQL
  create database データベース名;
```

``` SQL
  create database book_store;
  show databases;　　データベースの確認
```

## 命名ルール
- 半角アルファベット・・・a,b,c
- 半角数字・・・0,1,2
- アンダースコア・・・_
- ただし、名前の最初は半角のアルファベットとする

### 具体例
- ○ users
- ○ mydb2
- ○ products_categories
- × _users
- × 1_users

## テーブルの追加
``` SQL
  use book_store;
  show tables;
  create table book(id int not null auto_increment primary key, title varchar(255) not null);
```

- 列名 id
 - int：整数型
 - not null：nullを許可しない
 - auto_increment：idを自動的にふる
 - primary key：主キーの設定
- 列名 title
  - varchar(255)：最大255文字の可変長文字列型
  - not null：nullを許可しない

## テーブルの構造の変更
``` SQL
  show columns from books;　　構造の確認
  alter table books add  price int after id;
```

## 列名の変更
構文
``` SQL
  alter table テーブル名 change 旧列名 新列名 データ型;
```
``` SQL
  alter table books change price unit_price int;
```

## 列名の削除
構文
``` SQL
  alter table テーブル名 drop 旧列名 新列名 データ型;
```
``` SQL
  alter table books drop price unit_price int;
```


## テーブルの削除
構文
``` SQL
  drop table テーブル名;
```
``` SQL
  drop table books;
```

## データベースの削除
構文
``` SQL
  drop database データベース名;
```
``` SQL
  drop database book_store;
```