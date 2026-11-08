# Event Handlers

## 役割

Node.jsのイベントハンドラには、標準CRUDに対する補正・検証、Actionの実装、外部サービス呼び出しなどを記述します。通常は `srv/catalog-service.js` に実装します。

## ハンドラの種類

| ハンドラ | 用途 |
| --- | --- |
| `before` | 入力検証、初期値設定、値の正規化 |
| `on` | 標準処理の置換、独自Actionの実装 |
| `after` | 応答値の補完・整形 |
| `srv.on('served')` | 起動後の初期化処理 |

## 実装例

```js
const cds = require('@sap/cds')

module.exports = cds.service.impl(function () {
  const { Orders } = this.entities

  this.before(['CREATE', 'UPDATE'], Orders, req => {
    if (req.data.status) req.data.status = req.data.status.toUpperCase()
  })

  this.on('submitOrder', async req => {
    const tx = cds.tx(req)
    const order = await tx.run(
      SELECT.one.from(Orders).where({ ID: req.data.orderID })
    )
    if (!order) return req.reject(404, '注文が見つかりません')

    await tx.run(
      UPDATE(Orders).set({ status: 'SUBMITTED' }).where({ ID: order.ID })
    )
    return tx.run(SELECT.one.from(Orders).where({ ID: order.ID }))
  })
})
```

## 実装時の原則

- 標準CRUDを使える処理は、独自の `on('CREATE')` に置き換えません。
- DB更新は `cds.tx(req)` を使い、リクエストと同じトランザクションで実行します。
- Actionでは対象データの存在確認、状態遷移、認可、エラー応答を明示します。
- 外部通信はタイムアウト・失敗時の扱いを決めてから実装します。
