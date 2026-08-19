# ARTIFACT_SYNC_STATUS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：回収ArtifactとGitHub Canonical候補の同期状態を一意にする。

## 現在状態

**P0本文確認完了 + M15 JSON/Schema同期完了 + M16本文確認完了。残りはM13全文確認。**

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
- 元M14 Artifactと抽出を混同しない

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
- Excel Master = 上位正本 / Runtime = APPROVED配布層 / Work・Replitへ片方向：PASS
- APPROVED + human_approvedのみ本番読込：PASS
- Fintokei Variant / HOLD 5件保護：PASS
- Affiliate / Commission / Coupon / Priceの診断採点混入禁止：PASS
- 個別Schema JSONは元Artifactとして存在しない。仕様書内Schema草案のみ。
- 実装前課題：
  - diagnosis candidate Schemaに`variant`が未定義なのにFintokei例が`variant`を持つ
  - SourceHealth logical label ↔ Master Canonical ID mapping未確定
  - Runtime APPROVEDとMonitor実行承認を機械的に分離するGate未確定
  - plansの確定値`source_refs>=1`は本文/Validationでは要求するがSchema単体では未強制
- Runtime Snapshot実装：NO-GO

### M13｜GitHub Master/Artifact同期設計

- 状態：`USER_REPORTED_ATTACHED_PENDING_INGEST`

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

共通：human_only / auto_unblock=false / top3_blocked=true。

## 現在のGate

- Work監査：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：NO-GO

詳細は `docs/IMPLEMENTATION_READINESS.md` を正とする。

## 次

1. M13本文確認
2. M13 ↔ M16最終cross-check
3. Work復活後Day0監査
4. P0 / FAQをGOへ昇格できるか判定
5. M08 QA後にのみ公開判断
