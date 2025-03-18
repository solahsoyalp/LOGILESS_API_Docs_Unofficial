# 商品対応表

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID商品対応表をユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| mapped\_code | マップされた商品コード |
| mapped\_choice1 | マップされた選択肢1 |
| mapped\_choice2 | マップされた選択肢2 |
| mapped\_choice3 | マップされた選択肢3 |
| attr1 | フリー項目1 |
| article\_option | 明細行備考欄 |
| cached\_stock\_quantity | キャッシュされた在庫数 |
| standby\_stock\_quantity | 予備在庫数 |
| stock\_allocation\_rate | 在庫割当率 |
| max\_stock\_quantity | 上限在庫数 |
| min\_stock\_quantity | 下限在庫数 |
| available\_stock\_quantity | キャッシュされた在庫数から計算された販売可能在庫数 |
| is\_inventory\_synced | 在庫連携されたかどうか - 連携されている場合: 1、連携されていない場合: 0 |
| is\_automatic\_inventory\_sync\_enables | 自動在庫連携が有効かどうか - 有効な場合: 1、有効でない場合: 0 |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

### article

| プロパティ | 説明 |
| --- | --- |
| id | ID商品情報をユニークに識別するための数値です。 |
| code | 商品コード |
| object\_code | ロジレスコード |
| name | 商品名 |
| article\_type | [商品区分](type/article_type.md) - デフォルトは `Single` |
| tax\_indicator | [税区分](type/tax_indicator.md) - デフォルトは `Included` |
| temperature\_control | [配送温度](type/temperature_control.md) |
| unit | 数量単位 |
| limiting\_sales | 販売制限数 |
| created\_at | [読取専用] 商品登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 商品更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

### store

| プロパティ | 説明 |
| --- | --- |
| id | ID店舗情報をユニークに識別するための数値です。 |
| name | 店舗名 |

## エンドポイント

* [商品対応表の一覧を取得](#get_list)

### 商品対応表の一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/article_maps`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| store | 店舗 |
| article\_code | 商品コード |
| is\_automatic\_inventory\_sync\_enables | 自動在庫連携が有効かどうか - 有効な場合: 1、有効でない場合: 0 |
| has\_error | 最後の在庫連携時にエラーがあったかどうか - エラーがある場合: 1、エラーがない場合: 0 |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

#### レスポンス

`HTTP/1.1 200`

```
{
  "data":[
    { 
      "id": 1,
      "mapped_code": "2000000000015",
      "mapped_choice1": "1",
      "mapped_choice2": "2",
      "mapped_choice3": "0",
      "attr1": "test",
      "article_option": "1",
      "cached_stock_quantity": 41,
      "standby_stock_quantity": 3,
      "stock_allocation_rate": 20,
      "max_stock_quantity": 25,
      "min_stock_quantity": 0,
      "is_inventory_synced": false,
      "is_automatic_inventory_sync_enables": false,
      "created_at": "2019-01-21 11:49:58",
      "updated_at": "2019-01-25 17:04:50",
      "article":{
      "id": 1,
      "code": "2000000000015",
      "object_code": "2000000000015",
      "name": "テスト商品1",
      "article_type": "Single",
      "tax_indicator": "TaxIncluded",
      "temperature_control": "Normal",
      "unit": "個",
      "limiting_sales": 0,
      "created_at": "2018-08-19 16:05:04",
      "updated_at": "2018-08-19 16:05:04"
      },
      "store":{
      "id": 1,
      "name": "株式会社第一マーチャント (general)"
      }
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```


