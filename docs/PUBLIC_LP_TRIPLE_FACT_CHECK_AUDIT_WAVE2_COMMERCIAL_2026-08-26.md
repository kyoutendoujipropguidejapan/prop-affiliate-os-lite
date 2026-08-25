# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 2 COMMERCIAL

更新日：2026-08-26 JST
Status：AUDIT IN PROGRESS / NO PRODUCTION CHANGE
Scope：公開中LPのCampaign / Coupon / commercial high-risk facts
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中LPで現在表示している割引・キャンペーンについて、最低3回ファクトチェックを遡及適用する。

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

Check 1 — Official Japanese Instant page
`https://funded7.com/ja/instant-funding/`

Current rendered selector:
- WELCOME
- 20% OFF

Check 2 — Official English Instant page
`https://funded7.com/instant-funding/`

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
- price after 60% discount $55.60
- other Ascent/Accelerated standard prices and 60%-discount examples

This independently reconciles the campaign arithmetic and base price.

Check 3 — fresh current homepage recheck on 2026-08-26
Current rendered homepage still displays `FUTURES60` and 60% off immediately before publication audit close.

### Result

`TRIPLE_VERIFIED_WITH_SCOPE`

Verified:
- code currently rendered by official site
- 60% effect
- Ascent 25K $139 → $55.60 example

Caution:
- Help Center corroborates 60% pricing but does not independently name FUTURES60 in the retrieved article.
- therefore future publication/patch must fresh-check the live product page/checkout again.

No current commercial correction required for the scoped LP promo.

---

## 3. Fintokei — NEW20

### Public surface observed

LP currently treats NEW20 as:
- 20% OFF
- first challenge / first purchase type welcome offer

### Check 1 — Official global Fintokei homepage
`https://www.fintokei.com/`

Current rendered page explicitly states:
- `Grab 20% off your first Fintokei challenge!`
- `Use promo code NEW20 at checkout`

Check 1：PASS.

### Check 2 — Official Japanese homepage
`https://www.fintokei.com/jp/`

Fresh rendered Japanese homepage on 2026-08-26 does **not** contain `NEW20` in the retrieved page text.

This is not proof that the code fails in Japan, but the Japanese public product page does not independently corroborate the code in the retrieved surface.

Check 2：`NOT_CORROBORATED_ON_JP_PAGE`.

### Check 3 — fresh pre-publication/checkout

Not yet independently verified through an official Japanese checkout result or direct official support statement in this audit.

Check 3：`PENDING_JP_CHECKOUT_OR_DIRECT_OFFICIAL_CONFIRMATION`.

### Result

Status：`NOT_YET_TRIPLE_VERIFIED_FOR_JAPAN_SCOPE`

Do not label the code invalid.
Do not remove it solely because the JP homepage lacks the string.
Do not claim Japan-scope triple verification until checkout/direct official confirmation is obtained.

Safe public handling until fresh checkout confirmation:
- if already displayed, mark purchase-screen final confirmation required,
- do not strengthen scope language beyond what the global official source says,
- fresh-check before any next patch/republication.

---

## 4. Commercial audit queue from Wave 2

### No correction currently required
- Funded7 WELCOME scoped discount rates: verified
- Blueberry Futures FUTURES60 scoped promo: verified with scope/caution

### Verification required before stronger claim
- Fintokei NEW20 Japan applicability / live checkout acceptance

### Absolute boundary
Campaign/Coupon verification does not alter:
- Plan HOLD
- Diagnosis eligibility
- SourceHealth conflict
- Profit/Loss rule values

---

## 5. Next Wave

Continue retrospective triple checks on:

1. affiliate-exclusive codes / KYOUTEN codes
2. Blue Guardian current campaign/bundle claims
3. SuperFunded current promotions / code scope
4. Blueberry Funded current promo claims
5. Fundora public/current campaign after internal repo reconciliation
6. current price / plan-status claims on public firm sections

Production writes remain blocked pending internal Git authentication recovery and source reconciliation.

Final Status：
`WAVE2_COMMERCIAL_AUDIT_COMPLETE_WITH_ONE_JP_SCOPE_VERIFICATION_GAP`
