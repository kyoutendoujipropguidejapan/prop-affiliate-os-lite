# IMPLEMENTATION_READINESS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：Work復活前後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work監査開始：**GO**
- M07 P0実装開始：**CONDITIONAL GO**
- M14 FAQ統合：**CONDITIONAL GO**
- 監視Dry Run開始：**NO-GO**
- Runtime Snapshot実装：**NO-GO**
- 本番公開：**NO-GO**

## 1. 実体確認済みArtifact

### M07

回収PDF 24ページを全文確認済み。

- P0 = 13項目
- 最初はP0-01〜P0-03
- DiagnosisLogicV2不変
- Affiliate / commission / coupon / priceを診断採点に使わない
- Official CTA / Affiliate CTA分離
- 14社一覧で65プラン詳細を初期展開しない
- 390px横スクロール禁止
- SourceHealth競合を自動解消しない
- 自動監視・Cron・通知はP0対象外
- Fresh render / M08 QAを公開前Exit Gateとする

### M14

回収PDF 18ページを全文確認済み。

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

UPDATE_REQUIRED 10件は `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md` に検証済み抽出。

### M15 monitor_sources.json

元Artifactを改変せず `monitoring/monitor_sources.json` へ同期済み。

- `DRAFT_NOT_ACTIVE`
- `not_started`
- Primary 5 / Shadow 4 = 9 URL
- M12 URLセット一致
- Fintokei Variant保護5条件あり
- Master / SourceHealth / Diagnosis / Work / siteの自動反映禁止
- auto publish / auto unblock禁止

### M15 monitor_sources.schema.json

元Artifactを改変せず `schemas/monitor_sources.schema.json` へ同期済み。

- JSON Schema draft 2020-12自己検証：PASS
- `monitor_sources.json` をSchema検証：PASS（0 error）
- 詳細：`docs/M15_SCHEMA_VALIDATION.md`

ただしSchemaは意味的整合を完全には強制しないため、監視開始はNO-GO。

### M16 Runtime Snapshot仕様

回収PDF 12ページを全文確認済み。検証済み抽出は `docs/M16_VERIFIED_EXTRACTION_FROM_PDF.md`。

確認PASS：

- Excel Master = 編集・監査用の上位正本
- Runtime Snapshot = human-approvedされた配布層
- Work / Replitへread-only片方向
- APPROVED + human_approved=trueのみ本番利用
- manifest hash / source_master_version / source_master_hash / supersedes / rollback
- Fintokei Variantの5保護条件
- HOLD 5件のhuman_only / auto_unblock=false / top3_blocked=true
- Affiliate / Commission / Coupon / Priceを診断採点Runtimeへ混ぜない
- DiagnosisLogicV2の採点式・重み・質問順をRuntimeへ複製しない
- M15 monitor source executionとRuntime Snapshot承認を同一視しない

ただし実装前に解消すべき内部不整合があるためM16本文判定はPASS_WITH_CAUTION。

## 2. 絶対保護条件

### Fintokei｜速攻プロ

Variant単位でのみ扱う。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- legacy account separation required
- Evidence required
- human approval required

購入日や旧口座を安全に区別できない場合はTop3 Block継続。

### HOLD 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`
- FAQ schemaへ入れない
- 診断Top3根拠へ使わない

### Diagnosis

- DiagnosisLogicV2を不用意に変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

## 3. Work Gate

### Work監査：GO

`docs/WORK_DAY0_START_PROMPT.md` を入口にする。

最初のターンはコード変更禁止。確認対象：

1. 未公開Work作業版の現在状態
2. Master v2.2との差分
3. M07 P0-01〜P0-13の反映状況
4. M14 UPDATE_REQUIRED 10件の反映状況
5. HOLD 5件 / Fintokei Variant
6. GA4既存イベントとの重複
7. 390px / UX / SEO / Official-Affiliate分離

### P0実装：CONDITIONAL GO

GO昇格条件：

- Day0監査で差分を明示
- Master v2.2 / DiagnosisLogicV2 / SourceHealth保護を確認
- Fintokei VariantとHOLD 5件を表現可能
- 人間が実装開始を承認

### FAQ統合：CONDITIONAL GO

GO昇格条件：

- M11と現行WorkのQ IDを照合
- UPDATE_REQUIRED 10件だけ差し替える
- PASS_WITH_CAUTIONの再確認条件を維持
- HOLD 5件をschema化しない
- Fintokei速攻プロ限定Variant FAQをschema化しない

## 4. 監視Dry Run Gate

現時点：**NO-GO**

JSON + Schemaの構造検証はPASSしたが、以下が未完了。

1. `sourcehealth_ids` の契約確定
   - Canonical IDのみ許可するか
   - logical tagを許可してmappingするか
2. Preflight全PASS
3. HTTP/Baseline/failure handlingの実装確認
4. 人間がACTIVE化を明示承認

代表的なID差：

- `SH_FINTOKEI_SWIFT` ↔ Canonical `SH001`
- `SH_HANTEC_INSTANT_LITE` ↔ `SH003`
- `SH_FTM_INSTANT_PRO` ↔ `SH012`
- `SH_THE5ERS_FUTURES_LOCALE` ↔ `SH008`

`DRAFT_NOT_ACTIVE` のままでは監視開始しない。

## 5. Runtime Snapshot Gate

現時点：**NO-GO**

M16本文は確認済みだが、以下が未解消。

### R16-01｜diagnosis candidate Schema / Fintokei example

Schema草案は `additionalProperties:false` なのに、Fintokei具体例は未定義の `variant` を持つ。このままでは例がSchema violationになる。

### R16-02｜SourceHealth ID mapping

M16のFintokei例も `SH_FINTOKEI_SWIFT` を使う。M15と同じlogical label ↔ Master Canonical ID問題が残る。

### R16-03｜Monitor execution gate

M16本文はRuntime Snapshot APPROVEDとMonitor実行承認を分離すると定義するが、Runtime用monitor_sources Schema草案はtop-level `DRAFT_NOT_ACTIVE` を持たない。Worker側またはmanifest policyで明示的なexecution gateが必要。

### R16-04｜source_refs hardening

本文/V12はCONFIRMED/CURRENT確定値にsource_refs 1件以上を要求するが、plans Schema草案単体では `minItems:1` を強制していない。Validation layerまたは新Schema versionで強制する。

### R16-05｜M13全文cross-check

M16は作成時点でM13設計書実体を直接読めず、PROGRESSの二層Canonical要約を前提にしている。M13全文回収後に優先順位・保存境界・one-way sync・versioningを最終照合する。

Runtime実装開始条件：

- M13全文とのcross-check PASS
- R16-01〜04のcontract decisionを確定
- Runtime実JSON / Schemaを新versionとして生成
- 全V01〜V17 / Preflight PASS
- manifest APPROVED + human_approved=true
- 人間承認

## 6. 公開Gate

本番公開はM08完走までNO-GO。

必要条件：

- M08 Full Regression
- BLOCKER = 0
- CRITICAL = 0
- 390px fresh render
- DiagnosisLogicV2不変
- HOLD 5件Top3除外
- Fintokei Variant誤適用なし
- Official / Affiliate link分離
- GA4破損・二重発火なし
- 人間の明示公開承認

## 7. 次に確認するArtifact

1. M13｜`M13_github_master_artifact_sync_design.md`

M07 / M14 / M15 JSON / M15 Schema / M16はこのセッションで本文確認済み。
