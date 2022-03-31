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
- ✖️ _users
- ✖️ 1_users

## テーブルの追加
``` SQL
  use book_store;
  show tables;
  create table book(id int not null auto_increment primary key, title varchar(255) not null);
```

- 列名 id
  
- 列名 title