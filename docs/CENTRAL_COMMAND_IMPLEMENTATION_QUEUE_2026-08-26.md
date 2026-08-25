# CENTRAL COMMAND IMPLEMENTATION QUEUE

更新日：2026-08-26 JST
Status：EXECUTION ORDER / NO PRODUCTION CHANGE

## P0 — Blocker resolution

### 1. Internal Git authentication
Status：BLOCKED / condition watch active

Preserve:
- Evidence `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora `2191f06dc56006b4018f16ec8c2ac51161d2f70a`

No amend / rebase / squash / recreate.

### 2. Production reconciliation
Status：READY TO RUN AFTER AUTH RECOVERY

Use:
`WORK_REENTRY_RECONCILIATION_PROMPT_2026-08-26.md`

Public crawl has produced reconciliation signals:
`PUBLIC_SURFACE_RECONCILIATION_SNAPSHOT_2026-08-26.md`

## P1 — Existing accepted backlog

After reconciliation only:

1. Confirm Evidence commit remote state
2. Confirm Fundora commit remote state
3. Complete Fundora campaign Production handling if still pending and campaign window remains relevant
4. Resolve current public/source discrepancy
5. actual iPhone Safari QA

No new feature should bypass this backlog.

## P2 — Small confirmed corrections

Only if reconciliation proves still pending:

- Fintokei current new-purchase SwiftTrader cohort
  - official recheck available in `FINTOKEI_LIVE_OFFICIAL_RECHECK_2026-08-26.md`
- The5ers Futures Day Trade 25K price
- Blueberry Futures Accelerated base prices
  - official recheck available in `PRICE_GAP_LIVE_OFFICIAL_RECHECK_2026-08-26.md`

Apply only as minimal patches against current source, not from stale GitHub summary.

## P3 — Firm Detail foundation

Pilot only:
- Fundora
- Fintokei

Use:
- `FIRM_DETAIL_PROGRAM_INDEX_2026-08-26.md`
- `WORK_FIRM_DETAIL_PILOT_HANDOFF_2026-08-26.md`

Pilot PASS before remaining firms.

## P4 — Firm rollout

Incremental Waves only after Pilot stability.

Do not batch all 14 into one release.

## P5 — Platform

Canonical scope：9
- MT5
- MT4
- TradeLocker
- cTrader
- Match-Trader
- DXtrade
- BlackArrow
- Quantower
- Volumetrica

Research/content prep：READY
Firm mapping：PENDING CURRENT PRODUCTION RECONCILIATION
Production implementation：HOLD UNTIL FIRM DETAIL FOUNDATION STABLE

Use：
`PLATFORM_PROGRAM_INDEX_2026-08-26.md`

## P6 — Payout

Status：SOURCE_REQUIRED / FULL REAL-DATA HOLD

Missing exact source archives：
- P00R
- P01
- P10

No web substitution / reconstruction / AI fill-in.

## Compliance — all phases

Mandatory source/index：
`COMPLIANCE_PROGRAM_INDEX_2026-08-26.md`

Any C2/C3 issue => `COMPLIANCE_HOLD`.

## Current central-command decision

Do not spend Work/Codex on planning already completed in Chat/Handoff.

Next Work session is reconciliation, not new implementation.

Final Status：
`QUEUE_READY_WAITING_INTERNAL_GIT_AUTH_RECOVERY`
