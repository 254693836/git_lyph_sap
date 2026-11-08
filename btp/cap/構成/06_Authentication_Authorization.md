# 認証・認可

## 基本概念

CAPでは、認証により利用者を識別し、認可によりサービス・Entity・操作へのアクセスを制御します。本番環境では通常、SAP BTPのXSUAAまたはIdentity Authenticationを利用します。

## CDSでの認可例

```cds
@requires: 'authenticated-user'
service CatalogService {
  @restrict: [
    { grant: 'READ', to: 'Viewer' },
    { grant: '*',    to: 'Admin'  }
  ]
  entity Orders as projection on db.Orders;
}
```

## 代表的なロール設計

| ロール | 例 |
| --- | --- |
| Viewer | データ参照のみ |
| SalesClerk | 注文の作成・更新 |
| Approver | 承認Actionの実行 |
| Admin | 管理操作・全権限 |

## 実装上の注意

- ロールは業務責務で分け、個人や画面単位で増やしすぎないようにします。
- 認可はUI非表示だけでなく、サービス側の `@restrict` で強制します。
- Actionにも対象ロールを設定し、状態遷移を保護します。
- ローカル開発用のモックユーザー設定と、本番のIdentity Provider設定を分けます。

## 確認項目

- 未認証アクセスが拒否されること。
- Viewerが更新できないこと。
- 権限を持つ利用者のみActionを実行できること。
- テナントや組織ごとのデータ分離が必要な場合、その条件がクエリへ反映されること。
