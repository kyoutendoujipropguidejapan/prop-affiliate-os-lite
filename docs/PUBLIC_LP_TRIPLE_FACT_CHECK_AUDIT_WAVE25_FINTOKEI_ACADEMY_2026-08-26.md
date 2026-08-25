# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 25 / FINTOKEI ACADEMY

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / CORE ACADEMY FACTS VERIFIED / XP MERGE PROHIBITED / 50% BENEFIT NOT VERIFIED
Scope：Fintokei Academy current facts for Home / Firm Detail / article integration
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`
Policy：general/current facts = English-first; Japan-only availability gets Japan-scope treatment.

## 0. Purpose

Fintokei Academyについて、現在の公式情報で確認できる機能・地域・シミュレーション性・XPの扱いを整理し、MyFintokei Loyalty ProgramのXPや未確認の割引特典と混同しない。

## 1. Check 1 — current English Academy getting-started FAQ

Official:
`https://support.fintokei.com/en/articles/15516282-getting-started-with-the-fintokei-academy-app`

Current official states:
- Fintokei Academy App is currently available in Japan only
- Learn
- Drills
- simulated Trade
- Trade Analytics
- Roadmap
- XP / levels / milestones / rewards
- app trading is simulation-based, not real-money trading

Result:
`PASS`

## 2. Check 2 — current English Academy app-flow FAQ

Official:
`https://support.fintokei.com/en/articles/15516677-how-the-app-fits-together`

Current official independently states:
- currently Japan-only
- Learn -> Drill -> Trade -> Analyze -> Roadmap cycle
- simulation balance is a practice balance
- simulated trading is used to practice execution/risk management without real money

Result:
`PASS`

## 3. Check 3 — current English Academy Roadmap / XP FAQ

Official:
`https://support.fintokei.com/en/articles/15516660-roadmap-rewards-levels-xp-and-unlocks`

Current official states:
- Academy XP is the progress system inside the app
- XP is typically earned through lessons and milestones
- Roadmap shows current level, next level, required XP and unlockable rewards
- levels and milestones represent progress inside the Academy journey

Result:
`PASS`

## 4. Additional corroboration — account deletion FAQ

Official:
`https://support.fintokei.com/en/articles/15260496-how-can-i-delete-my-fintokei-academy-account`

Current article again states Japan-only availability and separately identifies Academy data such as:
- learning progress
- XP
- level
- streaks
- claimed rewards
- virtual balance / virtual trade history / win-rate stats

This further supports that Academy has its own app-specific progress/simulation data model.

## 5. Result — Academy core facts

Status:
`TRIPLE_VERIFIED_CURRENT_JAPAN_SCOPE`

Safe public facts:
- Fintokei Academy is currently available in Japan
- it is a structured training app
- Learn / Drills / simulated Trade / Trade Analytics / Roadmap are core sections
- trading inside the Academy app is simulation-based
- Academy has XP, levels, milestones and rewards as an in-app progress system

## 6. Critical XP boundary — Academy XP vs MyFintokei Loyalty XP

Current Loyalty official source:
`https://support.fintokei.com/en/articles/13387718-fuel-your-journey-what-are-experience-points-xp`

The Loyalty Program source says:
- XP balance/history is shown in **MyFintokei**, under My Tier
- Loyalty XP comes from actions such as registration, KYC, active trading days, MyFintokei login, payouts/events/purchases
- XP raises Loyalty Tier and unlocks Boosts

Academy official sources instead say:
- XP is an in-app progress system
- earned mainly through lessons/milestones
- displayed in Academy Roadmap with Academy levels/rewards

### Governance decision

The official material reviewed here does **not** establish that the two XP balances are the same, synchronized, transferable, or mutually redeemable.

Therefore:
`ACADEMY_XP != ASSUME_MYFINTOKEI_LOYALTY_XP`

Safe public wording:
`Academy内にもXP・レベル制度があります。一方、MyFintokeiのLoyalty Programにも別途XP制度があります。今回確認した公式資料だけでは、両者が同一残高・自動連携するとは確認できないため、別枠として案内します。`

Do not:
- add Academy XP to Loyalty XP totals
- say Academy lesson XP raises MyFintokei Tier
- say Loyalty XP can be spent/unlocked inside Academy
unless a future official source explicitly establishes the connection.

## 7. 50% OFF / Academy completion benefit

Fresh official searches on 2026-08-26 did not identify a current Fintokei Academy official FAQ/product source establishing a universal `AcademyをクリアするとFintokei Challenge 50% OFF` benefit.

Search results did identify other unrelated 50% mechanisms/campaigns, e.g. SwiftTrader Second Chance, which must not be conflated with Academy.

Status:
`ACADEMY_50_PERCENT_BENEFIT_NOT_YET_TRIPLE_VERIFIED / HOLD`

Operational rule:
- do not publish a universal Academy->50% OFF claim from inference or old promotional context
- if there is an in-app current reward/offer, capture the exact Academy screen, terms, eligibility, expiry and target plan
- then obtain an independent official source/direct confirmation and fresh pre-publish check

This does not prove the benefit does not exist; it means current retained evidence is insufficient for the new 3-check standard.

## 8. Service-nature / compliance wording

Academy simulation must not be described as:
- real-money trading
- live brokerage execution
- investment-advice service
- guaranteed preparation for passing a challenge

Safe:
`学習・判断練習・シミュレーション取引・振り返りを一つのアプリで回すトレーニング環境。`

## 9. Production/public boundary

Earlier public crawler did not reliably observe `Fintokei Academy` on the current site.

Status remains:
`PUBLIC_NOT_OBSERVED / NOT PROOF OF NON-DEPLOYMENT`

After internal Git recovery:
1. inspect actual Academy route/content in Production source
2. inspect actual CTA/source links
3. compare public wording with this Wave25 audit
4. keep Academy XP and Loyalty XP separate unless new official evidence appears
5. do not add 50% claim without completed evidence gate

## 10. Final

Production change performed：NONE

Final Status：
`WAVE25_COMPLETE_ACADEMY_CORE_TRIPLE_VERIFIED_XP_SEPARATION_ENFORCED_50PCT_BENEFIT_HOLD`
