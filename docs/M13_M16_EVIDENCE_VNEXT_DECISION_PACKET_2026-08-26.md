# M13/M16 × Evidence vNext Decision Packet

更新日：2026-08-26 JST
Status：HUMAN APPROVAL REQUIRED / NO PRODUCTION CHANGE

## 0. Purpose

旧M13/M16で未決定のRuntime Snapshot / Monitoring契約を、2026-08-25以降に成立したEvidence Phase1設計と衝突しない形へ統合する。

この文書は実装指示ではない。Production / internal Sites repository / Master / Diagnosis / GA4には変更を加えない。

## 1. 結論提案

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

新しい検証済みFactのGitHub側SSOT候補。

### Layer 2.5 — Existing Product Catalog Boundary

既存Excel Master / Production `app/master-data.json` 等は、現行Product Catalog / Diagnosis依存の運用Canonicalとして**移行完了まで保護継続**する。

Evidence Registryを作ったことだけを理由に既存Masterを即置換しない。

Canonical Factと既存Product Catalogが競合した場合：

`AUTO WRITE禁止 → reconciliation → human approval → minimal patch`

### Layer 3 — Runtime Distribution Snapshot

Path：`runtime/*`

`runtime/*`はCanonicalではない。

- approved Canonical Fact
- accepted current Product Catalog
- SourceHealth / diagnosis policy

から生成するread-only distribution artifactとする。

手編集禁止。RuntimeからCanonical / Masterへ逆流禁止。

## 2. M13/M16未決定事項の解決案

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

## 3. HOLD Policy

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

## 4. Runtime Snapshot Start Gate

Runtime vNext実装は以下をすべて満たすまで開始しない。

1. internal Git authentication recovered
2. Evidence Phase1 accepted commit remote reconciliation PASS
3. current Production baseline reconciliation PASS
4. Firm Detail foundationが安定
5. Canonical/Product Catalogの責務境界が本Decisionとして承認済み
6. Schema migration plan approved
7. protected Master / Diagnosisへの影響が明示されている

したがって、承認後も直ちにWorkでRuntime実装しない。

## 5. Monitoring Start Gate

Monitoring Dry RunはRuntime実装とは別Gate。

最低条件：

1. SourceHealth Canonical ID mapping確定
2. parser / source preflight PASS
3. change classification contract確定
4. human review queue確定
5. no auto canonical write
6. no auto production publish
7. user / central-command activation approval

## 6. Migration Principle

Evidence vNext導入時に既存Productionを大規模移行しない。

段階：

1. current Productionをそのまま保護
2. Evidence / Canonicalをshadow registryとして育成
3. conflict reconciliationを実案件で検証
4. Runtime Snapshotをread-only distributionとして生成
5. Firm単位で差分検証
6. 十分な実績後にProduct Catalog移行を別Decisionとして検討

## 7. Supabase Phase2 Boundary

SupabaseはCanonicalの自動上位化をしない。

Phase2開始条件は別既定値を維持：

- Evidence Packets >= 30
- Canonical Facts >= 20
- real conflict >= 1
- coupon ended history >= 1
- rule change >= 1
- major schema changeなし30日

開始時はGitHub Canonicalのmirror / query layerから入り、双方向自動writeは後続承認まで禁止。

## 8. Impact

このDecisionを承認しても即時のProduction変更は0。

効果：

- M13/M16二重Canonical問題を解消
- Evidence Phase1を無駄にしない
- Fintokei Variantを安全に表現
- HOLD解除の自動化を防止
- MonitoringとRuntimeを切り離す
- 将来Supabaseへ移りやすい

## 9. Human Decision Required

中央承認が必要なArchitecture Decision：

**提案A（推奨）**

`data/canonical/* = GitHub Canonical Fact Registry`

`runtime/* = generated read-only distribution snapshot`

既存Excel Master / Production Masterは移行完了までProduct Catalog運用Canonicalとして保護。

Monitoring activationはRuntime approvalから独立。

この提案を承認した場合、M13/M16 Runtime reconciliationを`DECIDED / IMPLEMENTATION DEFERRED`へ更新できる。

未承認の場合は現状どおり`NO-GO`維持。

Final Status：
`READY_FOR_HUMAN_ARCHITECTURE_APPROVAL`
