# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 12 / PAY AFTER PASS + PAYG ROUTE

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：`/pay-after-pass-payg`
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中の合格後払い / PAYG比較記事を英語公式優先で再監査する。

---

## 1. Funded7 PAYG — payment structure

### Public article

Article correctly describes the staged-payment concept:
- Phase 1 fee first
- Phase 2 fee after P1 pass
- Funded-stage fee after P2 pass
- total cost when fully completed is presented by Funded7 as equal to the corresponding standard total
- PAYG allocation exception / higher payout-cap concept is referenced

### Current official checks

Check 1 — current English homepage PAYG section
`https://funded7.com/`

Confirms staged-payment structure and current account-size purchase flow.

Check 2 — current official allocation FAQ
`https://funded7.com/faq/evaluation-maximum-allocation-limits-per-client/`

Confirms:
- PAYG sits outside standard allocation cap
- PAYG monthly payout cap is $20,000

Check 3 — fresh official current surface recheck
Current PAYG homepage still presents Phase 1 → Phase 2 → Funded staged payments.

Result for payment structure:
`TRIPLE_VERIFIED_WITH_SCOPE`

---

## 2. Funded7 PAYG — loss rules are NOT safe as a single value

### Public article currently states

`日次4%・最大8%の固定型`

This is currently presented as a definite rule.

### Check 1 — current English challenge comparison
`https://funded7.com/challenge-comparison/`

Current PAYG row states:
- Daily Loss：5%
- Max Total Loss：10%
- Drawdown：Static
- target：8% / 6%
- profit split：80/20
- MT5

### Check 2 — current-accessible official 2026 guide
`https://funded7.com/blog/how-to-pass-the-funded7-challenge-a-step-by-step-guide/`

The PAYG section states:
- Daily Loss：4%
- Max Total Loss：8%
- Static
- target：8% / 6%
- MT5 only
- 80/20

### Check 3 — current English homepage / PAYG purchase section
The homepage confirms PAYG exists and the staged price flow, but the retrieved PAYG section does not independently settle the Daily/Max pair.

### Result

Material official English conflict:
- 5% / 10% on current comparison
- 4% / 8% on official current-accessible guide

Status：`CORRECTION_REQUIRED_TO_CONFLICT_SAFE / PAYG_RULE_HOLD`

Public article must not continue to present `4% / 8%` as an unqualified current fact after the next approved Production patch.

Safe replacement direction:
`PAYGの損失上限は現行公式ページ間で差異を確認中。購入前にPAYGの購入画面・専用ルールを確認。`

Do not choose 5/10 or 4/8 until live configurator / dedicated authoritative rules / direct official clarification resolves it.

---

## 3. Trading Cult Pro — Pay After Pass core structure

### Public article currently states
- $9.99 entry
- remaining balance after pass
- payment within 14 calendar days
- funded PAP rules include 3% trailing/max loss
- 5 minimum trading days
- qualifying day >=1%
- stability 25% / 30%

### Check 1 — current English Pro TradingCult purchase surface
`https://pro.tradingcult.com/`

Current surface confirms:
- Pay After Pass is a current model
- starts at $9.99
- 1-Step / 2-Step variants
- MT5 platform family

### Check 2 — current official TradingCult Help content
Official current PAP FAQ mirrors state:
- $9.99 entry
- remaining balance due within 14 calendar days after passing
- 80% funded split
- funded trailing DD 3% / Max Loss 3%
- min 5 trading days
- valid day >=1%
- stability 25% 1-Step / 30% 2-Step

### Check 3 — fresh current Pro product recheck
Current Pro page continues to advertise Pay After Pass as current and starting at $9.99.

### Result

Status：`VERIFIED_WITH_CAUTION`

Core payment structure is supported. Detailed funded rules are supported by current official Help mirrors but should receive one fresh English-help/checkout check immediately before any future rewrite.

No correction required to the public article from this scoped audit.

---

## 4. FundedElite — Flash Activation / pay-after-pass entry

### Public article currently states
- starts from $5
- after pass, activation fee is required
- account-size-specific final fee should be checked at purchase

### Check 1 — current English Flash Activation product page
`https://fundedelite.com/challenges/flash-activation`

Confirms:
- $5 entry
- one phase
- activation fee after passing
- standard activation fees displayed by size
- no minimum evaluation days
- standard/default FAQ rule block 6% target, 3% daily, 6% static max

### Check 2 — current official FAQ
`https://faq.fundedelite.com/en/articles/12683940-flash-activation-challenge`

Confirms the same $5 → pass → KYC/contract → activation-fee flow.

### Check 3 — current FundedElite homepage
Current homepage still markets Flash Activation as Pay After Pass starting at $5.

### Result

Payment-flow portion of the public article:
`TRIPLE_VERIFIED_WITH_SCOPE / NO CORRECTION REQUIRED`

Separate existing HOLD remains for the exact customization matrix because the product page simultaneously markets configurable targets, payout pace and up-to-95% split while the standard FAQ block shows 6% / 80% / 14 days.

---

## 5. Route correction queue

### P0 after auth + Production reconciliation
1. Funded7 PAYG article rule sentence: remove definite `4% / 8%` current-rule claim and switch to conflict-safe wording until resolved.

### No scoped correction
2. Trading Cult Pro PAP core payment flow
3. FundedElite Flash Activation core payment flow

### HOLD preserved
4. Funded7 PAYG exact Daily/Max values
5. FundedElite exact custom-option matrix

Final Status：
`WAVE12_COMPLETE_PAYG_PUBLIC_RULE_CLAIM_REQUIRES_CONFLICT_SAFE_PATCH`
