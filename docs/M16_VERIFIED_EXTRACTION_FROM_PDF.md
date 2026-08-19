# M16_VERIFIED_EXTRACTION_FROM_PDF

更新日：2026-08-20 JST
対象：`M16｜最小Runtime Snapshot仕様.pdf`
Source SHA-256：`cc8abf5b143ca2eb9ab6e3a504606a1022b30a8ec3d98826df05fcb7938b6141`
原文更新日：2026-08-17 JST
位置づけ：**元M16成果物そのものではなく、回収PDFをChatGPTが全文確認して作成した検証済み実装用抽出。** 元Artifactと同一扱いしない。

## 結論

M16は12ページ。Runtime Snapshot v0.1の最小構成、Repository Tree、manifest Draft、5種のデータ契約、Fintokei Variant、HOLD 5件、Validation Rules、Approval / Rollback Flow、Work / Replit読み込み順、Preflight、Excel Masterからの最小Field抽出を定義している。

全体方針はM13要約・M15安全条件・Master v2.2の運用方針と整合する。

- Excel Master = 編集・監査用の上位正本
- GitHub Runtime Snapshot = human-approvedされた配布層
- Work / Replitへread-onlyの片方向
- RuntimeからMaster / SourceHealth / DiagnosisLogicV2へ逆流させない
- Work / Replitが本番利用できるのは `status=APPROVED` かつ `human_approved=true` のSnapshotのみ
- Coupon / Price / Affiliate / Commissionを診断採点用Runtimeへ混ぜない
- M15 Monitor Sourceの実行状態とRuntime Snapshotの承認状態を混同しない

## 最小Runtime構成

```text
runtime/
├── manifest.json
├── firms.json
├── plans.json
├── diagnosis_candidates.json
├── source_health.json
└── monitor_sources.json
```

Schema契約案：

```text
schemas/
├── runtime-manifest.schema.json
├── firms.schema.json
├── plans.schema.json
├── diagnosis-candidates.schema.json
├── source-health.schema.json
└── monitor-sources-runtime.schema.json
```

旧Snapshotは `archive/runtime/<snapshot_version>/` へ不変保存する案。

## Manifest要点

Draft例は以下を持つ。

- `snapshot_version`
- `generated_at`
- `verified_at`
- `source_master_version`
- `source_master_hash`
- `human_approved`
- `status`
- `supersedes`
- `snapshot_contract_version`
- 各Runtime file path + sha256
- `runtime_read_policy = APPROVED_ONLY`
- `source_of_truth = Excel_Master`
- auto publish / auto Master / auto SourceHealth / auto Diagnosis update = false

`source_master_hash` が未確定のDraftは承認禁止。

## データ契約の役割

### firms.json

14社の安定識別子・表示基本情報。価格、割引、Coupon、Affiliate、Commissionは持たせない。

### plans.json

Plan / Rule / Source / 適用期間。Unknownを0 / false / 空文字で代用しない。確定値はsource_refsを持つ。

### diagnosis_candidates.json

DiagnosisLogicV2のコピーではなく、候補母集団・安全なBlock状態・出典参照のみ。採点式・重み・質問順は入れない。

### source_health.json

Conflict、確認状態、解除条件、安全Block境界。`auto_unblock_allowed=false` を基本とする。

### monitor_sources.json

M15全設定を無批判に複製せず、Runtime Workerに必要な最小メタデータだけを配布。診断採点には使用しない。

## Fintokei速攻プロ

M16は安全側で設計している。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- `legacy_account_separation_required = true`
- `evidence_required = true`
- `human_approved = true`
- `legacy_policy = BLOCK_UNLESS_SEPARATELY_VERIFIED`

購入日、新旧口座、EvidenceのいずれかをRuntimeで安全に評価できない場合：

- `eligible_for_diagnosis = false`
- `top3_blocked = true`

を維持する。

## HOLD 5件

- `funded7_one_phase`
- `funded7_instant`
- `ftm_instant_pro`
- `hantec_instant_lite`
- `fundedelite_flash_activation`

共通：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`

確定値として診断Top3、FAQ Schema、候補理由へ使用しない。

## Validation Rules

M16はV01〜V17を定義する。重要点：

- 全Schema PASS
- APPROVED + human_approved=true
- firm ID 14社整合
- plan_id重複なし / orphanなし
- candidate参照整合
- HOLD 5件がtop3_blocked=true
- HOLD 5件がhuman_only / auto_unblock=false
- Fintokei 5保護条件 + legacy分離
- Fintokei購入日判定不能ならTop3禁止
- diagnosis_candidatesにAffiliate / Commission / Coupon / Discount / Priceがない
- CONFIRMED / CURRENT確定値にsource_refsあり
- invalid / 外部不許可 / 未確認redirectなし
- supersedesで旧APPROVED Snapshot追跡可
- APPROVED以外をWork本番利用しない
- manifest hashと実体一致
- DiagnosisLogicV2の採点式・重み・質問順をRuntimeへ入れない

## Approval Flow

1. Excel Master対象SheetからField抽出
2. `source_master_version / source_master_hash / generated_at` 付与
3. Schema・14社・参照・SourceHealth・Block・Fintokei境界を検証
4. 人間がExcelとRuntime差分 / Evidence / verified_at確認
5. `human_approved=true / status=APPROVED`
6. GitHubへSnapshot一式を同一commitで保存しhash確定
7. Work / Replitはそのcommit / snapshot versionを固定参照

Draft / ReviewedのままWorkへ渡さない。承認後に内容変更する場合は同Versionを上書きせず新Snapshotを作る。

## Rollback

- current version / commit / hash / manifest記録
- supersedesを辿り直前APPROVEDを選ぶ
- 旧Snapshotのhash / Schemaを再検証
- 旧不変commitへ参照先だけ戻す
- 理由・Version・実施者・時刻・影響範囲をAudit Log
- 旧Snapshot削除・上書き禁止

## Work / Replit読み込み順

1. 固定commit / snapshot version
2. manifest
3. APPROVED / human_approved / hash / contract確認
4. Schema + hash validation
5. firms
6. plans
7. source_healthを先に適用
8. diagnosis_candidates
9. monitor_sourcesは監視メタデータのみ
10. Preflight全PASS後にread-onlyで公開アプリへ渡す

## Excel Masterからの最小Field

### firms

`firm_id, firm_name, status, verified_at, effective_from, source_refs`

### plans

`firm_id, plan_id, plan_name, plan_status, program_type, profit_target, daily_loss, max_loss, dd_type, min_trading_days, payout, news_trading, weekend_holding, platforms, verified_at, effective_from, supersedes, source_refs`

### diagnosis_candidates

`candidate_id, plan_id, eligible_for_diagnosis, top3_blocked, block_reason, status, confidence, sourcehealth_refs, verified_at` + Fintokei Variant保護Field。

### source_health

`sourcehealth_id, firm_id, plan_id, field, status, conflict_summary, affected_values, source_refs, verified_at, effective_from, resolution_mode, human_approved, auto_unblock_allowed, top3_blocked`

### monitor_sources

M15から `source_id, firm_id, url, source_priority, watch_category, frequency, enabled, dry_run_group, human_review_required, auto_publish_allowed, sourcehealth_ids, parser_profile, activation_phase` のみ。

## 実装前に解消が必要な内部不整合 / Hardening候補

### R16-01｜Fintokei `variant` と diagnosis_candidates Schema

M16の `diagnosis_candidates.json` Schemaは `additionalProperties:false` だが、後段のFintokei具体例は `variant` オブジェクトを追加している。Schemaのpropertiesには `variant` が定義されていないため、**具体例をそのSchemaへそのまま投入するとSchema violationになる**。

Runtime実装前に、次のどちらかを新versionの契約として明示する必要がある。

- diagnosis candidate Schemaへ正式な`variant`定義を追加する
- Variantを別契約 / source_health / plans variantへ分離し、candidateはreferenceだけ持つ

元M16を改変しない。

### R16-02｜SourceHealth ID mapping

Fintokei例は `sourcehealth_refs:["SH_FINTOKEI_SWIFT"]`。M15もlogical labelを用いる一方、Master Canonical IDは `SH001` 等。

M15で検出した問題がM16でも継続している。Runtime実装前に、Canonical IDのみか、logical tag→Canonical mappingかを決める。

### R16-03｜Runtime monitor sourceの実行状態

M16は「M15のDRAFT_NOT_ACTIVEをACTIVEに変換して配布禁止」「Runtime APPROVEDでも監視実行は別承認」と明記しているが、Runtime用 `monitor_sources.json` Schema案は配列のみでtop-level `status=DRAFT_NOT_ACTIVE` を持たない。

したがって実装時には、Runtime Snapshot APPROVEDとMonitor execution approvalを別Gateで機械的に強制できるField / manifest policy / worker-side gateが必要。

### R16-04｜確定値source_refsのSchema強制

本文とV12は「CONFIRMED / CURRENT確定値にsource_refs 1件以上」を要求するが、plans Schema草案の `source_refs` 自体には `minItems:1` がない。

Validation layerでV12を必須実装するか、新Schema versionで条件制約を強化する。

## M13との照合状態

M16自身が、作成時点でM13設計書ファイルをGitHub treeから直接確認できず、PROGRESSに記録されたM13二層Canonical方針を前提にしたと明記している。

したがってM13全文を回収後、以下を最終cross-checkする。

- Excel Master / Runtimeの優先順位
- GitHub保存対象とprivate除外
- one-way sync
- versioning / supersedes / rollback
- public/sanitized data boundary

## Gate判定

M16本文自体：**PASS_WITH_CAUTION**。

仕様の安全思想は妥当だが、Runtime実装開始はまだNO-GO。

NO-GO理由：

1. M13全文との最終cross-check未完了
2. R16-01 Schema/example内部不整合
3. R16-02 SourceHealth ID mapping未確定
4. R16-03 Monitor execution gateの機械強制が未確定
5. Runtime実JSON / Schemaはまだ生成・承認されていない

M16原文の指示どおり、現段階では仕様のみであり、Runtime実体生成・Work/Replit反映・公開は行わない。
