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


## 全体
  - テーブル名はスネークケースで複数形にする必要があります。

## admins
  - カラム名のadmin_の接頭辞は必要ありません。

## users
  - member_statusだと、何のステータスを意味するかわかりません。

## ships
  - 主キーにindexがありません。
  - カラム名のship_の接頭辞は必要ありません。
  
## products
  - discsとproductsの関係が逆です。discs_idが必要です。
    > discs_idは必要ありません。一つのdiscに複数のproductsが紐づくことになってしまいます。
    
  - stockは入荷と売上から算出できるので不要です。
  
## discs
  - products_idが不要です。
    > 一つの商品が複数のdiscを所有したいときはどうしますか？

  - 外部キーは「テーブル名の単数形_id」になります。
  - テーブル名に使用されている単語はカラム名に使用しません。

## cart items
  - 外部キーは「テーブル名の単数形_id」になります。
  
## sell_details
  - 購入時価格を保持するカラムがありません。
  - 親モデルのidを持っていません。
  
## sells
  - totalは何のtotalかわかりません。
  - 子モデルのidは不要です。
