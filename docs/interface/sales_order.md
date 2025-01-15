

受注伝票
====


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID受注伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。受注コードとは異なります。 |
| code | [必須] 受注コード |
| parent\_code | 親受注コード |
| document\_status | [読取専用] [伝票ステータス](errors.md#伝票ステータス) |
| allocation\_status | [読取専用] [引当ステータス](type/.mdallocation_status) |
| delivery\_status | [読取専用] [配送ステータス](type/.mddelivery_status) |
| incoming\_payment\_status | [入金ステータス](type/.mdincoming_payment_status) |
| authorization\_status | [承認ステータス](type/.mdauthorization_status) |
| customer\_code | 顧客コード |
| buyer\_name1 | [必須] 購入者名(1) |
| buyer\_name2 | 購入者名(2) |
| buyer\_name\_kana1 | 購入者名かな(1) |
| buyer\_name\_kana2 | 購入者名かな(2) |
| buyer\_country | 購入者 国 - デフォルトは `JP` |
| buyer\_post\_code | 購入者 郵便番号 |
| buyer\_prefecture | 購入者 都道府県 |
| buyer\_address1 | 購入者 住所1 |
| buyer\_address2 | 購入者 住所2 |
| buyer\_address3 | 購入者 住所3 |
| buyer\_phone | 購入者 電話番号 |
| buyer\_fax | 購入者 FAX番号 |
| buyer\_email | 購入者メールアドレス |
| recipient\_name1 | [必須] お届け先名(1) |
| recipient\_name2 | お届け先名(2) |
| recipient\_name\_kana1 | お届け先名かな(1) |
| recipient\_name\_kana2 | お届け先名かな(2) |
| recipient\_country | お届け先 国 - デフォルトは `JP` |
| recipient\_post\_code | お届け先 郵便番号 |
| recipient\_prefecture | お届け先 都道府県 |
| recipient\_address1 | [必須] お届け先 住所1 |
| recipient\_address2 | お届け先 住所2 |
| recipient\_address3 | お届け先 住所3 |
| recipient\_phone | お届け先 電話番号 |
| recipient\_fax | お届け先 FAX番号 |
| recipient\_email | お届け先 メールアドレス |
| subtotal | [読取専用] 商品合計金額（小計） |
| use\_point | ポイント利用 - デフォルトは `0` |
| use\_coupon | クーポン利用 - デフォルトは `0` |
| delivery\_fee | 送料 - デフォルトは `0` |
| sundry\_fee | その他手数料 - デフォルトは `0` |
| discount | 値引き - デフォルトは `0` |
| tax\_processing\_method | [税の計算順序](type/.mdtax_processing_method) - デフォルトは マーチャントの設定 |
| tax\_rounding\_method | [税の丸め](type/.mdtax_rounding_method) - デフォルトは マーチャントの設定 |
| document\_tax\_rate | 伝票の税率 - デフォルトは `0` |
| tax\_total | 税の合計 - 登録時のデフォルトは `NULL` （数値を指定した場合、税の自動計算が行われなくなります。） |
| total | [読取専用] 合計金額 |
| payment\_method | [必須] [支払方法](type/.mdpayment_method) |
| delivery\_method | [必須] [配送方法](type/.mddelivery_method) |
| delivery\_package\_quantity | 梱包数 - デフォルトは `1` |
| express\_type | [お急ぎ区分](type/.mdexpress_type) |
| delivery\_temperature\_control | [配送温度](type/.mdtemperature_control) - デフォルトは `Normal` |
| scheduled\_shipping\_date | [登録時のみ - 出荷伝票に転記] 出荷予定日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_time\_zone | お届け希望時間帯 |
| is\_isolated\_area | 離島かどうか - 離島の場合は `1` |
| delivery\_tracking\_number | 送り状番号出荷伝票に登録された送り状番号のうち、1つを返却します。 |
| buyer\_comment | 購入者備考欄 |
| merchant\_comment | マーチャント備考欄 |
| statement\_notes | 納品書 特記事項 |
| picking\_notes | 出荷指示書 特記事項 |
| way\_bill\_notes | 送り状 特記事項 |
| gift | ギフトかどうか - ギフトの場合は `1` |
| wrapping | ラッピング |
| noshi | 熨斗 |
| attr1 | フリー項目1 |
| attr2 | フリー項目2 |
| attr3 | フリー項目3 |
| attr4 | フリー項目4 |
| attr5 | フリー項目5 |
| attr6 | フリー項目6 |
| attr7 | フリー項目7 |
| attr8 | フリー項目8 |
| attr9 | フリー項目9 |
| attr10 | フリー項目10 |
| waiting\_for\_confirmation | [読取専用] 確認待ちかどうか - 確認待ちの場合は `1` |
| shipping\_confirmed | 出荷通知を実行済みかどうか - 実行済みの場合は `1` |
| is\_multiple\_deliveries | 出荷が分割されているかどうか - 分割されている場合は `1` |
| subscription\_id | 定期購入ID |
| subscription\_delivery\_number | 定期購入 お届け回数 |
| subscription\_next\_delivery\_date | 定期購入 次回配送日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| posting\_date | [読取専用] 転記日付 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| total\_quantity | [読取専用] 合計数量 |
| purchasing\_times | 購入回数 |
| tags | 受注伝票のタグ（配列） |
| ordered\_at | 注文日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) - デフォルトは現在時刻 |
| finished\_at | [読取専用] 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| lines | [必須][配列] 明細行 - [line](#property_line)の配列 |
| outbound\_deliveries | [読取専用] 出荷伝票 - [outbound\_delivery](interface/.mdoutbound_delivery)のプロパティを参照 |
| store | [必須] 店舗 - 店舗IDで指定 / レスポンスの際は[store](interface/.mdstore)のプロパティを参照 |
| warehouse | [登録時のみ - 出荷伝票に転記] 出荷元倉庫 - 倉庫IDで指定 / 指定がない場合は店舗のデフォルトの出荷元倉庫を使用 |
| cod\_total | [登録時のみ - 出荷伝票に転記] 代金引換金額 - デフォルトは受注伝票の合計金額（通常は指定しません） |
| document\_date | 伝票日付 - `Y-m-d`形式 (例 : `2018-01-01`) |
| payment\_due\_date | [読取専用] 入金期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |


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
| quantity | [必須] 数量 |
| is\_parent | [読取専用] 親明細行かどうか - 親明細行の場合は `1`そうでない場合は`0` |
| is\_child | [読取専用] 子明細行かどうか - 子明細行の場合は `1`そうでない場合は`0` |
| parent\_id | [読取専用] 親明細行ID（子明細行の場合にのみ設定されます） |
| cached\_allocated\_quantity | [読取専用] 在庫が引き当てられた数量 |
| is\_partial\_cancel | [読取専用] 一部キャンセルかどうか キャンセルの場合は`1`そうでない場合は`0` |
| tax\_indicator | [税区分](type/.mdtax_indicator) - デフォルトは `Included` |
| tax\_rate | 税率 - デフォルトは `10` |
| tax\_total | [読取専用] 税の合計 |
| subtotal | [読取専用] 小計 |
| deadline | （物理在庫の指定）出荷期限日 |
| lot\_number | （物理在庫の指定）ロット番号 |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |
| origin | [読取専用] 受注伝票 - [origin](#property_origin)のプロパティを参照 |


### article




| プロパティ | 説明 |
| --- | --- |
| id | ID商品マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| code | 商品コード |
| identification\_code | 識別コード |
| object\_code | ロジレスコード |
| model\_number | 型番 |
| name | 商品名 |
| name\_kana | 商品名かな |


### origin




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID受注伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。受注コードとは異なります。 |
| code | 受注コード |


エンドポイント
-------


* [受注伝票の一覧を取得](#get_list)
* [受注伝票の検索](#search)
* [受注伝票を登録](#post)
* [受注伝票を編集](#put)
* [受注伝票をキャンセル](#reversal)
* [明細行をキャンセル](#reversal_line)


### 受注伝票の一覧を取得


id, codeは単一指定のみリクエストが可能です。


複数指定されたい場合は[受注伝票の検索](#search) をご利用ください。


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/sales_orders`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| id | ID |
| object\_code | 受注管理番号 |
| code | 受注コード |
| parent\_code | 親受注コード |
| document\_status | [伝票ステータス](errors.md#伝票ステータス) - 複数指定する場合はカンマ区切り |
| delivery\_status | [配送ステータス](type/.mddelivery_status) - 複数指定する場合はカンマ区切り |
| incoming\_payment\_status | [入金ステータス](type/.mdincoming_payment_status) - 複数指定する場合はカンマ区切り |
| authorization\_status | [承認ステータス](type/.mdauthorization_status) - 複数指定する場合はカンマ区切り |
| allocation\_status | [引当ステータス](type/.mdallocation_status) - 複数指定する場合はカンマ区切り |
| delivery\_method | [配送方法](type/.mddelivery_method) |
| waiting\_for\_confirmation | 確認待ちかどうか - 確認待ちの場合は `1`、確認待ちでない場合は `0` |
| ordered\_at\_from | 注文日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered\_at\_to | 注文日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_from | 完了日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_to | 完了日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| store | 店舗 - 店舗ID |
| scheduled\_shipping\_date\_from | 出荷予定日（From） - `Y-m-d`形式 (例 : `2018-01-01`) |
| scheduled\_shipping\_date\_to | 出荷予定日（To） - `Y-m-d`形式 (例 : `2018-01-10`) |


id, codeは単一指定のみリクエストが可能です。
複数指定されたい場合は[受注伝票の検索](#search) をご利用ください。


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": "7621",
      "code": "test-20180101-4",
      "document_date": "2018-02-02",
      "posting_date": "2018-02-02",
      "status": "WaitingForAllocation",
      "delivery_status": "WaitingForShipment",
      "incoming_payment_status": "NotPaid",
      "authorization_status": "Authorized",
      "buyer_name1": "山田 太郎",
      "buyer_country": "JP",
      "recipient_name1": "山田 華子",
      "recipient_country": "JP",
      "recipient_post_code": "1700005",
      "recipient_prefecture": "東京都",
      "recipient_address1": "豊島区",
      "recipient_address2": "南大塚3-36-7",
      "recipient_address3": "南大塚T&Tビル 5F",
      "subtotal": 1000,
      "use_point": 0,
      "discount": 0,
      "delivery_fee": 0,
      "sundry_fee": 0,
      "tax_processing_method": "LineByLine",
      "tax_rounding_method": "RoundOff",
      "document_tax_rate": 8,
      "tax_total": 0,
      "payment_method": "credit_card_payment",
      "delivery_method": "yamato",
      "delivery_package_quantity": 1,
      "delivery_temperature_control": "Normal",
      "scheduled_shipping_date": "2018-02-02",
      "is_isolated_area": 0,
      "gift": 0,
      "waiting_for_confirmation": 1,
      "shipping_confirmed": 0,
      "is_multiple_deliveries": 0,
      "total_quantity": 1,
      "purchasing_times": 1,
      "tags": [
        "新規",
        "定期"
      ],
      "ordered_at": "2018-02-02 17:49:45",
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46",
      "lines":[
        {
          "id": 8837,
          "status": "WaitingForAllocation",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "quantity": 1
        }
      ],
      "outbound_deliveries":[
         {
           "id": 1090,
           "code": "2300000010909",
           "document_date": "2018-02-02 00:00:00",
           "posting_date": "2018-02-02 00:00:00",
           "document_status": "WaitingForAllocation",
           "delivery_status": "WaitingForShipment",
           "shipper_name_1": "ロジレス ストア",
           "shipper_country": "JP",
           "shipper_post_code": "1700005",
           "shipper_prefecture": "東京都",
           "shipper_address_1": "豊島区",
           "shipper_address_2": "南大塚3-36-7",
           "shipper_address_3": "南大塚T&Tビル 5F",
           "shipper_phone": "09058949377",
           "recipient_name_1": "山田 華子",
           "recipient_country": "JP",
           "recipient_post_code": "1700005",
           "recipient_prefecture": "東京都",
           "recipient_address_1": "豊島区",
           "recipient_address_2": "南大塚3-36-7",
           "cod_total": 0,
           "delivery_method": "yamato",
           "delivery_package_quantity": "1",
           "delivery_temperature_control": "Normal",
           "delivery_tracking_numbers":[],
           "gift": false,
           "total_quantity": 1,
           "total_weight": 0,
           "total_size_coefficient": 0,
           "ordered_at": "2018-02-02 12:22:08",
           "created_at": "2018-02-02 12:22:09",
           "updated_at": "2018-02-02 12:22:09",
           "lines":[
             {
               "id": 8837,
               "status": "WaitingForAllocation",
               "article_code": "article-1",
               "article_name": "商品(1)",
               "quantity": 1
             }
           ],
           "warehouse": 6,
           "store": 7
         }
      ],
      "store": {
        "id": 7,
        "name": "本店"
      }
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

### 受注伝票の検索


複数の識別子(ids, codes)をもとに在庫の一覧取得を行います。


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/sales_orders/search`


Request Body


| パラメーター | 型 | 説明 |
| --- | --- | --- |
| ids | array of numbers | ID - 最大100件まで指定可能 ※ |
| codes | array of strings | 受注コード - 最大100件まで指定可能 ※ |




※ `ids`, `codes`いずれかの指定が必須となります。


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": "7621",
      "code": "test-20180101-4",
      "document_date": "2018-02-02",
      "posting_date": "2018-02-02",
      "status": "WaitingForAllocation",
      "delivery_status": "WaitingForShipment",
      "incoming_payment_status": "NotPaid",
      "authorization_status": "Authorized",
      "buyer_name1": "山田 太郎",
      "buyer_country": "JP",
      "recipient_name1": "山田 華子",
      "recipient_country": "JP",
      "recipient_post_code": "1700005",
      "recipient_prefecture": "東京都",
      "recipient_address1": "豊島区",
      "recipient_address2": "南大塚3-36-7",
      "recipient_address3": "南大塚T&Tビル 5F",
      "subtotal": 1000,
      "use_point": 0,
      "discount": 0,
      "delivery_fee": 0,
      "sundry_fee": 0,
      "tax_processing_method": "LineByLine",
      "tax_rounding_method": "RoundOff",
      "document_tax_rate": 8,
      "tax_total": 0,
      "payment_method": "credit_card_payment",
      "delivery_method": "yamato",
      "delivery_package_quantity": 1,
      "delivery_temperature_control": "Normal",
      "scheduled_shipping_date": "2018-02-02",
      "is_isolated_area": 0,
      "gift": 0,
      "waiting_for_confirmation": 1,
      "shipping_confirmed": 0,
      "is_multiple_deliveries": 0,
      "total_quantity": 1,
      "purchasing_times": 1,
      "tags": [
        "新規",
        "定期"
      ],
      "ordered_at": "2018-02-02 17:49:45",
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46",
      "lines":[
        {
          "id": 8837,
          "status": "WaitingForAllocation",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "quantity": 1
        }
      ],
      "outbound_deliveries":[
         {
           "id": 1090,
           "code": "2300000010909",
           "document_date": "2018-02-02 00:00:00",
           "posting_date": "2018-02-02 00:00:00",
           "document_status": "WaitingForAllocation",
           "delivery_status": "WaitingForShipment",
           "shipper_name_1": "ロジレス ストア",
           "shipper_country": "JP",
           "shipper_post_code": "1700005",
           "shipper_prefecture": "東京都",
           "shipper_address_1": "豊島区",
           "shipper_address_2": "南大塚3-36-7",
           "shipper_address_3": "南大塚T&Tビル 5F",
           "shipper_phone": "09058949377",
           "recipient_name_1": "山田 華子",
           "recipient_country": "JP",
           "recipient_post_code": "1700005",
           "recipient_prefecture": "東京都",
           "recipient_address_1": "豊島区",
           "recipient_address_2": "南大塚3-36-7",
           "cod_total": 0,
           "delivery_method": "yamato",
           "delivery_package_quantity": "1",
           "delivery_temperature_control": "Normal",
           "delivery_tracking_numbers":[],
           "gift": false,
           "total_quantity": 1,
           "total_weight": 0,
           "total_size_coefficient": 0,
           "ordered_at": "2018-02-02 12:22:08",
           "created_at": "2018-02-02 12:22:09",
           "updated_at": "2018-02-02 12:22:09",
           "lines":[
             {
               "id": 8837,
               "status": "WaitingForAllocation",
               "article_code": "article-1",
               "article_name": "商品(1)",
               "quantity": 1
             }
           ],
           "warehouse": 6,
           "store": 7
         }
      ],
      "store": {
        "id": 7,
        "name": "本店"
      }
    }
  ]
}

```

### 受注伝票を登録


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/sales_orders/new`



```
{
  "sales_order": {
    "code":"test-20180101-1",
    "buyer_name1":"山田 太郎",
    "recipient_name1":"山田 華子",
    "recipient_post_code":"170-0005",
    "recipient_prefecture":"東京都",
    "recipient_address1":"豊島区",
    "recipient_address2":"南大塚3-36-7",
    "recipient_address3":"南大塚T&Tビル 5F",
    "payment_method":"credit_card_payment",
    "delivery_method":"yamato",
    "ordered_at":"2018-01-01 23:59:59",
    "purchasing_times": 2,
    "tags": [
      "新規",
      "定期"
    ],
    "lines": [
      {
          "article_code":"article-1",
          "article_name":"商品(1)",
        "price":1000,
        "quantity":1
      }
    ],
    "store": 51
  }
}

```

#### レスポンス


`HTTP/1.1 201 Created`



```
{
  "id": "7621",
  "code": "test-20180101-4",
  "document_date": "2018-02-02",
  "posting_date": "2018-02-02",
  "document_status": "WaitingForAllocation",
  "allocation_status": "WaitingForAllocation",
  "delivery_status": "WaitingForShipment",
  "incoming_payment_status": "NotPaid",
  "authorization_status": "Authorized",
  "buyer_name1": "山田 太郎",
  "buyer_country": "JP",
  "buyer_prefecture": "東京都",
  "recipient_name1": "山田 華子",
  "recipient_country": "JP",
  "recipient_post_code": "1700005",
  "recipient_prefecture": "東京都",
  "recipient_address1": "豊島区",
  "recipient_address2": "南大塚3-36-7",
  "recipient_address3": "南大塚T&Tビル 5F",
  "subtotal": 1000,
  "use_point": 0,
  "use_coupon": 0,
  "discount": 0,
  "delivery_fee": 0,
  "sundry_fee": 0,
  "tax_processing_method": "LineByLine",
  "tax_rounding_method": "RoundOff",
  "document_tax_rate": 8,
  "tax_total": 0,
  "total": 1000,
  "payment_method": "credit_card_payment",
  "delivery_method": "yamato",
  "delivery_package_quantity": 1,
  "delivery_temperature_control": "Normal",
  "is_isolated_area": 0,
  "gift": 0,
  "waiting_for_confirmation": 1,
  "shipping_confirmed": 0,
  "is_multiple_deliveries": 0,
  "total_quantity": 1,
  "purchasing_times": 2,
  "ordered_at": "2018-02-02 17:49:45",
  "created_at": "2018-02-02 17:49:46",
  "updated_at": "2018-02-02 17:49:46",
  "lines":[
    {
      "id": 8837,
      "status": "WaitingForAllocation",
      "article_code": "article-1",
      "article_name": "商品(1)",
      "price": "1000",
      "quantity": "1",
      "is_parent": 0,
      "is_child": 0,
      "cached_allocated_quantity": 0,
      "is_partial_cancel": 0,
      "tax_indicator": "TaxIncluded",
      "tax_rate": 10,
      "tax_total": 91,
      "subtotal": 1000,
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46"
    }
  ],
  "outbound_deliveries": [
    {
      "id": "2",
      "code": "2300000000023",
      "document_date": "2018-02-02",
      "posting_date": "2018-02-02",
      "document_status": "WaitingForAllocation",
      "allocation_status": "WaitingForAllocation",
      "delivery_status": "WaitingForShipment",
      "shipper_name1": "店舗-01",
      "shipper_country": "JP",
      "shipper_post_code": "1420062",
      "shipper_prefecture": "東京都",
      "shipper_address1": "品川区",
      "shipper_address2": "小山1-5-7",
      "shipper_phone": "0364261416",
      "recipient_name1": "山田 華子",
      "recipient_country": "JP",
      "recipient_post_code": "1700005",
      "recipient_prefecture": "東京都",
      "recipient_address1": "豊島区",
      "recipient_address2": "南大塚3-36-7",
      "recipient_address3": "南大塚T&Tビル 5F",
      "cod_total": 0,
      "delivery_method": "yamato",
      "delivery_package_quantity": 1,
      "delivery_temperature_control": "Normal",
      "delivery_tracking_numbers": [],
      "gift": false,
      "total_quantity": 1,
      "total_weight": 0,
      "total_size_coefficient": 0,
      "waiting_for_confirmation": true,
      "ordered_at": "2018-01-01 23:59:59",
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46",
      "lines": [
        {
          "id": 2,
          "status": "WaitingForAllocation",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "price": "1000",
          "quantity": "1",
          "is_parent": 0,
          "is_child": 0,
          "cached_allocated_quantity": 0,
          "is_partial_cancel": 0,
          "tax_indicator": "TaxIncluded",
          "tax_rate": 10,
          "tax_total": 91,
          "subtotal": 1000,
          "origin": {
            "id": "2",
            "code": "test-20180101-1"
          },
          "created_at": "2018-02-02 17:49:46",
          "updated_at": "2018-02-02 17:49:46"
        }
      ],
      "shipped_actual_stocks": [],
      "warehouse": 6,
      "store": 51,
      "sales_order": {
        "id": "2",
        "code": "test-20180101-1"
      }
    }
  ],
  "store": {
    "id": 51,
    "name": "店舗-01"
  },
  "tags": [
    "新規",
    "定期"
  ]
}

```

### 受注伝票を編集


#### リクエスト


`PUT /api/v1/merchant/#{merchant_id}/sales_orders/#{id}`




| パラメーター | 説明 |
| --- | --- |
| incoming\_payment\_status | [入金ステータス](type/.mdincoming_payment_status) |
| authorization\_status | [承認ステータス](type/.mdauthorization_status) |
| buyer\_name1 | 購入者名(1) |
| buyer\_name2 | 購入者名(2) |
| buyer\_name\_kana1 | 購入者名かな(1) |
| buyer\_name\_kana2 | 購入者名かな(2) |
| buyer\_country | 購入者 国 - デフォルトは `JP` |
| buyer\_post\_code | 購入者 郵便番号 |
| buyer\_prefecture | 購入者 都道府県 |
| buyer\_address1 | 購入者 住所1 |
| buyer\_address2 | 購入者 住所2 |
| buyer\_address3 | 購入者 住所3 |
| buyer\_phone | 購入者 電話番号 |
| buyer\_fax | 購入者 FAX番号 |
| buyer\_email | 購入者メールアドレス |
| recipient\_name1 | お届け先名(1) |
| recipient\_name2 | お届け先名(2) |
| recipient\_name\_kana1 | お届け先名かな(1) |
| recipient\_name\_kana2 | お届け先名かな(2) |
| recipient\_country | お届け先 国 - デフォルトは `JP` |
| recipient\_post\_code | お届け先 郵便番号 |
| recipient\_prefecture | お届け先 都道府県 |
| recipient\_address1 | [必須] お届け先 住所1 |
| recipient\_address2 | お届け先 住所2 |
| recipient\_address3 | お届け先 住所3 |
| recipient\_phone | お届け先 電話番号 |
| recipient\_fax | お届け先 FAX番号 |
| recipient\_email | お届け先 メールアドレス |
| delivery\_preferred\_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_time\_zone | お届け希望時間帯 |
| use\_point | ポイント利用 |
| use\_coupon | クーポン利用 |
| delivery\_fee | 送料 |
| sundry\_fee | その他手数料 |
| discount | 値引き |
| payment\_method | [支払方法](type/.mdpayment_method) |
| purchasing\_times | 購入回数 |
| merchant\_comment | マーチャント備考欄 |
| attr1 | フリー項目1 |
| attr2 | フリー項目2 |
| attr3 | フリー項目3 |
| attr4 | フリー項目4 |
| attr5 | フリー項目5 |
| attr6 | フリー項目6 |
| attr7 | フリー項目7 |
| attr8 | フリー項目8 |
| attr9 | フリー項目9 |
| attr10 | フリー項目10 |
| tags | 受注伝票のタグ（配列） |



```
{
  "sales_order": {
    "authorization_status":"AuthorizationFailure",
    "tags": [
      "新規2",
      "定期2"
    ]
  }
}

```

#### レスポンス


`HTTP/1.1 200`



```
{
  "id": "7621",
  "code": "test-20180101-4",
  "document_date": "2018-02-02",
  "posting_date": "2018-02-02",
  "document_status": "WaitingForAllocation",
  "allocation_status": "WaitingForAllocation",
  "delivery_status": "WaitingForShipment",
  "incoming_payment_status": "NotPaid",
  "authorization_status": "AuthorizationFailure",
  "buyer_name1": "山田 太郎",
  "buyer_country": "JP",
  "buyer_prefecture": "東京都",
  "recipient_name1": "山田 華子",
  "recipient_country": "JP",
  "recipient_post_code": "1700005",
  "recipient_prefecture": "東京都",
  "recipient_address1": "豊島区",
  "recipient_address2": "南大塚3-36-7",
  "recipient_address3": "南大塚T&Tビル 5F",
  "subtotal": 1000,
  "use_point": 0,
  "use_coupon": 0,
  "discount": 0,
  "delivery_fee": 0,
  "sundry_fee": 0,
  "tax_processing_method": "LineByLine",
  "tax_rounding_method": "RoundOff",
  "document_tax_rate": 8,
  "tax_total": 0,
  "total": 1000,
  "payment_method": "credit_card_payment",
  "delivery_method": "yamato",
  "delivery_package_quantity": 1,
  "delivery_temperature_control": "Normal",
  "delivery_preferred_date": "2018-02-04",
  "delivery_preferred_time_zone": "午前中",
  "is_isolated_area": 0,
  "gift": 0,
  "waiting_for_confirmation": 1,
  "shipping_confirmed": 0,
  "is_multiple_deliveries": 0,
  "total_quantity": 1,
  "purchasing_times": 2,
  "ordered_at": "2018-02-02 17:49:45",
  "created_at": "2018-02-02 17:49:46",
  "updated_at": "2018-02-02 17:49:46",
  "lines":[
    {
      "id": 8837,
      "status": "WaitingForAllocation",
      "article_code": "article-1",
      "article_name": "商品(1)",
      "price": 1000,
      "quantity": 1,
      "is_parent": 0,
      "is_child": 0,
      "cached_allocated_quantity": 0,
      "is_partial_cancel": 0,
      "tax_indicator": "TaxIncluded",
      "tax_rate": 10,
      "tax_total": 91,
      "subtotal": 1000,
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46"
    }
  ],
  "outbound_deliveries": [
    {
      "id": "2",
      "code": "2300000000023",
      "document_date": "2018-02-02",
      "posting_date": "2018-02-02",
      "document_status": "WaitingForAllocation",
      "allocation_status": "WaitingForAllocation",
      "delivery_status": "WaitingForShipment",
      "shipper_name1": "店舗-01",
      "shipper_country": "JP",
      "shipper_post_code": "1420062",
      "shipper_prefecture": "東京都",
      "shipper_address1": "品川区",
      "shipper_address2": "小山1-5-7",
      "shipper_phone": "0364261416",
      "recipient_name1": "山田 華子",
      "recipient_country": "JP",
      "recipient_post_code": "1700005",
      "recipient_prefecture": "東京都",
      "recipient_address1": "豊島区",
      "recipient_address2": "南大塚3-36-7",
      "recipient_address3": "南大塚T&Tビル 5F",
      "cod_total": 0,
      "delivery_method": "yamato",
      "delivery_package_quantity": 1,
      "delivery_temperature_control": "Normal",
      "delivery_tracking_numbers": [],
      "gift": false,
      "total_quantity": 1,
      "total_weight": 0,
      "total_size_coefficient": 0,
      "waiting_for_confirmation": true,
      "ordered_at": "2018-01-01 23:59:59",
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46",
      "lines": [
        {
          "id": 2,
          "status": "WaitingForAllocation",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "price": 1000,
          "quantity": 1,
          "is_parent": 0,
          "is_child": 0,
          "cached_allocated_quantity": 0,
          "is_partial_cancel": 0,
          "tax_indicator": "TaxIncluded",
          "tax_rate": 10,
          "tax_total": 91,
          "subtotal": 1000,
          "origin": {
            "id": "2",
            "code": "test-20180101-1"
          },
          "created_at": "2018-02-02 17:49:46",
          "updated_at": "2018-02-02 17:49:46"
        }
      ],
      "shipped_actual_stocks": [],
      "warehouse": 6,
      "store": 51,
      "sales_order": {
        "id": "2",
        "code": "test-20180101-1"
      }
    }
  ],
  "store": {
    "id": 51,
    "name": "店舗-01"
  },
  "tags": [
    "新規2",
    "定期2"
  ]
}

```

### 受注伝票をキャンセル


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/sales_orders/#{id}/reversal`




| パラメーター | 説明 |
| --- | --- |
| clears\_code | 同じ受注コードで新規受注の作成を許可 - デフォルトは `false` |



```
{
  "clears_code": false
}

```

#### レスポンス


`HTTP/1.1 200`



```
{
  "id": "7621",
  "code": "test-20180101-4",
  "document_date": "2018-02-02",
  "posting_date": "2018-02-02",
  "document_status": "Cancel",
  "allocation_status": "WaitingForAllocation",
  "delivery_status": "Cancel",
  "incoming_payment_status": "NotPaid",
  "authorization_status": "Authorized",
  "buyer_name1": "山田 太郎",
  "buyer_country": "JP",
  "buyer_prefecture": "東京都",
  "recipient_name1": "山田 華子",
  "recipient_country": "JP",
  "recipient_post_code": "1700005",
  "recipient_prefecture": "東京都",
  "recipient_address1": "豊島区",
  "recipient_address2": "南大塚3-36-7",
  "recipient_address3": "南大塚T&Tビル 5F",
  "subtotal": 0,
  "use_point": 0,
  "use_coupon": 0,
  "discount": 0,
  "delivery_fee": 0,
  "sundry_fee": 0,
  "tax_processing_method": "LineByLine",
  "tax_rounding_method": "RoundOff",
  "document_tax_rate": 8,
  "tax_total": 0,
  "total": 0,
  "payment_method": "credit_card_payment",
  "delivery_method": "yamato",
  "delivery_package_quantity": 1,
  "delivery_temperature_control": "Normal",
  "is_isolated_area": 0,
  "gift": 0,
  "waiting_for_confirmation": 0,
  "shipping_confirmed": 0,
  "is_multiple_deliveries": 0,
  "total_quantity": 0,
  "purchasing_times": 2,
  "ordered_at": "2018-02-02 17:49:45",
  "finished_at": "2018-02-02 17:49:46",
  "created_at": "2018-02-02 17:49:46",
  "updated_at": "2018-02-02 17:49:46",
  "lines":[
    {
      "id": 8837,
      "status": "Cancel",
      "article_code": "article-1",
      "article_name": "商品(1)",
      "price": 1000,
      "quantity": 1,
      "is_parent": 0,
      "is_child": 0,
      "cached_allocated_quantity": 0,
      "is_partial_cancel": 0,
      "tax_indicator": "TaxIncluded",
      "tax_rate": 10,
      "tax_total": 91,
      "subtotal": 1000,
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46"
    }
  ],
  "outbound_deliveries": [
    {
      "id": "2",
      "code": "2300000000023",
      "document_date": "2018-02-02",
      "posting_date": "2018-02-02",
      "document_status": "Cancel",
      "allocation_status": "Cancel",
      "delivery_status": "Cancel",
      "shipper_name1": "店舗-01",
      "shipper_country": "JP",
      "shipper_post_code": "1420062",
      "shipper_prefecture": "東京都",
      "shipper_address1": "品川区",
      "shipper_address2": "小山1-5-7",
      "shipper_phone": "0364261416",
      "recipient_name1": "山田 華子",
      "recipient_country": "JP",
      "recipient_post_code": "1700005",
      "recipient_prefecture": "東京都",
      "recipient_address1": "豊島区",
      "recipient_address2": "南大塚3-36-7",
      "recipient_address3": "南大塚T&Tビル 5F",
      "cod_total": 0,
      "delivery_method": "yamato",
      "delivery_package_quantity": 1,
      "delivery_temperature_control": "Normal",
      "delivery_tracking_numbers": [],
      "gift": false,
      "total_quantity": 0,
      "total_weight": 0,
      "total_size_coefficient": 0,
      "waiting_for_confirmation": false,
      "ordered_at": "2018-01-01 23:59:59",
      "finished_at": "2018-02-02 17:49:46",
      "created_at": "2018-02-02 17:49:46",
      "updated_at": "2018-02-02 17:49:46",
      "lines": [
        {
          "id": 2,
          "status": "Cancel",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "price": 1000,
          "quantity": 1,
          "is_parent": 0,
          "is_child": 0,
          "cached_allocated_quantity": 0,
          "is_partial_cancel": 0,
          "tax_indicator": "TaxIncluded",
          "tax_rate": 10,
          "tax_total": 91,
          "subtotal": 1000,
          "origin": {
            "id": "2",
            "code": "test-20180101-1"
          },
          "created_at": "2018-02-02 17:49:46",
          "updated_at": "2018-02-02 17:49:46"
        }
      ],
      "shipped_actual_stocks": [],
      "warehouse": 6,
      "store": 51,
      "sales_order": {
        "id": "2",
        "code": "test-20180101-1"
      }
    }
  ],
  "store": {
    "id": 51,
    "name": "店舗-01"
  },
  "tags": [
    "新規2",
    "定期2"
  ]
}


```

### 明細行をキャンセル


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/sales_orders/#{id}/sales_order_lines/{id}/reversal`


#### レスポンス


`HTTP/1.1 200`



```
{
  "id": 2,
  "status": "Cancel",
  "article_code": "article-1",
  "article_name": "商品(1)",
  "price": 1000,
  "quantity": 1,
  "is_parent": 0,
  "is_child": 0,
  "cached_allocated_quantity": 0,
  "is_partial_cancel": 0,
  "tax_indicator": "TaxIncluded",
  "tax_rate": 10,
  "tax_total": 91,
  "subtotal": 1000,
  "article":{
    "id": 1,
    "code": "test-20180101-1",
    "object_code": "2000000000015",
    "name": "商品(1)"
  },
  "created_at": "2018-02-02 17:49:46",
  "updated_at": "2018-02-02 17:49:46"
}

```


