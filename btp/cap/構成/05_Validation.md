# Validation

## 基本方針

入力検証は `before` ハンドラで実装し、問題があれば `req.reject()` で処理を止めます。UIの入力チェックだけに依存せず、APIから呼ばれた場合も同じルールを保証します。

## 項目検証の例

```js
this.before(['CREATE', 'UPDATE'], 'Orders', req => {
  const { orderDate, status } = req.data

  if (orderDate && new Date(orderDate) > new Date()) {
    return req.reject(400, '注文日は未来日にできません')
  }

  const allowed = ['OPEN', 'SUBMITTED', 'CANCELLED']
  if (status && !allowed.includes(status)) {
    return req.reject(400, 'ステータスが不正です')
  }
})
```

## 明細を含む検証の例

```js
this.before('CREATE', 'OrderItems', req => {
  if (req.data.quantity <= 0) {
    return req.reject(400, '数量は1以上で入力してください', 'quantity')
  }
  if (req.data.unitPrice < 0) {
    return req.reject(400, '単価は0以上で入力してください', 'unitPrice')
  }
})
```

## 検証観点

| 分類 | 例 |
| --- | --- |
| 必須 | 顧客、商品、数量が入力されている |
| 形式 | 日付、コード、桁数が正しい |
| 範囲 | 数量が正、金額が0以上 |
| 相関 | 終了日が開始日以降 |
| 状態遷移 | 確定済み注文を再確定しない |
| 参照整合性 | 親注文、商品マスタが存在する |

## テスト

正常系だけでなく、各エラー条件に対しHTTP 400と期待メッセージが返ることをテストします。エラーメッセージは利用者が修正できる内容にします。
