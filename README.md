# Documentation for Logiless API

このリポジトリにはLogiless APIに関するドキュメントが含まれています。以下は各Markdownファイルの説明と役割です。

## ファイル一覧

### docsフォルダ

1. [**authentication.md**](docs/authentication.md)

   - 認証と認可に関する情報が記載されています。
   - アプリケーションの登録方法や認可コードの取得、アクセストークンの交換手順が詳述されています。

2. [**specifications.md**](docs/specifications.md)

   - APIの仕様に関する情報が記載されています。
   - エンドポイントやデータフォーマットの詳細を含みます。

3. [**errors.md**](docs/errors.md)

   - エラーメッセージおよびエラーコードに関する情報が記載されています。
   - 各エラーコードの説明やレスポンス形式が詳述されています。

### interfaceフォルダ

- [**actual_inventory_summary.md**](interface/actual_inventory_summary.md)

  - 実際の在庫サマリに関する情報を提供します。

- [**location.md**](interface/location.md)

  - ロケーション情報の管理について記載されています。

- [**outbound_delivery.md**](interface/outbound_delivery.md)

  - 出荷配送に関する情報を提供します。

- [**inbound_delivery.md**](interface/inbound_delivery.md)

  - 入荷配送に関する情報を提供します。

- [**reorder_point.md**](interface/reorder_point.md)

  - 再注文点の設定や管理に関する情報を提供します。

- [**article.md**](interface/article.md)

  - 商品情報の管理に関する情報を提供します。

- [**inter_warehouse_transfer.md**](interface/inter_warehouse_transfer.md)

  - 倉庫間移動に関する情報を提供します。

- [**transaction_log.md**](interface/transaction_log.md)

  - 取引ログの記録に関する情報を提供します。

- [**supplier.md**](interface/supplier.md)

  - サプライヤー情報の管理に関する情報を提供します。

- [**article_map.md**](interface/article_map.md)

  - 商品マッピングに関する情報を提供します。

- [**logical_inventory_summary.md**](interface/logical_inventory_summary.md)

  - 論理的な在庫サマリについて記載されています。

- [**store.md**](interface/store.md)

  - 店舗情報の管理について記載されています。

- [**sales_order.md**](interface/sales_order.md)

  - 受注情報の管理について記載されています。

- [**warehouse.md**](interface/warehouse.md)

  - 倉庫情報の管理について記載されています。

- [**daily_inventory_summary.md**](interface/daily_inventory_summary.md)

  - 日次在庫サマリに関する情報を提供します。

### document_statusフォルダ

- [**delivery_status.md**](type/delivery_status.md)

  - 配送ステータスに関する情報を提供します。

- [**authorization_status.md**](type/authorization_status.md)

  - 認証ステータスに関する情報を提供します。

- [**document_status.md**](type/document_status.md)

  - ドキュメントのステータス管理について記載されています。

- [**article_type.md**](type/article_type.md)

  - 商品タイプに関する情報を提供します。

- [**inbound_delivery_status.md**](type/inbound_delivery_status.md)

  - 入荷配送ステータスについて記載されています。

- [**incoming_payment_status.md**](type/incoming_payment_status.md)

  - 受領済み支払いのステータスに関する情報を提供します。

- [**tax_rounding_method.md**](type/tax_rounding_method.md)

  - 税金の丸め方法について記載されています。

- [**delivery_method.md**](type/delivery_method.md)

  - 配送方法に関する情報を提供します。

- [**document_line_status.md**](type/document_line_status.md)

  - ドキュメント行のステータスについて記載されています。

- [**tax_processing_method.md**](type/tax_processing_method.md)

  - 税金処理の方法について記載されています。

- [**temperature_control.md**](type/temperature_control.md)

  - 温度管理に関する情報を提供します。

- [**payment_method.md**](type/payment_method.md)

  - 支払い方法に関する情報を提供します。

- [**inbound_delivery_category.md**](type/inbound_delivery_category.md)

  - 入荷配送カテゴリに関する情報を提供します。

- [**tax_indicator.md**](type/tax_indicator.md)

  - 税金インジケーターについて記載されています。

- [**express_type.md**](type/express_type.md)

  - エクスプレス配送のタイプについて記載されています。

- [**transaction_type.md**](type/transaction_type.md)

  - 取引タイプに関する情報を提供します。

- [**inventory_summary_layer.md**](type/inventory_summary_layer.md)

  - 在庫サマリレイヤーについて記載されています。

## リンクについて

ファイル間リンクや外部リンクは以下の通り修正されています：

- `/developer/documents/*` へのリンクは該当するMarkdownファイルへの相対リンクに変更。
- その他のリンクはLogilessの公式URLに変更。

## 使用方法

1. このリポジトリをクローンします。

   ```bash
   git clone https://github.com/solahsoyalp/LOGILESS_API_Unofficial_Docs.git
   ```

2. 各Markdownファイルを開き、必要な情報を確認してください。

## 貢献

ドキュメントの修正や改善案がある場合、Pull Requestを歓迎します。

## 著作権および免責

このファイルは公式APIドキュメント（<https://app2.logiless.com/developer/>）をMarkdown形式にまとめたものです。著作権は全て株式会社ロジレスに帰属します。
