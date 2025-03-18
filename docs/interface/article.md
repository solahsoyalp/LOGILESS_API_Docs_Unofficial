# 商品マスタ

## プロパティ

| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID商品マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。商品コードとは異なります。 |
| code | 商品コード |
| identification\_code | 識別コード |
| object\_code | ロジレスコード |
| model\_number | 型番 |
| name | [必須] 商品名 |
| name\_kana | 商品名かな |
| article\_type | [必須] [商品区分](type/article_type.md) - デフォルトは `Single` （APIで登録可能な商品区分は、`Single`と`Assortment`のみ） |
| price | 価格 |
| tax\_indicator | [税区分](type/tax_indicator.md) - デフォルトは `Included` |
| tax\_rate | 税率 - デフォルトは `8` |
| list\_price | 定価 |
| cost | 原価 |
| color | カラー |
| color\_code | カラーコード |
| size | サイズ |
| size\_code | サイズコード |
| temperature\_control | [配送温度](type/temperature_control.md) |
| width | 幅 |
| height | 高さ |
| depth | 奥行き |
| weight | 重さ |
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
| attr11 | フリー項目11 |
| attr12 | フリー項目12 |
| attr13 | フリー項目13 |
| attr14 | フリー項目14 |
| attr15 | フリー項目15 |
| attr16 | フリー項目16 |
| attr17 | フリー項目17 |
| attr18 | フリー項目18 |
| attr19 | フリー項目19 |
| attr20 | フリー項目20 |
| comment | 備考欄 |
| unit | 数量単位 |
| delivery\_category | 配送カテゴリ |
| default\_delivery\_method | デフォルトの[配送方法](type/delivery_method.md) |
| size\_coefficient | サイズ係数 |
| release\_date | 発売日 - `Y-m-d`形式 (例 : `2018-01-01`) |
| contents\_description | 内容品欄 |
| label\_text | ラベルテキスト |
| limiting\_sales | 販売制限数 |
| reorder\_point | 発注点 |
| tags | タグ(配列) |
| supplier\_code | [登録時のみ] 仕入先コード |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| supplier | [読取専用] 仕入先マスタ - [supplier](interface/supplier.md)のプロパティを参照 |
| components | 構成商品 - [component](#property_component)の配列 |

### プロパティの各項目について

レスポンスデータには "値が設定されている項目" についてのみ返却します

### component

| プロパティ | 説明 |
| --- | --- |
| component | 構成商品の商品コード |
| quantity | 構成商品の数量 |

## エンドポイント

* [商品マスタの一覧を取得](#get_list)
* [商品マスタを登録](#post)
* [商品マスタを複数件まとめて登録](#post-multiple)
* [商品マスタを編集](#put)
* [商品マスタを削除](#delete)

### 商品マスタの一覧を取得

#### リクエスト

`GET /api/v1/merchant/#{merchant_id}/articles`

| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| code | 商品コード |
| identification\_code | 識別コード |
| article\_type | [商品区分](type/article_type.md) |
| model\_number | 型番 |
| default\_delivery\_method | デフォルトの[配送方法](type/delivery_method.md) |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |

#### レスポンス

`HTTP/1.1 200 OK`

```
{
  "data":[
    {
      "id": "1",
      "code": "article-1",
      "object_code": "2000000000039",
      "name": "商品(1)",
      "article_type": "Single",
      "tax_indicator": "TaxIncluded",
      "temperature_control": "Normal",
      "unit": "個",
      "tags": ["tag-1","tag-2"],
      "limiting_sales": 0,
      "created_at": "2017-12-14 16:57:06",
      "updated_at": "2018-01-26 18:56:01"
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

### 商品マスタを登録

#### リクエスト

`POST /api/v1/merchant/#{merchant_id}/articles/new`

```
{
  "article": {
    "code": "test-1",
    "name":"商品(1)"
  }
}

```

#### レスポンス

`HTTP/1.1 201 Created`

```
{
  "id": "16467",
  "code": "test-1",
  "object_code": "2000000164670",
  "name": "商品(1)",
  "article_type": "Single",
  "tax_indicator": "TaxIncluded",
  "temperature_control": "Normal",
  "unit": "個",
  "limiting_sales": 0,
  "created_at": "2018-02-07 22:11:16",
  "updated_at": "2018-02-07 22:11:16"
}

```

### 商品マスタを複数件まとめて登録

#### リクエスト

100件までまとめて登録できます。

`POST /api/v1/merchant/#{merchant_id}/articles/new/multiple`

```
{
  "articles": [
    {
      "code": "test-1",
      "name":"商品(1)"
    },
    {
      "code": "test-2",
      "name":"商品(2)"
    }
  ]
}

```

#### レスポンス

`HTTP/1.1 200 OK`

```
[
  {
    "id": "16467",
    "code": "test-1",
    "object_code": "2000000164670",
    "name": "商品(1)",
    "article_type": "Single",
    "tax_indicator": "TaxIncluded",
    "temperature_control": "Normal",
    "unit": "個",
    "limiting_sales": 0,
    "created_at": "2018-02-07 22:11:16",
    "updated_at": "2018-02-07 22:11:16"
  },
  {
    "id": "16467",
    "code": "test-2",
    "object_code": "2000000164670",
    "name": "商品(2)",
    "article_type": "Single",
    "tax_indicator": "TaxIncluded",
    "temperature_control": "Normal",
    "unit": "個",
    "limiting_sales": 0,
    "created_at": "2018-02-07 22:11:16",
    "updated_at": "2018-02-07 22:11:16"
  }
]

```

### 商品マスタを編集

#### リクエスト

`PUT /api/v1/merchant/#{merchant_id}/articles/{id}`

```
{
  "article": {
    "name":"テスト商品(1)_編集"
  }
}

```

#### レスポンス

`HTTP/1.1 200 OK`

```
{
  "id": "16467",
  "code": "2000000164670",
  "object_code": "2000000164670",
  "name": "テスト商品(1)_編集",
  "article_type": "Single",
  "tax_indicator": "TaxIncluded",
  "temperature_control": "Normal",
  "unit": "個",
  "limiting_sales": 0,
  "created_at": "2018-02-07 22:11:16",
  "updated_at": "2018-02-07 22:11:16"
}

```

### 商品マスタを削除

#### リクエスト

`DELETE /api/v1/merchant/#{merchant_id}/articles/{id}/delete`

#### レスポンス

`HTTP/1.1 200 OK`

```
{
  "code": "200",
  "message": "article is successfully deleted"
}

```


