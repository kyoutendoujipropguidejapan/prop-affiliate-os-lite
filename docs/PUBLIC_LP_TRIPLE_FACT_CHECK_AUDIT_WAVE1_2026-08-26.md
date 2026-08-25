# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 1

更新日：2026-08-26 JST
Status：AUDIT IN PROGRESS / NO PRODUCTION CHANGE
Scope：公開中 `kyouten-prop-guide.utsr.chatgpt.site` の高リスクFact
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中LP/記事の既存Factへ最低3回ファクトチェックを遡及適用する。

本Waveは特に変更頻度・誤表示影響の高い以下を優先する。

- payout / reward conditions
- profit split
- minimum trading / profitable days
- campaign/product availability
- plan size / current product status

Production sourceは内部Git認証HOLD中のため、本書では監査・修正候補の固定のみ行い、Production変更はしない。

---

## 1. Fintokei payout conditions

### Public surface observed

`/prop-firm-payout-comparison`

- 初回：プロ口座の最初の取引から14日
- 以後：前回申請から14日
- チャレンジ・入門：payout要件として最低3取引日
- 速攻プロ：payout要件として最低5取引日 + 初期資金3%以上の利益
- Instant Payout approval：多くが10〜20秒

### Triple check

Check 1 — JP payout FAQ
`https://support.fintokei.com/ja/articles/6538884-...`

- Challenge / Start：最低3日
- SwiftTrader：最低5日 + 3%以上profit
- first payout：first tradeから2週間
- subsequent：前回申請から2週間

Check 2 — Instant Payout FAQ
`https://support.fintokei.com/ja/articles/11904545-...`

- request auto-approved within seconds
- most requests 10–20 seconds
- first eligibility after two weeks from first Pro account trade
- subsequent after two weeks

Check 3 — EN payout / Instant Payout FAQ
`https://support.fintokei.com/en/articles/6538884-...`
`https://support.fintokei.com/en/articles/11904545-...`

Current English official guidance materially corroborates the same cycle / processing structure.

### Important distinction

SwiftTrader evaluationの最低取引日数3日（2026-07-15以降のnew-purchase evaluation）と、Pro account payout eligibilityの最低5取引日は別条件。

この2つを混同しない。

### Result

`TRIPLE_VERIFIED / NO CORRECTION REQUIRED` for the payout-page wording above.

Earlier audit signal that payout-page `速攻プロ5日` should become3日は撤回。3日はevaluation条件、5日はpayout eligibility条件。

---

## 2. FTM 1-Step Nitro X profit split

### Public surface observed

Home/current catalog crawl：

`1ステップ Nitro X`

- 出金条件：`On-demand／最大80%`

### Triple check

Check 1 — official Nitro X FAQ EN
`https://fundedtradermarkets.com/faq/category/1-step-nitro-x`

- simulated funded Nitro X = 100% lifetime profit split
- 50% of total profits must remain in account as risk buffer
- remaining 50% can be withdrawn at 100% reward rate

Check 2 — official Nitro X FAQ JP
`https://fundedtradermarkets.com/ja/faq/category/1-step-nitro-x`

Same structure:
- lifetime 100%
- 50% profit buffer retained
- remaining 50% withdrawable at 100%

Check 3 — dedicated payout/DD FAQ
`https://fundedtradermarkets.com/faq/what-impact-does-the-trailing-overall-drawdown-have-on-payouts-in-a-nitrox-simulated-funded-account`

- confirms 50% buffer rule
- confirms remaining 50% is withdrawable at 100% reward rate
- also states minimum performance reward threshold before request

Additional corroboration：recent FTM guide also describes Nitro X as 100% lifetime split with 50% buffer.

### Result

Public `最大80%` is materially stale/wrong for Nitro X current reward structure.

Status：`CORRECTION_REQUIRED`

### Safe correction direction

Do not replace with just `100%`.

Recommended current wording:

`On-demand／引き出し対象部分は100%配分（総利益の50%をリスクバッファとして口座に維持）`

Also preserve current payout threshold / consistency conditions separately.

---

## 3. The5ers Summer Plan 200K

### Public surfaces observed

`/the5ers-summer-plan`

Current public article claims:

- NEW Summer 200K 2-Step
- 10/5 $249
- 8/5 $279
- funded split 80%
- payout cap $3,000
- 200K fixed account

`/prop-firm-payout-comparison`

- `Summer Plan 200K`
- split 80%
- payout cap $3,000
- minimum $250

### Triple check — current official Summer offering

Check 1 — current official Summer Plan product page
`https://the5ers.com/summer-plan/`

Current rendered product:
- Summer Plan centered on $100K
- 1-Step $249
- current funded 1-Step split 75/25
- payout cap $2,000
- minimum withdrawal $250
- 2-Step Summer options described as routes to $100K

Check 2 — current The5ers homepage program selector
`https://the5ers.com/`

Current Summer Plan display:
- $100K
- 1-Step current table
- 75/25 split
- $2,000 payout cap
- $250 minimum withdrawal

Check 3 — current official Summer Plan 2026 article
`https://the5ers.com/prop-firm-summer-plan-2026/`

- describes two evaluation paths to a $100,000 account
- current Summer entry starting at $149
- no current 200K Summer offer described

Fresh exact searches for `Summer Plan 200K`, `200,000 Summer Plan`, and `$3,000 Summer payout cap` on the current The5ers domain did not return a current CFD Summer 200K product page.

### Result

The public 200K Summer sections are no longer supported by the current official Summer offering observed on 2026-08-26.

Status：`CORRECTION_REQUIRED / CURRENT_PRODUCT_REMOVED_OR_SUPERSEDED`

### Safe correction direction

Do not silently convert every old 200K number into 100K numbers.

Required Production patch direction after source reconciliation:

1. remove / archive current-product claims for Summer 200K unless checkout/current source proves still purchasable,
2. make current Summer section 100K-led,
3. use current plan-specific values only,
4. preserve historical 200K only in history/legacy context if evidence warrants,
5. fresh Check 3 again immediately before publish.

---

## 4. SuperFunded minimum payout

### Public surface observed

`/prop-firm-payout-comparison`

Current wording:
`公式FAQでは全プラン共通の最低申請額を確認できませんでした。`

### Official recheck

Current Rules and Conditions V2.0 dated 2026-01-29 states:

- Minimum Payout = $100
- profit share applied first, then minimum payout threshold checked
- Payout Waiting Period = 14 days
- initial three approved payouts Profit Cap = 5% of Nominated Bankroll

Older official Rules documents also state $100, which corroborates continuity.

However, current public FAQ page does not expose the same minimum-payout field in its rendered FAQ text.

### Result

Public wording is conservative rather than false.

Status：`UPDATE_CANDIDATE / SINGLE-CURRENT-DOCUMENT LIMITATION`

Do not patch merely to make the page more specific until Check 3 at implementation time confirms the current V2 Rules remain governing and no product-specific override exists.

---

## 5. FTM payout comparison — Nitro / 2-Step Plus

### Public surface observed

- on-demand after conditions
- 5 profitable trading days
- each qualifying day >=0.5%
- minimum simulated profit = 1% of initial balance before split
- Nitro funded consistency example 45%

### Triple check

Check 1 — official general minimum trading days FAQ
`https://fundedtradermarkets.com/faq/is-there-a-requirement-for-a-minimum-number-of-trading-days`

- Nitro simulated funded: 5 days
- 2-Step Plus simulated funded: 5 days
- only days >=0.5% profit count

Check 2 — official General Trading Rules category / other locale
Same current requirement is reproduced in current official FAQ category/locales.

Check 3 — official Payments and Withdrawals FAQ/current page
- minimum simulated profit for payout = 1% initial balance before split

Current FTM pages also preserve on-demand structure.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED` for the scoped Nitro / 2-Step Plus payout summary.

Do not generalize to Nitro X / Instant Pro / newer cohorts.

---

## 6. Wave 1 correction queue

### P0 correction after internal Git recovery + Production reconciliation

1. FTM Nitro X reward split wording
2. The5ers Summer 200K current-product claims on:
   - `/the5ers-summer-plan`
   - `/prop-firm-payout-comparison`

### P1 update candidate

3. SuperFunded minimum payout $100 — only after fresh current-rule/override recheck

### No correction from this Wave

- Fintokei payout 3-day / 5-day distinction
- FTM Nitro / 2-Step Plus 5 profitable days + 1% minimum profit

---

## 7. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked.

When auth recovers:

1. reconcile actual Production source first,
2. confirm affected strings/routes still exist,
3. run Check 3 fresh again,
4. minimal patch only,
5. regression / protected hashes / 390px / compliance,
6. central/human publish approval.

Final Status：
`WAVE1_AUDIT_COMPLETE_CORRECTIONS_QUEUED_NO_PRODUCTION_CHANGE`
