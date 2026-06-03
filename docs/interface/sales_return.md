# 売上返品

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] 売上返品をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| lines | [配列] 返品対象の受注伝票明細行 - [line](#property_line)の配列 |
| quantity | 返品数量 |
| remarks | 備考 |
| is_approved | 承認済みかどうか - 承認済みの場合は `1`、未承認の場合は `0` |
| resolution_type | 対応方法 - `Refund`（返金）/ `Exchange`（交換） |
| created_at | [読取専用] 作成日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| approved_at | [読取専用] 承認日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

### line

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] 受注伝票明細行ID |
| code | 明細行コード |
| article_code | 商品コード（店舗） |
| article_name | 商品名 |
| article_option | 明細行備考欄 |
| price | 販売単価 |
| quantity | 販売数量 |
| parent_id | [読取専用] 親明細行ID（子明細行の場合にのみ設定されます） |
| tax_indicator | [税区分](../document_status/tax_indicator.md) |
| tax_rate | 税率 |
| tax_total | [読取専用] 税の合計 |
| subtotal | [読取専用] 小計 |
| created_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| article | [読取専用] 商品マスタ - [article](#property_article)のプロパティを参照 |
| sales_order | [読取専用] 受注伝票 - [sales_order](#property_sales_order)のプロパティを参照 |

### article

| プロパティ | 説明 |
| --- | --- |
| id | 商品マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| code | 商品コード（商品マスタ） |
| identification_code | 識別コード |
| object_code | ロジレスコード |
| model_number | 型番 |
| name | 商品名 |
| name_kana | 商品名かな |

### sales_order

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] 受注伝票ID |
| code | 受注コード |
| object_code | 受注管理番号 |
| document_status | [読取専用] [伝票ステータス](../document_status/document_status.md) |
| use_point | ポイント利用 |
| use_coupon | クーポン利用 |
| delivery_fee | 送料 |
| sundry_fee | その他手数料 |
| discount | 値引き |
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
| store_coupon | [読取専用] クーポン利用（ストア発行） |
| mall_coupon | [読取専用] クーポン利用（モール発行） |
| finished_at | [読取専用] 完了日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

## エンドポイント

* [売上返品の一覧を取得](#get_list)

### 売上返品の一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/sales_returns`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値あり |
| page | ページ - デフォルトは `1` |
| sales_order_code | 受注コード |
| article_code | 商品コード |
| article_name | 商品名 |
| quantity | 売上返品数量 |
| is_approved | 承認済みかどうか - 承認済みの場合は `1`、未承認の場合は `0` |
| created_at_from | 作成日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| created_at_to | 作成日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| approved_at_from | 承認日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| approved_at_to | 承認日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

#### レスポンス

`HTTP/1.1 200 OK`

```
{
  "data": [
    {
      "id": 12345,
      "lines": [
        {
          "id": 67890,
          "code": "LINE-001",
          "article_code": "ART-001",
          "article_name": "Sample Product",
          "article_option": "Color: Red, Size: M",
          "price": 1000,
          "quantity": 1,
          "tax_indicator": "TaxExcluded",
          "tax_rate": 10,
          "tax_total": 90,
          "subtotal": 1000,
          "created_at": "2024-01-01 23:59:59",
          "updated_at": "2024-01-02 23:59:59",
          "article": {
            "id": 3456,
            "code": "ART-001",
            "identification_code": "ID-001",
            "object_code": "2100000034567",
            "model_number": "MN-001",
            "name": "Sample Product",
            "name_kana": "サンプルプロダクト"
          },
          "sales_order": {
            "id": 7621,
            "code": "ORDER-001",
            "object_code": "2100000076215",
            "document_status": "Shipped",
            "use_point": 100,
            "use_coupon": 200,
            "delivery_fee": 500,
            "sundry_fee": 50,
            "discount": 150,
            "attr1": "Value1",
            "attr2": "Value2",
            "attr3": "Value3",
            "finished_at": "2024-01-05 12:00:00",
            "created_at": "2024-01-01 10:00:00",
            "updated_at": "2024-01-03 10:00:00"
          }
        }
      ],
      "quantity": 2,
      "remarks": "Customer returned due to defect",
      "is_approved": 1,
      "resolution_type": "Refund",
      "created_at": "2024-01-01 12:00:00",
      "updated_at": "2024-01-02 12:00:00",
      "approved_at": "2024-01-03 12:00:00"
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

| フィールド | 説明 |
| --- | --- |
| data | 売上返品オブジェクトの配列 |
| current_page | 現在のページ番号 |
| limit | 1ページあたりの取得数 |
| total_count | 合致するレコード総数 |
