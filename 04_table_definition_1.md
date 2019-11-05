# テーブル定義書1_問題指摘
## 共通
- テーブル名の命名規則がNG。
- カラム名の接頭辞にテーブル名がついてる。
- created_atが全てユーザ登録日時になっている。
- updated_atが全てユーザ更新日時になっている。
- idがない。

## Admin
- 命名が複数形じゃない。
- PKがない。

## Users
- user_という接頭辞がついてる。
- 命名に略語を使っている。
- 住所とは別の配送先住所がある(配送先を複数登録することを考慮してない)。
- 郵便番号がinteger型
- 電話番号がinteger型
- member_statusが何を意味しているか不明。
- member_statusがstring型

## Products
- product_という接頭辞がついてる。
- FKの記載がない。
- 子テーブルのidを持っている。
- cd_titleはtitleで十分。
- 在庫状況をステータス管理しているので、在庫数と食い違う可能性がある。
- 在庫数カラムがある（入荷と売上から算出できる）。

## Discs
- disc_という接頭辞がついてる。
- products_idではなく、product_idにすべき。
- track_noの用途が不明。
- 複数枚組を考慮してない。

## Songs
- songカラムが曲名をもつならば命名はnameなどとするべき。
- songカラムが曲名をもたせるのに、integerとなってる。

## Labels
- product_idは不要。
- labelカラムがレーベル名をもつならばnameなどとするべき。

## Artists
- product_idは不要。
- artistカラムがアーティスト名をもつならばnameなどとするべき。
- artistカラムが曲名をもたせるのに、integerとなってる。

## Genre
- テーブル名が単数形になっている。
- product_idは不要。
- genreカラムがアーティスト名をもつならばnameなどとするべき。
- genreカラムが曲名をもたせるのに、integerとなってる。

## Cart item
- products_idではなく、product_idにすべき。
- buy numの意味が不明。_(アンダースコア)をつけてない。
- 小計金額は不要（数量と商品の価格から算出可能）。

## Buy
- buyだと受注の意味じゃない。
- 子テーブル（buy_details）のidをFKとして持っている。
- payが何を意味しているか不明。
- 支払合計がstockになっていて意味不明。
- 支払い方法がstringになっており、enumを考慮してない。
- 送付先住所はあるが、郵便番号と住所がない。

## Buy details
- buy detailsだと受注詳細の意味にならない。
- buy numは意味不明。スネークケースになってない。


* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。