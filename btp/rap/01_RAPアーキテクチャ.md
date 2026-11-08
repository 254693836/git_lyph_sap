# RAPアーキテクチャ

## RAPとは

SAP RAP（RESTful Application Programming Model）は、ABAPでトランザクションアプリケーションとODataサービスを開発するためのプログラミングモデルです。CDSを中心にデータモデル、業務ロジック、サービス公開、Fiori Elements UIを一貫して定義します。

## 主な構成要素

| レイヤー | 役割 | 主なオブジェクト |
| --- | --- | --- |
| データモデル | 業務データと関連を表現 | CDS View Entity、Association、Composition |
| ビジネスオブジェクト | 更新可能な単位を定義 | Behavior Definition、Behavior Implementation |
| サービス | 外部公開範囲を定義 | Service Definition、Service Binding |
| UI | 標準UIを構成 | UIアノテーション、Fiori Elements |

## 処理の流れ

```text
Fiori Elements / API Client
        ↓ OData V4
Service Binding
        ↓
Service Definition（公開するエンティティ）
        ↓
Projection Behavior
        ↓
Interface Behavior / Behavior Implementation
        ↓
CDS View Entity → 永続化テーブル
```

## Managed と Unmanaged

| 観点 | Managed RAP | Unmanaged RAP |
| --- | --- | --- |
| CRUD処理 | RAPフレームワークが標準処理を提供 | 開発者が実装 |
| 適した場面 | 新規開発、標準テーブルへのCRUD | 既存BAPI・独自保存処理の再利用 |
| 実装量 | 少ない | 多い |
| 学習開始 | 推奨 | Managed理解後に推奨 |

## 開発時の基本順序

1. Interface CDS View Entityでルート／子エンティティを定義する。
2. Behavior Definitionで更新操作とDraftの有無を定義する。
3. 必要に応じてBehavior ImplementationにAction、Determination、Validationを実装する。
4. Projection ViewとProjection Behaviorで公開範囲を絞る。
5. Service DefinitionとOData V4 Service Bindingを作成する。
6. UIアノテーションを追加し、Fiori Elementsで確認する。

## 設計上のポイント

- ルートエンティティは業務オブジェクトのライフサイクルを管理します。
- 子エンティティはCompositionでルートに結び付けます。
- Interface層は内部モデル、Projection層はサービス公開用として責務を分離します。
- 画面制御ではなく、Behaviorで業務ルールを守る設計を基本とします。
