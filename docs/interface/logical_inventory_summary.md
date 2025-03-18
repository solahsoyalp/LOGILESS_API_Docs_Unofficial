# 在庫

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | ID在庫情報をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| layer | [在庫レイヤー](type/inventory_summary_layer.md) |
| ordered | 受注済み |
| in\_transit | 入荷待ち |
| received | 入庫待ち |
| available | 保管中 |
| blocked | 保留 |
| allocated | 引当済み |
| stock\_out | 引当待ち |
| free | フリー在庫 |
| shipped | 出荷済み |
| issued | 出庫済み |
| is\_reorder\_level | 発注点割れ |
| reached\_reorder\_level\_at | 発注点を割った日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | 商品マスタ - [article](interface/article.md)のプロパティを参照 |
| warehouse | 倉庫 - [warehouse](interface/warehouse.md)のプロパティを参照 |
| article\_id | （非推奨）商品マスタID |
| warehouse\_id | （非推奨）倉庫ID |

## エンドポイント

* [在庫の一覧を取得](#get_list)
* [在庫の検索](#search)

### 在庫の一覧を取得

article\_code, identification\_codeは単一指定のみリクエストが可能です。

複数指定されたい場合やmodel\_numbers(型番)を指定されたい場合は[在庫の検索](#search) をご利用ください。

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/logical_inventory_summaries`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| article\_code | 商品コード |
| identification\_code | 識別コード |
| layer | [在庫レイヤー](type/inventory_summary_layer.md) - デフォルトは `Article` |
| article\_type | [商品区分](type/article_type.md) - デフォルトは `Single` |
| min\_in\_transit | 入荷待ち（最小） |
| max\_in\_transit | 入荷待ち（最大） |
| min\_received | 入庫待ち（最小） |
| max\_received | 入庫待ち（最大） |
| min\_blocked | 保留（最小） |
| max\_blocked | 保留（最大） |
| min\_free | フリー在庫（最小） |
| max\_free | フリー在庫（最大） |
| min\_allocated | 引当済み（最小） |
| max\_allocated | 引当済み（最大） |
| min\_stock\_out | 引当待ち（最小） |
| max\_stock\_out | 引当待ち（最大） |
| min\_shipped | 出荷済み（最小） |
| max\_shipped | 出荷済み（最大） |
| is\_reorder\_level | 発注点割れかどうか |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse | 倉庫ID |
| ~~ean\_code~~ | ~~識別コード~~ （廃止予定 : identification\_codeを使用してください） |

#### レスポンス

`HTTP/1.1 200`

```
{
  "data":[
    {
      "id": 32509,
      "layer": "Article",
      "ordered": 0,
      "in_transit": 0,
      "received": 1,
      "available": 13,
      "blocked": 0,
      "allocated": 0,
      "stock_out": 0,
      "free": 13,
      "shipped": 9,
      "issued": 0,
      "is_reorder_level": 0,
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article_id": 113,
      "article": {
        "id": 113,
        "code": "2000000000022",
        "object_code": "2000000000022",
        "name": "商品",
        "article_type": "Single",
        "tax_indicator": "TaxIncluded",
        "temperature_control": "Normal",
        "unit": "個",
        "limiting_sales": 0,
        "created_at": "2017-01-06 15:50:37",
        "updated_at": "2018-01-26 15:20:37"
      },
      "warehouse": {
        "id": 12,
        "name": "外部倉庫"
      }
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

### 在庫の検索

複数の識別子(article\_codes, identification\_codes, model\_numbers)をもとに在庫の一覧取得を行います。

#### リクエスト

`POST /api/v1/merchant/#{merchant_id}/logical_inventory_summaries/search`

Request Body

| パラメーター | 型 | 説明 |
| --- | --- | --- |
| article\_codes | array of strings | 商品コード - 最大100件まで指定可能 ※ |
| identification\_codes | array of strings | 識別コード - 最大100件まで指定可能 ※ |
| model\_numbers | array of strings | 型番 - 最大100件まで指定可能 ※ |
| warehouse\_id | number | 倉庫ID |




※ `article_codes`, `identification_codes`, `model_numbers` いずれかの指定が必須となります。


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": 32509,
      "layer": "Article",
      "ordered": 0,
      "in_transit": 0,
      "received": 1,
      "available": 13,
      "blocked": 0,
      "allocated": 0,
      "stock_out": 0,
      "free": 13,
      "shipped": 9,
      "issued": 0,
      "is_reorder_level": 0,
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article_id": 113,
      "article": {
        "id": 113,
        "code": "2000000000022",
        "object_code": "2000000000022",
        "name": "商品",
        "article_type": "Single",
        "tax_indicator": "TaxIncluded",
        "temperature_control": "Normal",
        "unit": "個",
        "limiting_sales": 0,
        "created_at": "2017-01-06 15:50:37",
        "updated_at": "2018-01-26 15:20:37"
      },
      "warehouse": {
        "id": 12,
        "name": "外部倉庫"
      }
    }
  ]
}

```


