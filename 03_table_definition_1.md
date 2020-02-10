# テーブル定義書1
## 全体
- 送付先住所を管理するテーブルがない。

## Songs/Labels/Artists/Genre/Cart item
- PKがない。
- FKに対してAUTO INCREMENTをつけている。

## Users
- カラム名に「user_」という接頭辞がついているが接頭辞は必要ない
- 「user_f_name」,「user_f_kana」の NOT NULLに◯が入っていない
- 「user_f_name」,「user_tel」などでカラム名に略語を使ってるが、略語は使うべきでない
- 「member_status」のデータ型がstringになっているが,DEFAULTがFALSEになっている。退会しているか否かの2通りなら,データ型はbooleanが適している。
- 「member_status」というカラム名では会員の何のステータスを表しているか分からない。
- 現状でははじめに登録した住所にしか配送先を管理できていない。

## Admin
- テーブル名がAdminsではなくAdminと単数になっている。
- [Products]が1で[Discs]が多なので「disc_id」は必要ない
- 「admin_id(正しくはid)」のPK,AUTO INCREMENt,INDEXに◯が入っていない

## Products
- 「genre_id」,「label_id」,「artist_id」はFK
- カラム名に「product_」という接頭辞がついているが接頭辞は必要ない
- 「cd_image」はrefileを使うなら「cd_image_id」とする必要がある。またデータ型はstringのほうが好ましい
- 「stock_status」のデータ型はintegerにして、enumで管理したほうがいい
- 在庫数は入荷数と販売数に依存するものなので、データとして持つ必要はありません。

## Songs
- 曲名をもつカラムを「song」としているが、「name」などにすべき
- 「song」のデータ型がintegerになっているが,正しくはstring

## Artists
- FK「product_id」は必要ない
- 「artist」のデータ型がintegerになってるが、正しくはstring
- アーティスト名をもつカラムを「artist」としているが、「name」などにすべき
- FKはAUTO INCREMENtではない,INDEXにする必要もない

## Genre
- FK「product_id」は必要ない
- テーブル名が単数形になっている
- FKはAUTO INCREMENtではない,INDEXにする必要もない
- 「genre」のデータ型がintegerになってるが、正しくはstring
- ジャンル名をもつカラムを「genre」としているが、「name」などにすべき

## Cart item
- テーブル名が単数形になっている。_で区切ってcart_itemとするのが正しい
- FKが「products_id」となっていますが、「product_id」にすべき
- FKはAUTO INCREMENtではない,INDEXにする必要もない
- 「buy num」となっているが「buy_num」とする必要がある
- 「subtotal」は必要ない
- products_idにデータ型が入力されていない。

## Buy details
- テーブル名が「受注詳細」の意味になっていないので「order_details」などにするべき
- [Buy details]が多で[Buy]が1なので、FKとして「buy_id」が必要
- 「buy num」が何を表しているかわかりにくい&スネークケースになっていない。「qunantity」などにするべき

## Buy
- テーブル名が「受注」の意味になっていないので「orders」などにするべき
- Buy detailsで述べたとおり、[Buy details]が多で[Buy]が1なのでFK「buy_details_Id」は必要ない
- 「pay」のデータ型はintegerにして、enumで管理したほうがいい
- 「pay」が何を意味しているかわかりにくいので、「payment_method」などにすべき
- 「buy_at」はcreated_atと同じなので、必要ない
- 「stock」が何を表しているかわからないので、「total_price」などにすべき
- 送付先住所はあるが、郵便番号と宛名がない

## Discs
- ディスクテーブルにtrack_numがあり、曲ごとにトラックNo.を管理できていない。
- 「disc_id(正しくはid)」のINDEXに◯がない
- FKが「products_id」となっていますが、「product_id」にすべき


# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。
