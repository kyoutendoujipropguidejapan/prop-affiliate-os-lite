# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 8 / FINTOKEI + FUNDORA

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中 Fintokei / Fundora の主要Fact
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Method

- current official product page
- current official Help/FAQ
- separate current official rule/article/price notice
- purchase date / cohort / localeを分離
- public crawlerで観測できるLP表示と照合
- Production sourceは内部Git認証HOLD中のため編集しない

---

## 1. Fintokei SwiftTrader / 速攻プロ — public conflict display

### Public surface observed

Current public LP still displays SwiftTrader as `公式情報を確認中` and shows old/new values side by side:

- Profit target: `公開FAQ 10%／8月案内 6%`
- Daily Loss: `公開FAQ 3%／8月案内 2%`
- Max Loss: `公開FAQ 6%／8月案内 3%固定`
- Minimum Trading Days: `公開FAQ 5日／8月案内 最短3日`

It remains excluded from Diagnosis Top3.

### Check 1 — current official JP SwiftTrader product page
`https://www.fintokei.com/jp/swifttrader/`

Current product page states:
- one evaluation phase
- target 6%
- minimum 3 trading days
- maximum 60 evaluation days
- Daily Loss -2%
- Total Loss -3%
- performance reward 90%
- minimum profit per reward +3%
- 30-day activity requirement

### Check 2 — current official EN SwiftTrader challenge rules
`https://support.fintokei.com/en/articles/12040973-how-does-swifttrader-challenge-work-what-are-the-rules`

For accounts purchased after 2026-07-15:
- target 6%
- Daily Loss 2% equity
- Max Loss 3% from starting balance
- min3 trading days
- max60 evaluation days
- evaluation daily profit cap 3%

The same article separately retains the previous 10/3/6 cohort as historical/pre-2026-07-15 rules.

### Check 3 — current official EN account-maintenance rules
`https://support.fintokei.com/en/articles/8409176-what-rules-do-i-have-to-follow-to-keep-my-swifttrader-account`

Again separates purchase cohorts and confirms for post-2026-07-15:
- Daily2% equity
- Max3% static
- minimum3 trading days for evaluation / payout qualification scope stated by the article
- max60 evaluation days
- 30-day activity rule

### Additional corroboration — current JP SwiftTrader overview
`https://support.fintokei.com/ja/articles/8408932-速攻プロプラン-swifttrader-とは`

Again states post-2026-07-15:
- performance reward 90%
- evaluation profit target 6%

### Result

The current public `10/3/6/5 vs 6/2/3/3` display is no longer a live unresolved conflict. It is a cohort distinction.

Status：`CORRECTION_REQUIRED / HIGH_PRIORITY / COHORT_AWARE`

Safe current display:

`2026-07-15以降購入：利益目標6%／日次損失2%（Equity）／最大損失3% Static／最低3取引日`

Historical note:
`2026-07-15より前の対象口座は旧条件（10%／3%／6%／5日）が適用。`

Do not overwrite the historical cohort.

### Diagnosis gate

The numeric conflict reason can be removed after actual Production source reconciliation.

However, re-entry into Diagnosis Top3 is a separate decision and must only occur after:
- current Production data is reconciled,
- eligibility/source-health gates are clear,
- fresh implementation-time verification,
- protected Diagnosis logic remains unchanged unless separately approved.

This audit does **not** auto-enable SwiftTrader in Diagnosis.

---

## 2. Fintokei SwiftTrader — payout/evaluation day distinction

The project previously detected a possible `3日 vs 5日` discrepancy in payout content.

Current official sources show purchase-date/cohort and context distinctions. The public payout comparison that says SwiftTrader payout conditions can involve 5 days must not be mechanically replaced by 3 solely because the current evaluation minimum is 3 days.

Status：`SCOPE_SENSITIVE / DO_NOT_BULK_REPLACE`

Before editing payout-specific text, recheck the dedicated payout FAQ, not just evaluation rules.

---

## 3. Fintokei platforms

Current public Firm card:
`MT4 / MT5 / cTrader / TradingView`

Current Fintokei product/support ecosystem continues to expose MT4/MT5/cTrader and TradingView access in the supported cTrader context.

Status：`CURRENT_SUPPORTED / NO CORRECTION REQUIRED`

Do not present TradingView as a standalone broker/account type when it is an interface/connection path.

---

## 4. Fintokei service-nature wording

Current official SwiftTrader FAQ explicitly states:
- Fintokei provides trading education/evaluation
- no customer deposits tied to real trading
- no financial services
- provided accounts are virtual demo environments
- Fintokei is not a broker
- website information is educational/general market commentary, not investment advice

Status：`CURRENT_OFFICIAL_CONFIRMED`

Public/Firm Detail copy must preserve this distinction.

---

## 5. Fundora — current evaluation core

### Public surface observed

Current public Firm card uses a generic Fundora 2-Step model:
- target 8% / 5%
- Daily Loss 5%
- Max Loss 10% fixed-equivalent
- minimum3 days each phase
- news trading allowed
- weekend holding allowed
- payout first28 days then14 days / 80%
- Pro stage 33.3% consistency warning

### Check 1 — current official Fundora shop/home
`https://shop.fundora-trading.com/`

Confirms:
- 2 phases
- 8% / 5%
- min3 days
- Daily5%
- Max10%
- 80% share
- no evaluation time limit, with 30-day inactivity rule
- demo environment

### Check 2 — current official Fundora FAQ
`https://shop.fundora-trading.com/pages/faq`

Confirms:
- Phase1 target8 / Phase2 target5
- Daily5 / Total10
- minimum3 days
- cTrader
- first reward from 28 days after Pro account trading starts, then every14 days if conditions are met
- 80% compensation
- demo-account service nature

### Check 3 — current official Trading Rules guide
`https://fundora-trading.com/blog/fundora-trading-rules-guide`

Again confirms:
- 8% / 5%
- Daily5 / Max10
- minimum3 days each phase
- news trading allowed
- weekend position holding allowed for all supported instruments
- crypto-only weekend market trading
- 80% compensation after evaluation
- demo environment

### Result

Status：`TRIPLE_VERIFIED / CORE RULES`

No correction required for the current public generic Fundora core rule summary.

Clarification candidate:
`週末持ち越し可` is correct for positions, but `週末に市場で取引可能` is not universal; current rules say weekend trading itself is crypto-only. Keep the concepts separate.

---

## 6. Fundora — 33.3% rule

### Check 1 — current official JP 33.3% rule article
`https://fundora-trading.com/blog/risk-management-about-the-333-rule`

### Check 2 — official shop mirror 33.3% rule article
`https://shop.fundora-trading.com/blogs/aboutfundora/risk-33`

### Check 3 — current Trading Rules guide

All materially agree:
- not applied in Challenge Phase1/Phase2
- applies to Pro demo account reward eligibility
- maximum daily profit / total profit <= 33.33% framework

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

Current public company-level warning `Pro段階は33.3% consistencyに注意` is properly scoped.

---

## 7. Fundora — payout cycle

### Triple check

Check 1 — official FAQ
- initial reward from 28 days after Pro trading begins
- later every14 days
- unmet conditions postpone to next14-day cycle

Check 2 — official standardization notice
`https://fundora-trading.com/news/important-clarification-of-payout-date-and-standardization-of-website-terminology`

Explicitly confirms first28 / subsequent14 and postponement when conditions are unmet.

Check 3 — shop notice mirror
`https://shop.fundora-trading.com/blogs/news/terminology`

Materially repeats the same payout-cycle interpretation.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

Do not phrase `28日` as a guarantee of payment exactly on day28; it is an earliest scheduled eligibility point conditional on all reward requirements.

---

## 8. Fundora — platform

Current official FAQ and current purchase-flow page identify cTrader.

Current public Firm card says `公式案内で確認`.

Status：`UPDATE_CANDIDATE`

Safe direction after Production reconciliation:
`cTrader`

Do not infer additional platforms without separate evidence.

---

## 9. Fundora — current standard pricing conflict across official surfaces

The project has used the March 2026 standard prices:
- Entry ¥26,999
- Lite ¥36,999
- Growth ¥66,999
- Standard ¥99,999
- Professional ¥249,999
- Master ¥449,999

### Current official March price revision
`https://fundora-trading.com/news/price-revision-terms-and-customer-harassment-policy-march-2026`

Confirms the six standard prices above and states existing purchased/in-progress plans are unaffected.

### Current legacy/shop pricing surface
`https://shop.fundora-trading.com/pages/pricing`

Still renders older:
- Professional ¥193,999
- Master ¥319,999
while Entry/Lite/Growth/Standard match.

### Current main-site plan route
`https://fundora-trading.com/plan`

Dynamic route exposes the current purchase flow but static extraction does not provide all six JPY tabs in one reliable capture.

### Result

There is a live official-surface discrepancy for Professional/Master pricing.

Status：`OFFICIAL_SURFACE_CONFLICT / PURCHASE_FLOW_PRIORITY_REQUIRED`

Do not downgrade the March 2026 announced standard prices solely because the old shop pricing page remains live.

Before any public price edit:
1. check the actual current JPY purchase/configuration tab,
2. confirm March price notice remains governing,
3. fresh-check immediately before publish.

The public current generic Firm card does not expose these prices, so no immediate public correction is required from this conflict.

---

## 10. Fundora current campaign boundary

The Fundora `FND25` first-challenge-support campaign exists only in the accepted local Work commit and has not been confirmed on current Production due the internal Git blocker.

Do not infer deployment from public crawler absence.

Status：`LOCAL_ACCEPTED / PRODUCTION_NOT_CONFIRMED`

If auth recovery occurs while the campaign window remains relevant, reconcile actual Production source and campaign timing before any publish action.

---

## 11. Wave 8 queue

### P0 after internal Git recovery + Production reconciliation

1. Fintokei SwiftTrader public conflict card
   - convert old/new `conflict` into explicit purchase-date cohorts
   - post-2026-07-15 current = 6 / 2 / 3 / 3 days
   - preserve pre-2026-07-15 legacy

### P1

2. Fundora platform display
   - generic -> cTrader

3. Fundora Professional/Master prices
   - no public edit yet; reconcile live purchase JPY tabs vs March standard-price notice vs old shop page

### No correction

4. Fundora core 8/5, 5/10,3 days,80%
5. Fundora 33.3% Pro-only consistency scope
6. Fundora first28/subsequent14 conditional cycle
7. Fintokei platform family

---

## 12. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

Before any Production patch:
1. reconcile actual source and Version/SHA
2. fresh official Check3
3. preserve cohort/variant semantics
4. minimal patch only
5. regression + protected hashes + 390px + compliance
6. human publish approval

Final Status：
`WAVE8_AUDIT_COMPLETE_FINTOKEI_COHORT_CORRECTION_FUNDORA_CORE_VERIFIED_PRICE_SURFACE_CONFLICT_NO_PRODUCTION_CHANGE`
