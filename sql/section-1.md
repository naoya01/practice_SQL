# SQL文の基礎
データベース mydb<br>
- テーブル users
  カラム id, first_name, last_name

- テーブル products<br>
  カラム id, price

**使用するデータベースを選択する**<br>
use データベース名

**必要なデータを取得する**<br>
selsct * from テーブル名; 

## エラー
select * form users;(スペルミス)
ｓｅｌｅｃｔ * form users;(全角文字)

## エラーしない(大文字、小文字は同じ扱い)
SELECT * FROM USERS;
SELECT * form users;
SElect * form users;
## コメントアウトの種類
「--」
-- select * form users;

「/**/」
/* select * form users; */

## 複数の列を取得
例1)select id, last_name form users;

例2)select
  id,
  last_name
from
  users;