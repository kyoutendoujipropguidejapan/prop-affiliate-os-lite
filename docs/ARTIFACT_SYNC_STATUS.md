# ARTIFACT_SYNC_STATUS

更新日：2026-08-19 JST
対象：プロップファームの歩き方
目的：Manus側で回収できた既存成果物と、GitHub上で実体確認できる正本を混同しないための同期待ち台帳。

## 現在の結論

M01〜M16の回収・照合により、実装前優先度が高い6成果物はManus側で回収済み。

2026-08-19、M07とM14の元PDFはこのChatGPTセッションで全文読取・安全条件確認まで完了した。

**全体状態：P0_ARTIFACTS_INGESTED_VERIFIED_PENDING_ORIGINAL_SYNC**

## 6成果物の現在状態

### P0

1. M07｜`M07_integrated_work_implementation_spec.md`
   - 状態：**INGESTED_VERIFIED_NOT_SYNCED**
   - 受領実体：`M07｜M01〜M06統合・Work実装仕様確定.pdf` 24ページ
   - Source SHA-256：`bbd606616fd0c06de2ef3241b5b909e77e7834c600a0fa6764064c4809f5fa24`
   - 内容確認：PASS
   - 安全条件確認：PASS
   - GitHub原Artifact本文同期：未実施
2. M14｜`M14_firm_faq_primary_source_final_check.md`
   - 状態：**INGESTED_VERIFIED_DERIVATIVE_SYNCED_ORIGINAL_NOT_SYNCED**
   - 受領実体：`M14｜14社FAQの公式一次情報最終チェック.pdf` 18ページ
   - Source SHA-256：`f2c05035952f8ec38033ff31eecf89b324000462c2e9a85e99d00b8b437e648d`
   - 内容確認：PASS
   - 安全条件確認：PASS
   - 70 FAQ判定：PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5
   - GitHub検証済み抽出：`docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`
   - 注意：上記は元M14 Artifactそのものではなく、回収PDFから作成した検証済み実装用抽出
   - GitHub原Artifact本文同期：未実施

### P1

3. M15｜`monitor_sources.json`
   - 状態：USER_REPORTED_ATTACHED_PENDING_INGEST
4. M15｜`monitor_sources.schema.json`
   - 状態：USER_REPORTED_ATTACHED_PENDING_INGEST
5. M16｜`M16_minimum_runtime_snapshot_spec.md`
   - 状態：USER_REPORTED_ATTACHED_PENDING_INGEST
6. M13｜`M13_github_master_artifact_sync_design.md`
   - 状態：USER_REPORTED_ATTACHED_PENDING_INGEST

M16は仕様書内にSchema草案を含むが、個別Schema JSON実体は元Artifactとして回収されていない。存在しないSchemaを再生成して「回収Artifact」と扱わない。

## M07全文確認結果

M07は、Work復活後のP0実装仕様・受入条件・実装プロンプトを統合した24ページの文書で、以下を確認した。

- 本番Version 78は変更・公開しない
- M01〜M06の成果を作り直さず強化する方針
- P0は13項目（P0-01〜P0-13）
- 最初の実装単位はP0-01〜P0-03のデータ／SourceHealth整合
- `DiagnosisLogicV2` は変更しない
- Affiliate / commission / price / Couponを診断採点・Top3順位へ使わない
- 390pxで横スクロールを発生させない
- 14社一覧で65プラン詳細を初期展開しない
- Official CTAとAffiliate CTAを分離する
- 価格・CouponはHero／診断／主比較の主役にしない
- SourceHealth競合を自動解消しない
- 自動監視・Cron・通知はP0で実装しない
- Fresh render / regressionを公開前Exit Gateとする

### Fintokei｜速攻プロ

M07内で次を確認したため、安全条件はPASS。

- `purchase_date_start = 2026-07-15`
- `new_purchase_only = true`
- 旧口座を別Variantとして分離
- Evidence保持
- 人間承認
- 条件欠落時はBlock継続
- firm-levelの単純 `block=false` 禁止

### HOLD / Block継続 5件

M07は次の5件を `BLOCKED_SOURCE_CONFLICT` として固定Blockする。

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Top3へ出さず、競合を勝手に解消しない方針を確認済み。

### M07でWork実装時に再照合すべき点

M07にはGA4追加イベント案として `guide_start`、`next_preview_click`、`firm_plan_group_open`、`plan_detail_open`、`source_status_click`、`diagnosis_start`、`diagnosis_optional_open`、`diagnosis_complete`、`diagnosis_reason_open`、`official_cta_click` がある。

後続のMaster v2.2 / UXMeasurement / M08 / 現行Workで既存イベント命名が存在するため、**イベント名をM07だけで一括置換・二重追加しない**。既存GA4 ID・既存イベントを維持し、Day0監査で差分を確認してから実装する。

## M14全文確認結果

M14は14社・70 FAQを公式一次情報で最終照合した18ページの文書。

- PASS：32
- PASS_WITH_CAUTION：23
- UPDATE_REQUIRED：10
- HOLD：5

HOLD 5件はM07/M06と一致し、FAQ schema対象外・診断Top3根拠外。

Fintokei速攻プロも、2026-07-15以降の新規購入限定Variant、旧口座分離、Evidence、人間承認を維持する。

UPDATE_REQUIRED 10件は、回収PDFから `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md` へ実装用に検証済み抽出した。元Artifactそのものではないことを明示している。

主な差し替え対象：

- Fintokei Q2
- Funded7 Q5
- The5ers Q1/Q2
- SuperFunded Q3
- Blueberry Futures Q2/Q4
- Trading Cult Pro Q5
- Blueberry Funded Q2
- The5ers Futures Q3

## GitHub昇格条件

各Artifactは、次を満たした場合のみGitHub上の読める正本候補へ昇格する。

1. このセッションで実ファイル本文を読み取る
2. 内容を全文確認する
3. 既存GitHub成果物と重複・矛盾を照合する
4. Fintokei速攻プロの安全条件を確認する
5. HOLD 5件のBlock継続条件を確認する
6. M15は `DRAFT_NOT_ACTIVE` を確認する
7. 自動公開・自動Master更新等の禁止条件を確認する
8. 適切な保存先と名称を確定する
9. GitHub同期後に再Fetchし、内容とSHAを確認する
10. `PROGRESS.md` / `IMPLEMENTATION_READINESS.md` を同期済み状態へ更新する

## 推奨GitHub保存先

- `docs/M07_FINAL_INTEGRATION_SPEC.md`
- `docs/M14_FAQ_FINAL_AUDIT.md`
- `monitoring/monitor_sources.json`
- `schemas/monitor_sources.schema.json`
- `docs/M16_RUNTIME_SNAPSHOT_SPEC.md`
- `docs/M13_MASTER_GITHUB_SYNC_DESIGN.md`

元ファイル名とsource hashをSync Logに残し、意味内容を改変しない。

## Readinessへの影響

P0で重要だったM07/M14の本文不確実性は解消した。ただし元Markdown Artifact自体はGitHub未同期であるため、WorkではPDF検証済み抽出・本台帳・Day0監査を併用する。

- Work監査：GO
- P0実装：CONDITIONAL GO（M07本文確認PASS。Day0監査で現行Workとの差分確認後にGOへ昇格可能）
- FAQ統合：CONDITIONAL GO（M14本文確認PASS、10差し替え抽出済み。Day0でM11/現行Workとの一致確認後にGOへ昇格可能）
- 監視Dry Run：NO-GO（M15本文確認・同期・Preflight・人間承認待ち）
- Runtime Snapshot実装：NO-GO（M16本文確認・同期待ち）
- 本番公開：NO-GO

## 次のアクション

残る4ファイル（M15 JSON、M15 Schema、M16、M13）をこのセッションで読み取り、**全文確認 → 安全条件検証 → 必要なGitHub同期/検証済み抽出 → Readiness再判定** の順で進める。

不足内容をPROGRESS要約から再生成して、回収Artifactと同一扱いしない。
