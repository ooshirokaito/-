# テーブル定義書1
## 全体
- 送付先住所を管理するテーブルがない。

## Songs/Labels/Artists/Genre/Cart item
- PKがない。
- FKに対してAUTO INCREMENTをつけている。

## Admin
- テーブル名がAdminsではなくAdminになっている。
- PKがない。

## Products
- 親であるProductsがディスクID,ジャンルID,レーベルIDを持っている。

## Buy
- Buy detailsに対してBuyが子になってしまっている。

## Discs
- ディスクテーブルにtrack_numがあり、曲ごとにトラックNo.を管理できていない。

## Cart item
- products_idにデータ型が入力されていない。

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。
