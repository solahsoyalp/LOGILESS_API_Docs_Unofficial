# LOGILESS API 非公式ドキュメント

本リポジトリは、株式会社ロジレスが提供する LOGILESS API のドキュメントを Markdown で整理した非公式リポジトリです。公式ドキュメントの内容を読みやすい形にまとめ、あわせて機械可読な API 仕様（OpenAPI 3.0）を提供します。

> 最終確認日: 2026-06-04（公式 https://app2.logiless.com/developer/ を反映済み）

> 機械可読仕様 (OpenAPI 3.0): API リソースごとの OpenAPI 定義を `spec/` に用意しています。公式は機械可読仕様を提供していないため、本リポジトリで独自に整備しています。今後の仕様修正は `spec/*.json` を単一ソース（Single Source of Truth）として編集し、`docs/` 配下の Markdown は参照用とします。

## 免責事項

本リポジトリは非公式であり、株式会社ロジレスとは一切関係ありません。公式の情報は https://app2.logiless.com/developer/ を参照してください。本リポジトリの内容は正確性を保証するものではなく、利用は自己責任でお願いします。

## 目次

- [認証・認可](#認証認可)
- [基本エンドポイント](#基本エンドポイント)
- [データフォーマット](#データフォーマット)
- [エラーレスポンス](#エラーレスポンス)
- [APIリスト（インターフェース）](#apiリストインターフェース)
- [エンドポイント早見表](#エンドポイント早見表)
- [列挙型（ステータス・区分）](#列挙型ステータス区分)
- [更新履歴](#更新履歴)
- [利用方法](#利用方法)
- [貢献](#貢献)
- [著作権および免責](#著作権および免責)

## 認証・認可

LOGILESS API は OAuth2（認可コードフロー）で認証を行います。利用には事前に LOGILESS Developers でのアプリケーション登録（審査あり）が必要です。認可コードをアクセストークンと交換し、取得したアクセストークンを `Authorization: Bearer <ACCESS_TOKEN>` ヘッダーで送信してリクエストします。

詳細は [docs/authentication.md](docs/authentication.md) を参照してください。

```bash
curl -X GET "https://app2.logiless.com/api/v1/merchant/{merchant_id}/sales_orders" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

## 基本エンドポイント

基本エンドポイントは https://app2.logiless.com/api/ です。通信は https（TLS1.2 以上）のみに対応しています。

各リソースの URL は次の形式になります。

```
https://app2.logiless.com/api/v1/merchant/{merchant_id}/...
```

`{merchant_id}` は、API を利用するマーチャント（事業者アカウント）を識別する ID です。リクエスト対象のマーチャントに応じて、この値を実際の ID に置き換えてください。

## データフォーマット

リクエスト・レスポンスともに JSON 形式を使用し、文字コードは UTF-8 です。POST・PUT の際は `Content-Type: application/json` を付与し、リクエストボディに JSON を送信します。

HTTP メソッドは操作の種類を表します。

- `GET` - 参照
- `POST` - 新規登録
- `PUT` - 更新
- `DELETE` - 削除

## エラーレスポンス

API リクエストに問題がある場合は、HTTP エラーコードとともにレスポンスが返されます。

| コード | 説明 |
| --- | --- |
| 400 | リクエスト時に指定したパラメータがロジレス API で期待されたものと一致しない場合に返されます。返却されたメッセージは何が間違っているか、何が正しくないかを伝えます。 |
| 401 | 必要な認証・認可情報がリクエストに存在しないか、正しくない場合に返されます。 |
| 403 | リクエストへの応答を拒否しています。 |
| 423 | 指定されたリソースの伝票ステータスが変更不可の場合に返されます。 |
| 429 | API のリクエストレート制限を超えた場合に返されます。 |
| 500 | 内部的な問題によってデータを返すことができない場合に返されます。 |

詳細（レスポンス JSON の形式など）は [docs/errors.md](docs/errors.md) を参照してください。

## APIリスト（インターフェース）

| リソース | ドキュメント | 機械可読仕様 |
| --- | --- | --- |
| [受注伝票](docs/interface/sales_order.md) | `docs/interface/sales_order.md` | [`spec/sales_order.json`](spec/sales_order.json) |
| [売上返品](docs/interface/sales_return.md) | `docs/interface/sales_return.md` | [`spec/sales_return.json`](spec/sales_return.json) |
| [出荷伝票](docs/interface/outbound_delivery.md) | `docs/interface/outbound_delivery.md` | [`spec/outbound_delivery.json`](spec/outbound_delivery.json) |
| [入荷予定伝票](docs/interface/inbound_delivery.md) | `docs/interface/inbound_delivery.md` | [`spec/inbound_delivery.json`](spec/inbound_delivery.json) |
| [倉庫間移動伝票](docs/interface/inter_warehouse_transfer.md) | `docs/interface/inter_warehouse_transfer.md` | [`spec/inter_warehouse_transfer.json`](spec/inter_warehouse_transfer.json) |
| [商品マスタ](docs/interface/article.md) | `docs/interface/article.md` | [`spec/article.json`](spec/article.json) |
| [商品対応表](docs/interface/article_map.md) | `docs/interface/article_map.md` | [`spec/article_map.json`](spec/article_map.json) |
| [仕入先マスタ](docs/interface/supplier.md) | `docs/interface/supplier.md` | [`spec/supplier.json`](spec/supplier.json) |
| [在庫（論理在庫サマリ）](docs/interface/logical_inventory_summary.md) | `docs/interface/logical_inventory_summary.md` | [`spec/logical_inventory_summary.json`](spec/logical_inventory_summary.json) |
| [保管状況（実在庫サマリ）](docs/interface/actual_inventory_summary.md) | `docs/interface/actual_inventory_summary.md` | [`spec/actual_inventory_summary.json`](spec/actual_inventory_summary.json) |
| [日次在庫表](docs/interface/daily_inventory_summary.md) | `docs/interface/daily_inventory_summary.md` | [`spec/daily_inventory_summary.json`](spec/daily_inventory_summary.json) |
| [在庫操作ログ](docs/interface/transaction_log.md) | `docs/interface/transaction_log.md` | [`spec/transaction_log.json`](spec/transaction_log.json) |
| [倉庫別発注点](docs/interface/reorder_point.md) | `docs/interface/reorder_point.md` | [`spec/reorder_point.json`](spec/reorder_point.json) |
| [店舗](docs/interface/store.md) | `docs/interface/store.md` | [`spec/store.json`](spec/store.json) |
| [倉庫](docs/interface/warehouse.md) | `docs/interface/warehouse.md` | [`spec/warehouse.json`](spec/warehouse.json) |
| [ロケーション](docs/interface/location.md) | `docs/interface/location.md` | [`spec/location.json`](spec/location.json) |

## エンドポイント早見表

ベース URL: `https://app2.logiless.com/api/v1/merchant/{merchant_id}`

| メソッド | パス | 概要 | ドキュメント |
| --- | --- | --- | --- |
| GET | `/api/v1/merchant/{merchant_id}/sales_orders` | 受注伝票の一覧を取得 | [sales_order](docs/interface/sales_order.md) |
| POST | `/api/v1/merchant/{merchant_id}/sales_orders/search` | 受注伝票の検索（ids/codesで複数取得） | [sales_order](docs/interface/sales_order.md) |
| POST | `/api/v1/merchant/{merchant_id}/sales_orders/new` | 受注伝票を登録 | [sales_order](docs/interface/sales_order.md) |
| PUT | `/api/v1/merchant/{merchant_id}/sales_orders/{id}` | 受注伝票を編集 | [sales_order](docs/interface/sales_order.md) |
| POST | `/api/v1/merchant/{merchant_id}/sales_orders/{id}/reversal` | 受注伝票をキャンセル | [sales_order](docs/interface/sales_order.md) |
| POST | `/api/v1/merchant/{merchant_id}/sales_orders/{id}/sales_order_lines/{id}/reversal` | 明細行をキャンセル | [sales_order](docs/interface/sales_order.md) |
| GET | `/api/v1/merchant/{merchant_id}/sales_returns` | 売上返品の一覧を取得 | [sales_return](docs/interface/sales_return.md) |
| GET | `/api/v1/merchant/{merchant_id}/outbound_deliveries` | 出荷伝票の一覧を取得 | [outbound_delivery](docs/interface/outbound_delivery.md) |
| GET | `/api/v1/merchant/{merchant_id}/inbound_deliveries` | 入荷予定伝票の一覧を取得 | [inbound_delivery](docs/interface/inbound_delivery.md) |
| POST | `/api/v1/merchant/{merchant_id}/inbound_deliveries/new` | 入荷予定伝票を登録 | [inbound_delivery](docs/interface/inbound_delivery.md) |
| POST | `/api/v1/merchant/{merchant_id}/inbound_deliveries/{id}/reversal` | 入荷予定伝票をキャンセル | [inbound_delivery](docs/interface/inbound_delivery.md) |
| GET | `/api/v1/merchant/{merchant_id}/inter_warehouse_transfers` | 倉庫間移動伝票の一覧を取得 | [inter_warehouse_transfer](docs/interface/inter_warehouse_transfer.md) |
| POST | `/api/v1/merchant/{merchant_id}/inter_warehouse_transfers/new` | 倉庫間移動伝票を登録 | [inter_warehouse_transfer](docs/interface/inter_warehouse_transfer.md) |
| GET | `/api/v1/merchant/{merchant_id}/articles` | 商品マスタの一覧を取得 | [article](docs/interface/article.md) |
| POST | `/api/v1/merchant/{merchant_id}/articles/new` | 商品マスタを登録 | [article](docs/interface/article.md) |
| POST | `/api/v1/merchant/{merchant_id}/articles/new/multiple` | 商品マスタを複数件まとめて登録 | [article](docs/interface/article.md) |
| PUT | `/api/v1/merchant/{merchant_id}/articles/{id}` | 商品マスタを編集 | [article](docs/interface/article.md) |
| DELETE | `/api/v1/merchant/{merchant_id}/articles/{id}/delete` | 商品マスタを削除 | [article](docs/interface/article.md) |
| GET | `/api/v1/merchant/{merchant_id}/article_maps` | 商品対応表の一覧を取得 | [article_map](docs/interface/article_map.md) |
| GET | `/api/v1/merchant/{merchant_id}/suppliers` | 仕入先マスタの一覧を取得 | [supplier](docs/interface/supplier.md) |
| POST | `/api/v1/merchant/{merchant_id}/suppliers/new` | 仕入先マスタを登録 | [supplier](docs/interface/supplier.md) |
| PUT | `/api/v1/merchant/{merchant_id}/suppliers/{id}` | 仕入先マスタを編集 | [supplier](docs/interface/supplier.md) |
| GET | `/api/v1/merchant/{merchant_id}/logical_inventory_summaries` | 在庫の一覧を取得 | [logical_inventory_summary](docs/interface/logical_inventory_summary.md) |
| POST | `/api/v1/merchant/{merchant_id}/logical_inventory_summaries/search` | 在庫の検索 | [logical_inventory_summary](docs/interface/logical_inventory_summary.md) |
| GET | `/api/v1/merchant/{merchant_id}/actual_inventory_summaries` | 保管状況の一覧を取得 | [actual_inventory_summary](docs/interface/actual_inventory_summary.md) |
| POST | `/api/v1/merchant/{merchant_id}/actual_inventory_summaries/search` | 保管状況の検索 | [actual_inventory_summary](docs/interface/actual_inventory_summary.md) |
| GET | `/api/v1/merchant/{merchant_id}/daily_inventory_summaries` | 在庫の一覧を取得 | [daily_inventory_summary](docs/interface/daily_inventory_summary.md) |
| GET | `/api/v1/merchant/{merchant_id}/transaction_logs` | 在庫操作ログの一覧を取得 | [transaction_log](docs/interface/transaction_log.md) |
| GET | `/api/v1/merchant/{merchant_id}/reorder_points` | 倉庫別発注点の一覧を取得 | [reorder_point](docs/interface/reorder_point.md) |
| GET | `/api/v1/merchant/{merchant_id}/stores` | 店舗の一覧を取得 | [store](docs/interface/store.md) |
| GET | `/api/v1/merchant/{merchant_id}/warehouses` | 倉庫の一覧を取得 | [warehouse](docs/interface/warehouse.md) |
| GET | `/api/v1/merchant/{merchant_id}/warehouses/{warehouse_id}/locations` | ロケーションの一覧を取得 | [location](docs/interface/location.md) |

## 列挙型（ステータス・区分）

| 型 | slug |
| --- | --- |
| [伝票ステータス](docs/document_status/document_status.md) | `document_status` |
| [引当ステータス](docs/document_status/allocation_status.md) | `allocation_status` |
| [配送ステータス](docs/document_status/delivery_status.md) | `delivery_status` |
| [入金ステータス](docs/document_status/incoming_payment_status.md) | `incoming_payment_status` |
| [承認ステータス](docs/document_status/authorization_status.md) | `authorization_status` |
| [明細行ステータス](docs/document_status/document_line_status.md) | `document_line_status` |
| [配送方法](docs/document_status/delivery_method.md) | `delivery_method` |
| [支払方法](docs/document_status/payment_method.md) | `payment_method` |
| [お急ぎ区分](docs/document_status/express_type.md) | `express_type` |
| [配送温度](docs/document_status/temperature_control.md) | `temperature_control` |
| [税区分](docs/document_status/tax_indicator.md) | `tax_indicator` |
| [税の計算順序](docs/document_status/tax_processing_method.md) | `tax_processing_method` |
| [税の丸め](docs/document_status/tax_rounding_method.md) | `tax_rounding_method` |
| [商品区分](docs/document_status/article_type.md) | `article_type` |
| [入荷予定ステータス](docs/document_status/inbound_delivery_status.md) | `inbound_delivery_status` |
| [入荷予定カテゴリ](docs/document_status/inbound_delivery_category.md) | `inbound_delivery_category` |
| [在庫操作区分](docs/document_status/transaction_type.md) | `transaction_type` |
| [在庫レイヤー](docs/document_status/inventory_summary_layer.md) | `inventory_summary_layer` |

## 更新履歴

| 日付 | 変更内容 |
| --- | --- |
| 2026-06-04 | リポジトリ構成を刷新。OpenAPI 3.0 仕様（spec/）を新設。README に共通仕様・エンドポイント早見表・更新履歴を追加。CONTRIBUTING と更新検知用 GitHub Actions を整備。 |
| 2026-06-04 | 公式の新規ドキュメントを反映: 売上返品（sales_return）インターフェースと引当ステータス（allocation_status）列挙型を追加。 |

## 利用方法

本リポジトリをクローンし、`docs/` 配下の Markdown や `spec/` の OpenAPI 定義を参照してください。

```bash
git clone https://github.com/solahsoyalp/LOGILESS_API_Docs_Unofficial.git
```

`docs/` には各インターフェースや列挙型の解説が、`spec/` には機械可読な OpenAPI 3.0 定義が含まれています。

## 貢献

誤りの報告や改善の提案を歓迎します。Issue・Pull Request はお気軽にお寄せください。詳細は [CONTRIBUTING.md](CONTRIBUTING.md) を参照してください。

## 著作権および免責

本ファイルは、公式 API ドキュメント（https://app2.logiless.com/developer/）を Markdown 形式にまとめたものであり、その内容の著作権は全て株式会社ロジレスに帰属します。本リポジトリは非公式であり、内容の正確性を保証するものではありません。
