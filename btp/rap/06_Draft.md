# Draft

## Draftとは

Draftは、利用者が編集中のデータを本データ（Active）とは分けて保持する仕組みです。Fiori ElementsのObject Pageで編集・保存・取消を自然に扱うために利用します。

## 状態遷移

```text
Active ── Edit ──> Draft
  ↑                   │
  └── Activate <──────┘
        │
        └── Discard（Draftを破棄してActiveへ戻る）
```

## BDEFの例

```abap
with draft;

define behavior for ZI_TRAVEL alias Travel
persistent table ztravel
draft table ztravel_d
lock master
total etag LastChangedAt
{
  create;
  update;
  delete;
  association _Booking { create; }

  draft action Edit;
  draft action Activate;
  draft action Discard;
  draft action Resume;
  draft determine action Prepare;
}
```

## 用語

| 用語 | 説明 |
| --- | --- |
| Active | 確定済みの業務データ |
| Draft | 編集途中の一時データ |
| ETag | 同時更新を検出するためのバージョン情報 |
| Lock | 同一データの同時編集を制御する仕組み |
| Prepare | 編集開始時などに必要なDeterminationやValidationを実行するAction |

## 設計時の注意

- ルートと子はCompositionで構成し、Draftも一貫した単位で扱います。
- Draftテーブルと永続化テーブルの項目差分を管理します。
- 編集開始からActivateまでの間に他者が更新した場合を想定し、ETagとロックを設定します。
- Draftを使わない単純な即時更新と、長時間編集が必要な業務を区別します。
