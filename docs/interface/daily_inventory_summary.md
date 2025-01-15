

日次在庫
====


※この機能を使用するには事前に利用申込が必要です。


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | ID在庫情報をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| date | 日付 - `Y-m-d`形式 (例 : `2018-01-01`) |
| layer | [在庫レイヤー](type/.mdinventory_summary_layer) |
| received | 入庫待ち |
| available | 保管中 |
| blocked | 保留 |
| allocated | ピッキング中 |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | 商品マスタ - [article](interface/.mdarticle)のプロパティを参照 |
| warehouse | 倉庫 - [warehouse](interface/.mdwarehouse)のプロパティを参照 |


エンドポイント
-------


* [在庫の一覧を取得](#get_list)


### 在庫の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/daily_inventory_summaries`




| パラメーター | 説明 |
| --- | --- |
| date | [必須] 日付 - `Y-m-d`形式 (例 : `2018-01-01`) |
| article\_code | 商品コード |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| warehouse | 倉庫ID |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": 32509,
      "date": "2019-01-26",
      "layer": "Article",
      "received": 1,
      "available": 13,
      "blocked": 0,
      "allocated": 9,
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article": {
        "id": 113,
        "code": "2000000000091",
        "object_code": "2000000000091",
        "name": "商品(1)",
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


