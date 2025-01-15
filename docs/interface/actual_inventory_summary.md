

保管状況
====


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | ID在庫情報をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| layer | [在庫レイヤー](type/.mdinventory_summary_layer) |
| deadline | 出荷期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| lot\_number | ロット番号 |
| received | 入庫待ち |
| available | 保管中 |
| blocked | 保留 |
| allocated | ピッキング中 |
| shipped | 出荷済み |
| issued | 出庫済み |
| actual\_unit | 数量単位 |
| logical\_unit | 数量単位（構成商品） - 集合包装の場合のみセットされます。 |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| logical\_article\_id | 商品マスタID（構成商品） - 集合包装の場合のみセットされます。 |
| article | 商品マスタ - [article](interface/.mdarticle)のプロパティを参照 |
| location | ロケーション - [location](interface/.mdlocation)のプロパティを参照 |
| warehouse | 倉庫 - [warehouse](interface/.mdwarehouse)のプロパティを参照 |
| article\_id | （非推奨）商品マスタID |
| warehouse\_id | （非推奨）倉庫ID |


エンドポイント
-------


* [保管状況の一覧を取得](#get_list)
* [保管状況の検索](#search)


### 保管状況の一覧を取得


article\_code, identification\_codeは単一指定のみリクエストが可能です。


複数指定されたい場合やmodel\_numbers(型番)を指定されたい場合は[在庫の検索](#search) をご利用ください。


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/actual_inventory_summaries`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| article\_code | 商品コード |
| identification\_code | 識別コード |
| layer | [在庫レイヤー](type/.mdinventory_summary_layer) - デフォルトは `Article` |
| article\_type | [商品区分](type/.mdarticle_type) - デフォルトは `Single` |
| lot\_number | ロット番号 |
| min\_received | 入庫待ち（最小） |
| max\_received | 入庫待ち（最大） |
| min\_available | 保管中（最小） |
| max\_available | 保管中（最大） |
| min\_blocked | 保留（最小） |
| max\_blocked | 保留（最大） |
| min\_allocated | ピッキング中（最小） |
| max\_allocated | ピッキング中（最大） |
| min\_shipped | 出荷済み（最小） |
| max\_shipped | 出荷済み（最大） |
| deadline\_from | 出荷期限日（から） |
| deadline\_to | 出荷期限日（まで） |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) ※ updated\_at\_from 指定されない場合、在庫数が 0 のレコードは返却されませんのでご注意ください。 |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| warehouse\_id | 倉庫ID |
| ~~ean\_code~~ | ~~識別コード~~ （廃止予定 : identification\_codeを使用してください） |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": 32509,
      "layer": "Location",
      "received": 1,
      "available": 13,
      "blocked": 0,
      "shipped": 9,
      "issued": 0,
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article": {
        "id": 113,
        "code": "",
        "object_code": "",
        "name": ""
      },
      "location": {
        "id": 113,
        "code": "2950000001133",
        "name": "1-1-1"
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

### 保管状況の検索


複数の識別子(article\_codes, identification\_codes, model\_numbers)をもとに保管状況の一覧取得を行います。


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/actual_inventory_summaries/search`


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
      "layer": "Location",
      "received": 1,
      "available": 13,
      "blocked": 0,
      "shipped": 9,
      "issued": 0,
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article": {
        "id": 113,
        "code": "",
        "object_code": "",
        "name": ""
      },
      "location": {
        "id": 113,
        "code": "2950000001133",
        "name": "1-1-1"
      },
      "warehouse": {
        "id": 12,
        "name": "外部倉庫"
      }
    }
  ]
}


```


