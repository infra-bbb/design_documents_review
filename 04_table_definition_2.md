# テーブル定義書2
## 全体
  - 接頭辞にテーブル名をつける必要はありません。admins_id -> id

## admins
  - idカラムのINDEXに◯をつけましょう。

## users
  - user_l_name, user_f_nameと略さず、last_name, first_namtと命名しましょう。

## ships
  - テーブル名は名詞にしてください。ここではaddressesと命名する方が良いです。
  
## products
  - stock_statusは在庫数で判別可能なため、カラムを持つ必要はありません。
  - discsとproductsの関係が逆です。discs_idが必要です。
  
## discs
  - products_idが不要です。
  - INDEXに◯がついていません。

## songs
  - songカラムの内容が不明瞭です。曲名を持たせるならnameにした方がいいです。
  
## labels
  - labelカラムの内容が不明瞭です。レーベル名を持たせるならnameにした方がいいです。
  
## artists
  - artistカラムの内容が不明瞭です。アーティスト名を持たせるならnameにした方がいいです。
  
## genre
  - genreカラムの内容が不明瞭です。ジャンル名を持たせるならnameにした方がいいです。
  
## cart items
  - テーブル名に複数語を使用する場合はスネークケースで命名しましょう。
  - カラム名に複数語を使用する場合はスネークケースで命名しましょう。　buy num -> buy_num
  - buy numでは意味が不明瞭です。購入数量を持たせるならquantityにした方がいいです。
  
## sell_details
  - テーブルの命名をsell_detailsではなく、order_detailsにしましょう。
  - products_idカラムのFKに◯をつけましょう。
  - numでは意味が不明瞭です。購入数量を持たせるならquantityにした方がいいです。
  
## sells
  - テーブルの命名をsellsではなく、ordersにしましょう。
  - idカラムのINDEDXに◯をつけましょう。
  - payカラムの意味が不明瞭です。payment_wayなどわかりやすい命名にしましょう。
  
# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。
