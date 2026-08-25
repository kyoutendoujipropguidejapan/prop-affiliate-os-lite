# FUNDED7 HOLD RECHECK

確認日：2026-08-26 JST
Status：CURRENT OFFICIAL CONFLICT RECONFIRMED / HOLD CONTINUES
Production code changes：NONE
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 1. Purpose

M14でHOLDとなっているFunded7 1フェーズ / Instantに加え、公開LP監査でConflict化したPAYGについて、Current official webを最低3方向で再確認し、解消可否を評価する。

同じページの再読は独立Checkとしない。official同士の不一致は多数決で解消しない。

---

## 2. One Phase — HOLD continues

### Check 1 — current Challenge Comparison EN/JP

`https://funded7.com/challenge-comparison/`
`https://funded7.com/ja/challenge-comparison/`

Current comparison currently states:
- Profit Target 10%
- Max Daily Loss 4%
- Max Total Loss 8%
- Trailing / relative drawdown
- Profit Split 50/50
- min3 days / 10 trades
- MT5 / cTrader
- payout7 days

### Check 2 — current One Phase product EN/JP

`https://funded7.com/one-phase/`
`https://funded7.com/ja/one-phase/`

Current live product page states:
- Profit Target 10%
- Max Daily Loss 5%
- Max Total Loss 10%
- Trailing
- Profit Split 50%
- min3 days
- MT5 / cTrader
- payout7 days

### Check 3 — dedicated One Phase FAQ EN/JP

`https://funded7.com/faq/one-phase-challenge/`
`https://funded7.com/ja/faq/one-phase-challenge/`

Dedicated FAQ currently states:
- Target10%
- Daily4%
- Total8%
- min3 days / 10 trades

### Additional current official blog

`https://funded7.com/blog/how-to-pass-the-funded7-challenge-a-step-by-step-guide/`

Published June 2026 and currently live:
- One Phase Daily4%
- Total8%
- trailing
- split starts50/50, add-on context

### Result

Current official conflict is now sharply confirmed:

- Daily Loss：`4% vs 5%`
- Max Total Loss：`8% vs 10%`

Profit Split is now more consistently 50/50 in the current comparison/product/blog, while an older comparison/FAQ surface had previously shown80%; do not use that improvement to resolve the DD conflict.

Status：
`FUNDED7_ONE_PHASE_HOLD_CONTINUES_CURRENT_OFFICIAL_CONFLICT`

Do not publish a single definitive Daily/Max value until a current authoritative purchase/rules source or direct official clarification explains which source governs new purchases.

---

## 3. Instant Funding — HOLD continues

### Check 1 — current Challenge Comparison EN/JP

Current comparison states:
- no evaluation target in JP view
- Daily5%
- Max Total8%
- Trailing
- Profit Split50/50
- min3 days / 10 trades
- MT5 / cTrader
- payout7 days

### Check 2 — current Instant product EN/JP

`https://funded7.com/instant-funding/`
`https://funded7.com/ja/instant-funding/`

Current product page states:
- Daily5%
- Max Total10%
- Trailing
- Profit Split50/50
- min3 days
- payout7 days

### Check 3 — dedicated Instant FAQ

EN:
`https://funded7.com/faq/instant-funding-challenge/`

Current-accessible dedicated FAQ states:
- Daily5%
- Max Total6%
- Profit Split50%

JP:
`https://funded7.com/ja/faq/instant-funding-challenge/`

Current-accessible JP FAQ instead says risk limits are assigned under OREF tiers and does not expose one universal Max Total value.

### Additional current official blog

June 2026 guide states:
- Daily5%
- Max Total8%
- trailing
- split50/50

### Result

Current official ecosystem concurrently represents Max Total Loss as:
- `6%`
- `8%`
- `10%`
- `OREF tier-dependent`

Daily5% and split50% are comparatively stable, but the total-loss rule is materially unresolved.

Status：
`FUNDED7_INSTANT_HOLD_CONTINUES_CURRENT_OFFICIAL_CONFLICT`

Do not select one value based on newest-looking URL or crawl date.

---

## 4. PAYG — HOLD added by retrospective public audit

### Public LP currently used

The current public article has used:
- target8% / 6%
- Daily4%
- Max8%
- Static
- MT5
- 80/20

### Check 1 — current Challenge Comparison EN

Current PAYG row states:
- target8% /6%
- Daily5%
- Max10%
- Static
- min3 days /10 trades
- 80/20
- MT5
- payout7d / minimum$100

### Check 2 — current Challenge Comparison JP

Again states:
- Daily5%
- Max10%
- absolute/static drawdown
- 80/20
- MT5

### Check 3 — current-accessible official June 2026 guide

`https://funded7.com/blog/how-to-pass-the-funded7-challenge-a-step-by-step-guide/`

States PAYG:
- target8% /6%
- Daily4%
- Max8%
- Static
- MT5
- 80/20

### Dedicated PAYG product route

Current dedicated PAYG page explains staged payment and the same-rules relationship between phases, but in the captured static text does not provide a separate authoritative DD pair sufficient to break the conflict.

### Result

Official conflict remains:

`Daily5 / Max10` vs `Daily4 / Max8`

Status：
`FUNDED7_PAYG_HOLD_CURRENT_OFFICIAL_CONFLICT`

Do not silently switch the public LP from4/8 to5/10. Required resolution path:
1. live checkout/configurator for the exact current PAYG account,
2. dedicated current rules/terms if exposed,
3. direct Funded7 confirmation if conflict survives,
4. fresh Check3 immediately before implementation.

Until resolved, safest public numeric handling is `公式情報を確認中` rather than choosing either pair.

---

## 5. Two Phase control check

Current Challenge Comparison, current product flow and current June guide materially agree on the standard Two Phase core:
- target8% /6%
- Daily5%
- Max10% Static
- min3 days /10 trades
- 80/20

This control confirms the audit method is capable of finding agreement where official sources actually align.

Status：`CONTROL_CURRENTLY_ALIGNED`

It does not resolve One Phase / Instant / PAYG.

---

## 6. PAYG allocation / payout-cap facts

Current official Funded7 pages/FAQ continue to support:
- PAYG payment is staged; the next stage fee is paid only after the current stage is passed
- PAYG sits outside the standard maximum allocation cap structure
- PAYG monthly payout cap = $20,000

Status：`SUPPORTED_SCOPED`

These facts do not imply the disputed DD values are resolved.

---

## 7. Governance decision

Do not unblock:
- One Phase
- Instant Funding
- PAYG disputed DD fields

Rules:
- FAQ Schema：exclude affected conflict claims
- Diagnosis Top3：existing block continues unless separately accepted current evidence exists
- Public Detail：use `公式情報を確認中` / conflict-safe wording
- do not pick newest-looking source solely by date
- direct contact, if obtained, must explain or scope the published-source conflict; it does not erase the conflicting evidence history
- preserve cohort/tier/OREF distinctions

---

## 8. Compliance note

Some current Funded7 pages use marketing language such as funded capital, real payout and spendable cash. Our site must not mechanically copy marketing terminology into a regulatory/service-nature claim.

Before Firm Detail publication, establish service nature from current Terms/legal/risk disclosure and keep factual plan mechanics separate from editorial/commercial wording.

Final Status：
`FUNDED7_ONE_PHASE_INSTANT_PAYG_CURRENT_HOLD_RECONFIRMED`
