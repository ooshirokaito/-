# テーブル定義書1
## 全体
- 送付先住所を管理するテーブルがない。
 > 複数の送付先を管理できるようにしましょう。

## Songs/Labels/Artists/Genre/Cart item
- PKがない。
 > PKを作りましょう。
- FKに対してAUTO INCREMENTをつけている。
 > FKはAUTO INCREMENTではありません。

## Users
- カラム名に「user_」という接頭辞がついているが接頭辞は必要ない
 > カラム名に「user_」という接頭辞がついているが接頭辞は必要ないです。
- 「user_f_name」,「user_f_kana」の NOT NULLに◯が入っていない
 > 「user_f_name」,「user_f_kana」の NOT NULLに◯をつけましょう。
- 「user_f_name」,「user_tel」などでカラム名に略語を使ってるが、略語は使うべきでない
 > 「user_f_name」,「user_tel」などでカラム名に略語を使ってるが、略語は避けましょう。
- 「member_status」のデータ型がstringになっているが,DEFAULTがFALSEになっている。退会しているか否かの2通りなら,データ型はbooleanが適している。
 > 退会しているか否かの2通りなら,データ型はbooleanが適しています。
- 「member_status」というカラム名では会員の何のステータスを表しているか分からない。
 > カラム名では何を表しているか分かるように命名しましょう。
- 現状でははじめに登録した住所にしか配送先を管理できていない。
 > 複数の配送先を管理できるようにしましょう。

## Admin
- テーブル名がAdminsではなくAdminと単数になっている。
 > 正しいテーブル名をつけましょう。
- [Products]が1で[Discs]が多なので「disc_id」は必要ない
 > 親にはFKは必要ないので、修正しましょう。
- 「admin_id(正しくはid)」のPK,AUTO INCREMENt,INDEXに◯が入っていない
 > 正しいオプションをつけましょう。

## Products
- 「genre_id」,「label_id」,「artist_id」はFK
 > 「genre_id」,「label_id」,「artist_id」はFKですか？でしたらオプションを付けましょう。
- カラム名に「product_」という接頭辞がついているが接頭辞は必要ない
 > 接頭辞は必要ありません。
- 「cd_image」はrefileを使うなら「cd_image_id」とする必要がある。またデータ型はstringのほうが好ましい
 > 「cd_image」はrefileを使うなら「cd_image_id」とする必要があります。またデータ型はstringのほうが適切です。
- 「stock_status」のデータ型はintegerにして、enumで管理したほうがいい
 > 正しいデータ型で管理しましょう。
- 在庫数は入荷数と販売数に依存するものなので、データとして持つ必要はありません。
 > 在庫数はデータとして持つ必要はありません。

## Songs
- 曲名をもつカラムを「song」としているが、「name」などにすべき
 > カラム名は役割がわかる命名をしましょう。
- 「song」のデータ型がintegerになっているが,正しくはstring
 > 正しいデータ型を選択しましょう。

## Artists
- FK「product_id」は必要ない
 > 親子関係を確認し、不必要なFKは削除しましょう。
- 「artist」のデータ型がintegerになってるが、正しくはstring
 > 正しいデータ型を選択しましょう。
- アーティスト名をもつカラムを「artist」としているが、「name」などにすべき
 > カラム名は役割がわかる命名をしましょう。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
 > FKはAUTO INCREMENt,INDEXにする必要はありません。

## Genre
- FK「product_id」は必要ない
 > 親子関係を確認し、不必要なFKは削除しましょう。
- テーブル名が単数形になっている
 > テーブル名は複数形にしましょう。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
 > FKはAUTO INCREMENt,INDEXにする必要はありません。
- 「genre」のデータ型がintegerになってるが、正しくはstring
 > 正しいデータ型を選択しましょう。
- ジャンル名をもつカラムを「genre」としているが、「name」などにすべき
 > カラム名は役割がわかる命名をしましょう。

## Cart item
- テーブル名が単数形になっている。_で区切ってcart_itemとするのが正しい
 > テーブル名が単数形になっている。_で区切ってcart_itemとするのが正しいです。
- FKが「products_id」となっていますが、「product_id」にすべき
 > FKは単数形にしましょう。
- FKはAUTO INCREMENtではない,INDEXにする必要もない
 > FKはAUTO INCREMENt,INDEXにする必要はありません。
- 「buy num」となっているが「buy_num」とする必要がある
 > カラム名の命名は単語と単語の間は_で区切りましょう。
- 「subtotal」は必要ない
 > 不必要なカラムは削除しましょう。
- products_idにデータ型が入力されていない。
 > データ型を入力しましょう。

## Buy details
- テーブル名が「受注詳細」の意味になっていないので「order_details」などにするべき
 > テーブル名やカラム名は管理者視点で命名しましょう。
- [Buy details]が多で[Buy]が1なので、FKとして「buy_id」が必要
 > 親子関係を見直し、FKなどを用意しましょう。
- 「buy num」が何を表しているかわかりにくい&スネークケースになっていない。「qunantity」などにするべき
 > 「buy num」が何を表しているかわかりにくい&スネークケースになっていない。「qunantity」などが適切です。

## Buy
- テーブル名が「受注」の意味になっていないので「orders」などにするべき
 > テーブル名やカラム名は管理者視点で命名しましょう。
- Buy detailsで述べたとおり、[Buy details]が多で[Buy]が1なのでFK「buy_details_Id」は必要ない
 > 親子関係を見直し、不必要なFKは削除しましょう。
- 「pay」のデータ型はintegerにして、enumで管理したほうがいい
 > 正しいデータ型を選択しましょう。
- 「pay」が何を意味しているかわかりにくいので、「payment_method」などにすべき
 > カラムの命名は役割がわかりやすいものにしましょう。
- 「buy_at」はcreated_atと同じなので、必要ない
 > 役割が重複するカラムは削除しましょう。
- 「stock」が何を表しているかわからないので、「total_price」などにすべき
 > カラムの命名は役割がわかりやすいものにしましょう。
- 送付先住所はあるが、郵便番号と宛名がない
 > 郵便番号や宛名を管理しましょう。

## Discs
- ディスクテーブルにtrack_numがあり、曲ごとにトラックNo.を管理できていない。
 > 曲ごとにトラックNo.を管理しましょう。
- 「disc_id(正しくはid)」のINDEXに◯がない
 > disc_idはINDEXをつけるのが適切です。
- FKが「products_id」となっていますが、「product_id」にすべき
 > FKは単数形にしましょう。


# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。

# 研修担当レビュー
<font color="Red">再提出の際はこのレビューを残しておいてください。</font>

## product
- 「genre_id」,「label_id」,「artist_id」はFK
 >「genre_id」,「label_id」,「artist_id」はFKです。
  -FKです。と言い切るのではなく、「FKですか？でしたらオプションを付けてください」というように一回確認をとってもいいかもしれません！

## bbb
- 要件でyyyとなっていますが、それに対する指摘が足りていません



