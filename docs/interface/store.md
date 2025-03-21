# 店舗

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID店舗をユニークに識別するための数値です。主に、APIでのアクセスに使用します。 |
| name | [必須] 店舗名 |

## エンドポイント

* [店舗の一覧を取得](#get_list)

### 店舗の一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/stores`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |

#### レスポンス

`HTTP/1.1 200 OK`

```
{
  "data": [
    {
      "id": 100001,
      "name": "店舗-01"
    },
    {
      "id": 100002,
      "name": "店舗-02"
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 2
}

```


