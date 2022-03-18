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
  多対多
  1対1