# M13/M16 × Evidence vNext Decision Packet

更新日：2026-08-26 JST
Status：APPROVED / IMPLEMENTATION DEFERRED / NO PRODUCTION CHANGE

## 0. Purpose

旧M13/M16で未決定のRuntime Snapshot / Monitoring契約を、2026-08-25以降に成立したEvidence Phase1設計と衝突しない形へ統合する。

この文書は実装指示ではない。Production / internal Sites repository / Master / Diagnosis / GA4には変更を加えない。

2026-08-26、中央承認により提案Aを正式採用した。

全Factの検証には `docs/FACT_CHECK_STANDARD_V1_2026-08-26.md` を必須適用する。新規Fact・変更Fact・Canonical昇格・HOLD解除は最低3回のファクトチェックを通過しなければならない。

## 1. Approved Architecture Decision

M13の意味契約を維持しつつ、M16の`runtime/*`をCanonicalではなく**生成済み配布Snapshot**へ降格する。

二重正本を作らない。

### Layer 0 — Raw Evidence

- 公式ページsnapshot
- 公式PDF / screenshot
- direct-contact原文
- timestamp / hash

原則 immutable。PII / credentialは公開GitHubへ入れない。

### Layer 1 — Evidence Registry

Path：`data/evidence/*`

- Evidence Packet
- source metadata
- provenance
- conflict history

AIはPacket作成補助可。ただしCanonical昇格は自動化しない。

### Layer 2 — Canonical Fact Registry

Path：`data/canonical/*`

- human-approved Canonical Fact
- current / stale / superseded / ended / conflict
- variant / scope / effective period
- evidence links
- structured approval
- fact-check record

新しい検証済みFactのGitHub側SSOT候補。

Canonical昇格には最低3回のファクトチェックを要求する。

### Layer 2.5 — Existing Product Catalog Boundary

既存Excel Master / Production `app/master-data.json` 等は、現行Product Catalog / Diagnosis依存の運用Canonicalとして**移行完了まで保護継続**する。

Evidence Registryを作ったことだけを理由に既存Masterを即置換しない。

Canonical Factと既存Product Catalogが競合した場合：

`AUTO WRITE禁止 → reconciliation → minimum 3 fact checks → human approval → minimal patch`

### Layer 3 — Runtime Distribution Snapshot

Path：`runtime/*`

`runtime/*`はCanonicalではない。

- approved Canonical Fact
- accepted current Product Catalog
- SourceHealth / diagnosis policy

から生成するread-only distribution artifactとする。

手編集禁止。RuntimeからCanonical / Masterへ逆流禁止。

## 2. M13/M16未決定事項のDecision

### C01 Path

- Canonical：`data/canonical/*`
- Distribution：`runtime/*`

責務を分離し、同一値を2つのCanonicalとして扱わない。

### C02 Variant

`variant_id`をfirst-classとする。

最低Field：

- `plan_id`
- `variant_id`
- `scope`
- `effective_from`
- `effective_to`
- `legacy_of` / `supersedes`

Diagnosis CandidateはVariant詳細を複製せずreferenceする。

Fintokei速攻プロのcurrent / legacy分離はこの契約を使用する。

### C03 Human Approval

Boolean単体は禁止。

Canonical Approval Object：

```json
{
  "status": "APPROVED",
  "approved_by": "human",
  "approved_at": "ISO-8601",
  "approval_scope": "fact|variant|release",
  "approval_note": "..."
}
```

`human_approved=true` が必要なRuntimeでは上記から派生可。

### C04 Provenance

Canonical Factの確定値には最低：

- `source_evidence_ids`
- `source_priority`
- `verified_at`
- `fact_check_count >= 3`
- check results / checked_at

を要求する。

`source_refs` / URLは補助表示であり、provenanceの唯一根拠にしない。

### C05 SourceHealth → Diagnosis

Canonical判断はscope-aware policyから導出する。

`top3_blocked` はRuntime上の派生cacheとして保持可。ただし唯一の正本判断にしない。

例：

- VERIFIED current scope → candidate可能
- CONDITIONAL scope判定不能 → block
- CONFLICT → block
- HOLD → block
- legacy/current混在 → block

### C06 Monitoring Execution Gate

Snapshot approvalとMonitor実行承認を完全分離する。

`monitoring/monitor_sources.json` は引き続き `DRAFT_NOT_ACTIVE`。

別のexecution gateを持つまでCron / active polling / auto publishは禁止。

最低Policy：

- `monitor_execution_status = DISABLED`
- `human_activation_required = true`
- `auto_publish_allowed = false`
- `auto_canonical_write_allowed = false`

### C07 File format

- Evidence / Canonical / Runtime machine contract：JSON優先
- human-readable design / audit：Markdown
- CSV/YAMLは既存正本との互換や大量表形式で明確な利点がある場合のみ

形式乱立よりschema validationを優先する。

### C08 SourceHealth ID

Canonical IDを一意にする。

Primary：`SH001`等のCanonical ID

`SH_FINTOKEI_SWIFT`等のlogical labelはaliasのみ。

例：

```json
{
  "sourcehealth_id": "SH001",
  "aliases": ["SH_FINTOKEI_SWIFT"]
}
```

Runtime / Evidence / Monitoring間の参照はCanonical IDを使用する。

## 3. Minimum Three Fact-Check Rule

本Architectureに入るFactは `FACT_CHECK_STANDARD_V1_2026-08-26.md` を満たすこと。

最低：

1. Primary Source Verification
2. Independent Reconciliation
3. Pre-Publication / Pre-Implementation Fresh Recheck

重要：3回確認は「3つの検索結果を集める」ことではない。一次情報を優先し、同一ページの単純再読だけを独立Checkと数えない。

高リスクFactで独立一次根拠が不足する場合は`SINGLE_SOURCE_LIMITATION`を残し、完全VERIFIEDへ上げない。

Material Conflictが1件でも残る場合は多数決せず、`CONFLICT` / `HOLD`を維持する。

## 4. HOLD Policy

HOLD解除は自動化しない。

現行確認対象：

- Funded7 One Phase
- Funded7 Instant
- FTM Instant Pro
- FundedElite Flash Activation

Hantec Instant Liteは旧M14 HOLDだが、後続Block Reviewで`RESOLVED_FOR_PATCH`候補になっているため、current Production reconciliationで最終確認する。

HOLD / CONFLICT：

- FAQ schemaへ自動昇格しない
- Diagnosis Top3根拠へ使わない
- AI単独でVerified化しない
- human-only release
- minimum 3 fact checks required

HOLD解除には3回チェックに加え、元Conflict説明・Variant/cohort/locale差確認・Evidence/SourceHealth更新案・human approvalを要求する。

## 5. Runtime Snapshot Start Gate

Runtime vNext実装は以下をすべて満たすまで開始しない。

1. internal Git authentication recovered
2. Evidence Phase1 accepted commit remote reconciliation PASS
3. current Production baseline reconciliation PASS
4. Firm Detail foundationが安定
5. Canonical/Product Catalogの責務境界が本Decisionとして承認済み
6. Schema migration plan approved
7. protected Master / Diagnosisへの影響が明示されている
8. 対象Factがminimum 3 fact checks PASS

したがって、承認後も直ちにWorkでRuntime実装しない。

## 6. Monitoring Start Gate

Monitoring Dry RunはRuntime実装とは別Gate。

最低条件：

1. SourceHealth Canonical ID mapping確定
2. parser / source preflight PASS
3. change classification contract確定
4. human review queue確定
5. no auto canonical write
6. no auto production publish
7. user / central-command activation approval
8. monitored fact publication pathにminimum 3 fact-check gate実装

## 7. Migration Principle

Evidence vNext導入時に既存Productionを大規模移行しない。

段階：

1. current Productionをそのまま保護
2. Evidence / Canonicalをshadow registryとして育成
3. conflict reconciliationを実案件で検証
4. Runtime Snapshotをread-only distributionとして生成
5. Firm単位で差分検証
6. 十分な実績後にProduct Catalog移行を別Decisionとして検討

## 8. Supabase Phase2 Boundary

SupabaseはCanonicalの自動上位化をしない。

Phase2開始条件は別既定値を維持：

- Evidence Packets >= 30
- Canonical Facts >= 20
- real conflict >= 1
- coupon ended history >= 1
- rule change >= 1
- major schema changeなし30日

開始時はGitHub Canonicalのmirror / query layerから入り、双方向自動writeは後続承認まで禁止。

## 9. Impact

このDecision承認による即時Production変更は0。

効果：

- M13/M16二重Canonical問題を解消
- Evidence Phase1を無駄にしない
- Fintokei Variantを安全に表現
- HOLD解除の自動化を防止
- MonitoringとRuntimeを切り離す
- 将来Supabaseへ移りやすい
- 全重要Factに最低3回の検証Gateを適用

## 10. Decision

2026-08-26 中央承認：**提案Aを正式採用**。

確定：

`data/canonical/* = GitHub Canonical Fact Registry`

`runtime/* = generated read-only distribution snapshot`

既存Excel Master / Production Masterは移行完了までProduct Catalog運用Canonicalとして保護。

Monitoring activationはRuntime approvalから独立。

Runtime実装はStart Gateを満たすまで延期する。

Final Status：
`DECIDED / IMPLEMENTATION DEFERRED / MINIMUM_THREE_FACT_CHECKS_REQUIRED`
