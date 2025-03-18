# 出荷伝票

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID出荷伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。出荷管理番号とは異なります。 |
| code | 出荷管理番号 |
| document_status | [伝票ステータス](errors.md#伝票ステータス) - 複数指定する場合はカンマ区切り |
| allocation_status | [引当ステータス](type/allocation_status.md) |
| delivery_status | [配送ステータス](type/delivery_status.md) - 複数指定する場合はカンマ区切り |
| shipper_name1 | 荷送人名(1) |
| shipper_name2 | 荷送人名(2) |
| shipper_name_kana1 | 荷送人名かな(1) |
| shipper_name_kana2 | 荷送人名かな(2) |
| shipper_country | 荷送人 国 - デフォルトは `JP` |
| shipper_post_code | 荷送人 郵便番号 |
| shipper_prefecture | 荷送人 都道府県 |
| shipper_address1 | 荷送人 住所1 |
| shipper_address2 | 荷送人 住所2 |
| shipper_address3 | 荷送人 住所3 |
| shipper_phone | 荷送人 電話番号 |
| recipient_name1 | お届け先名(1) |
| recipient_name2 | お届け先名(2) |
| recipient_name_kana1 | お届け先名かな(1) |
| recipient_name_kana2 | お届け先名かな(2) |
| recipient_country | お届け先 国 - デフォルトは `JP` |
| recipient_post_code | お届け先 郵便番号 |
| recipient_prefecture | お届け先 都道府県 |
| recipient_address1 | お届け先 住所1 |
| recipient_address2 | お届け先 住所2 |
| recipient_address3 | お届け先 住所3 |
| recipient_phone | お届け先 電話番号 |
| cod_total | 代金引換合計金額 - デフォルトは `0` |
| delivery_method | [配送方法](type/delivery_method.md) |
| delivery_package_quantity | 梱包数 - デフォルトは `1` |
| delivery_temperature_control | [配送温度](type/temperature_control.md) - デフォルトは `Normal` |
| scheduled_shipping_date | 出荷予定日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| release_date | 発売日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery_preferred_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery_preferred_time_zone | [お届け希望時間帯](https://support.logiless.com/merchant/order-management/delivery-methods/delivery-preferred-timezones/) |
| delivery_tracking_numbers | [配列] 送り状番号の一覧 |
| picking_notes | 出荷指示書 特記事項 |
| way_bill_notes | 送り状 特記事項 |
| gift | ギフトかどうか(boolean) - ギフトの場合は `true`、ギフトでない場合は `false` |
| wrapping | ラッピング |
| attr1 | フリー項目1 |
| attr2 | フリー項目2 |
| attr3 | フリー項目3 |
| noshi | 熨斗 |
| total_quantity | 合計数量 |
| total_weight | 合計重量 |
| total_size_coefficient | 合計サイズ係数 |
| waiting_for_confirmation | 確認待ちかどうか(boolean) - 確認待ちの場合は `true`、確認待ちでない場合は `false` |
| lines | [配列] 明細行 - [line](#property_line)の配列 |
| shipped_actual_stocks | [読取専用][配列] 出荷済みの物理在庫 - [shipped_actual_stock](#property_shipped_actual_stock)の配列 |
| warehouse | 出荷元倉庫 - 倉庫ID |
| store | 店舗 - 店舗ID |
| sales_order | 受注伝票 - [sales_order](#property_sales_order)のプロパティを参照※同梱された出荷伝票の場合、同梱先となった受注伝票がセットされます。出荷された全ての受注伝票を取得するには、`lines`エンティティの`origin`を参照します。 |
| is_combined | 同梱されているかどうか(boolean) - 同梱されている場合は `true`、同梱されていない場合は `false` |
| combined_shipping | 同梱処理中かどうか(boolean) - 同梱処理中の場合は `true`、同梱処理中でない場合は `false` |
| combined_payment_receipts | 領収書を同梱するかどうか(boolean) - 領収書も同梱する場合は `true`、領収書を同梱しない場合は `false` |
| document_date | 伝票日付 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| posting_date | 転記日付 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished_at | 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

### line

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID受注伝票明細行をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| code | 明細行コード |
| status | [読取専用] [明細ステータス](type/document_line_status.md) |
| article_code | [必須] 商品コード |
| article_name | [必須] 商品名 |
| article_option | 明細行備考欄 |
| price | 価格 - デフォルトは `0` |
| quantity | 数量 |
| tax_indicator | [税区分](type/tax_indicator.md) - デフォルトは `Included` |
| tax_rate | 税率 - デフォルトは `8` |
| subtotal | [読取専用] 小計 |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |
| origin | [読取専用] 受注伝票 - [origin](#property_origin)のプロパティを参照 |
| cached_allocated_quantity | [読取専用] 在庫が引き当てられた数量 |
| is_child | [読取専用] 子明細行かどうか - 子明細行の場合は `1`そうでない場合は`0` |
| is_parent | [読取専用] 親明細行かどうか - 親明細行の場合は `1`そうでない場合は`0` |
| is_partial_cancel | [読取専用] 一部キャンセルかどうか キャンセルの場合は`1`そうでない場合は`0` |
| tax_total | 税の合計 |

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
| model_number | 型番 |
| name | [必須] 商品名 |
| name_kana | 商品名かな |
| identification_code | 識別コード |
| object_code | ロジレスコード |

### shipped_actual_stock

伝票ステータスが出荷済みで、かつ出荷期限日、またはロット番号が含まれる在庫が引き当てられた場合に利用できます。

| プロパティ | 説明 |
| --- | --- |
| article_code | [必須] 商品コード |
| deadline | 出荷期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| lot_number | ロット番号 |
| quantity | 数量 |

### sales_order

| プロパティ | 説明 |
| --- | --- |
| id | ID受注伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。受注コードとは異なります。 |
| code | 受注コード |
| parent_code | 親受注コード |

## エンドポイント

* [出荷伝票の一覧を取得](#get_list)

### 出荷伝票の一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/outbound_deliveries`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| id | ID |
| object_code | 出荷管理番号 |
| document_status | [伝票ステータス](errors.md#伝票ステータス) - 複数指定する場合はカンマ区切り |
| delivery_status | [配送ステータス](type/delivery_status.md) - 複数指定する場合はカンマ区切り |
| ordered_at_from | 注文日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered_at_to | 注文日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished_at_from | 完了日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished_at_to | 完了日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse | 倉庫 - 倉庫ID |
| store | 店舗 - 店舗ID |
| scheduled_shipping_date_from | 出荷予定日（From） - `Y-m-d`形式 (例 : `2018-01-01`) |
| scheduled_shipping_date_to | 出荷予定日（To） - `Y-m-d`形式 (例 : `2018-01-10`) |



