

認証・認可
=====


新しいアプリケーションを作成する
----------------


LOGILESS APIは、OAuth2プロトコルでの認証を行います。利用には事前にLOGILESS Developersへの「アプリケーションの登録」が必要です。




 **アプリケーションの登録には審査があります。**


 アプリケーションの登録には審査があります。このページのフォームから申請後、3〜5営業日で審査結果をメールでお知らせします。審査結果のメールは、このフォームで登録されたアドレスにお送りいたします。
 

### 新しいアプリケーションの作成フロー


1. **[アプリケーション](https://app2.logiless.com/developer/console/clients)**から「**[新しいアプリケーション登録](https://app2.logiless.comhttps://app2.logiless.com/developer/console/clients/new)**」をクリックし、フォームに移動します。 アプリケーション一覧へのアクセスにはLOGILESS アカウントが必要です。アカウントをお持ちでない方は、**[こちら](https://app2.logiless.com/merchant/sign_up)**から登録してください。
2. 登録画面で、審査に必要な情報を入力します。入力いただいた情報は、アプリケーションの利用状況の把握や、アプリケーションの不正利用を防ぐ目的で使用いたします。
3. アプリケーションの審査が完了すると「**クライアントID**」と「**クライアントシークレット**」がアプリケーションの詳細画面で確認できるようになります。クライアントIDとクライアントシークレットは「**LOGILESSの認証ページを表示する**」「**認可コードとアクセストークン、リフレッシュトークンを交換**」のそれぞれのステップで必要となります。


ロジレスの認証ページを表示する
---------------


https://app2.logiless.com/oauth/v2/auth に、必要なパラメータを付加してGETリクエストを行ってください。
ロジレス ユーザーIDの認証を行うページが表示されます。




| パラメータ名 | 有効な値 |
| --- | --- |
| client\_id | クライアントID |
| response\_type | "code" を指定 |
| redirect\_uri | アプリケーション登録時に入力したリダイレクトURLと同一のものを指定 |


URLにアクセスすると、認可ページが表示されます。
ロジレス ユーザーIDを持つ利用者は、このページで、アプリケーションがアカウントのデータにアクセスすることを許可します。


認可コードを取得
--------


利用者が認可ページにて承認ボタンを押下すると、ロジレスから認可コードが発行されます。
以下の方法で、アプリケーションから認可コードを取得し、アクセストークンと交換します。


### Webサーバを用いる場合


redirect\_uri に指定したURLへリダイレクトされます。
承認された場合、 code という名前のURLパラメータに認可コードが付与されます。
承認がキャンセルされた場合、またはエラーの場合、error パラメータにエラーの内容を表す英数字の文字列が付与されます。


認可コードの有効期限は30秒間です。


認可コードとアクセストークン、リフレッシュトークンを交換
----------------------------


認可コードを使って、アクセストークンとリフレッシュトークンを取得します。
https://app2.logiless.com/oauth2/token に、必要なパラメータを付加してGETリクエストを行ってください。




| パラメータ名 | 有効な値 |
| --- | --- |
| client\_id | クライアントID |
| client\_secret | クライアントシークレット |
| code | 認可コード |
| grant\_type | "authorization\_code" を指定 |
| redirect\_uri | アプリケーション登録時に入力したリダイレクトURLと同一のものを指定 |


**レスポンス** - リクエストが成功すると、以下のようなレスポンスがJSONで返ります。



```
{"access_token":"d461ab8XXXXXXXXXXXXXXXXXXXXXXXXX","token_type":"bearer","expires_in":2592000,"refresh_token":d461ab8XXXXXXXXXXXXXXXXXXXXXXXXX,"scope":""}

```

access\_token プロパティに格納されている値が、アクセストークンです。
refresh\_token プロパティに格納されている値が、リフレッシュトークンです。


アクセストークンを取得すれば、ロジレス API にアクセスする準備は完了です。


認可コードをアクセストークンに交換できるのは1度だけです。


APIの呼び出し
--------


アクセストークン使用して HTTPリクエストを行うことで、ロジレスAPIにアクセスすることができます。
リクエスト、レスポンス、どちらも JSON でやりとりを行います。


Authorizationヘッダーでアクセストークンを送信して認証してください。



```
Authorization: Bearer {Access_Token}

```

各 API は、URL と HTTP メソッドで操作を表します。


* GET - 参照
* POST - 新規登録
* PUT - 更新
* DELETE - 削除


POST、PUTの際には、ヘッダにContent-Type: application/jsonをつけ、リクエストボディにJSONを送信します。
リクエストボディのJSONに日本語が含まれる場合は 文字コードはUTF-8、\uNNNN 形式でエンコードされている必要があります。


アクセストークンの再取得
------------


アクセストークンの有効期間が過ぎると、そのトークンではアクセスできなくなります。その場合、アクセストークンと同時に送られてきたリフレッシュトークンを用いて、新たなトークンを取得する必要があります。


https://app2.logiless.com/oauth2/token に、必要なパラメータを付加してGETリクエストを行ってください。




| パラメータ名 | 有効な値 |
| --- | --- |
| client\_id | クライアントID |
| client\_secret | クライアントシークレット |
| refresh\_token | リフレッシュトークン |
| grant\_type | "refresh\_token" を指定 |


**レスポンス** - リクエストが成功すると、以下のようなレスポンスがJSONで返ります。



```
{"access_token":"d461ab8XXXXXXXXXXXXXXXXXXXXXXXXX","token_type":"bearer","expires_in":2592000,"refresh_token":d461ab8XXXXXXXXXXXXXXXXXXXXXXXXX,"scope":""}

```

access\_token プロパティに格納されている値が、新しいアクセストークンです。


