# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 2 COMMERCIAL

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / ENGLISH-FIRST AMENDED / NO PRODUCTION CHANGE
Scope：公開中LPのCampaign / Coupon / commercial high-risk facts
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中LPで現在表示している割引・キャンペーンについて、最低3回ファクトチェックを遡及適用する。

Current product / rule / commercial facts are checked against the current English official surface first unless the fact itself is Japan-specific. Japanese/localized pages remain corroboration and Japan-scope evidence, not an automatic freshness winner.

Discount validityはplan-rule verificationとは別Gate。割引が確認できても、対象PlanのDaily Loss / Max Loss等のHOLDを解除しない。

---

## 1. Funded7 — WELCOME

### Public surface observed

Current LP displays WELCOME discount examples for Funded7 including:

- Two Phase：25% OFF
- One Phase：25% OFF
- Instant：20% OFF

### Two Phase — triple check

Check 1 — Official Japanese Two Phase page
`https://funded7.com/ja/two-phase/`

Current rendered checkout selector states:
- WELCOME
- 25% OFF

Check 2 — Official Japanese main page
`https://funded7.com/ja/`

Current Two Phase selector independently shows:
- WELCOME
- 25% OFF

Check 3 — fresh current rendered recheck on 2026-08-26
The same code/effect remains visible in the current official product flow.

Result：`TRIPLE_VERIFIED` for Two Phase discount scope.

### One Phase — triple check

Check 1 — Official Japanese One Phase page
`https://funded7.com/ja/one-phase/`

Current rendered selector states:
- WELCOME
- 25% OFF

Check 2 — Official One Phase product flow / locale counterpart
Current product selector shows the same WELCOME discount structure.

Check 3 — fresh recheck 2026-08-26
25% WELCOME remains rendered for One Phase.

Result：`TRIPLE_VERIFIED` for One Phase discount scope.

Important：One Phase rule values remain official-source CONFLICT/HOLD. WELCOME verification does not resolve Daily/Max Loss or split conflicts.

### Instant — triple check

Check 1 — Official English Instant page
`https://funded7.com/instant-funding/`

Current rendered selector:
- WELCOME
- 20% OFF

Check 2 — Official Japanese Instant page
`https://funded7.com/ja/instant-funding/`

Same:
- WELCOME
- 20% OFF

Check 3 — fresh recheck 2026-08-26
Current product flow still renders 20% WELCOME.

Result：`TRIPLE_VERIFIED` for Instant discount scope.

Important：Instant loss-rule values remain CONFLICT/HOLD and must not be inferred from discount verification.

### Overall Funded7 commercial result

`TRIPLE_VERIFIED / NO COMMERCIAL CORRECTION REQUIRED` for the scoped WELCOME discount rates.

---

## 2. Blueberry Futures — FUTURES60

### Public surface observed

LP displays current Blueberry Futures promo:
- code `FUTURES60`
- 60% OFF
- Ascent 25K example

### Triple check

Check 1 — Official Blueberry Futures homepage
`https://blueberryfutures.com/`

Current rendered page explicitly states:
- `60% off - use code FUTURES60`
- Ascent 25K standard $139 → displayed $55.60

Check 2 — Official Help Center price article
`https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations`

Current official price table states:
- Ascent 25K standard $139
- price after a 60% discount $55.60

Check 3 — fresh current homepage recheck on 2026-08-26
Current rendered homepage still displays `FUTURES60` and 60% off.

### Result

`TRIPLE_VERIFIED_WITH_SCOPE`

Verified:
- code currently rendered by official site
- 60% effect
- Ascent 25K $139 → $55.60 example

Caution:
- Help Center corroborates 60% pricing but does not independently name FUTURES60 in the retrieved article.
- future publication/patch must fresh-check the live product page/checkout again.

No current commercial correction required for the scoped LP promo.

---

## 3. Fintokei — NEW20 (English-first amendment)

### Public surface observed

LP currently treats NEW20 as:
- 20% OFF
- first challenge welcome offer
- purchase-screen final confirmation required

### Check 1 — Current official English/global homepage
`https://www.fintokei.com/`

Current rendered page explicitly states:
- `Grab 20% off your first Fintokei challenge!`
- `Use promo code NEW20 at checkout`

Check 1：PASS.

### Check 2 — Current official English 2026 price/program guide
`https://www.fintokei.com/blog/how-much-is-prop-trading-2026-price-and-program-guide/`

Current 2026 guide states:
- NEW20 at checkout
- 20% off the first challenge
- wording indicates the discount works for `any first challenge`

Check 2：PASS.

### Check 3 — fresh official English recheck
Current official English Fintokei surfaces continue to advertise the 20% first-challenge offer; current contest/education surfaces also continue to state that new customers receive 20% off their first challenge.

Check 3：PASS for the general/global offer.

### Japanese-page absence

The Japanese homepage not showing NEW20 in a text crawl is **not** treated as a negative fact. Localized pages may lag the English source and absence is not equivalent to checkout rejection.

Japan-specific checkout acceptance was not directly captured in this audit, so final-price confirmation at checkout remains required.

### Result

Status：`TRIPLE_VERIFIED_GENERAL_SCOPE / JP_CHECKOUT_CAUTION`

Operational handling:
- do not remove NEW20 solely because the JP homepage omits it
- do not call the code invalid
- current public wording may remain if it preserves purchase-screen final confirmation
- do not state a guaranteed final price before checkout

---

## 4. Blue Guardian Futures multi-account promo — current official conflict

### Public surface observed

Current LP commercial cards currently present as confirmed:
- Reserve 25K ×1：40% off
- Reserve 25K ×5：buy four / one free style benefit

### Check 1 — current official English Futures landing
`https://origin.blueguardian.com/futures`

Current rendered purchase surface shows a newer progressive multi-account structure in the live plan UI, including:
- 2 accounts：30% extra
- 3 accounts：35% extra
- 4 accounts：40% extra

The current plan surface does not support treating `40%` as the generic first-account tier.

### Check 2 — recent official English/current promotion article
Official article published 2026-08-11:
`https://blueguardian.com/blogs/blue-guardian-futures-multi-account-discounts`

Current article states:
- 1st account 25%
- 2nd 30%
- 3rd 35%
- 4th 40%
- 5th Standard/Direct/Express 100%
- 5th Reserve 70%

### Check 3 — official English Help Center
`https://helpfutures.blueguardian.com/en/articles/15693969-how-does-bundle-pricing-work`

This still states an older/different structure:
- 1 account 40%
- 2 accounts 45%
- 3 accounts 50%
- 4 accounts 55%
- 5 accounts buy 4 get 1 free

The Help table also applies the free fifth account to Reserve.

### Result

Current official English sources materially conflict.

Status：`COMMERCIAL_CONFLICT / CONFIRMED_LABEL_UNSAFE / CHECKOUT_REQUIRED`

Do not choose the newer-looking value solely because it is newer.
Do not keep treating the old 40% / fifth-free Reserve examples as fully verified.

Safe Production direction after auth recovery:
- if checkout still cannot resolve the conflict, downgrade these Blue Guardian Futures promo cards from `確認済み` to `確認中`
- do not show a definitive Reserve first-account discount or fifth-account benefit until live checkout/current campaign state is reconciled
- preserve historical campaign values separately if needed

---

## 5. Commercial audit queue from Wave 2

### No correction currently required
- Funded7 WELCOME scoped discount rates
- Blueberry Futures FUTURES60 scoped promo
- Fintokei NEW20 general/global first-challenge offer, with checkout-final-price caution

### Correction / hold candidate
- Blue Guardian Futures multi-account Reserve cards: current official English conflict; `確認済み` status is not supportable without current checkout reconciliation

### Absolute boundary
Campaign/Coupon verification does not alter:
- Plan HOLD
- Diagnosis eligibility
- SourceHealth conflict
- Profit/Loss rule values

---

## 6. Production boundary

Production writes remain blocked pending internal Git authentication recovery and source reconciliation.

Before any commercial patch:
1. inspect actual Production source
2. fresh-check English official page / checkout
3. preserve product/model scope
4. do not infer nonexistence from crawler absence
5. require final displayed price to match purchase surface

Final Status：
`WAVE2_COMMERCIAL_AUDIT_COMPLETE_ENGLISH_FIRST_NEW20_VERIFIED_BG_FUTURES_CONFLICT_HELD`
