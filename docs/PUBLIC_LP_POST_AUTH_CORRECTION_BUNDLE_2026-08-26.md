# PUBLIC LP POST-AUTH CORRECTION BUNDLE

更新日：2026-08-26 JST
Status：CURRENT CONSOLIDATED QUEUE / DO NOT IMPLEMENT BEFORE AUTH + PRODUCTION RECONCILIATION
Depends on：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開LPの遡及3重ファクトチェックで確定した修正候補・HOLD・Do Not Touchを、内部Git認証復旧後にWorkへ渡すための現行Queueとして一本化する。

本書はコード変更・Production変更・publish承認ではない。

General product/rule facts are checked English-first. Japan-specific facts remain separately gated.

---

## Gate 0 — mandatory before any patch

1. internal origin auth/fetch recovery
2. confirm branch / local HEAD / remote HEAD / ahead-behind / clean worktree
3. confirm actual current Production Version/SHA
4. confirm Evidence commit `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f` disposition
5. confirm Fundora commit `2191f06dc56006b4018f16ec8c2ac51161d2f70a` disposition
6. confirm protected hashes
7. inspect actual affected strings/routes in Production source
8. fresh Check 3 for every changed claim
9. current English official product/rules/help is the default freshness anchor for general facts
10. Japan eligibility / JPY price / Japan-only promo / Japanese-support scope gets a separate local gate
11. any unresolved material official conflict stays HOLD
12. if Production source differs materially from the audit snapshot -> STOP and reclassify

---

## P0-A — accepted local backlog

### Evidence Phase1
Preserve exact accepted commit:
`3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`

### Fundora campaign
Preserve exact accepted commit:
`2191f06dc56006b4018f16ec8c2ac51161d2f70a`

Campaign window:
2026-08-25 20:00 JST → 2026-09-01 23:59 JST

If auth returns after the campaign is no longer useful, do not blindly publish stale campaign UI. Reconcile and decide through the approved path; do not rewrite accepted history casually.

---

## P0-B — public factual corrections ready for minimal patch after reconciliation

### 1. Fintokei SwiftTrader cohort framing
Current public issue:
old/new values are framed as unresolved official conflict.

Safe current structure:
- purchases on/after 2026-07-15: target6 / Daily2 Equity / Max3 Static / min3 evaluation days
- applicable older cohort: target10 / Daily3 / Max6 / min5

Do not bulk-replace payout-specific `5日`; payout eligibility has a separate rule context.
Do not auto-return SwiftTrader to Diagnosis Top3 in the same correction patch.

### 2. Blueberry Funded Instant Lite current cohort
For purchases on/after 2026-08-17:
- Daily2%
- Max4% Static
- no minimum trading days
- payout consistency15%
- standard14-day reward cycle
- 80% split, with current scaling context where applicable

Preserve older cohorts separately.

### 3. Blue Guardian 1 Step Standard
Current-new cohort purchased on/after 2026-08-20:
- target9%

Older applicable cohort:
- target10%

### 4. Blue Guardian 2 Step Standard
Current-new cohort purchased on/after 2026-08-20:
- min3 profitable days

Older applicable cohort:
- 5 days

### 5. FTM Japanese-support wording
Replace stale future-facing wording with safe current wording such as:
`日本語サイト・FAQあり。重要なプラン固有条件は英語原文・購入画面も確認。`

Do not claim complete/full Japanese localization.

### 6. FTM Nitro X reward wording
Current public `最大80%` is stale.

Safe direction:
`On-demand／引き出し対象部分は100%配分（総利益の50%をリスクバッファとして口座に維持）`

Do not advertise only `100%` without the buffer condition.

### 7. FTM dedicated article program count
Current public article says `現行5プラン` and omits Nitro X.

Safe direction after fresh check:
`現行6プラン：1 Step Nitro、1 Step Nitro X、2 Step Plus、Instant Standard、Instant Pro、Instant Plus`

Instant Pro rule conflict remains separate.

### 8. Blueberry Futures funded consistency
Replace company-wide `35%` wording with plan-specific:
- Ascent 35%
- Accelerated 20%

This is funded payout consistency, not evaluation consistency.

### 9. The5ers Futures Day Trade 25K
Current English official product + FAQ + fresh recheck support:
- current price $59
- activation fee none
- Max Loss EOD4%
- consistency40%

Current public `価格確認中` card is stale/conservative.

Safe direction:
- show Day Trade 25K current price `$59`
- activation fee `なし`
- keep final purchase-screen confirmation

This is unrelated to the CFD Summer 200K plan.

### 10. Funded7 PAYG public article conflict-safe correction
Current `/pay-after-pass-payg` states PAYG as definite:
`日次4%・最大8%の固定型`

Current official English sources conflict:
- challenge comparison：Daily5 / Max10 / Static
- official 2026 guide：Daily4 / Max8 / Static

Safe replacement until resolved:
`PAYGの損失上限は現行公式ページ間で差異を確認中。購入前にPAYGの購入画面・専用ルールを確認。`

Do not choose 5/10 or 4/8 in this patch.

### 11. Home/page freshness metadata
Replace stale global-style dates with page/section-level `last verified` where architecture permits.

Do not imply every page Fact was checked on one date.

---

## P1 — clarification / coverage updates

### 12. Hantec Instant Lite
Central approved:
`HOLD -> VERIFIED_WITH_CAUTION`

Display:
`標準5% Trailing（決済後残高追随→5%利益到達後に開始残高でLock）／+1% Max Loss Add-onで6%`

Trading-day scope:
`評価・開始の最低取引日数：なし／出金周期の条件：5利益日（各0.5%以上）`

### 13. Hantec EnhancedX minimum days
Safe direction after fresh check:
`最低取引日数：なし（ただしChallengeはConsistency 35%以下が必要。対象Add-onで評価側Consistency解除可）`

### 14. Fundora platform
Current official platform:
`cTrader`

Replace generic platform wording only after actual Production-source inspection.

### 15. Blue Guardian Nano coverage
Current official models include:
- 1 Step Nano
- 2 Step Nano

Do not add pricing until current purchase surface is confirmed.

### 16. Blueberry Prime minimum days
Safe current wording after fresh check:
`現行新規購入は3日/Phase。旧購入条件・一部表示では5日を保持するため購入日を確認。`

### 17. FundingPips 2 Step Standard reward options
Do not collapse current structure to one `7日／80%` value if Production does so.

Current official options include weekly60%, bi-weekly80%, monthly100%, and conditional on-demand90%.

### 18. FundingPips Zero profitable-day threshold
Where displayed:
`7 profitable days / rolling30, each >=0.25%`

### 19. Trading Cult Pro platform
Current official family uses MT5.

Change generic platform wording to `MT5` only after model-specific source check.

### 20. Fintokei NEW20 commercial status
Current English official surfaces triple-support:
- NEW20
- 20% off
- first challenge / any first challenge wording

Status:
`TRIPLE_VERIFIED_GENERAL_SCOPE / JP_CHECKOUT_CAUTION`

Japanese homepage omission is not negative evidence. Keep final checkout confirmation and do not guarantee final price.

---

## COMMERCIAL / RULE HOLD — do not choose one side

### A. Funded7 One Phase
Official conflict remains:
- comparison / FAQ / guide：Daily4 / Max8
- current product page：Daily5 / Max10

### B. Funded7 Instant
Current official Max Total is represented as 6 / 8 / 10 / OREF-dependent across official surfaces.

### C. Funded7 PAYG exact loss values
Current official English conflict:
- comparison：Daily5 / Max10
- official guide：Daily4 / Max8

Public article must become conflict-safe, but canonical numeric value remains HOLD.

### D. FTM Instant Pro
Official conflict remains:
- dedicated FAQ Daily3%
- other official Instant page includes no-Daily-DD language while comparison shows3%

### E. FundedElite Flash Activation exact customization matrix
Core $5 → pass → activation-fee flow is verified.

HOLD remains for universal default/custom claims involving:
- profit target
- reward split
- payout pace
- add-on combinations

Current product marketing offers customization while standard FAQ values remain 6% / 80% / 14 days.

### F. Blueberry Futures Accelerated 25K price
Current English official conflict:
- live homepage：$110.40 standard / $44.16 at60%
- Help price + detailed parameters：$129 standard / $51.60 at60%

Keep public price hidden / confirmation state until checkout or direct official clarification resolves it.

### G. Blue Guardian Futures Reserve multi-account promo
Current public cards use the older structure as `確認済み`:
- first account 40%
- fifth Reserve effectively free

Current English official conflict:
- current purchase surface + 2026-08-11 article support newer progression 25 / 30 / 35 / 40 and fifth Reserve 70%
- Help Center still says 40 / 45 / 50 / 55 and fifth free

If live checkout cannot settle this at implementation time:
- downgrade public cards from `確認済み` to `確認中`
- suppress exact Reserve discount/5th-account benefit

Do not choose values by recency alone.

### H. Fundora Professional/Master price surfaces
Official current-accessible JPY surfaces conflict.
Current purchase JPY tab must be checked before public price write.

### I. Hantec Endurance active purchase availability
Current English dedicated page contains purchase content while other current official navigation/labels still indicate Coming Soon.

Core rules may be used where separately verified; active sale status remains checkout-gated.

---

## DO NOT TOUCH

### The5ers Summer 200K
There has never been a user instruction to delete this plan.

Project record:
`NO USER DELETION INSTRUCTION / CURRENT AVAILABILITY ASSERTED BY OPERATOR / OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING`

Rules:
- do not remove Summer 200K
- do not convert the public page to 100K-only
- static/crawler absence is not proof of nonexistence
- English dynamic purchase/checkout/support evidence must be checked before any future rewrite of its detailed values

### Diagnosis protected logic
No changes to question set/order/scoring/eligibility/ranking in this correction bundle.

### Master / Affiliate / Coupon / Price protected layers
No broad architecture migration inside a factual correction release.

### GA4 initialization
No change.

---

## Required QA for any correction release

- fresh Check3 evidence log
- build PASS
- existing regression PASS
- protected hash match
- route/sitemap/canonical check
- 390px mobile QA
- CTA-level PR disclosure QA
- no unknown/conflict coerced into verified values
- no service-nature wording drift

Final gate:
`CENTRAL/HUMAN PUBLISH APPROVAL REQUIRED`

Final Status：
`POST_AUTH_CORRECTION_BUNDLE_CONSOLIDATED_THROUGH_WAVE12 / AUTH_AND_PRODUCTION_RECONCILIATION_BLOCK_IMPLEMENTATION`
