# ARTIFACT_SYNC_STATUS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：回収ArtifactとGitHub Canonical候補の同期状態を一意にする。

## 現在状態

**優先6 Artifactすべて実体確認完了。M15 JSON/Schemaは元ArtifactをGitHub同期済み。M07/M14/M16/M13は回収PDFを全文確認し、必要な検証済み抽出をGitHubへ保存済み。**

元Markdown Artifactが存在するものについて、回収PDF由来の抽出を元Artifactそのものと混同しない。

## P0

### M07｜最終統合仕様

- 受領：PDF 24ページ
- 状態：`INGESTED_VERIFIED_ORIGINAL_MARKDOWN_NOT_SYNCED`
- 内容確認：PASS
- 安全条件：PASS
- Source SHA-256：`bbd606616fd0c06de2ef3241b5b909e77e7834c600a0fa6764064c4809f5fa24`
- P0 = 13項目
- Fintokei Variant / HOLD 5件保護確認済み

### M14｜14社FAQ最終チェック

- 受領：PDF 18ページ
- 状態：`INGESTED_VERIFIED_DERIVATIVE_SYNCED_ORIGINAL_MARKDOWN_NOT_SYNCED`
- Source SHA-256：`f2c05035952f8ec38033ff31eecf89b324000462c2e9a85e99d00b8b437e648d`
- PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5
- 検証済み実装用抽出：`docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`

## P1

### M15｜monitor_sources.json

- 状態：`INGESTED_VERIFIED_SYNCED_DRAFT`
- GitHub：`monitoring/monitor_sources.json`
- Source SHA-256：`c481efa8997694971e52350d1ff4e9a3c620ad002d3d19faef5b2afe57efc8fc`
- Git blob SHA：`ec92a4798dd8cccd06dd4dff199fbda1fd9441a7`
- Primary 5 / Shadow 4 / 9 URL：PASS
- M12 URL一致：PASS
- `DRAFT_NOT_ACTIVE`：PASS
- Fintokei Variant保護：PASS
- 自動反映禁止：PASS

### M15｜monitor_sources.schema.json

- 状態：`INGESTED_VERIFIED_SYNCED_DRAFT`
- GitHub：`schemas/monitor_sources.schema.json`
- Source SHA-256：`203771945744817cda6a461c588038646f1b83ef1245dec4ca3e1f4b95b5ad5f`
- Git blob SHA：`d5db16cb2006aff451aca11943405432f662ef6b`
- Draft 2020-12 Schema自己検証：PASS
- monitor_sources.json validation：PASS / error 0
- 検証記録：`docs/M15_SCHEMA_VALIDATION.md`
- Activation：NO-GO
- 残課題：SourceHealth ID mapping contract / Preflight / 人間承認

### M16｜Runtime Snapshot仕様

- 受領：PDF 12ページ
- 状態：`INGESTED_VERIFIED_DERIVATIVE_SYNCED_ORIGINAL_MARKDOWN_NOT_SYNCED`
- Source SHA-256：`cc8abf5b143ca2eb9ab6e3a504606a1022b30a8ec3d98826df05fcb7938b6141`
- 本文確認：PASS_WITH_CAUTION
- 検証済み実装用抽出：`docs/M16_VERIFIED_EXTRACTION_FROM_PDF.md`
- Runtime Snapshot実装：NO-GO

### M13｜GitHub Master/Artifact同期設計

- 受領：PDF 20ページ
- 状態：`INGESTED_VERIFIED_DERIVATIVE_SYNCED_ORIGINAL_MARKDOWN_NOT_SYNCED`
- Source SHA-256：`84ba35a65f7cfcbd3ce46d27f7d7542e1da8e8df2539f93bc4e45f8dc7828af9`
- 本文確認：PASS_WITH_CAUTION
- 検証済み実装用抽出：`docs/M13_VERIFIED_EXTRACTION_FROM_PDF.md`
- M13↔M16 cross-check：`docs/M13_M16_CROSSCHECK.md`
- 大原則は一致。ただしLayer B path、Variant model、human approval、provenance、SourceHealth→Diagnosis契約等に実装前reconciliationが必要。

## M13 ↔ M16で確定したこと

一致：

- Excel Masterが上位正本
- GitHub snapshotは承認済み配布層
- Work / Replitへread-only片方向
- 本番公開は別承認
- DiagnosisLogicV2を複製・変更しない
- Fintokei速攻プロは5保護条件が欠ければBlock
- HOLD 5件は自動解除しない

未決定：

- `data/canonical/*` と `runtime/*` のどちらを唯一のLayer B stable pathにするか
- `variant_id + scope` をRuntime Schemaへどう組み込むか
- structured human approval contract
- `source_priority + source_evidence_ids` とM16 `source_refs` の統合
- scope-aware diagnosis policyと派生 `top3_blocked` の役割分担
- Monitor execution approvalの独立Gate
- SourceHealth logical tag ↔ Canonical ID mapping

## 絶対保護

### Fintokei｜速攻プロ

- effective_from = 2026-07-15
- new purchase only
- legacy account separation
- Evidence
- human approval
- 条件判定不能ならBlock継続

### HOLD 5

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：human_only / auto_unblock=false / top3_blocked=true相当の安全状態を維持する。

## 現在のGate

- Work監査：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：NO-GO

詳細は `docs/IMPLEMENTATION_READINESS.md` を正とする。

## 次

1. Work復活後Day0監査
2. 未公開Work作業版とMaster v2.2 / M07 / M14の差分確認
3. P0 / FAQをGOへ昇格できるか判定
4. M08 QA後にのみ公開判断
5. M13/M16 Runtime reconciliationはWork P0とは分離して後続で確定
