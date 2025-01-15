

在庫操作ログ
======


説明
--


在庫操作ログと在庫数との関係については [ヘルプセンターの記事](https://docs.logiless.com/%E5%9C%A8%E5%BA%AB%E7%AE%A1%E7%90%86/%E5%9C%A8%E5%BA%AB%E6%93%8D%E4%BD%9C%E3%81%AE%E5%B1%A5%E6%AD%B4%E3%82%92%E7%A2%BA%E8%AA%8D%E3%81%99%E3%82%8B) をご確認ください。


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | ID在庫操作履歴をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| transaction\_type | [在庫操作区分](type/.mdtransaction_type) |
| ordered | 受注数量の増減 |
| in\_transit | 入荷待ち数量の増減 |
| transferring | 転送中数量の増減 |
| received | 入庫待ち数量の増減 |
| allocated | 引当済み数量の増減 |
| available | 保管中数量の増減 |
| moving | 移動数量の増減 |
| blocked | 保留数量の増減 |
| issued | 出庫数量の増減 |
| shipped | 出荷数量の増減 |
| article\_type | [商品区分](type/.mdarticle_type) |
| multiplier | 乗数商品区分が`Crate`の場合、通常商品ベースに換算する際の乗数です。たとえば、10個入りの集合包装の場合、乗数は10になります。 |
| deadline | 出荷期限日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| lot\_number | ロット番号 |
| is\_force | 強制処理かどうか |
| source | 処理元伝票 - [source](#property_source)のプロパティを参照 |
| remarks | 備考 |
| logical\_available | 在庫操作後の保管中数量 |
| created\_at | 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | [商品マスタ](interface/.mdarticle) |
| location\_from | [ロケーション(1)](interface/.mdlocation)在庫操作区分が、`PutAway`、`Moving`、`Issue`、`Shipment`の場合は、移動元ロケーションがセットされます。 |
| location\_to | [ロケーション(2)](interface/.mdlocation)在庫操作区分が、`Receipt`、`PutAway`、`Moving`、`ShipmentReversal`の場合は、移動先ロケーションがセットされます。 |
| logical\_article | [論理商品マスタ](interface/.mdartciel)商品区分が`Crate`の場合、構成する通常商品の商品マスタがセットされます。 |
| outbound\_delivery | 出荷伝票在庫操作区分が`shipment`の場合にセットされます。`id`と`code`のみが含まれます。 |
| warehouse | [倉庫](interface/.mdwarehouse) |


### source




| プロパティ | 説明 |
| --- | --- |
| inbound\_delivery | [入荷予定伝票](interface/.mdinbound_delivery) |


エンドポイント
-------


* [在庫操作ログの一覧を取得](#get_list)


### 在庫の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/transaction_logs`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| transaction\_type | [在庫操作区分](type/.mdtransaction_type)複数を指定する場合は `,`（カンマ）区切り |
| article\_code | 商品コード |
| warehouse\_id | 倉庫ID |
| created\_at\_from | 操作日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created\_at\_to | 操作日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": 1234,
      "transaction_type": "Receipt",
      "ordered": 0,
      "in_transit": 0,
      "transferring": 0,
      "received": 10,
      "allocated": 0,
      "available": 0,
      "moving": 0,
      "blocked": 0,
      "issued": 0,
      "shipped": 0,
      "article_type": "Single",
      "multiplier": 1,
      "is_force": true,
      "created_at": "2018-01-01 00:00:00",
      "updated_at": "2018-01-01 00:00:00",
      "article":{
        "id": 1,
        "code": "1-10-16MT-01-01",
        "object_code": "2000000000015",
        "name": "テスト商品(1)",
        "article_type": "Single",
        "unit": "個",
        "created_at": "2018-01-01 00:00:00",
        "updated_at": "2018-01-01 00:00:00"
      },
      "location_to":{
        "id": 113,
        "code": "2950000001133",
        "name": "001"
      },
      "logical_article":{
        "id": 1,
        "code": "1-10-16MT-01-01",
        "object_code": "2000000000015",
        "name": "テスト商品(1)",
        "article_type": "Single",
        "unit": "個",
        "created_at": "2018-01-01 00:00:00",
        "updated_at": "2018-01-01 00:00:00"
      },
      "warehouse":{
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


