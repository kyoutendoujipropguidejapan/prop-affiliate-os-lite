# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 9 / FTM DETAIL

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中 `/funded-trader-markets` とHomeのFTM表示
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

FTM専用公開記事はHomeより日本語対応表現が新しい一方、現行プラン数・Nitro X・報酬表現に差があるため、current officialを最低3方向で再確認する。

Production sourceは内部Git認証HOLD中のため、本書はCorrection Queueのみを固定する。

---

## 1. FTM current program count

### Public dedicated page observed

`/funded-trader-markets` currently says:

`現行5プラン`

and lists:
- 1 Step Nitro
- 2 Step Plus
- Instant Standard
- Instant Pro
- Instant Plus

This omits Nitro X from the stated current-program set.

### Public Home observed

A newer/current Home surface separately manages `6プラン` and includes:
- 1 Step Nitro
- 1 Step Nitro X
- 2 Step Plus
- Instant Standard
- Instant Pro
- Instant Plus

### Triple official check — Nitro X is current

Check 1 — current official EN Nitro X FAQ category
`https://fundedtradermarkets.com/faq/category/1-step-nitro-x`

Current live category labels Nitro X as `1-Step Nitro X Evaluation` and contains current activation, target, consistency, drawdown and reward rules.

Check 2 — current official JP Nitro X FAQ category
`https://fundedtradermarkets.com/ja/faq/category/1-step-nitro-x`

Current Japanese category independently exposes the same active Nitro X program and current rules.

Check 3 — current official global FAQ navigation
`https://fundedtradermarkets.com/faq`

Current program navigation explicitly contains both:
- 1-Step Nitro Evaluation
- 1-Step Nitro X Evaluation
alongside 2-Step Plus and all three Instant programs.

### Result

The dedicated public FTM article's `現行5プラン` statement is stale/incomplete.

Status：`CORRECTION_REQUIRED / HIGH_PRIORITY`

Safe correction after Production reconciliation:

`現行6プラン：1 Step Nitro、1 Step Nitro X、2 Step Plus、Instant Standard、Instant Pro、Instant Plus`

Do not infer that Home source is canonical solely because it already shows 6; inspect actual Production source first.

---

## 2. Nitro X current core

### Public Home card observed

Current Home surface contains Nitro X:
- target6%
- Daily3%
- Overall3% trailing -> lock at +3%
- no minimum evaluation days
- funded consistency25%
- reward wording `On-demand／最大80%`

### Triple official check

Check 1 — official Nitro X category / profit target
- target6%

Check 2 — official Daily DD FAQ
`https://fundedtradermarkets.com/ja/faq/how-does-the-maximum-daily-drawdown-limit-for-the-1-step-nitrox-evaluation-work`
- Daily3%

Check 3 — official Overall DD FAQ
`https://fundedtradermarkets.com/ja/faq/how-does-the-overall-drawdown-limit-for-the-1-step-nitrox-evaluation-work`
- Overall3% from highest recorded balance
- locks at initial balance after +3% profit

Additional corroboration — official funded consistency FAQ
`https://fundedtradermarkets.com/faq/is-there-a-rule-regarding-consistency-for-1-step-nitro-x-accounts`
- no evaluation consistency
- funded consistency25%

### Result

Target / Daily / Overall / Lock / funded-consistency fields are current-official supported.

Status：`TRIPLE_VERIFIED_SCOPED`

---

## 3. Nitro X reward split — public correction remains required

### Current official

Check 1 — JP Nitro X category
- lifetime100% reward split
- must retain50% of total profit as risk buffer
- remaining50% can be withdrawn at100% reward rate

Check 2 — EN reward/buffer FAQ
`https://fundedtradermarkets.com/faq/what-impact-does-the-trailing-overall-drawdown-have-on-payouts-in-a-nitrox-simulated-funded-account`
- minimum profit threshold3%
- 50% buffer rule
- withdrawable portion paid at100% reward rate

Check 3 — current EN/JP category navigation and current dedicated reward article remain live under Nitro X.

### Result

Public Home `最大80%` is stale for current Nitro X.

Status：`CORRECTION_REQUIRED / ALREADY_IN_P0_BUNDLE`

Safe wording:

`On-demand／引き出し対象部分は100%配分（総利益の50%をリスクバッファとして口座に維持）`

Also expose where practical:
- minimum performance reward threshold3%
- funded consistency25%
- per-request reward cap $5,000 where the current official rule is applied to the selected account/cohort

Do not reduce the structure to the marketing phrase `100% split` without the buffer rule.

---

## 4. 1 Step Nitro current core

### Public dedicated article
- target10
- Daily4
- Overall6 trailing -> lock
- evaluation consistency50
- funded consistency45

### Triple official check

Check 1 — current Nitro category
`https://fundedtradermarkets.com/faq/category/1-step-nitro-evaluation`

Check 2 — current Overall DD FAQ
`https://fundedtradermarkets.com/faq/how-does-the-overall-drawdown-limit-for-the-1-step-nitro-evaluation-work`

Check 3 — current Daily DD FAQ
`https://fundedtradermarkets.com/faq/how-does-the-maximum-daily-drawdown-limit-for-the-1-step-nitro-evaluation-work`

Current official confirms:
- target10%
- Overall6% trailing from HWM, lock at initial after +6%
- Daily4% for normal Nitro sizes
- special 300K Nitro Daily3%
- evaluation consistency50%
- funded consistency45%

General minimum-days FAQ confirms no minimum evaluation days and payout requires5 profitable days at >=0.5% each.

### Result

Public core is materially aligned.

Status：`TRIPLE_VERIFIED_WITH_ACCOUNT_SIZE_CAUTION`

The 300K Daily3% exception must remain explicit wherever a universal Daily4% claim could be inferred.

---

## 5. 2 Step Plus current core

Current public dedicated values:
- 8% / 5%
- Daily4%
- Max10% static
- min3 each evaluation phase
- funded payout qualification 5 profitable days

Current official checks:
1. 2-Step Plus category
2. JP target FAQ
3. General Minimum Trading Days FAQ

Materially align on the scoped fields.

Status：`TRIPLE_VERIFIED_SCOPED / NO CORRECTION REQUIRED`

---

## 6. Instant Standard / Plus current minimum-day + consistency

Public dedicated article says:
- Instant Standard: 5 profitable days +15% consistency
- Instant Plus: 5 profitable days +15% consistency

Current official:
- General Minimum Trading Days FAQ confirms all three Instant types require5 payout-qualifying days, each >=0.5% profit.
- Current Instant Standard consistency FAQ confirms15%.
- Current category structure keeps Instant Standard/Plus as separate active programs.

Status：`CURRENT_OFFICIAL_SUPPORTED`

Before declaring every Standard/Plus numeric field `TRIPLE_VERIFIED`, capture plan-specific Daily/Overall DD articles separately. No correction from the scoped days/consistency fields.

---

## 7. Instant Pro remains HOLD

Do not change prior decision.

Current official ecosystem still contains a conflict around Daily DD interpretation:
- dedicated/current detail material supports3%
- another current official presentation has used `no Daily Drawdown` wording while comparison/FAQ show3%

Status：`HOLD / CONFLICT`

Do not use majority vote.

---

## 8. FTM Japanese support — cross-route consistency

The dedicated FTM article already correctly says:
- Japanese page exists
- Japanese FAQ exists
- full end-to-end Japanese coverage is not guaranteed

Home in at least one current public surface still says `日本語対応予定`.

Status:
- dedicated article: `NO CORRECTION REQUIRED`
- Home: `CORRECTION_REQUIRED`

This is a cross-route consistency defect, not an evidence problem.

---

## 9. Wave 9 correction queue

### P0 after auth + Production reconciliation

1. `/funded-trader-markets` current program count:
   - 5 -> 6
   - add Nitro X to current program summary

2. Nitro X reward wording:
   - remove `最大80%`
   - use100% withdrawable-part wording + mandatory50% profit buffer

3. Home FTM Japanese support:
   - stale future-facing wording -> current Japanese site/FAQ wording

### No correction

4. 1 Step Nitro scoped core values
5. 2 Step Plus scoped core values
6. dedicated FTM Japanese-support explanation

### HOLD

7. Instant Pro Daily DD conflict

---

## 10. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

Required before patch:
1. actual Production Version/SHA/source
2. actual source count/list for FTM
3. fresh official Check3
4. minimal route-specific patch
5. regression/protected hashes/390px/CTA PR
6. human publish approval

Final Status：
`WAVE9_FTM_DETAIL_AUDIT_COMPLETE_PROGRAM_COUNT_AND_NITROX_REWARD_CORRECTIONS_QUEUED_NO_PRODUCTION_CHANGE`
