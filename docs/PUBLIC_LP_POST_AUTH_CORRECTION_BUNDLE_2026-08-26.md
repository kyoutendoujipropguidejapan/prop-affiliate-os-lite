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

## P0-B — public factual/compliance corrections ready for minimal patch after reconciliation

### 1. Fintokei SwiftTrader cohort framing
Current public issue:
old/new values are framed as unresolved official conflict.

Safe current structure:
- purchases on/after 2026-07-15: target6 / Daily2 Equity / Max3 Static / min3 evaluation days
- applicable older cohort: target10 / Daily3 / Max6 / min5

Do not bulk-replace payout-specific `5日`; payout eligibility has a separate rule context.
Do not auto-return SwiftTrader to Diagnosis Top3 in the same correction patch.

### 2. Fintokei ProTrader Slim current status
Current public Home marks Slim as:
- `新規販売対象外`
- `2026年3月31日で新規販売終了`

Current official sources now support a relaunched/current Japan/JPY ProTrader Slim variant.

Safe direction:
- remove legacy-only current status
- current scoped baseline: 2-Step / 8%+6% / Daily5% / Max10% / min3 days per phase / MT5-only
- preserve Japan/Japanese-user scope
- preserve earlier historical sale-end/relaunch chronology only in history context
- do not auto-change Diagnosis scoring in this patch

### 3. Fintokei current-program taxonomy FAQ
Current English onboarding taxonomy:
- StartTrader
- SwiftTrader
- ProTrader
- ProTrader Swing

ProTrader Slim is a current specialized ProTrader variant, not a peer top-level program in the same taxonomy.

Safe FAQ wording:
`Fintokeiの現行トップレベルのプログラムは StartTrader（入門）、SwiftTrader（速攻プロ）、ProTrader（チャレンジ）、ProTrader Swing（チャレンジ・スイング）。ProTrader Slimは日本/JPY向けのProTrader派生プランとして提供されています。`

This newer current-source adjudication supersedes the old M14 current-plan sentence for publication.

### 4. Blueberry Funded Instant Lite current cohort
For purchases on/after 2026-08-17:
- Daily2%
- Max4% Static
- no minimum trading days
- payout consistency15%
- standard14-day reward cycle
- 80% split, with current scaling context where applicable

Preserve older cohorts separately.

### 5. Blue Guardian 1 Step Standard
Current-new cohort purchased on/after 2026-08-20:
- target9%

Older applicable cohort:
- target10%

### 6. Blue Guardian 2 Step Standard
Current-new cohort purchased on/after 2026-08-20:
- min3 profitable days

Older applicable cohort:
- 5 days

### 7. FTM Japanese-support wording
Replace stale future-facing wording with safe current wording such as:
`日本語サイト・FAQあり。重要なプラン固有条件は英語原文・購入画面も確認。`

Do not claim complete/full Japanese localization.

### 8. FTM Nitro X reward wording
Current public `最大80%` is stale.

Safe direction:
`On-demand／引き出し対象部分は100%配分（総利益の50%をリスクバッファとして口座に維持）`

Keep minimum-profit/cap/consistency conditions separately. Do not advertise plain `100%` without the buffer condition.

### 9. FTM dedicated article program count
Current `/funded-trader-markets` says `現行5プラン` and omits Nitro X.

Safe direction:
`現行6プラン：1 Step Nitro、1 Step Nitro X、2 Step Plus、Instant Standard、Instant Pro、Instant Plus`

### 10. FTM dedicated article Instant Pro Daily DD
Current dedicated article presents Daily3% as settled truth.

Current English official conflict:
- dedicated FAQ: Daily DD3%
- current Instant Pro marketing copy: `no daily drawdown limits`
- same current product page comparison matrix: Daily DD3%

Safe public direction:
`日次損失：詳細FAQ・比較表は3%／公式Instant Pro紹介文は「no daily drawdown limits」と記載。公式内差異を確認中。`

Exact Daily DD stays HOLD. Max Loss3% trailing may remain separately verified-with-caution.

### 11. Blueberry Futures funded consistency
Replace company-wide `35%` wording with plan-specific:
- Ascent35%
- Accelerated20%

This is funded payout consistency, not evaluation consistency.

### 12. The5ers company-level consistency/payout-cap warning
Current Home says:
`1日50% consistency・Payout capに注意`

This is overgeneralized.
Current official program scopes differ:
- Summer 1-Step uses50% consistency
- The5ers Futures uses40% consistency
- High Stakes / Growth / Bootcamp do not establish one universal company-wide50% consistency or one universal payout cap

Safe company-level wording:
`ConsistencyやPayout capはプラン別。Summer・Futuresなど対象プランの条件を個別確認。`

Keep numeric consistency/cap only at plan scope.

### 13. The5ers Futures Day Trade25K
Current English official product + FAQ + fresh recheck support:
- current price $59
- activation fee none
- Max Loss EOD4%
- consistency40%

Current public `価格確認中` is stale/conservative.

Safe direction:
- current price `$59`
- activation fee `なし`
- keep final purchase-screen confirmation

This is unrelated to CFD Summer200K.

### 14. Funded7 PAYG public article conflict-safe correction
Current `/pay-after-pass-payg` states PAYG as definite:
`日次4%・最大8%の固定型`

Current English official sources conflict:
- challenge comparison：Daily5 / Max10 / Static
- official2026 guide：Daily4 / Max8 / Static

Safe replacement:
`PAYGの損失上限は現行公式ページ間で差異を確認中。購入前にPAYGの購入画面・専用ルールを確認。`

Do not choose5/10 or4/8.

### 15. Home/page freshness metadata
Replace stale global-style dates with page/section-level `last verified` where architecture permits.

Do not imply every page Fact was checked on one date.

### 16. Home official-information link / affiliate CTA separation
Current public surfaces include Firm-card CTAs labeled like `最新条件を見る` while some destinations are Affiliate/Partner/Referral paths.

Approved Compliance Baseline requires:
- clean official-information source link separated from commercial conversion CTA
- nearby PR disclosure for affiliate CTA
- global disclosure alone not treated as sufficient architecture

Safe target:
1. `公式情報を確認` -> clean non-affiliate official product/rules/help URL
2. `PR｜特典・申込みを確認` -> affiliate/referral URL
3. concise nearby commercial disclosure
4. factual evidence continues to reference clean official sources

Do not remove monetization. Do not alter Diagnosis ranking/scoring.

---

## P1 — clarification / coverage updates

### 17. Hantec Instant Lite
Central approved:
`HOLD -> VERIFIED_WITH_CAUTION`

Display:
`標準5% Trailing（決済後残高追随→5%利益到達後に開始残高でLock）／+1% Max Loss Add-onで6%`

Trading-day scope:
`評価・開始の最低取引日数：なし／出金周期の条件：5利益日（各0.5%以上）`

### 18. Hantec EnhancedX minimum days
Safe direction after fresh check:
`最低取引日数：なし（ただしChallengeはConsistency35%以下が必要。対象Add-onで評価側Consistency解除可）`

### 19. Fundora platform
Current official platform:
`cTrader`

Replace generic platform wording only after actual Production-source inspection.

### 20. Blue Guardian Nano coverage
Current official models include:
-1 Step Nano
-2 Step Nano

Do not add pricing until current purchase surface is confirmed.

### 21. Blueberry Prime minimum days
Safe current wording after fresh check:
`現行新規購入は3日/Phase。旧購入条件・一部表示では5日を保持するため購入日を確認。`

### 22. FundingPips 2 Step Standard reward options
Do not collapse current structure to one `7日／80%` value if Production does so.

Current official options include weekly60%, bi-weekly80%, monthly100%, and conditional on-demand90%.

### 23. FundingPips Zero profitable-day threshold
Where displayed:
`7 profitable days / rolling30, each >=0.25%`

### 24. Trading Cult Pro platform
Current official family uses MT5.

Change generic platform wording to `MT5` only after model-specific source check.

### 25. Fintokei NEW20 commercial status
Current English official surfaces triple-support:
- NEW20
-20% off
- first challenge / any first challenge wording

Status:
`TRIPLE_VERIFIED_GENERAL_SCOPE / JP_CHECKOUT_CAUTION`

Japanese homepage omission is not negative evidence. Keep final checkout confirmation and do not guarantee final price.

### 26. Fintokei payout minimum amount content gap
Current official English payout FAQ states minimums:
-100 EUR
-100 USD
-2,000 CZK
-20,000 JPY
with exceptions for certain400K ProTrader accounts and SwiftTrader minimum-profit rule.

Current public payout page is not false, but may add the20,000 JPY minimum where useful after fresh Japan-scope check.

Status：`UPDATE_CANDIDATE / NOT_REQUIRED_FOR_CORRECTION`

### 27. Beginner/Home service-nature wording hardening
Current generic wording that many retail prop services use simulated environments is supported by current Fintokei, Hantec Trader and SuperFunded official material.

Preferred precision update:
`当サイトで扱う多くのサービスでは、評価や報酬算定にシミュレーション口座・仮想資金が使われます。サービスの法的・契約上の位置づけは各社で異なるため、個別ページでは各社Terms / FAQの説明に従います。`

This is a precision/compliance improvement, not a claim that every Firm has the same legal/business model.

### 28. Generic educational rule articles
Wave17 triple recheck supports the current generic framing of:
- `/articles/minimum-trading-days`
- `/articles/news-trading-rules`

No factual patch required.
Keep future named-Firm examples behind fresh three-check scope.

---

## COMMERCIAL / RULE HOLD — do not choose one side

### A. Funded7 One Phase
Official conflict remains:
- comparison / FAQ / guide：Daily4 / Max8
- current product page：Daily5 / Max10

### B. Funded7 Instant
Current official Max Total is represented as6 /8 /10 / OREF-dependent.

### C. Funded7 PAYG exact loss values
Current English official conflict:
- comparison：Daily5 / Max10
- guide：Daily4 / Max8

### D. FTM Instant Pro Daily DD
Current English official conflict remains inside current surfaces: `no daily drawdown limits` vs3%.

### E. FundedElite Flash Activation exact customization matrix
Core $5 → pass → activation-fee flow is verified.

HOLD remains for universal default/custom claims involving target / split / payout pace / add-on combinations.

### F. Blueberry Futures Accelerated25K price
Current English official conflict:
- live homepage：$110.40 standard / $44.16 at60%
- Help price + detailed parameters：$129 standard / $51.60 at60%

Keep price hidden/confirmation state until checkout/direct clarification resolves it.

### G. Blue Guardian Futures Reserve multi-account promo
Current public cards use older structure as `確認済み`.

Current English official conflict:
- current purchase surface + 2026-08-11 article:25/30/35/40 progression; fifth Reserve70%
- Help:40/45/50/55; fifth free including Reserve

If checkout cannot settle at implementation:
- downgrade `確認済み` -> `確認中`
- suppress exact Reserve discount / fifth-account benefit

### H. Fundora Professional/Master JPY prices
Current official-accessible JPY surfaces conflict. Current purchase JPY tab required.

### I. Hantec Endurance active purchase availability
Current English dedicated page exposes purchase content while other official surfaces still indicate Coming Soon.

Core rules may be used where independently verified; sale status stays checkout-gated.

---

## DO NOT TOUCH

### The5ers Summer200K
There has never been a user instruction to delete this plan.

Project record:
`NO USER DELETION INSTRUCTION / CURRENT AVAILABILITY ASSERTED BY OPERATOR / OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING`

Rules:
- do not remove Summer200K
- do not convert the public page to100K-only
- static/crawler absence is not proof of nonexistence
- English dynamic purchase/checkout/support evidence must be checked before any future rewrite of detailed values

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
-390px mobile QA
- CTA-level PR disclosure QA
- Official URL / Affiliate URL separation PASS
- no unknown/conflict coerced into verified values
- no service-nature wording drift

Final gate:
`CENTRAL/HUMAN PUBLISH APPROVAL REQUIRED`

Final Status：
`POST_AUTH_CORRECTION_BUNDLE_CONSOLIDATED_THROUGH_WAVE18 / AUTH_AND_PRODUCTION_RECONCILIATION_BLOCK_IMPLEMENTATION`
