

ロケーション
======


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | IDロケーションをユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| code | ロケーションコード |
| name | ロケーション名 |


エンドポイント
-------


* [ロケーションの一覧を取得](#get_list)


### 在庫の一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/warehouses/#{warehouse_id}/locations`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| code | ロケーションコード |
| name | ロケーション名 |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": 1,
      "code": "2950000000013",
      "name": "1-1-1"
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

