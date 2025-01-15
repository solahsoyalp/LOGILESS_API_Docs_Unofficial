

出荷伝票
====


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID出荷伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。出荷管理番号とは異なります。 |
| code | 出荷管理番号 |
| document\_status | [伝票ステータス](errors.md#伝票ステータス) |
| allocation\_status | [引当ステータス](type/.mdallocation_status) |
| delivery\_status | [配送ステータス](type/.mddelivery_status) |
| shipper\_name1 | 荷送人名(1) |
| shipper\_name2 | 荷送人名(2) |
| shipper\_name\_kana1 | 荷送人名かな(1) |
| shipper\_name\_kana2 | 荷送人名かな(2) |
| shipper\_country | 荷送人 国 - デフォルトは `JP` |
| shipper\_post\_code | 荷送人 郵便番号 |
| shipper\_prefecture | 荷送人 都道府県 |
| shipper\_address1 | 荷送人 住所1 |
| shipper\_address2 | 荷送人 住所2 |
| shipper\_address3 | 荷送人 住所3 |
| shipper\_phone | 荷送人 電話番号 |
| recipient\_name1 | お届け先名(1) |
| recipient\_name2 | お届け先名(2) |
| recipient\_name\_kana1 | お届け先名かな(1) |
| recipient\_name\_kana2 | お届け先名かな(2) |
| recipient\_country | お届け先 国 - デフォルトは `JP` |
| recipient\_post\_code | お届け先 郵便番号 |
| recipient\_prefecture | お届け先 都道府県 |
| recipient\_address1 | お届け先 住所1 |
| recipient\_address2 | お届け先 住所2 |
| recipient\_address3 | お届け先 住所3 |
| recipient\_phone | お届け先 電話番号 |
| cod\_total | 代金引換合計金額 - デフォルトは `0` |
| delivery\_method | [配送方法](type/.mddelivery_method) |
| delivery\_package\_quantity | 梱包数 - デフォルトは `1` |
| delivery\_temperature\_control | [配送温度](type/.mdtemperature_control) - デフォルトは `Normal` |
| scheduled\_shipping\_date | 出荷予定日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| release\_date | 発売日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_time\_zone | [お届け希望時間帯](https://support.logiless.com/merchant/order-management/delivery-methods/delivery-preferred-timezones/) |
| delivery\_tracking\_numbers | [配列] 送り状番号の一覧 |
| picking\_notes | 出荷指示書 特記事項 |
| way\_bill\_notes | 送り状 特記事項 |
| gift | ギフトかどうか(boolean) - ギフトの場合は `true`、ギフトでない場合は `false` |
| wrapping | ラッピング |
| attr1 | フリー項目1 |
| attr2 | フリー項目2 |
| attr3 | フリー項目3 |
| noshi | 熨斗 |
| total\_quantity | 合計数量 |
| total\_weight | 合計重量 |
| total\_size\_coefficient | 合計サイズ係数 |
| waiting\_for\_confirmation | 確認待ちかどうか(boolean) - 確認待ちの場合は `true`、確認待ちでない場合は `false` |
| lines | [配列] 明細行 - [line](#property_line)の配列 |
| shipped\_actual\_stocks | [読取専用][配列] 出荷済みの物理在庫 - [shipped\_actual\_stock](#property_shipped_actual_stock)の配列 |
| warehouse | 出荷元倉庫 - 倉庫ID |
| store | 店舗 - 店舗ID |
| sales\_order | 受注伝票 - [sales\_order](#property_sales_order)のプロパティを参照※同梱された出荷伝票の場合、同梱先となった受注伝票がセットされます。出荷された全ての受注伝票を取得するには、`lines`エンティティの`origin`を参照します。 |
| is\_combined | 同梱されているかどうか(boolean) - 同梱されている場合は `true`、同梱されていない場合は `false` |
| combined\_shipping | 同梱処理中かどうか(boolean) - 同梱処理中の場合は `true`、同梱処理中でない場合は `false` |
| combined\_payment\_receipts | 領収書を同梱するかどうか(boolean) - 領収書も同梱する場合は `true`、領収書を同梱しない場合は `false` |
| document\_date | 伝票日付 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| posting\_date | 転記日付 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at | 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


### line




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID受注伝票明細行をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| code | 明細行コード |
| status | [読取専用] [明細ステータス](type/.mddocument_line_status) |
| article\_code | [必須] 商品コード |
| article\_name | [必須] 商品名 |
| article\_option | 明細行備考欄 |
| price | 価格 - デフォルトは `0` |
| quantity | 数量 |
| tax\_indicator | [税区分](type/.mdtax_indicator) - デフォルトは `Included` |
| tax\_rate | 税率 - デフォルトは `8` |
| subtotal | [読取専用] 小計 |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |
| origin | [読取専用] 受注伝票 - [origin](#property_origin)のプロパティを参照 |
| cached\_allocated\_quantity | [読取専用] 在庫が引き当てられた数量 |
| is\_child | [読取専用] 子明細行かどうか - 子明細行の場合は `1`そうでない場合は`0` |
| is\_parent | [読取専用] 親明細行かどうか - 親明細行の場合は `1`そうでない場合は`0` |
| is\_partial\_cancel | [読取専用] 一部キャンセルかどうか キャンセルの場合は`1`そうでない場合は`0` |
| tax\_total | 税の合計 |


### origin




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID受注伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。受注コードとは異なります。 |
| code | 受注コード |


### article




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID商品マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| code | 商品コード |
| model\_number | 型番 |
| name | [必須] 商品名 |
| name\_kana | 商品名かな |
| identification\_code | 識別コード |
| object\_code | ロジレスコード |


### shipped\_actual\_stock


伝票ステータスが出荷済みで、かつ出荷期限日、またはロット番号が含まれる在庫が引き当てられた場合に利用できます。




| プロパティ | 説明 |
| --- | --- |
| article\_code | [必須] 商品コード |
| deadline | 出荷期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| lot\_number | ロット番号 |
| quantity | 数量 |


### sales\_order




| プロパティ | 説明 |
| --- | --- |
| id | ID受注伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。受注コードとは異なります。 |
| code | 受注コード |
| parent\_code | 親受注コード |


エンドポイント
-------


* [出荷伝票の一覧を取得](#get_list)


### 出荷伝票の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/outbound_deliveries`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| id | ID |
| object\_code | 出荷管理番号 |
| document\_status | [伝票ステータス](errors.md#伝票ステータス) - 複数指定する場合はカンマ区切り |
| delivery\_status | [配送ステータス](type/.mddelivery_status) - 複数指定する場合はカンマ区切り |
| ordered\_at\_from | 注文日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered\_at\_to | 注文日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_from | 完了日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_to | 完了日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse | 倉庫 - 倉庫ID |
| store | 店舗 - 店舗ID |
| scheduled\_shipping\_date\_from | 出荷予定日（From） - `Y-m-d`形式 (例 : `2018-01-01`) |
| scheduled\_shipping\_date\_to | 出荷予定日（To） - `Y-m-d`形式 (例 : `2018-01-10`) |



