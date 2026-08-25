# WORK FIRM DETAIL PILOT HANDOFF

更新日：2026-08-26 JST
対象：Fundora / Fintokei Firm Detail Pilot
位置づけ：Work開始時に読む最短ハンドオフ。詳細設計は既存Contractを参照し、Work側で再設計しない。

## 1. Start Gate
実装開始前に以下を確認し、1つでも未達なら停止：
- internal git authentication recovered
- Evidence pending commit remote confirmed
- Fundora pending commit remote confirmed
- Fundora campaign Production handling complete
- current Production reconciled
- worktree clean
- protected hashes understood
- unknown Production diff = 0

未達時：`HOLD_BEFORE_FIRM_DETAIL_IMPLEMENTATION`

## 2. Read Order
1. `docs/CURRENT_TRUTH_HIERARCHY_2026-08-26.md`
2. `docs/FIRM_DETAIL_PILOT_IMPLEMENTATION_SPEC_2026-08-26.md`
3. `docs/FIRM_DETAIL_CONTENT_CONTRACT_2026-08-26.md`
4. `docs/FIRM_DETAIL_SOURCE_PRECEDENCE_POLICY_2026-08-26.md`
5. `docs/COMPLIANCE_BASELINE_V1_2026-08-26.md`
6. `docs/COMPLIANCE_COPY_LIBRARY_V1_2026-08-26.md`
7. `docs/FIRM_DETAIL_SEO_SCHEMA_CONTRACT_2026-08-26.md`
8. `docs/FIRM_DETAIL_RELEASE_GATE_V1_2026-08-26.md`
9. `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
10. `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`

Analyticsは別承認。必要時のみ：
`docs/FIRM_DETAIL_ANALYTICS_CONTRACT_2026-08-26.md`

## 3. Implement Only
- shared Firm Detail template
- `/firms/fundora/`
- `/firms/fintokei/`
- existing accepted data wiring
- M11 + M14 FAQ application
- official / affiliate CTA separation
- disclosure / disclaimer
- title / meta / canonical
- tests / regression / 390px QA

## 4. Do Not Implement
- remaining 12 Firm pages
- Platform Registry / Platform detail routes
- Payout Registry / Payout routes
- payout source reconstruction
- new ranking / review score / stars
- Diagnosis changes
- Master redesign
- new GA4 config
- new DB / Supabase
- AI auto-generation

## 5. Frozen
Do not alter meaning or behavior of:
- `app/master-data.json`
- DiagnosisLogicV2
- 7 questions / order
- score / eligibility / ranking
- Affiliate / Coupon / Commission / Base Price logic
- existing GA4 initialization
- Evidence Phase1 schema

## 6. Compliance Gate
Must PASS:
- PR disclosure visible
- Official / Affiliate URL separation
- guaranteed claims 0
- unsupported superiority claims 0
- provided-account / sponsor disclosure when applicable
- Japan eligibility / regulatory status confusion 0
- service nature misrepresentation 0
- status + checked date visible
- disclaimer visible
- PII analytics 0

## 7. Source Rule
Do not invent missing facts.
Do not use stale FAQ over newer accepted Production truth.
Do not clear HOLD without current Evidence.
Do not convert Unknown to Unsupported.

## 8. QA Minimum
- V82-series regression >= 53/53 PASS or newer accepted baseline PASS
- Build PASS
- lint error 0
- git diff --check PASS
- protected hashes unchanged unless explicitly approved
- Fundora/Fintokei route tests PASS
- SEO PASS
- FAQ safety PASS
- 390px PASS
- actual iPhone Safari PASS before publish

## 9. Commit
Do not amend / rebase / squash existing accepted Evidence/Fundora commits.
Pilot changes must remain independently rollbackable.

## 10. Publish
Do not publish automatically.
Expected pre-publish status：`FIRM_DETAIL_PILOT_RC_READY`

Central command approval required for Production publish.

## 11. Return Report
Report:
- baseline
- changed/new files
- route status
- data source status
- M11/M14 application
- compliance
- SEO/schema
- tests/regression/build/lint
- protected hashes
- 390px/iPhone
- worktree
- commit SHA
- blockers/cautions
- publish status
