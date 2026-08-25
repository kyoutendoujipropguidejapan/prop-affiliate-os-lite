# CENTRAL COMMAND INTERRUPTED WORK AUDIT

更新日：2026-08-26 JST
Status：CURRENT RECONCILED INTERRUPTED-WORK MAP
目的：過去に中断・保留となった作業を、現行の優先順位・最新Truth・遡及3重ファクトチェック結果に照らして再分類する。

## A. 現在も実行待ちの主要残件

### 1. Internal Git / Production Reconciliation
Status: `BLOCKED_BY_INTERNAL_AUTH / SUPPORT_SPECIALIST_ESCALATED`

- OpenAI Support専門担当へエスカレーション済み
- local accepted commits preserved:
  - Evidence `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
  - Fundora `2191f06dc56006b4018f16ec8c2ac51161d2f70a`
- Worktree clean
- bundle backup verified in Work `/tmp/work-backup.bundle`
- bundle SHA256 `1ce07d49df77e0221c4236a9f95482c36c20348aead45139d605bc0dfb1d7ed7`
- auth recovery後は reconciliation first
- credential/origin/historyを自己判断で変更しない

### 2. Evidence / Fundora remote normalization
Status: `WAITING_AUTH`

- remote presence確認
- fast-forward可能時のみexact accepted history維持
- no amend / rebase / squash / recreate
- 0/0 clean確認

### 3. Fundora campaign Production handling
Status: `WAITING_RECONCILIATION`

Campaign window: 2026-08-25 20:00 JST to 2026-09-01 23:59 JST.

認証復旧後：
- current date/time
- actual Production source
- campaign still commercially relevant
を再判定して扱う。

終了後にstale campaign UIを盲目的に公開しない。

### 4. Public/source discrepancy minimal corrections
Status: `AUDIT_EXPANDED / READY_AFTER_RECONCILIATION`

旧3件だけではなく、遡及3重監査Wave1–25でCorrection/HOLD/Update候補を整理済み。

Primary implementation sources:
- `PUBLIC_LP_POST_AUTH_CORRECTION_BUNDLE_2026-08-26.md`
- `PUBLIC_LP_POST_AUTH_CORRECTION_BUNDLE_ADDENDUM_WAVE19_21_2026-08-26.md`
- `PUBLIC_LP_POST_AUTH_CORRECTION_BUNDLE_ADDENDUM_WAVE22_25_2026-08-26.md`
- `PUBLIC_LP_TRIPLE_FACT_CHECK_COVERAGE_MATRIX_2026-08-26.md`
- `PUBLIC_ROUTE_RETROSPECTIVE_AUDIT_LEDGER_2026-08-26.md`

High-priority examples:
- Fintokei SwiftTrader cohort framing
- Fintokei ProTrader Slim current status
- Fintokei Free Trial Japan scope 10 vs general English top-level scope 8
- FTM Nitro X reward wording / current program count
- FTM Instant Pro conflict-safe wording
- Blueberry Funded Instant Lite current cohort
- Blue Guardian current cohort values
- The5ers company-level consistency wording
- The5ers Futures Day Trade25K current price
- Funded7 PAYG conflict-safe wording
- SuperFunded minimum payout $100
- Home official-source CTA / affiliate CTA separation
- page/section-level freshness metadata

### 5. Actual mobile / analytics verification
Status: `PENDING_REAL_ENVIRONMENT`

- actual iPhone Safari390px Production確認
- CTA-level PR disclosure visibility
- GA4 actual event delivery確認
- no PII/KYC/bank/card/wallet/personal-trading-data leakage
- cache/render divergenceをactual browserで確認

古いV78/V81 QAを現行PASSとして流用しない。

---

## B. Retrospective fact-check program

### 6. Public LP triple fact-check
Status: `IN_PROGRESS / HIGH-RISK FIRST PASS COMPLETE`

- 14 represented Firms: high-risk first pass complete
- route-level audit advanced through Wave25
- English official current source is default freshness anchor for general facts
- Japan eligibility / JPY price / Japan-only offer / Japanese-support scope has separate local gate
- crawler/index non-observation != nonexistence

Not yet full-site complete:
- all remaining article routes
- all Firm-specific FAQ numbers
- all price/history entries
- all campaign/coupon history entries
- all affiliate-exclusive code effects
- all source-link destinations
- actual Production route inventory

### 7. Affiliate-exclusive code Evidence backfill
Status: `BACKFILL_REQUIRED / NO CODE INVALIDATED`

Use:
`AFFILIATE_CODE_EVIDENCE_BACKFILL_QUEUE_2026-08-26.md`

Priority:
- Funded7 `KYOUTENP` +10% reward split claim first
- major discount codes next

Public search absence is not invalidation evidence.
Need checkout/partner portal/direct official confirmation + fresh pre-publish check.

---

## C. Firm program

### 8. Firm Detail Pilot
Status: `READY_DESIGN / IMPLEMENTATION_BLOCKED_BY_START_GATE`

Pilot:
- Fundora
- Fintokei

Start Gate:
- auth recovered
- accepted commits normalized
- Current Production reconciliation PASS
- correction backlog disposition known
- unknown diff0
- fresh Check3 on facts used by Pilot

### 9. Remaining Firm rollout
Status: `PENDING_PILOT_PASS`

Pilot共通Template・Compliance・390px・CTA separation安定後にWave展開。

---

## D. Platform program

### 10. Platform Hub / Detail pages
Status: `RESEARCH_READY / IMPLEMENTATION_HOLD`

Canonical9:
- MT5
- MT4
- TradeLocker
- cTrader
- Match-Trader
- DXtrade
- BlackArrow
- Quantower
- Volumetrica

Firm Detail foundation安定後に実装。
Firm×Platform relationはCurrent Production reconciliation後に確定。
Vendor capabilityをFirm-enabled capabilityへ自動変換しない。

---

## E. Payout program

### 11. Payout integration
Status: `SOURCE_REQUIRED / FULL HOLD`

Missing exact source archives:
- `P00R-PROP-PAYOUT-JOURNEY-source.zip`
- `P01-PROP-PAYOUT-METHODS-source.zip`
- `P10-PAYOUT-ROUTE-DB-source.zip`

Web代替、推測、再構成、AI fillは禁止。

---

## F. Historical infrastructure work

### 12. Monitoring M15 activation / Dry Run
Status: `DEFERRED_NO_GO`

旧Artifactでは `DRAFT_NOT_ACTIVE`。
残条件:
- SourceHealth ID mapping contract
- Preflight
- human approval
- Monitor execution approval gate
- current Evidence/Canonical architectureとの再照合

Firm/Platformより優先しない。

### 13. Runtime Snapshot M13/M16
Status: `ARCHITECTURE_DECISION_APPROVED / IMPLEMENTATION_DEFERRED`

旧「未決定」は解消済み。
Approved Proposal A:
- `data/evidence/*` = Evidence Registry
- `data/canonical/*` = Canonical Fact Registry
- `runtime/*` = generated read-only delivery Snapshot
- existing Product Master remains protected until approved migration
- `variant_id + scope + effective period`
- structured human approval
- canonical SourceHealth IDs
- Canonical -> Runtime one-way only
- Monitoring activation approval separated from Runtime approval

古いM13/M16仕様をそのまま実装しない。
ImplementationはEvidence Phase2前後の適切な時点までDeferred。

---

## G. HOLD / evidence-resolution items

### 14. Current unresolved Firm rule/commercial items

HOLD continues:
- Funded7 One Phase
- Funded7 Instant
- Funded7 PAYG exact Daily/Max
- FTM Instant Pro Daily DD
- FundedElite Flash exact customization matrix
- Blueberry Futures Accelerated25K current price
- Blue Guardian Futures Reserve promo exact progression/5th-account benefit
- Fundora Professional/Master JPY current price
- Hantec Endurance active sale status

Resolved from old HOLD list:
- Hantec Instant Lite -> `VERIFIED_WITH_CAUTION` by human/central approval

### 15. Fintokei Academy
Status: `CORE_TRIPLE_VERIFIED / BENEFIT_BOUNDARY_ACTIVE`

Verified current core:
- Japan-only current Academy availability
- Learn / Drills / simulated Trade / Analytics / Roadmap
- Academy XP/levels/milestones/rewards
- simulation-based trading

Governance:
- Academy XP must not be merged with MyFintokei Loyalty XP without explicit future official evidence
- universal Academy completion ->50% Challenge discount remains `EVIDENCE_REQUIRED / HOLD`
- unrelated50% campaigns must not be conflated

### 16. Fintokei Free Trial
Status: `SCOPE_RESOLVED`

- general English top-level programs:4 × up to2 =8
- current Japan listed variants including Slim:5 ×2 =10

Japan-facing unqualified `最大8回` is update candidate if present in actual Production.
Do not conflate with Loyalty Free Challenge/campaign retry.

### 17. The5ers Summer200K
Status: `DO_NOT_REMOVE / DYNAMIC_SOURCE_RECHECK_BEFORE_FUTURE_REWRITE`

- user never instructed deletion
- operator/user confirms current availability
- static English Summer page being100K-led does not prove200K absence
- detailed200K values require dynamic official purchase/support recheck before future rewrite

---

## H. Superseded / do not resume as-is

Do not resume or reuse as Current Truth:
- GitHub `CURRENT_STATE.md` / old V78/V81 as Production canonical
- old five-HOLD list without later adjudication
- old Plan/Sitemap counts
- M13/M16 Runtime Snapshot old unresolved architecture
- Payout data reconstructed from web
- Japanese page as default freshest source for general rules where English current source is available
- crawler/index non-observation as proof of removal/nondeployment
- Academy XP == Loyalty XP assumption
- static The5ers100K page as proof of Summer200K removal

---

## Current execution order

1. Support/auth recovery
2. Production reconciliation/read-only route inventory
3. Evidence/Fundora remote normalization
4. Fundora current-window handling
5. retrospective correction bundle minimal patches
6. actual iPhone/CTA/GA4 QA
7. Firm Detail Pilot
8. Firm rollout
9. Platform
10. Payout after exact sources
11. Monitoring/Runtime implementation only at later Evidence phase

Final status：
`INTERRUPTED_WORK_CURRENTLY_AUDITED_REQUEUED_AND_STALE_STATUSES_RECONCILED`
