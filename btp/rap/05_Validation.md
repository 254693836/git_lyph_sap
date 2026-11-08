# Validation

## 役割

Validationは、保存を許可してよいかを業務ルールに基づいて判定します。エラーがある場合は `failed` と `reported` を設定し、保存を止めて利用者にメッセージを返します。

## BDEFでの宣言

```abap
validation validateDates on save
  { create; update; field BeginDate, EndDate; }
```

## 実装イメージ

```abap
METHOD validateDates.
  READ ENTITIES OF zi_travel IN LOCAL MODE
    ENTITY Travel
    FIELDS ( BeginDate EndDate )
    WITH CORRESPONDING #( keys )
    RESULT DATA(travels).

  LOOP AT travels INTO DATA(travel).
    IF travel-EndDate < travel-BeginDate.
      APPEND VALUE #( %tky = travel-%tky ) TO failed-travel.
      APPEND VALUE #(
        %tky = travel-%tky
        %msg = new_message(
          id       = 'ZTRAVEL'
          number   = '001'
          severity = if_abap_behv_message=>severity-error )
        %element-EndDate = if_abap_behv=>mk-on ) TO reported-travel.
    ENDIF.
  ENDLOOP.
ENDMETHOD.
```

## ValidationとDeterminationの使い分け

| 処理 | 選択 |
| --- | --- |
| 初期値を補完する | Determination |
| 合計金額を計算する | Determination |
| 開始日より終了日が前か確認する | Validation |
| 必須項目が未入力か確認する | Validation |
| 権限があるか判定する | Authorization |

## 設計上の注意

- メッセージは、どの項目を修正すべきか分かるように対象要素を指定します。
- 複数エラーをまとめて返せるため、最初のエラーだけで処理を終えない設計を検討します。
- UIだけの入力チェックに依存せず、Behavior層で必ず業務ルールを保証します。
