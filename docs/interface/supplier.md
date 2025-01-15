

仕入先マスタ
======


プロパティ
-----




| プロパティ | 説明 |
| --- | --- |
| id | [読取専用] ID仕入先マスタをユニークに識別するための数値です。主に、APIでのアクセスに使用します。仕入先コードとは異なります。 |
| code | 仕入先コード |
| name | [必須] 仕入先名 |
| name\_kana | 仕入先名かな |
| post\_code | 郵便番号 |
| prefecture | 都道府県 |
| address1 | 住所１ |
| address2 | 住所２ |
| address3 | 住所３ |
| phone | 電話番号 |
| fax | FAX番号 |
| email | メールアドレス |
| representative | 担当者名 |
| representative\_kana | 担当者名かな |
| comment | コメント |
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
| keyword | 検索用キーワード |
| created\_at | [読取専用] 登録日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at | [読取専用] 更新日時 - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


エンドポイント
-------


* [仕入先マスタの一覧を取得](#get_list)
* [仕入先マスタを登録](#post)
* [仕入先マスタを編集](#put)


### 仕入先マスタの一覧を取得


#### リクエスト


`GET /api/v1/merchant/#{merchant_id}/suppliers`




| パラメーター | 説明 |
| --- | --- |
| limit | 取得する結果の数 - デフォルトは `20` 最大値は `100` |
| page | ページ - デフォルトは `1` |
| code | 仕入先コード |
| updated\_at\_from | 更新日時（From） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |
| updated\_at\_to | 更新日時（To） - `Y-m-d H:i:s`形式 (例 : `2018-01-01 23:59:59`) |


#### レスポンス


`HTTP/1.1 200`



```
{
  "data":[
    {
      "id": "12345",
      "code": "supplier-1",
      "name": "仕入先(1)",
      "created_at": "2018-02-07 22:11:16",
      "updated_at": "2018-02-07 22:11:16"
    }
  ],
  "current_page": 1,
  "limit": 20,
  "total_count": 1
}

```

### 仕入先マスタを登録


#### リクエスト


`POST /api/v1/merchant/#{merchant_id}/suppliers/new`



```
{
  "supplier": {
    "code": "supplier-1",
    "name":"仕入先(1)"
  }
}

```

#### レスポンス


`HTTP/1.1 201 Created`



```
{
  "id": "12345",
  "code": "supplier-1",
  "name": "仕入先(1)",
  "created_at": "2018-02-07 22:11:16",
  "updated_at": "2018-02-07 22:11:16"
}

```

### 仕入先マスタを編集


#### リクエスト


`PUT /api/v1/merchant/#{merchant_id}/suppliers/{id}`



```
{
  "supplier": {
    "name":"仕入先(1)_編集"
  }
}

```

#### レスポンス


`HTTP/1.1 200`



```
{
  "id": "12345",
  "code": "supplier-1",
  "name": "仕入先(1)_編集",
  "created_at": "2018-02-07 22:11:16",
  "updated_at": "2018-02-07 22:11:16"
}

```


