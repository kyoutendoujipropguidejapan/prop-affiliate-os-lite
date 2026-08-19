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

重要更新：M07 / M14 / M15 JSON / M15 Schema / M16 / M13の優先6 Artifactはすべてこのセッションで実体確認済み。M13↔M16 cross-checkも完了した。

---

## 1. 実体確認済みArtifact

### M07

回収PDF 24ページ。本文・安全条件PASS。

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

回収PDF 18ページ。

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

### M16 Runtime Snapshot仕様

回収PDF 12ページ。`docs/M16_VERIFIED_EXTRACTION_FROM_PDF.md` に検証済み抽出。

大原則PASS：

- Excel Master = 上位正本
- Runtime Snapshot = human-approved配布層
- Work / Replitへread-only片方向
- APPROVED + human_approved=trueのみ本番利用
- rollback / supersedes / hash
- Fintokei / HOLD 5件保護
- commercial dataを診断採点へ混ぜない

ただしSchema/contractに内部不整合がありPASS_WITH_CAUTION。

### M13 GitHub Master/Artifact同期設計

回収PDF 20ページ。`docs/M13_VERIFIED_EXTRACTION_FROM_PDF.md` に検証済み抽出。

大原則PASS：

- Excel Master = Layer A Business Canonical
- GitHub approved snapshot = Layer B Runtime Canonical
- Workはread-only
- Work→GitHub Canonical逆流禁止
- GitHub→本番自動公開禁止
- 監視→Master自動反映禁止
- stable IDs / effective period / Source Priority / Evidence / structured human approval
- M08 QAと公開承認を分離

M13↔M16の実装契約差は `docs/M13_M16_CROSSCHECK.md` に固定した。

---

## 2. 絶対保護条件

### Fintokei｜速攻プロ

Variant単位でのみ扱う。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- legacy account separation required
- Evidence required
- human approval required

購入日・旧口座・scopeを安全に区別できない場合はTop3 Block継続。

### HOLD 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- human-only resolution
- auto unblock禁止
- Top3 Block継続
- FAQ schemaへ入れない
- 診断Top3根拠へ使わない

### Diagnosis

- DiagnosisLogicV2を不用意に変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

---

## 3. Work Gate

### Work監査：GO

`docs/WORK_DAY0_START_PROMPT.md` を入口にする。

最初のターンはコード変更禁止。確認対象：

1. 未公開Work作業版の現在状態
2. 本番Version 78との差分
3. Master v2.2との差分
4. M07 P0-01〜P0-13の反映状況
5. M14 UPDATE_REQUIRED 10件の反映状況
6. HOLD 5件 / Fintokei Variant
7. GA4既存イベントとの重複
8. 390px / UX / SEO / Official-Affiliate分離

**M13/M16 Runtime層はDay0/P0で新規実装しない。** Runtime path/contract未決定を理由に既存Master/Workを推測補完しない。

### P0実装：CONDITIONAL GO

GO昇格条件：

- Day0監査で差分を明示
- Master v2.2 / DiagnosisLogicV2 / SourceHealth保護を確認
- Fintokei VariantとHOLD 5件を現行Workで安全に表現可能
- 人間が実装開始を承認

### FAQ統合：CONDITIONAL GO

GO昇格条件：

- M11と現行WorkのQ IDを照合
- UPDATE_REQUIRED 10件だけ差し替える
- PASS_WITH_CAUTIONの再確認条件を維持
- HOLD 5件をschema化しない
- Fintokei速攻プロ限定Variant FAQをschema化しない

---

## 4. 監視Dry Run Gate

現時点：**NO-GO**

JSON + Schemaの構造検証はPASSしたが、以下が未完了。

1. `sourcehealth_ids` のCanonical mapping contract
2. Preflight全PASS
3. HTTP/Baseline/failure handlingの実装確認
4. 人間がACTIVE化を明示承認

代表的ID差：

- `SH_FINTOKEI_SWIFT` ↔ `SH001`
- `SH_HANTEC_INSTANT_LITE` ↔ `SH003`
- `SH_FTM_INSTANT_PRO` ↔ `SH012`
- `SH_THE5ERS_FUTURES_LOCALE` ↔ `SH008`

`DRAFT_NOT_ACTIVE` のままでは監視開始しない。

---

## 5. Runtime Snapshot Gate

現時点：**NO-GO**

M13/M16大原則は一致するが、実装契約を確定する必要がある。

### R01｜唯一のLayer B path

M13は `data/canonical/*`、M16は `runtime/*` を提案。二重Canonicalは禁止。唯一のstable pathを決める。

### R02｜Variant contract

M13は `variant_id + scope + effective period` をfirst-classで扱う。M16 plan Schemaにはvariant_idがなく、Fintokei例のvariant objectともSchema不整合。vNextで解消する。

### R03｜Human approval

M13は承認者・承認時刻・scopeを含むstructured approvalを要求。M16のBoolean中心契約を強化する。

### R04｜Provenance

M13の `source_priority + source_evidence_ids` を条件値のprovenanceとして維持する。M16 `source_refs` のみで弱めない。

### R05｜SourceHealth→Diagnosis

CanonicalではVariant/scope/approvalからdiagnosis policyを派生。`top3_blocked`は必要ならRuntime派生値として使うが、唯一の正本判断にしない。

### R06｜Monitor execution gate

Snapshot APPROVEDとMonitor ACTIVEを別承認にする。M15 `DRAFT_NOT_ACTIVE` を勝手にACTIVE化しない。

### R07｜SourceHealth ID mapping

logical tag ↔ Master Canonical ID mappingを明示する。

### R08｜source_refs hardening

確定値のprovenanceが空にならないようValidation/Schema vNextで強制する。

Runtime実装開始条件：

- R01〜R08のcontract decision確定
- Runtime実JSON / Schemaを新versionで生成
- M13/M16/M15安全条件をすべて保持
- 全Preflight PASS
- manifest APPROVED + structured human approval
- 人間承認

---

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

---

## 7. 明日の最短経路

1. Work復活確認
2. `docs/WORK_DAY0_START_PROMPT.md` を投入
3. コード変更なしでDay0監査
4. ChatGPT側で監査結果を照合
5. P0実装 GO / CONDITIONAL GO / NO-GO判定
6. 承認後、M07 P0差分実装
7. M14 FAQ差し替え
8. 必要なSEO統合
9. M08 Full Regression
10. 390px fresh render
11. Go / No-Go
12. 公開は別承認

Runtime Snapshot / MonitoringはこのWork P0ルートから分離し、未解決contractを抱えたまま混ぜない。
