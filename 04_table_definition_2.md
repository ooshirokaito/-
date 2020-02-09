# テーブル定義書2
## 全体
- 指摘事項

## sells/sell_details
- 購入に関するテーブルでテーブル名がsellになっている。
- 一つの購入詳細に対して複数の購入があるという親子関係になっている。

## sell_details
- 購入詳細IDのカラム名がsell_details_Idとなっており、idのiが大文字になっている。

## products
- 親のproductsがFK(genre_id,label_id,artist_id)を持っている。

## users
- member_statusのデータ型にenumを記述している。

## cart items
- カートアイテムIDのカラム名がCart item_idとなっており、頭文字が大文字かつスペースで単語を区切っている。
- 購入枚数のカラム名、buy numとなっており、スペースで単語を区切っている。

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。
