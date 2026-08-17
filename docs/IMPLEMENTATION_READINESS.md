# IMPLEMENTATION_READINESS

更新日：2026-08-17 JST
対象：プロップファームの歩き方
目的：Work復活前後に「完了記録」と「GitHub上の実体」を混同せず、安全に実装へ移るためのReadiness Gate。

## 0. 結論

現時点の判定：

- Workの**監査開始**：GO
- Workの**P0実装開始**：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run開始：NO-GO（M15実JSON未同期）
- Runtime Snapshot実装：NO-GO（M16実Schema/仕様書未同期）
- 本番公開：NO-GO（M08完走・人間承認前）

理由：M01〜M16は完了記録があるが、GitHubへ実体ファイルとして存在する成果物と、PROGRESSに要約のみ存在する成果物が分かれている。

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

現時点で直接読める主要成果物：

- `docs/M08_QA_REGRESSION_SPEC.md`：公開前QAの唯一の正本
- `docs/M09_SEO_CONTENT_PACK.md`：SEO完成原稿
- `docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`：監視技術設計
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`：14社FAQ原稿。ただしM14の後続判定あり
- `docs/M12_DRY_RUN_SOURCE_SET.md`：監視Dry Run URL正本
- `docs/WORK_RESTART_PROMPT.md`：Work復活時の入口
- `docs/CURRENT_STATE.md`：現行状態
- `docs/PROGRESS.md`：進捗・要約

### C. PROGRESSに要約はあるが実体ファイルを確認できない成果物

以下は「完了したという記録」は採用するが、存在しない詳細を推測しない。

- M01〜M07の各詳細報告／M07最終統合仕様
- M13 GitHub同期設計の全文
- M14 全70FAQ判定・UPDATE_REQUIRED 10件の差し替え全文
- M15 `monitor_sources` JSON Draft / JSON Schema 実体
- M16 Runtime Snapshot仕様書 / Schema実体

**ルール：PROGRESSの要約だけから、未保存成果物のField・差し替え文章・P0詳細を再現したことにしない。**

---

## 2. 実装別Gate

### Gate A｜Work監査

**GO**

`docs/WORK_RESTART_PROMPT.md` で未公開作業版の状態確認を開始してよい。

条件：最初はコードを書かず、現状・v2.2差分・依存・最小実装案だけ報告する。

### Gate B｜M07 P0実装

**CONDITIONAL GO**

M07の完了記録はあるが、最終仕様書実体はGitHubで未確認。

実装前に次のどちらかを満たす：

1. M07最終仕様書を回収してGitHubへ同期する。
2. 回収できない場合、`WORK_RESTART_PROMPT.md` + `PROGRESS.md` + Master v2.2をfallback contractとして使い、人間が実装範囲を確認してから開始する。

M07に存在したはずの詳細をAIが補完してはいけない。

### Gate C｜FAQ統合

**CONDITIONAL GO**

M11原稿はGitHubに存在する。
M14では70FAQを再照合し、PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5と記録されている。

ただしM14のUPDATE_REQUIRED 10件の差し替え全文はGitHubで未確認。

したがって：

- PASS：M11を候補として使用可
- PASS_WITH_CAUTION：注記・SourceHealth条件を保って使用
- UPDATE_REQUIRED：M14差し替え全文を回収するか、公開直前に公式一次情報で再照合してから置換
- HOLD 5：確定FAQ schemaに入れない。診断Top3根拠に使わない

### Gate D｜監視Dry Run

**NO-GO**

M12 URLセットとM10設計は存在するが、M15 `monitor_sources` 実JSON / SchemaがGitHubにない。

Dry Run開始条件：

- Primary 5 / Shadow 4 = 9 URLを実体JSONで確認
- status = `DRAFT_NOT_ACTIVE` から開始
- 全安全フラグ確認
- Preflight全PASS
- 人間がACTIVE化を明示承認

### Gate E｜Runtime Snapshot

**NO-GO**

M16完了記録はあるが、manifest / Firm / Plan / Diagnosis Candidate / SourceHealth / Monitor Source Schemaの実体ファイルがGitHubにない。

実装開始条件：

- M16仕様書または同等Schema実体をGitHubへ同期
- APPROVED以外をWork/Replitが本番利用しないGateを実装可能な形で確認
- rollback / supersedes / source_master_version を検証

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

---

## 4. GitHubへ回収・同期すると価値が高い不足成果物

### P0

1. M07最終統合仕様書
2. M14全70FAQ判定 + UPDATE_REQUIRED 10件の差し替え全文

### P1

3. M15 `monitor_sources.json` Draft
4. M15 JSON Schema
5. M16 Runtime Snapshot仕様書
6. M16各Schema / manifest Draft
7. M13 GitHub同期設計全文

### P2

8. M01〜M06詳細報告（将来の監査履歴として必要なら保存）

**P0/P1を回収できなくても、存在しない内容を再生成して「元成果物」と呼ばない。再設計する場合は新しい版として明示する。**

---

## 5. Work復活時の安全な順序

1. README
2. AGENTS
3. CURRENT_STATE
4. PROGRESS
5. IMPLEMENTATION_READINESS
6. WORK_RESTART_PROMPT
7. Master v2.2確認
8. 未公開Work作業版の監査（コード変更なし）
9. M07実体の有無を確認
10. 実装範囲を人間確認
11. P0差分実装
12. FAQはM14差し替え可否を確認して統合
13. M08 QA
14. 390px fresh render
15. Go / No-Go
16. 公開は別承認

---

## 6. Replit / 監視側の安全な順序

1. M10読む
2. M12読む
3. M15実JSON/Schemaの存在確認
4. `DRAFT_NOT_ACTIVE`確認
5. Schema validation
6. Primary 5だけPreflight
7. 人間承認後にDry Run
8. Shadow 4は後半条件を満たしてから有効化
9. Master / SourceHealth / Diagnosis / Work / siteへ自動反映しない

---

## 7. AI向け停止条件

以下の場合は推測で続行せず、該当部分だけ保留する。

- PROGRESSに書かれた成果物の実ファイルが見つからない
- M14 UPDATE_REQUIRED文章が必要だが差し替え本文がない
- Fintokeiの購入日Variantを表現できない
- HOLD 5件の自動解除を要求される
- DiagnosisLogicV2の変更が暗黙に必要になる
- Workの未公開版とMasterのどちらが新しいか判別できない
- 公開指示がないのに本番反映が必要になる

---

## 8. 現時点の最小結論

新規設計を増やすより、**不足成果物の回収 → Work監査 → P0差分実装 → M08 QA** が最短経路。

GitHubに存在するものだけを「読める正本」とし、PROGRESSは進捗・安全条件の要約として扱う。
