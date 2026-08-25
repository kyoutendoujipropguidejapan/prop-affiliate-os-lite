# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 7 / FUTURES

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中 Blueberry Futures / The5ers Futures 関連Fact
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Method

- current official product page
- current official Help/FAQ
- separate current official payout/rules route
- locale差・旧記事差をVariant/Conflictとして保持
- current product pageを最優先するが、official同士の矛盾は多数決で消さない
- Production sourceは内部Git認証HOLD中のため編集しない

---

## 1. Blueberry Futures — Ascent / Accelerated core structure

### Current official checks

Check 1 — official homepage
`https://blueberryfutures.com/`

Current 25K rows:

**Ascent**
- Drawdown Type: EOD
- Profit Target: $1,500
- Drawdown: $1,000
- Min Days to Pass: 2
- Profit Split: 90%
- consistency only on funded

**Accelerated**
- Drawdown Type: Trailing
- Profit Target: $1,500
- Drawdown: $1,000
- Min Days to Pass: 1
- Profit Split: 90%
- consistency only on funded

Check 2 — official Help / Detailed Parameters
`https://help.blueberryfutures.com/en/articles/12890893-detailed-parameters-of-our-challenges`

Confirms:
- Ascent = EOD / min2
- Accelerated = real-time trailing / min1
- 25K target $1,500 / DD $1,000 for both

Check 3 — official Help / Which account is right for me?
`https://help.blueberryfutures.com/en/articles/12915670-which-account-is-right-for-me`

Again confirms:
- Ascent EOD / 2 days
- Accelerated trailing / 1 day
- no evaluation consistency for either

### Result

Status：`TRIPLE_VERIFIED / CORE STRUCTURE`

No correction required for the audited core target/DD/min-day structure.

---

## 2. Blueberry Futures — funded consistency rule

### Public surface problem

Current public material has used a company-level `Funded consistency 35%` description, which can be read as applying to both Ascent and Accelerated.

### Triple check

Check 1 — official Consistency Rule
`https://help.blueberryfutures.com/en/articles/12921739-what-is-the-consistency-rule`

Current funded rule:
- Accelerated = max 20% of total profit from one trading day
- Ascent = max 35%

Check 2 — official payout cycle
`https://help.blueberryfutures.com/en/articles/11196024-how-is-the-payout-cycle-structured`

Again states:
- Accelerated 20%
- Ascent 35%

Check 3 — official first payout article
`https://help.blueberryfutures.com/en/articles/12942617-when-can-i-get-my-first-payout`

Again states:
- Accelerated 20%
- Ascent 35%

### Result

A universal `Funded consistency 35%` is wrong/misleading for Accelerated.

Status：`CORRECTION_REQUIRED / HIGH_PRIORITY`

Approved safe direction for later patch:

`Ascent：35%／Accelerated：20%（Funded Accountの出金判定）`

Do not apply either percentage to the Evaluation phase; current official comparison says no evaluation consistency.

---

## 3. Blueberry Futures — profitable-day / payout rule

### Triple check

Check 1 — payout cycle
- 5 profitable days
- each profitable day = net $200+ for the documented cycle

Check 2 — first payout article
- 5 profitable days
- $200+ definition
- consistency + buffer threshold also required

Check 3 — consistency article examples and current payout system context
- withdrawal eligibility is evaluated on funded-account consistency at request time

### Result

Status：`TRIPLE_VERIFIED_WITH_SCOPE`

Safe display:
`Funded出金：5利益日（各$200以上）＋プラン別一貫性＋必要バッファ`

Account-size specific payout minimum/cap/buffer should remain plan-size scoped rather than collapsed into one universal number.

---

## 4. Blueberry Futures — 60% promo and price conflict

### Current official homepage

Current homepage displays `FUTURES60` and 60% off.

Current 25K homepage price:
- Ascent: standard $139 → $55.60
- Accelerated: standard $110.40 → $44.16

### Current official Help / Detailed Parameters

Current Help table displays discounted 60% prices:
- Ascent 25K: $55.60
- Accelerated 25K: $51.60

$51.60 corresponds to a $129 standard price, not current homepage $110.40.

### Result

Ascent pricing currently aligns.

Accelerated current official sources conflict:
- homepage: $110.40 / $44.16
- Help: $129 implied / $51.60 discounted

Status：`CONFLICT / PRICE_HOLD / DO_NOT_INFER`

The existing public conservative handling of Accelerated price should remain until the live purchase/configuration surface is reconciled.

Do not replace the hidden/confirmation-needed value with either price solely from this audit.

---

## 5. Blueberry Futures — platform/service nature

Current homepage states BlackArrow is the platform technology and explicitly limits the program to listed Futures products on CME/CBOT/NYMEX/COMEX, not stocks/options/FX/crypto/CFDs.

It also states Evaluation Challenge trading is simulated and cites simulated-performance limitations.

Status：`CURRENT_OFFICIAL_CONFIRMED`

Firm Detail/Platform pages must not describe BlackArrow availability as proof that every historical account/cohort uses it; map current Firm-enabled scope separately.

---

## 6. The5ers Futures — current 25K Day Trade headline

### Check 1 — current official Futures page
`https://the5ers.com/futures/`

Current Day Trade 25K:
- Evaluation target 6%
- Funded target 4%
- Max Loss EOD 4%
- Consistency per position 40%
- price $59
- activation fee None
- pass in one day
- scale to $500K

### Check 2 — current official Futures Evaluation FAQ
`https://the5ers.com/futures-faqs/the5ers-futures-evaluation-programs-explained/`
last update 2026-06-10

States:
- Swing + Day Trade
- target 6%
- consistency 40%
- drawdown 4%
- prices: 25K $59 / 50K $100 / 100K $170 / 150K $199

### Check 3 — current Portuguese official Futures page
`https://the5ers.com/pt/futures/`

Current locale page states:
- target 6% / funded 4%
- consistency 40%
- 25K price $59
- activation fee None
but Max Loss EOD = 3%, not 4%.

### Additional official historical/current-ish article
`https://the5ers.com/how-does-a-futures-prop-firm-works/`
updated 2026-05-11

Still describes an older structure:
- Max Loss EOD 3%
- consistency 30%
- 25K/50K context

### Result

The strongest current English product page + later June FAQ agree on 4% / 40% and $59.

However, current Portuguese official page still shows 3% / 40%, and the May official article shows 3% / 30%.

Therefore:

- Price $59: `CURRENT_OFFICIAL_STRONGLY_SUPPORTED`
- Consistency 40%: `CURRENT_OFFICIAL_STRONGLY_SUPPORTED`
- Max Loss EOD 4%: `CURRENT_PRIMARY_SUPPORTED_BUT_LOCALE_CONFLICT`

Status for max-loss field：`CONFLICT_WITH_LOCALE / VERIFIED_WITH_CAUTION`

Do not call the 4% value universally conflict-free until the locale/purchase surface is reconciled.

---

## 7. The5ers Futures — current Day Trade operational rules

Current English product page states:
- positions must close at least 10 minutes before market close
- news trading allowed
- no monthly fee / one-time fee structure
- scaling at each 10% profit milestone

Swing section states no weekend holding.

Current June FAQ identifies Swing and Day Trade as the two current evaluation programs.

Status：`CURRENT_OFFICIAL_SUPPORTED`

No correction required for those scoped operational descriptions.

---

## 8. The5ers Futures — public price handling

The current English product page and June FAQ both support 25K = $59.

However, because the project previously detected price/source discrepancies and the live Production source is not yet reconciled, do not unhide or change any current public price field before:

1. current purchase/hub route verification,
2. Japan/locale applicability check,
3. fresh implementation-time Check 3.

Status：`PRICE_UPDATE_CANDIDATE / NOT_AUTOMATIC`

---

## 9. The5ers Summer 200K boundary

The user has confirmed the Summer 200K route still exists.

This Wave does not alter that status.

Static public 100K/Summer or Futures pages are not proof of 200K nonexistence.

Status remains:
`DO_NOT_CORRECT / USER_CONFIRMED_CURRENT / OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING`

---

## 10. Wave 7 correction / hold queue

### P0 after internal Git recovery + Production reconciliation

1. Blueberry Futures consistency display
   - universal 35% -> plan-specific `Ascent35 / Accelerated20`

2. Blueberry Futures Accelerated price
   - keep `CONFLICT / HOLD`; do not choose homepage or Help price yet

### P1 / verification

3. The5ers Futures 25K price
   - $59 strongly supported; update only after live purchase/Japan check

4. The5ers Futures Max Loss
   - English current =4%, current PT locale=3%
   - keep `VERIFIED_WITH_CAUTION / LOCALE_CONFLICT`

### No correction

5. Blueberry core Ascent/Accelerated DD types, targets and evaluation minimum days
6. The5ers Futures 40% current English consistency headline
7. Day Trade close-before-market/news/current scaling wording

---

## 11. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

Before any Production patch:
1. reconcile actual source
2. run fresh current purchase/locale check
3. retain Variant/Conflict semantics
4. minimal patch only
5. regression + protected hashes + 390px + compliance
6. human publish approval

Final Status：
`WAVE7_FUTURES_AUDIT_COMPLETE_BLUEBERRY_CONSISTENCY_CORRECTION_ACCELERATED_PRICE_HOLD_THE5ERS_LOCALE_CAUTION_NO_PRODUCTION_CHANGE`
