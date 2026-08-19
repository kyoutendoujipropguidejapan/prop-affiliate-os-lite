# M15_SCHEMA_VALIDATION

更新日：2026-08-19 JST
対象：`monitor_sources.json` / `monitor_sources.schema.json`
位置づけ：回収済みM15実Artifactの検証記録。元Artifactは改変しない。

## 結論

- JSON Schema draft 2020-12としてSchema自己検証：PASS
- `monitor_sources.json` を本Schemaで検証：PASS（validation error 0）
- JSON構文：PASS
- Source数：9件
- status：`DRAFT_NOT_ACTIVE`
- Primary 5 / Shadow 4：実JSON側で確認済み
- Fintokei Variant保護：実JSON側で確認済み
- 安全フラグ：実JSON側で確認済み

ただし、本SchemaはDraftとしては妥当だが、Activation前の意味的安全性まで完全には強制しない。よってDry Run開始はまだNO-GO。

## 元Artifact同一性

### Schema
- Source SHA-256：`203771945744817cda6a461c588038646f1b83ef1245dec4ca3e1f4b95b5ad5f`
- GitHub保存先：`schemas/monitor_sources.schema.json`
- Git blob SHA：`d5db16cb2006aff451aca11943405432f662ef6b`
- 元内容を改変せず同期

### Config
- Source SHA-256：`c481efa8997694971e52350d1ff4e9a3c620ad002d3d19faef5b2afe57efc8fc`
- GitHub保存先：`monitoring/monitor_sources.json`
- Git blob SHA：`ec92a4798dd8cccd06dd4dff199fbda1fd9441a7`

## Schemaが強制できている主要条件

- `status = DRAFT_NOT_ACTIVE`
- safety_policyの以下は常にfalse
  - master_auto_update_allowed
  - sourcehealth_auto_update_allowed
  - diagnosis_auto_update_allowed
  - work_auto_apply_allowed
  - site_auto_publish_allowed
- `conflict_resolution_default = human_only`
- source数は9件固定
- source_idはDR01〜DR09形式
- URLはhttps URI
- source_priorityはA1〜D1の許可値
- `human_review_required = true`
- `auto_publish_allowed = false`
- `sourcehealth_resolution_mode = human_only`
- `auto_unblock_allowed = false`
- Fintokei保護objectが存在する場合は、2026-07-15 / new purchase / legacy separation / evidence / human approval の5条件を固定

## Schemaだけでは強制していない条件

次は実JSON側では満たしているが、Schema単体では保証しない。

1. DR01〜DR09が重複なしで全件1つずつ存在すること
2. Primary 5 / Shadow 4の件数
3. Primaryはenabled=true、Shadowはenabled=false / phase_2であること
4. DR01に`variant_protection`が必須であること
5. Fintokei保護objectをDR01以外へ付けないこと
6. `sourcehealth_ids`がMaster Canonical SourceHealth IDを参照すること
7. `crosscheck_source_ids`が実在source_idを参照し、自己参照しないこと
8. top-level `activation_phase = not_started` を必須・固定すること
9. `config_id` / `schema_version` の期待値をconstで固定すること
10. `sourcehealth_resolution_requires_crosscheck` / `human_review_default` をSchemaで必須化すること
11. 自動Issue作成禁止を明示Fieldで強制すること
12. `source_id` / `crosscheck_source_ids` itemに明示的な`type: string`を持たせること
13. candidate_change_typesの許可セット・重複禁止

## SourceHealth IDの結論

Schemaの`sourcehealth_ids`は単なるstring arrayであり、Canonical ID形式を制約していない。

実JSONでは以下の意味ラベルが使われている。

- DR01：`SH_FINTOKEI_SWIFT`
- DR05/DR06：`SH_HANTEC_INSTANT_LITE`
- DR07：`SH_FTM_INSTANT_PRO`
- DR08/DR09：`SH_THE5ERS_FUTURES_LOCALE`

一方、現行Master Canonicalでは代表的にSH001 / SH003 / SH012 / SH008を使用している。

したがって、M15 Schema確認だけではこの差は解決しない。

Activation前に次のどちらかを明示契約する必要がある。

A. `sourcehealth_ids`はCanonical IDのみを許可する

または

B. 監視用logical tagを許可し、別mapping tableでCanonical IDへ解決する

元M15 Artifactは改変しない。修正する場合は新しいSchema/Config versionとして人間承認付きで作成する。

## Dry Run Gate

現時点：NO-GO

残条件：

1. SourceHealth ID mapping contract確定
2. Schema hardeningを行う場合は新versionとして作成・検証
3. Preflight全PASS
4. HTTP取得・Baseline保存先・failure handling確認
5. 人間によるACTIVE化明示承認

`DRAFT_NOT_ACTIVE`のままでは監視を開始しない。
