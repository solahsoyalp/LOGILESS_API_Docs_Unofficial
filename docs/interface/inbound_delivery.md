

入荷予定伝票
======


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID入荷予定伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。入荷予定コードとは異なります。 |
| code | 入荷予定コード |
| object\_code | [読取専用] 入荷予定管理番号 |
| document\_date | 伝票日付 - `Y-m-d`形式 (例 : `2018-01-01`) |
| posting\_date | 転記日付 - `Y-m-d`形式 (例 : `2018-01-01`) |
| inbound\_delivery\_category | [入荷予定カテゴリ](type/.mdinbound_delivery_category) |
| status | [入荷予定ステータス](type/.mdinbound_delivery_status) |
| supplier\_code | [登録時のみ] 仕入先コード |
| supplier\_name | 仕入先名 |
| supplier\_name\_kana | 仕入先名かな |
| supplier\_country | 仕入先 国 - デフォルトは `JP` |
| supplier\_post\_code | 仕入先 郵便番号 |
| supplier\_prefecture | 仕入先 都道府県 |
| supplier\_address1 | 仕入先 住所1 |
| supplier\_address2 | 仕入先 住所2 |
| supplier\_address3 | 仕入先 住所3 |
| supplier\_phone | 仕入先 電話番号 |
| supplier\_fax | 仕入先 FAX番号 |
| supplier\_email | 仕入先 メールアドレス |
| recipient\_name | お届け先名 |
| recipient\_name\_kana | お届け先名かな |
| recipient\_country | お届け先 国 - デフォルトは `JP` |
| recipient\_post\_code | お届け先 郵便番号 |
| recipient\_prefecture | お届け先 都道府県 |
| recipient\_address1 | お届け先 住所1 |
| recipient\_address2 | お届け先 住所2 |
| recipient\_address3 | お届け先 住所3 |
| recipient\_phone | お届け先 電話番号 |
| recipient\_fax | お届け先 FAX番号 |
| subtotal | [読取専用] 商品合計金額（小計） |
| tax\_processing\_method | [税の計算順序](type/.mdtax_processing_method) - デフォルトは マーチャントの設定 |
| tax\_rounding\_method | [税の丸め](type/.mdtax_rounding_method) - デフォルトは マーチャントの設定 |
| document\_tax\_rate | 伝票の税率 - デフォルトは `10` |
| tax\_total | [読取専用] 税の合計 |
| total | [読取専用] 合計金額 |
| delivery\_preferred\_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery\_preferred\_time\_zone | お届け希望時間帯 |
| purchase\_order\_notes | 発注書 特記事項 |
| scheduled\_delivery\_date | 納入予定日 |
| delivery\_career\_name | 納入配送会社 |
| delivery\_tracking\_numbers | [配列] 送り状番号の一覧 |
| is\_printed | 印刷済みかどうか (0:印刷済みでない, 1: 印刷済み) |
| receiving\_notes | 入荷予定表 特記事項 |
| remarks\_on\_received | 入荷時の備考 |
| attr1 | フリー項目1 |
| attr2 | フリー項目2 |
| attr3 | フリー項目3 |
| ordered\_at | 注文日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) - デフォルトは現在時刻 |
| finished\_at | [読取専用] 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| lines | 明細行 - [lines](#property_lines)のプロパティを参照 |
| supplier | 仕入先 - [supplier](#property_supplier)のプロパティを参照 |
| warehouse | 倉庫 - [warehouse](interface/.mdwarehouse)のプロパティを参照 |


### lines




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID入荷予定伝票明細行をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| code | 明細行コード |
| article\_code | [必須] 商品コード |
| supplier\_article\_code | メーカー品番 |
| article\_name | [必須] 商品名 |
| article\_option | 明細行備考欄 |
| deadline | 出荷期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| lot\_number | ロット番号 |
| price | 価格 - デフォルトは `0` |
| quantity | 数量 |
| received\_quantity | 検品済み数量 |
| tax\_indicator | [税区分](type/.mdtax_indicator) - デフォルトは `Included` |
| tax\_rate | 税率 - デフォルトは `10` |
| subtotal | [読取専用] 小計 |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |
| is\_partial\_cancel | 一部キャンセルかどうか キャンセルの場合は`1`そうでない場合は`0` |
| status | [明細ステータス](type/.mdinbound_delivery_status) |
| created\_at | 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


### supplier




| プロパティ | 説明 |
| --- | --- |
| id | ID仕入先をユニークに識別するための数値です。主に、APIでのアクセスに使用します。仕入先コードとは異なります。 |
| code | 仕入先コード |
| name | 仕入先名 |
| created\_at | 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


### article




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID商品マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| code | 商品コード |
| identification\_code | 識別コード |
| object\_code | ロジレスコード |
| model\_number | 型番 |
| name | [必須] 商品名 |
| name\_kana | 商品名かな |


### プロパティの各項目について


レスポンスデータには "値が設定されている項目" についてのみ返却します


エンドポイント
-------


* [入荷予定伝票の一覧を取得](#get_list)
* [入荷予定伝票を登録](#post)
* [入荷予定伝票をキャンセル](#reversal)


### 入荷予定伝票の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/inbound_deliveries`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| id | ID |
| code | 入荷予定コード |
| status | [入荷予定ステータス](type/.mdinbound_delivery_status) - 複数指定する場合はカンマ区切り |
| ordered\_at\_from | 作成日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered\_at\_to | 作成日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_from | 完了日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished\_at\_to | 完了日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse | 倉庫 - 倉庫ID |



```
{
  "data": [
    {
      "id": "1234",
      "code": "test-20200901-1",
      "object_code": "2960001234560",
      "document_date": "2020-09-01",
      "posting_date": "2020-09-01",
      "status": "WaitingForReceipt",
      "supplier_name": "東西商事",
      "supplier_country": "JP",
      "recipient_name": "自社倉庫",
      "recipient_country": "JP",
      "subtotal": 1000,
      "tax_processing_method": "UnitByUnit",
      "tax_rounding_method": "RoundDown",
      "document_tax_rate": 10,
      "tax_total": 0,
      "total": 1000,
      "delivery_tracking_numbers": [],
      "is_printed": 0,
      "ordered_at": "2020-09-01 00:00:00",
      "created_at": "2020-09-01 00:00:00",
      "updated_at": "2020-09-01 00:00:00",
      "lines": [
        {
          "id": 8837,
          "status": "WaitingForReceipt",
          "article_code": "article-1",
          "article_name": "商品(1)",
          "price": 1000,
          "quantity": 1,
          "received_quantity": 0,
          "is_partial_cancel": 0,
          "tax_indicator": "TaxIncluded",
          "tax_rate": 10,
          "tax_total": 91,
          "subtotal": 1000,
          "article": {
            "id": 2,
            "code": "2000000000022",
            "object_code": "2000000000022",
            "name": "テスト商品(1)"
          },
          "created_at": "2020-09-01 00:00:00",
          "updated_at": "2020-09-01 00:00:00",
        }
      ],
      "supplier": {
        "id": 0,
        "code": "sup-01-01-01",
        "name": "仕入先01",
        "created_at": "2020-09-01 00:00:00",
        "updated_at": "2020-09-01 00:00:00"
      },
      "warehouse": {
        "id": 1,
        "name": "自社倉庫"
      }
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
} 

```

### 入荷予定伝票を登録


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/inbound_deliveries/new`



```
{
  "inbound_delivery": {
    "code":"test-20200901-1",
    "supplier_name":"東西商事",
    "lines": [
      {
          "article_code":"article-1",
          "article_name":"商品(1)",
        "price":1000,
        "quantity":1
      }
    ],
    "warehouse": 1
  }
}

```

#### レスポンス


`HTTP/1.1 201 Created`



```
{
  "id": "1234",
  "code": "test-20200901-1",
  "status": "WaitingForReceipt",
  "document_date": "2020-09-01",
  "posting_date": "2020-09-01",
  "supplier_name": "東西商事",
  "supplier_country": "JP",
  "recipient_name": "自社倉庫",
  "recipient_country": "JP",
  "subtotal": 1000,
  "tax_processing_method": "UnitByUnit",
  "tax_rounding_method": "RoundDown",
  "document_tax_rate": 10,
  "tax_total": 0,
  "total": 1000,
  "is_printed": 0,
  "ordered_at": "2020-09-01 00:00:00",
  "created_at": "2020-09-01 00:00:00",
  "updated_at": "2020-09-01 00:00:00",
  "lines":[
    {
      "id": 8837,
      "status": "WaitingForReceipt",
      "article_code": "article-1",
      "article_name": "商品(1)"
      "price": "1000",
      "quantity": "1",
      "received_quantity": 0,
      "is_partial_cancel": 0,
      "tax_indicator": "TaxIncluded",
      "tax_rate": 10,
      "tax_total": 91,
      "subtotal": 1000,
      "article": {
        "id": 2,
        "code": "article-1",
        "object_code": "article-1",
        "name": "商品(1)"
      },
       "created_at": "2020-09-01 00:00:00",
       "updated_at": "2020-09-01 00:00:00",
    }
  ],
  "warehouse":{
    "id": 1,
    "name": "自社倉庫"
  }
}

```

### 入荷予定情報をキャンセル


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/inbound_deliveries/#{id}/reversal`




| パラメーター | 説明 |
| --- | --- |
| clears\_code | 同じ入荷予定コードで新規入荷予定の作成を許可 - デフォルトは `false` |



```
{
  "clears_code": false
}

```

#### レスポンス


`HTTP/1.1 200`



```
{
  "id": "1234",
  "code": "test-20200901-1",
  "document_date": "2020-09-01",
  "posting_date": "2020-09-01",
  "status": "Cancel",
  "supplier_name": "東西商事",
  "supplier_country": "JP",
  "recipient_name": "自社倉庫",
  "recipient_country": "JP",
  "subtotal": 0,
  "tax_processing_method": "UnitByUnit",
  "tax_rounding_method": "RoundDown",
  "document_tax_rate": 10,
  "tax_total": 0,
  "total": 0,
  "is_printed": 0,
  "ordered_at": "2020-09-01 00:00:00",
  "finished_at": "2020-09-01 00:00:00",
  "created_at": "2020-09-01 00:00:00",
  "updated_at": "2020-09-01 00:00:00",
  "lines":[
    {
      "id": 8837,
      "status": "Cancel",
      "article_code": "article-1",
      "article_name": "商品(1)"
      "price": 1000,
      "quantity": 1,
      "received_quantity": 0,
      "is_partial_cancel": 0,
      "tax_indicator": "TaxIncluded",
      "tax_rate": 10,
      "tax_total": 91,
      "subtotal": 1000,
      "article": {
        "id": 2,
        "code": "article-1",
        "object_code": "article-1",
        "name": "商品(1)"
      },
      "created_at": "2020-09-01 00:00:00",
      "updated_at": "2020-09-01 00:00:00"
    }
  ],
  "warehouse":{
    "id": 1,
    "name": "自社倉庫"
  }
}

```


