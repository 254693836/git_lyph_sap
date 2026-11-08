# Determination

## 役割

Determinationは、作成・更新・保存のタイミングで項目値を自動設定する仕組みです。初期ステータス設定、金額再計算、関連項目の補完などに利用します。

## 実行タイミング

| タイミング | 用途 | 例 |
| --- | --- | --- |
| `on modify` | ユーザー編集に応じて即時に値を導出 | 作成時の初期ステータス |
| `on save` | 保存直前に整合性のある値を確定 | 集計値・最終更新情報 |

## BDEFでの宣言

```abap
determination setInitialStatus on modify { create; }
determination recalculateTotal on modify
  { field BookingFee, TotalPrice; }
```

## 実装イメージ

```abap
METHOD setInitialStatus.
  READ ENTITIES OF zi_travel IN LOCAL MODE
    ENTITY Travel
    FIELDS ( OverallStatus )
    WITH CORRESPONDING #( keys )
    RESULT DATA(travels).

  MODIFY ENTITIES OF zi_travel IN LOCAL MODE
    ENTITY Travel
    UPDATE FIELDS ( OverallStatus )
    WITH VALUE #(
      FOR travel IN travels
      WHERE ( OverallStatus IS INITIAL )
      ( %tky = travel-%tky
        OverallStatus = 'O' ) ).
ENDMETHOD.
```

## 実装時の注意

- 対象フィールドが変更されるたびに不要な再計算をしないよう、トリガー項目を限定します。
- Determination内で同じトリガーを再更新すると、再実行や循環が起こる場合があります。
- 画面表示専用の値は、必要に応じてCDSの計算項目や仮想要素も検討します。
- 業務ルール違反の判定はDeterminationではなくValidationに分けます。

## テスト観点

- 新規作成時に初期値が設定されること。
- 関連項目の更新後に派生値が正しく更新されること。
- 明示入力された値を意図せず上書きしないこと。
