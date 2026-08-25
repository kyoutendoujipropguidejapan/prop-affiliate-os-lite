# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 5 / FUNDINGPIPS

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中 Home の FundingPips 主要5モデル・Free Trial・Platform表示
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Rules

- 同じURLを3回読むことは3回チェックと数えない
- dedicated model article / comparison / responsible-trading policy / free-trial articleを分けて照合する
- cohort / temporary trading-condition changesを保持する
- Production sourceは内部Git認証HOLD中のため編集しない

---

## 1. FundingPips — current model set

### Public surface observed

Current LP manages 5 models:
- 1 Step Flex
- 2 Step Standard
- 2 Step Pro
- 2 Step Flex
- Zero

### Triple check

Check 1 — official Get Started
`https://help.fundingpips.com/hc/en-us/articles/44390730743825-Get-Started`

Lists exactly the same five current models.

Check 2 — official Compare Account Models
`https://help.fundingpips.com/hc/en-us/articles/48368490585105-Choose-Your-Account-Type`

Again lists the same five current models.

Check 3 — official Responsible Trading Policy
`https://help.fundingpips.com/hc/en-us/articles/47328410434065-Responsible-Trading-Policy`

Comparison matrix again covers the same five active models.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

---

## 2. 1 Step Flex — headline rules

### Public surface observed

- target 12%
- Daily Loss 3%
- Max Loss 12% static
- no minimum evaluation days
- 14-day / 85% reward
- evaluation weekend hold allowed; Master temporarily not allowed

### Triple check

Check 1 — official 1 Step Flex
`https://help.fundingpips.com/hc/en-us/articles/34501697434385-1-Step-Flex`

Confirms:
- one phase
- 12% target
- 3% daily
- 12% static max loss
- no minimum trading days
- 85% bi-weekly reward

Check 2 — official Compare Account Models
`https://help.fundingpips.com/hc/en-us/articles/48368490585105-Choose-Your-Account-Type`

Confirms the same 12 / 3 / 12 / no-minimum evaluation structure.

Check 3 — official Responsible Trading Policy
`https://help.fundingpips.com/hc/en-us/articles/47328410434065-Responsible-Trading-Policy`

Again confirms 12% target, 3% Daily, 12% Static Max.

Additional current condition:
`https://help.fundingpips.com/hc/en-us/articles/34504137479441-News-Trading-Weekend-Holding`

confirms temporary Master weekend-hold restriction while evaluation holding remains allowed.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

Caution: if Profit Concentration policy is triggered in evaluation, Master reward eligibility can require 4 profitable days. Do not rewrite the generic `no minimum trading days` evaluation field into a universal no-day requirement for reward eligibility.

---

## 3. 2 Step Standard — headline rules

### Public/current managed structure

Current official model is:
- target 8% / 5%
- Daily 5%
- Max 10% static
- min 3 trading days per evaluation phase

### Triple check

Check 1 — official dedicated 2 Step Standard
`https://help.fundingpips.com/hc/en-us/articles/34501809112081-2-Step-Standard`

Confirms current values and explicitly states the old 10% Phase-1 target is no longer offered from 2026-07-24.

Check 2 — official Responsible Trading Policy

Confirms 8/5, Daily5, Max10 Static, 3 days/phase.

Check 3 — official Free Trial
`https://help.fundingpips.com/hc/en-us/articles/45363484760209-Free-Trial`

The trial is documented as mirroring the real 2 Step Standard and independently repeats:
- 8% / 5%
- Daily5
- Max10
- 3 days/phase

### Result

Status：`TRIPLE_VERIFIED`

Important current Master reward structure is more nuanced than a single fixed split:
- Weekly 60%
- Bi-Weekly 80%
- Monthly 100%
- On Demand 90% with conditions

Any public card that compresses this to only `7日周期／80%` should be treated as `UPDATE_CANDIDATE`, not necessarily false, because it omits currently documented reward-cycle options.

---

## 4. 2 Step Pro — headline rules

### Triple check

Check 1 — official 2 Step Pro
`https://help.fundingpips.com/hc/en-us/articles/34502027344017-2-Step-Pro-Model`

Confirms:
- 6% / 6%
- Daily3
- Max6 static
- min1 trading day/phase
- weekly reward at 80%

Check 2 — official Responsible Trading Policy

Again confirms 6/6, Daily3, Max6 Static, 1 day/phase.

Check 3 — official Free Trial

The official trial mirrors the live 2 Step Pro evaluation and independently repeats the same 6/6, 3/6 and 1 day/phase values.

### Result

Status：`TRIPLE_VERIFIED`

---

## 5. 2 Step Flex — headline rules

### Public surface observed

- target 10% / 6%
- Daily4
- Max12 static
- reward choice at purchase:
  - 85%: no minimum evaluation days
  - 95%: 3 profitable days >=0.5% each
- bi-weekly rewards

### Triple check

Check 1 — official dedicated 2 Step Flex
`https://help.fundingpips.com/hc/en-us/articles/47835196271249-2-Step-Flex`

Confirms all scoped fields above.

Check 2 — official Compare Account Models

Confirms 10/6, Daily4, Max12 Static.

Check 3 — official Responsible Trading Policy

Again confirms the same headline risk and target values.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

---

## 6. Zero — headline rules

### Public surface observed

- no evaluation
- 95% split
- Daily3
- Max5 trailing -> locks at starting balance after +5%
- rolling 30 days / 7 profitable days
- 15% consistency
- 3% safety cushion
- weekend/news restrictions

### Triple check

Check 1 — official FundingPips Zero
`https://help.fundingpips.com/hc/en-us/articles/34502157694865-FundingPips-Zero`

Confirms:
- no evaluation
- Daily3
- Max5 trailing
- 95% bi-weekly reward
- 7 profitable days per rolling30, each >=0.25%
- 15% consistency
- 3% cushion
- weekend/news hard-breach restrictions

Check 2 — official Compare Account Models

Confirms no evaluation, Daily3, Max5 trailing, 7 profitable days.

Check 3 — official Responsible Trading Policy

Again confirms Zero as Instant Master with Daily3 / Max5 trailing / 7 profitable days.

### Result

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

Minor clarity candidate: where public text says only `7利益日`, add the official threshold `各0.25%以上` when space allows.

---

## 7. Free Trial

### Public surface observed

LP FAQ says Free Trial is available for 2 Step Standard and 2 Step Pro.

### Triple check

Check 1 — official Free Trial article

Explicitly says only 2 Step Standard and 2 Step Pro.

Check 2 — official Help Center category landing
`https://help.fundingpips.com/hc/en-us/categories/33669987169425-FundingPips`

Free Trial block independently says available on 2 Step and 2 Step Pro.

Check 3 — official Free Trial comparison table

Within the current Free Trial article, the actual model table and setup steps both independently identify Standard and Pro and specify MT5-only trial environment.

### Result

Status：`TRIPLE_VERIFIED_WITHIN_OFFICIAL_FLOW / NO CORRECTION REQUIRED`

---

## 8. Platforms

### Public surface observed

`MT5 / cTrader / Match-Trader`

### Official checks

- Free Trial article states paid Evaluation Accounts support `cTrader, Match-Trader, MT5` while Trial itself is MT5-only.
- individual model pages document MT5 swap-free specifics and platform-dependent rules.
- current product/help ecosystem uses these three platform families.

Status：`SUPPORTED_CURRENT / KEEP DISPLAY`

Firm-enabled scope can change by model/add-on; deep Platform entity mapping remains separate work.

---

## 9. Current corrections / updates from Wave 5

### P1 update candidate

1. 2 Step Standard reward wording
   - current official reward structure offers 60/80/90/100% depending cycle/conditions
   - avoid reducing current model to only `7日周期／80%` if that string exists in Production source

2. Zero profitable-day clarity
   - `7 profitable days / rolling30` -> add `各0.25%以上` when practical

### No correction

- current 5-model set
- 1 Step Flex core values
- 2 Step Standard core target/DD/min-days
- 2 Step Pro core values
- 2 Step Flex core values
- Zero core values
- Free Trial model scope

---

## 10. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

Before any Production patch:
1. reconcile actual source
2. fresh current official check
3. preserve temporary-condition / cohort context
4. minimal patch only
5. regression + protected hashes + 390px + compliance
6. human publish approval

Final Status：
`WAVE5_FUNDINGPIPS_AUDIT_COMPLETE_CORE_TRIPLE_VERIFIED_TWO_UPDATE_CANDIDATES_NO_PRODUCTION_CHANGE`
