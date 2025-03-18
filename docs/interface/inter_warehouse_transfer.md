# 倉庫間移動伝票

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID入荷予定伝票をユニークに識別するための数値です。主に、APIでのアクセスに使用します。入荷予定コードとは異なります。 |
| code | 指示コード |
| status | [伝票ステータス](errors.md#伝票ステータス) |
| delivery_status | [配送ステータス](type/delivery_status.md) |
| delivery_method | [配送方法](type/delivery_method.md) |
| delivery_preferred_date | お届け希望日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| delivery_preferred_time_zone | お届け希望時間帯 |
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
| ordered_at | 依頼日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) - デフォルトは現在時刻 |
| finished_at | [読取専用] 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| lines | 明細行 - [lines](#property_lines)のプロパティを参照 |
| warehouse | 出荷元倉庫 - [warehouse](interface/warehouse.md)のプロパティを参照 |
| destination | 納品先倉庫 - [warehouse](interface/warehouse.md)のプロパティを参照 |

### lines

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID倉庫間移動伝票明細行をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| code | 明細行コード |
| status | [読取専用] [明細ステータス](type/document_line_status.md) |
| article_code | [必須] 商品コード |
| article_name | [必須] 商品名 |
| article_option | 明細行備考欄 |
| quantity | 数量 |
| uses_blocked_stock | 保留在庫を引き当てるかどうか |
| cached_allocated_quantity | 引当済み数量 |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |

## エンドポイント

* [倉庫間移動伝票の一覧を取得](#get_list)
* [倉庫間移動伝票を登録](#post)

### 倉庫間移動伝票の一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/inter_warehouse_transfers`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| document_status | [伝票ステータス](errors.md#伝票ステータス) - 複数指定する場合はカンマ区切り |
| delivery_status | [配送ステータス](type/delivery_status.md) - 複数指定する場合はカンマ区切り |
| ordered_at_from | 作成日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| ordered_at_to | 作成日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished_at_from | 完了日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| finished_at_to | 完了日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse | 出荷元倉庫 - 倉庫ID |
| destination | 納品先倉庫 - 倉庫ID |

### 倉庫間移動伝票を登録

#### リクエスト

`POST /api/v1/merchant/#{merchant_id}/inter_warehouse_transfers/new`

```
{
  "inter_warehouse_transfer": {
    "code":"test-20200901-1",
    "lines": [
      {
          "article_code":"article-1",
          "article_name":"商品(1)",
        "quantity":1
      }
    ],
    "delivery_method": "sagawa",
    "warehouse": 1,
    "destination": 2
  }
}

```

#### レスポンス

`HTTP/1.1 201 Created`

```
{
  "id": "1234",
  "code": "test-20200901-1",
  "status": "WaitingForAllocation",
  "delivery_status": "WaitingForShipment",
  "delivery_method": "sagawa",
  "ordered_at": "2020-09-01 00:00:00",
  "created_at": "2020-09-01 00:00:00",
  "updated_at": "2020-09-01 00:00:00",
  "lines":[
    {
      "id": 8837,
      "status": "WaitingForAllocation",
      "article_code": "article-1",
      "article_name": "商品(1)"
      "quantity": "1",
      "uses_blocked_stock": 0,
      "cached_allocated_quantity": 0,
      "created_at": "2020-09-01 00:00:00",
      "updated_at": "2020-09-01 00:00:00"
    }
  ],
  "warehouse":{
    "id": 1,
    "name": "自社倉庫"
  },
  "destination":{
    "id": 2,
    "name": "外部倉庫"
  }
}

```


