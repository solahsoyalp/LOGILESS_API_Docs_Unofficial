

倉庫別発注点
======


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | ID発注点情報をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| reorder\_point | 発注点 |
| inventory\_constant | 在庫定数 |
| inventory\_summary\_by\_warehouse | 倉庫別在庫数 - [property\_inventory\_summary\_by\_warehouse](#property_inventory_summary_by_warehouse)のプロパティを参照 |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | 商品マスタ - [article](interface/.mdarticle)のプロパティを参照 |
| warehouse | 倉庫 - [warehouse](interface/.mdwarehouse)のプロパティを参照 |


### inventory\_summary\_by\_warehouse


このプロパティの在庫数はリアルタイムではなく、10分程度の遅延があります。




| プロパティ | 説明 |
| --- | --- |
| in\_transit | 入荷待ち |
| transferring | 輸送中 |
| received | 入庫待ち |
| available | 保管中 |
| allocated | 引当済み |
| inter\_warehouse\_transfer | 倉庫間移動 - [inter\_warehouse\_transfer](#property_inter_warehouse_transfer)のプロパティを参照 |


### inter\_warehouse\_transfer




| プロパティ | 説明 |
| --- | --- |
| waiting\_for\_shipment | 未出荷の倉庫間移動数量 |


エンドポイント
-------


* [倉庫別発注点の一覧を取得](#get_list)


### 在庫の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/reorder_points`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| article\_code | 商品コード |
| warehouse\_id | 倉庫ID |
| is\_reorder\_level | 発注点割れかどうか |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data": [
    {
      "id": 32509,
      "reorder_point": 10,
      "inventory_constant": 100,
      "inventory_summary_by_warehouse": {
        "in_transit": 0,
        "transferring": 0,
        "received": 0,
        "available": 20,
        "allocated": 0,
        "inter_warehouse_transfer": {
          "waiting_for_shipment": 0
        }
      },
      "created_at": "2017-01-06 15:50:37",
      "updated_at": "2018-01-26 15:20:37",
      "article": {
        "id": 113,
        "code": "test-1",
        "object_code": "",
        "name": "テスト商品",
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


