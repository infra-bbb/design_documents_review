# ER図1
## 全体
- 登録日、更新日のカラムが必要。
  > ActiveRecordでデフォルトで作られる登録日、更新日の記述もお願いいたします。
- 入荷したものを管理するテーブルがない。
  > 入荷の情報はどこで管理しているでしょうか。
- 受注の詳細を管理するテーブルがない。
  > 決済の商品内容を商品テーブルと関連付けて取得することが想定されますが、現状多対多で関連付いてしまいます。新たにテーブルを作成し、この問題を解決しましょう。


## エンドユーザ
- 論理削除を考慮していない。
  > ユーザを削除した場合、該当のレコードはどうなりますか。
- 複数の配送先情報を管理できるようになっていない。
  > 複数の配送先情報を登録できる必要があります。
- カートを持てるようになっていない。
  > カートを持てるように関連付けしましょう。
- FKの管理人IDが不要。
- 管理人との関連付けが不要。
  > 管理人と関連付けされていますが、管理人が複数人いるという想定でしょうか、今回の要件では管理人は1人です。

## 管理人
- エンドユーザとの関連付けが不要。
  > エンドユーザと関連付けされていますが、管理人が複数人いるという想定でしょうか、今回の要件では管理人は1人です。
- 商品との関連付けが不要。
  > エンドユーザと関連付けされていますが、管理人が複数人いるという想定でしょうか、今回の要件では管理人は1人です。

## カート
- 関連付く商品とカラムが重複している。
  > アーティスト名、ジャケット画像、シングル/アルバム名は商品テーブルから取り出すことができるため、不要です。
- PKと命名が明らかに異なり、入れるデータはカート内商品のため、カート内商品テーブルなどの命名が適切。
  > PKと命名が異なっており適切なER図とは言えません。また入れるデータはカート内商品であるため、そのようなテーブル名にするべきです。
- 決済と多対多で関連付くことを考慮していない。
  > 現在このテーブルは、ユーザが持つカートの役割と決済の注文内容の2つの役割を担うような設計になっています。どちらかに限定した関連付けにしましょう。

## 商品
- ジャンルの値がテーブル内の複数のレコードと重複する。
  > ジャンル名を保存するカラムがありますが、取りうる値が限定されるため、現状複数のテーブルで値が重複する可能性があります。
- アーティスト名の値がテーブル内の複数のレコードと重複する。
  > アーティスト名を保存するカラムがありますが、取りうる値が限定されるため、現状複数のテーブルで値が重複する可能性があります。
- レーベル名の値がテーブル内の複数のレコードと重複する。
  > レーベル名を保存するカラムがありますが、取りうる値が限定されるため、現状複数のテーブルで値が重複する可能性があります。
- シングルアルバム内の曲名について、別エンティティで管理していないため、似たレコードの重複する。
  > シングルアルバム名内曲名について、1商品に対して曲名は単一でない可能性が高いため、複数の値が入ってします。
- ディスクが複数枚ある場合について考慮されていない。
  > シングルアルバム名内曲名について、1商品に対してディスクは単一でない可能性が高いため、複数の値が入ってします。
- FKの管理人IDが不要。
- 管理人との関連付けが不要。
  > 管理人と関連付けされていますが、管理人が複数人いるという想定でしょうか、今回の要件では管理人は1人です。
- 在庫数カラムは計算結果になり値が変動するため不必要。
  > 在庫数カラムについて、入荷と注文の計算結果で示されるため、カラムとして管理する場合、変動が多くなってしまいます。
  
## 決済
- 受取人氏名の情報を管理できていない。
  > 現状、受取人氏名の情報を保存できていません。
- 配送先郵便番号の情報を管理できていない。
  > 現状、配送先郵便番号の情報を保存できていません。
- 合計金額を保存できていない。
  > 現状、合計金額の情報を保存できていません。
- 送料を管理するカラムがない。
  > 現状、送料の情報を保存できていません。
- テーブル名の命名は管理側視点が適切であるため決済は不適切。
  > テーブル名は管理側視点で命名しましょう。
- 購入日の役割がcreated_atと重複する。
  > ActiveRecordでデフォルトで作られる登録日と役割が重複してしまいます。
- 購入した商品の情報をカートから呼び出そうとしている。
  > 購入した商品について、カートから呼び出してしまうと決済済みの商品がカートに残り続けてしまいます。

## 購入履歴
- PKがない。
  > PKがありません。記述しましょう。
- 決済とエンティティを分けて記述する必要がない。
  > 決済と1対1で関連付いていますが、テーブルを分けて管理する必要はあるでしょうか。

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。

## 指摘事項
## 全体
- 購入時の価格はどこで保存しますか？(値段が変わった時に購入履歴の値段も変わってしまいます。)
- 入荷したものを管理する場所がありません。

## 商品
- 在庫数カラムは計算結果(= 入荷数 - 売上)のため、データとして保存するのに適しません。
- 複数枚ディスクも考慮されていません。

## カート
- 入れるデータはカート内商品のため、カート内商品テーブルなどの命名が適切です。

## 決済
- テーブルの命名は管理側視点が適切です。(決済はユーザー視点なので、受注など)
- 送料、合計金額を管理するカラムがありません。
- 購入日はcreated_atと役割が重複するので不要です。

## レビュー2回目
- すみません、↓のレビュー違うところに書いてました。下の理由により、受注詳細テーブルの不足の指摘をお願いします。
 - カート、決済周りのリレーションが異なることが最大のポイントです。カートと決済のリレーションはどのように用いますか？また、決済テーブルは商品とリレーションを持って、商品情報を購入履歴などで確認したいですが、決済テーブルと商品テーブルは多対多のため、中間テーブル(受注詳細)の必要性を指摘し、作成するよう促したいです。

