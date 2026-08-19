# IMPLEMENTATION_READINESS

更新日：2026-08-19 JST
対象：プロップファームの歩き方
目的：Work復活前後に「完了記録」と「GitHub上の実体」を混同せず、安全に実装へ移るためのReadiness Gate。

## 0. 結論

現時点の判定：

- Workの**監査開始**：GO
- Workの**P0実装開始**：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run開始：NO-GO（M15実JSON/Schema本文未確認）
- Runtime Snapshot実装：NO-GO（M16本文未確認）
- 本番公開：NO-GO（M08完走・人間承認前）

重要更新：2026-08-19にM07とM14の元PDFをChatGPTで全文確認した。P0実装仕様とFAQ差し替え本文の「内容不明」状態は解消した。ただし元Markdown Artifact自体はGitHub未同期のため、現時点では検証済みPDF内容・GitHubの検証済み抽出・Day0監査を併用する。

---

## 1. 正本の優先順位

### A. データ・診断・SourceHealth

上位正本：`Prop_Firm_Master_v2_2_Final_UX_Copy.xlsx`

- PlanCatalogV2
- PlanCoverage
- DiagnosisPlanCurrent
- DiagnosisLogicV2
- SourceHealth
- Coupons
- PriceOffers
- UXJourney / PageUXSpec / UXCopyFinal / FirmUXCopy / FirmPlanFlow 等

Excel MasterをGitHubの要約文で上書きしない。

### B. GitHubに実体がある仕様・原稿

直接読める主要成果物：

- `docs/M08_QA_REGRESSION_SPEC.md`：公開前QAの唯一の正本
- `docs/M09_SEO_CONTENT_PACK.md`：SEO完成原稿
- `docs/M09B_SEO_CONTENT_PACK_2.md`：追加SEO完成原稿
- `docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`：監視技術設計
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`：14社FAQ原稿。M14判定を優先
- `docs/M12_DRY_RUN_SOURCE_SET.md`：監視Dry Run URL正本
- `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`：回収M14 PDFから作成した検証済み実装用抽出。元M14 Artifactそのものではない
- `docs/WORK_RESTART_PROMPT.md`
- `docs/WORK_RESTART_DAY0_CHECKLIST.md`
- `docs/WORK_DAY0_START_PROMPT.md`
- `docs/CURRENT_STATE.md`
- `docs/PROGRESS.md`
- `docs/ARTIFACT_SYNC_STATUS.md`

### C. 回収PDFで全文確認済みだが元MarkdownはGitHub未同期

- M07最終統合仕様：24ページ、内容確認PASS、安全条件PASS
- M14 14社FAQ最終チェック：18ページ、70 FAQ / 10差し替え / HOLD 5確認PASS

元ArtifactとGitHubの検証済み抽出を混同しない。

### D. まだ本文確認待ち

- M13 GitHub同期設計全文
- M15 `monitor_sources.json` Draft
- M15 JSON Schema
- M16 Runtime Snapshot仕様書

**ルール：PROGRESSの要約だけから、未確認成果物のField・Schemaを再現したことにしない。**

---

## 2. 実装別Gate

### Gate A｜Work監査

**GO**

`docs/WORK_DAY0_START_PROMPT.md` に従い、未公開作業版の状態確認を開始してよい。

条件：最初はコードを書かず、現状・Master v2.2差分・M07適合・M14反映状況・依存・最小実装案だけ報告する。

### Gate B｜M07 P0実装

**CONDITIONAL GO**

M07本文は回収PDFで全文確認済み。P0は13項目、最初の実装単位はP0-01〜P0-03。

GO昇格条件：

1. Work Day0監査で未公開作業版とM07の矛盾がない、または差分が明示される。
2. Master v2.2 / DiagnosisLogicV2 / SourceHealthの保護条件を確認。
3. Fintokei Variant境界とHOLD 5件のBlockが現行実装で表現可能。
4. 人間がP0差分実装を承認。

### Gate C｜FAQ統合

**CONDITIONAL GO**

M14本文は回収PDFで全文確認済み。

判定：

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

10件の差し替え本文は `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md` に検証済み抽出済み。

GO昇格条件：

1. Day0監査で現行Work/M11本文との対象Q ID一致を確認。
2. UPDATE_REQUIRED 10件だけを対象にし、他FAQを不要に改稿しない。
3. PASS_WITH_CAUTIONは公開直前再確認条件を保持。
4. HOLD 5件をFAQ schemaへ入れず、診断Top3根拠に使わない。
5. Fintokei速攻プロQ3は限定Variantとして扱い、schemaへ入れない。

### Gate D｜監視Dry Run

**NO-GO**

M12 URLセットとM10設計は存在するが、M15 `monitor_sources` 実JSON / Schema本文をこのセッションでまだ確認していない。

Dry Run開始条件：

- Primary 5 / Shadow 4 = 9 URLを実体JSONで確認
- status = `DRAFT_NOT_ACTIVE`
- 全安全フラグ確認
- Preflight全PASS
- 人間がACTIVE化を明示承認

### Gate E｜Runtime Snapshot

**NO-GO**

M16完了記録はあるが、仕様書本文をこのセッションでまだ確認していない。

実装開始条件：

- M16仕様書本文確認
- APPROVED以外をWork/Replitが本番利用しないGateを確認
- rollback / supersedes / source_master_version を検証
- M13の二層Canonical方針と矛盾しないことを確認

### Gate F｜公開

**NO-GO until M08 PASS**

公開条件：

- M08 Full Regression完走
- BLOCKER = 0
- CRITICAL = 0
- 390px fresh render確認
- DiagnosisLogicV2不変
- HOLD 5件Top3除外
- Fintokei Variant境界誤適用なし
- Official / Affiliate link separation維持
- GA4既存イベント破損・二重発火なし
- 人間が公開を明示承認

---

## 3. 絶対保護条件

### Fintokei｜速攻プロ

条件付き解除候補はVariant単位でのみ扱う。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- legacy account separation required
- Evidence required
- human approval required

購入日・旧口座を安全に区別できない環境ではTop3 Block継続。

### HOLD / Block継続 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`

### 診断

- DiagnosisLogicV2を不用意に変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- 不明値を0/falseで代用しない
- ConflictをVerifiedへ自動昇格しない

### FAQ schema

- 画面に実際に表示するQ&Aのみschema化
- HOLD 5件を入れない
- Coupon / Referral / Eligibility / SourceHealth競合など変動しやすいFAQは原則schema対象外
- 公開直前に本文とschemaの完全一致を再確認

---

## 4. まだ価値が高い未確認成果物

### P1

1. M15 `monitor_sources.json` Draft
2. M15 JSON Schema
3. M16 Runtime Snapshot仕様書
4. M13 GitHub同期設計全文

### P2

5. M01〜M06詳細報告（将来の監査履歴として必要なら保存）

**未確認内容をPROGRESSから再生成して「元成果物」と呼ばない。**

---

## 5. Work復活時の安全な順序

1. README
2. AGENTS
3. CURRENT_STATE
4. PROGRESS
5. IMPLEMENTATION_READINESS
6. ARTIFACT_SYNC_STATUS
7. WORK_RESTART_PROMPT
8. WORK_RESTART_DAY0_CHECKLIST
9. M14_VERIFIED_EXTRACTION_FROM_PDF
10. Master v2.2確認
11. 未公開Work作業版の監査（コード変更なし）
12. M07 P0適合・差分確認
13. M14 FAQ反映状況確認
14. 人間がP0実装開始を承認
15. P0差分実装
16. FAQ統合
17. M08 QA
18. 390px fresh render
19. Go / No-Go
20. 公開は別承認

---

## 6. Replit / 監視側の安全な順序

1. M10読む
2. M12読む
3. M15実JSON/Schema本文確認
4. `DRAFT_NOT_ACTIVE`確認
5. Schema validation
6. Primary 5だけPreflight
7. 人間承認後にDry Run
8. Shadow 4は後半条件を満たしてから有効化
9. Master / SourceHealth / Diagnosis / Work / siteへ自動反映しない

---

## 7. AI向け停止条件

以下の場合は推測で続行せず、該当部分だけ保留する。

- M15/M16/M13の実ファイルが必要だが本文未確認
- Fintokeiの購入日Variantを表現できない
- HOLD 5件の自動解除を要求される
- DiagnosisLogicV2の変更が暗黙に必要になる
- Workの未公開版とMasterのどちらが新しいか判別できない
- 公開指示がないのに本番反映が必要になる

---

## 8. 現時点の最小結論

P0で最重要だったM07/M14の内容不確実性は解消した。

次は **M15/M16/M13本文確認 → 明日のWork Day0監査 → P0/FAQをGOへ昇格 → 実装 → M08 QA** が最短経路。
