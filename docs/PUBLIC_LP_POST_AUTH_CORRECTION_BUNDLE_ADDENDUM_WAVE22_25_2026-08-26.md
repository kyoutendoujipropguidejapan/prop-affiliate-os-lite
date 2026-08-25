# PUBLIC LP POST-AUTH CORRECTION BUNDLE — ADDENDUM WAVE22–25

更新日：2026-08-26 JST
Status：CURRENT ADDENDUM / APPLY WITH MAIN BUNDLE AFTER AUTH + PRODUCTION RECONCILIATION
Parent：`docs/PUBLIC_LP_POST_AUTH_CORRECTION_BUNDLE_2026-08-26.md`

## Purpose

Wave22–25で確定したJapan eligibility / current-pick freshness / Free Trial scope / Fintokei Academyの追加判断を、認証復旧後の最小修正Queueへ追補する。

---

## No factual correction required

### Blue Guardian — Japan eligibility
Current Home `日本から利用可` is supported by current official evidence.

Keep legal-status separation:
`日本から利用可能（公式確認）。商品・プラン別の利用条件と本人確認条件は購入前に公式画面で確認。`

Do not convert this into Japanese regulatory-registration language.

---

## Freshness update required

### The5ers Home Summer100K current pick
Current values are supported:
-2-Step10/5 $149
-2-Step8/5 $179
-1-Step $249
- scoped current risk/target values

If Production still shows an old `VERIFIED 2026.08.01`/similar hard-coded date, update using page/section-level `last verified` after a fresh Check3.

Do not touch Summer200K from this task.

---

## Scope correction candidate

### Fintokei Free Trial
Current official scope resolves the apparent8-vs10 issue:

General English/top-level-program scope:
- StartTrader
- SwiftTrader
- ProTrader
- ProTrader Swing
- up to2 trials per program
=>8

Current Japan-specific listed plan variants:
- 入門
- チャレンジ
- チャレンジ・スイング
- チャレンジ・スリム
- 速攻
- each up to2
=>10 trial opportunities in the current Japan variant list.

If any current Japan-facing Production copy states unqualified `最大8回`, change only after actual source inspection to a scope-aware form such as:
`日本向け公式FAQでは現在、5つの掲載プラン/派生プランを各2回まで無料トライアル可能（合計最大10口座分の試用機会）。同一プランの同時複数保有は不可。`

Do not conflate with:
- Loyalty Free Challenge
- campaign/retry accounts

---

## Fintokei Academy — current core facts

Current official sources support:
- currently available in Japan
- Learn
- Drills
- simulated Trade
- Trade Analytics
- Roadmap
- in-app XP / levels / milestones / rewards
- simulation-based trading, not real-money trading

Safe integration wording:
`Fintokei Academyは、学習・ドリル・シミュレーション取引・分析・Roadmapを一つの流れで使う日本向けトレーニングアプリです。`

### XP separation — mandatory

Academy XP:
- Academy app/Roadmap progress
- lessons/milestones based

MyFintokei Loyalty XP:
- MyFintokei Tier/Missions/actions
- trading/login/KYC/purchases/events etc.

Current reviewed official sources do not prove a shared/synchronized balance.

Production rule:
- do not merge XP totals
- do not say Academy lessons raise MyFintokei Tier
- do not say Loyalty XP automatically unlocks Academy rewards
unless new official evidence explicitly establishes the connection.

Safe wording:
`Academy内にもXP制度がありますが、MyFintokeiのLoyalty Programにも別途XP制度があります。現在確認した公式資料だけでは同一残高・自動連携とは確認できないため、別枠として案内します。`

### Academy 50% benefit — HOLD

Do not publish a universal:
`AcademyをクリアするとChallengeが50% OFF`

The current official Academy sources reviewed in Wave25 do not establish that universal benefit.
Other unrelated50% campaigns exist and must not be conflated.

This is not proof the Academy benefit does not exist.
Required before publication:
1. exact current Academy in-app screen/terms
2. scope/eligibility/target plan/expiry
3. independent official support/direct confirmation
4. fresh pre-publish check

Status:
`ACADEMY_50_PERCENT_BENEFIT_EVIDENCE_REQUIRED`

---

## Public-route boundary

Earlier crawler did not reliably observe the Academy route/string.
Do not classify as not deployed.

After auth recovery:
1. enumerate actual Production Academy-related routes/content
2. compare to Wave25 facts
3. check actual CTA hrefs and PR disclosure
4. apply XP separation
5. keep50% claim out unless evidence gate is complete

---

## Release gate

Nothing in this addendum is implemented until:
- internal Git authentication restored
- actual Production source reconciled
- fresh Check3 for any changed claim
- regression / protected hashes /390px / compliance PASS
- human publish approval

Final Status：
`ADDENDUM_WAVE22_25_READY_NO_PRODUCTION_CHANGE`
