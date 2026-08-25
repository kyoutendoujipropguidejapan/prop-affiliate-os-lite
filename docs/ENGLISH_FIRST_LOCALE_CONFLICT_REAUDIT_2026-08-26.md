# ENGLISH-FIRST LOCALE CONFLICT RE-AUDIT

更新日：2026-08-26 JST
Status：RE-AUDIT COMPLETE / NO PRODUCTION CHANGE
Depends on：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

日本語ページが英語原本より遅れて更新される可能性を考慮し、locale差が主要因だった既存監査項目をcurrent English official sourceから再監査する。

---

## 1. The5ers Futures — Max Loss / Consistency

### Check 1 — current EN Futures product page
`https://the5ers.com/futures/`

Current Day Trade 25K card:
- Profit Target: 6% evaluation / 4% funded
- Max Loss (EOD): 4% / 4%
- Consistency Rule per position: 40% / 40%
- Price: $59
- Activation fee: None

### Check 2 — current EN Futures FAQ
`https://the5ers.com/futures-faqs/what-is-the-consistency-rule/`

Last update: 2026-07-20.
- Futures consistency = 40%
- applies to funded accounts too

### Check 3 — current JP Futures product page + fresh EN recheck
`https://the5ers.com/jp/futures/`

Current JP product surface independently renders:
- Max Loss (EOD) 4%
- Consistency 40%
- Price $59
- no activation fee

Fresh EN page recheck matches.

### Older official article
`https://the5ers.com/how-does-a-futures-prop-firm-works/`

Older article still contains 3% / 30% values, but explicitly labels them typical parameters and instructs users to verify current terms at the current Futures product page.

Therefore this older article is treated as a stale/historical official article, not as equal-weight Current Truth against the current dedicated product + current FAQ.

### Result

Current operational values:
- Max Loss EOD = 4%
- Consistency = 40%
- Day Trade 25K price = $59
- activation fee = none

Status:
`CURRENT_PRIMARY_TRIPLE_VERIFIED_WITH_HISTORICAL_SOURCE_CAUTION`

Do not keep a current HOLD solely because an older article still exposes 3% / 30%.

---

## 2. Hantec Endurance — availability status

### Current EN evidence

Dedicated EN Endurance page:
`https://htrader.hmarkets.com/programs/endurance/`

Body provides:
- account sizes through $200K
- rules
- prices
- `GET STARTED`
- purchase-process wording

Current EN Help article:
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445800-endurance-3-step-challenge-`

Modified 2026-08-20 and provides full current Endurance rules/add-ons/payouts.

### Remaining contradiction

The same EN product page navigation still labels Endurance `Coming soon` while the page body exposes purchase controls and checkout language.

Therefore this is **not merely a JP translation lag**. The contradiction exists inside the current English official surface itself.

### Result

Core Endurance rules can remain verified.

Active purchase availability status remains:
`AVAILABILITY_CONFLICT / CHECKOUT_CONFIRMATION_REQUIRED`

Do not resolve by language priority alone.

---

## 3. Fintokei NEW20 — Japan scope

Current global EN official supports `NEW20` / 20% off first challenge.

However Japan applicability is a Japan-specific commercial Fact.

Therefore English-first confirms the global campaign, but Japan scope still requires:
- Japanese/local checkout acceptance, or
- direct current official confirmation.

Status unchanged:
`GLOBAL_VERIFIED / JAPAN_SCOPE_PENDING`

---

## 4. The5ers Summer 200K

Current English static Summer landing page is 100K-led.
Official Hub purchase flow is dynamic and not fully exposed to static crawler.

This does not prove 200K is absent.

Project record:
`NO USER DELETION INSTRUCTION / CURRENT AVAILABILITY ASSERTED BY OPERATOR / OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING`

No removal or 100K-only conversion is authorized.

---

## 5. Governance effect

Going forward:
- current English official source is the default freshness anchor for general product/rule facts;
- Japanese pages remain essential for Japan-specific scope;
- older official articles can be classified stale/superseded when they explicitly defer to current product terms and newer dedicated sources disagree;
- current English internal contradictions still produce HOLD/CONFLICT;
- static absence never proves product discontinuation.

Final Status:
`LOCALE_REAUDIT_COMPLETE / THE5ERS_FUTURES_CURRENT_VALUES_RESOLVED / HANTEC_ENDURANCE_AVAILABILITY_STILL_CONFLICTED / NEW20_JAPAN_SCOPE_PENDING`
