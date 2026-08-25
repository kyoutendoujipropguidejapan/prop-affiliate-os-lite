# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 11 / ENGLISH-FIRST PRICE + PROMO

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開LPの価格確認中カード・Futures promo・locale優先再監査
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Operating rule

General product/rule/price facts:
1. current English official product/purchase surface
2. current English official Help / Rules / FAQ
3. fresh recheck immediately before implementation

Japan-specific facts remain separately gated.

Japanese/localized page lag is not used to overrule a fresher English primary source, but official English conflicts are never resolved by majority vote.

---

## 1. The5ers Futures — Day Trade 25K price

### Public surface observed

Current LP shows:
`The5ers Futures｜Day Trade — 現在、公式価格を確認中`

### Check 1 — current English official Futures product page
`https://the5ers.com/futures/`

Current 25K Day Trade card shows:
- Price：$59
- Activation fee：None
- Profit target：6%
- Max Loss EOD：4%
- Consistency：40%

### Check 2 — English official Futures FAQ
`https://the5ers.com/futures-faqs/the5ers-futures-evaluation-programs-explained/`
Last update：2026-06-10

Confirms:
- 25K price：$59
- 6% target
- 40% consistency
- 4% drawdown

The article contains historical wording around activation fees and a temporary no-activation-fee month, so the current product page remains the current fee authority.

### Check 3 — fresh current English product recheck
Fresh 2026-08-26 recheck continues to render:
- 25K $59
- activation fee none
- 4% EOD max loss
- 40% consistency

### Result

Status：`TRIPLE_VERIFIED_CURRENT_PRIMARY`

Public `価格確認中` is now stale/conservative.

Safe correction after Production reconciliation:
- Day Trade 25K current price：`$59`
- activation fee：`なし`
- retain fresh checkout confirmation requirement before publish

This does not make any statement about the separate CFD Summer 200K plan.

---

## 2. Blueberry Futures — Accelerated 25K price

### Public surface observed

Current LP shows:
`Blueberry Futures｜Accelerated — 現在、公式価格を確認中`

### Check 1 — current English official homepage
`https://blueberryfutures.com/`
Fresh current render:
- Accelerated 25K standard：$110.40
- current 60% promo display：$44.16
- FUTURES60 visible on the same current purchase surface

### Check 2 — English official Help price article
`https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations`

States:
- Accelerated 25K standard：$129
- after 60% discount：$51.60

### Check 3 — English official detailed-parameters article
`https://help.blueberryfutures.com/en/articles/12890893-detailed-parameters-of-our-challenges`

Also states:
- Accelerated 25K after 60%：$51.60

### Result

Current official English surface conflict remains:
- current homepage：$110.40 / $44.16
- Help：$129 / $51.60

Status：`OFFICIAL_PRICE_CONFLICT / HOLD`

Operational rule:
- do not choose homepage merely because it looks newer
- do not choose Help merely because two Help articles agree
- keep public price hidden/confirmation state until current checkout or direct official clarification resolves the discrepancy

---

## 3. Blue Guardian Futures — Reserve multi-account commercial claim

### Public surface observed

Current LP labels as confirmed:
- Reserve 25K x1：40% off
- Reserve 25K x5：4 accounts purchased + 1 account free style benefit

### Check 1 — current English official Futures purchase surface
`https://origin.blueguardian.com/futures`

Current rendered purchase UI shows the newer progressive tiers for additional accounts:
- 2 accounts 30%
- 3 accounts 35%
- 4 accounts 40%

### Check 2 — official current promotion article, published 2026-08-11
`https://blueguardian.com/blogs/blue-guardian-futures-multi-account-discounts`

States current structure:
- first 25%
- second 30%
- third 35%
- fourth 40%
- fifth Standard/Direct/Express 100%
- fifth Reserve 70%

### Check 3 — English official Help Center
`https://helpfutures.blueguardian.com/en/articles/15693969-how-does-bundle-pricing-work`

Still states:
- 1 account 40%
- 2 accounts 45%
- 3 accounts 50%
- 4 accounts 55%
- 5 accounts buy 4 get 1 free

Its Reserve table also prices the 5-pack as effectively one free account.

### Result

Official English conflict is material.

Status：`COMMERCIAL_CONFLICT / PUBLIC_CONFIRMED_BADGE_UNSAFE`

Safe correction direction if checkout cannot settle it at implementation time:
- downgrade public Reserve bundle cards from `確認済み` to `確認中`
- suppress exact discount/benefit until checkout/current campaign source is reconciled

Do not overwrite history; this likely represents a campaign transition or stale Help article, but that explanation is not yet proven.

---

## 4. Fintokei NEW20 — English-first commercial confirmation

Three-check evidence now supports the general/global claim:
- current official homepage：NEW20 / first challenge / 20%
- official 2026 price/program guide：NEW20 works for any first challenge
- fresh English current surfaces still advertise 20% first-challenge benefit

Status：`TRIPLE_VERIFIED_GENERAL_SCOPE / JP_CHECKOUT_CAUTION`

Japanese homepage text omission is not negative evidence.
Final checkout price remains the required last-mile confirmation.

---

## 5. Wave 11 correction queue

### Ready after auth + Production reconciliation + fresh Check3
1. The5ers Futures Day Trade 25K: remove `価格確認中`, current price $59, activation fee none

### Continue HOLD / confirmation state
2. Blueberry Futures Accelerated 25K price
3. Blue Guardian Futures Reserve multi-account exact promo values

### No removal / no correction instruction
4. The5ers CFD Summer 200K remains outside this Futures price audit and is not a deletion target.

Final Status：
`WAVE11_COMPLETE_THE5ERS_FUTURES_PRICE_READY_BLUEBERRY_AND_BG_FUTURES_HELD`
