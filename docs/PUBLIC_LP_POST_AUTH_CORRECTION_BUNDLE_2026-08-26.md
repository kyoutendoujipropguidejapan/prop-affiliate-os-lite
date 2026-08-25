# PUBLIC LP POST-AUTH CORRECTION BUNDLE

更新日：2026-08-26 JST
Status：PREPARED / DO NOT IMPLEMENT BEFORE AUTH + PRODUCTION RECONCILIATION
Depends on：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開LPの遡及3重ファクトチェックで確定した修正候補を、内部Git認証復旧後にWorkへ渡せる最小実装Queueとしてまとめる。

本書はコード変更・Production変更・publish承認ではない。

---

## Gate 0 — mandatory before any patch

1. internal origin auth/fetch recovery
2. confirm branch / local HEAD / remote HEAD / ahead-behind / clean worktree
3. confirm actual current Production Version/SHA
4. confirm Evidence commit `3e72c0b1...` and Fundora commit `2191f06d...` disposition
5. confirm protected hashes
6. inspect actual affected strings/routes in Production source
7. run a fresh official Check 3 for every changed claim
8. if source differs materially from audit snapshot -> STOP and reclassify

---

## P0-A — accepted backlog before audit corrections

### Evidence Phase1
Preserve exact accepted commit:
`3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`

### Fundora campaign
Preserve exact accepted commit:
`2191f06dc56006b4018f16ec8c2ac51161d2f70a`

Campaign window:
2026-08-25 20:00 JST → 2026-09-01 23:59 JST

If auth recovery occurs after the campaign is no longer useful, do not blindly publish stale campaign UI. Reconcile and decide whether the commit should remain historical/unpublished or be superseded through an approved path. Do not rewrite history without central approval.

---

## P0-B — public factual corrections

### 1. Fintokei SwiftTrader
Current public issue:
old/new values are shown as unresolved official conflict.

Replace conflict framing with cohort framing after source inspection:

- post-2026-07-15 purchase: target6 / Daily2 Equity / Max3 Static / min3 evaluation days
- pre-2026-07-15 applicable account: old10 / Daily3 / Max6 / min5

Do not bulk-replace payout-specific `5日` text; payout context requires dedicated payout-FAQ check.

Do not auto-return SwiftTrader to Diagnosis Top3 in the same patch.

### 2. Blueberry Funded Instant Lite
For purchases on/after 2026-08-17:
- Daily2%
- Max4% Static
- no minimum trading days
- payout consistency15%
- standard14-day reward cycle
- 80% split, scaling context where official applies

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

### 5. FTM Japanese support
Replace stale future-facing `日本語対応予定` with safe current wording such as:

`日本語サイト・FAQあり。プラン固有条件は購入前に公式画面で確認。`

Do not claim complete/full Japanese localization or support quality beyond evidence.

### 6. FTM Nitro X reward wording
Current public `最大80%` is stale.

Safe current direction:
`On-demand／引き出し対象部分は100%配分（総利益の50%をリスクバッファとして口座に維持）`

Keep minimum-profit / consistency / DD requirements separately.

### 7. Blueberry Futures funded consistency
Replace any company-wide `35%` wording with plan-specific:
- Ascent 35%
- Accelerated 20%

State this as funded payout consistency, not evaluation consistency.

### 8. Home/page freshness metadata
Update stale global/section verification dates based on actual page-level checks.

Preferred architecture:
- page-level `last verified`
- avoid one global date implying every linked fact was checked simultaneously

---

## P1 — clarification / coverage updates

### 9. Hantec Instant Lite
Central approved:
`HOLD -> VERIFIED_WITH_CAUTION`

Display:
`標準5% Trailing（決済後残高追随→5%利益到達後に開始残高でLock）／+1% Max Loss Add-onで6%`

Trading-day scope:
`評価・開始の最低取引日数：なし／出金周期の条件：5利益日（各0.5%以上）`

### 10. Fundora platform
Current official:
`cTrader`

Replace generic platform wording only after actual source inspection.

### 11. Blue Guardian Nano coverage
Current official models:
- 1 Step Nano
- 2 Step Nano

Do not add pricing until current checkout/purchase source is confirmed.

### 12. Blueberry Prime minimum days
Safe current wording after fresh check:
`現行新規購入は3日/Phase。旧購入条件・一部表示では5日を保持するため購入日を確認。`

### 13. FundingPips 2 Step Standard reward options
Avoid collapsing current structure to a single `7日／80%` if Production does so.

Current official options include:
- weekly60%
- bi-weekly80%
- monthly100%
- on-demand90% with conditions

### 14. FundingPips Zero profitable-day threshold
Where displayed, clarify:
`7 profitable days / rolling30, each >=0.25%`

### 15. Trading Cult Pro platform
Current official family uses MT5.

Generic platform wording may be changed to `MT5` after model-specific source check.

---

## HOLD — do not patch numeric value by choosing one side

### A. Funded7 One Phase
Official current-source conflict remains.

### B. Funded7 Instant
Official Max Loss / split and other fields conflict.

### C. Funded7 PAYG
Official sources conflict:
- challenge comparison: Daily5 / Max10
- official blog: Daily4 / Max8

Do not choose.
Need current purchase/configurator / dedicated rules / direct official confirmation.

### D. FTM Instant Pro
Official conflict remains:
- dedicated FAQ Daily3%
- other official Instant page includes no-Daily-DD language while comparison shows3%

### E. FundedElite Flash Activation exact option matrix
Pay-after-pass structure verified, but exact default-vs-custom:
- target
- reward split
- payout pace
- localized options
is not yet safe as one universal rule set.

### F. Blueberry Futures Accelerated 25K price
Current official conflict:
- homepage $110.40 standard / $44.16 at60%
- Help table $51.60 discounted, implying $129 standard

Keep price confirmation/HOLD state.

### G. The5ers Futures Max Loss locale discrepancy
Current EN product + June FAQ =4%
Current Portuguese official page =3%
Older May official article =3%/30 consistency

Use current primary EN value only with caution; do not claim official ecosystem is conflict-free.

### H. Fundora Professional/Master price surfaces
March 2026 official standard-price notice:
- Professional ¥249,999
- Master ¥449,999
Old shop pricing page remains live:
- ¥193,999 / ¥319,999

Current purchase JPY tab must be checked before any public price write.

### I. Fintokei NEW20 Japan scope
Global current official supports NEW20 20% first challenge.
Japan-scope checkout/direct official confirmation is still pending.
Do not call invalid; do not strengthen Japan applicability without evidence.

---

## DO NOT TOUCH

### The5ers Summer 200K
User confirmed current availability.
Status:
`DO_NOT_CORRECT / USER_CONFIRMED_CURRENT / OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING`

Static crawler absence must not be used as removal proof.

### Diagnosis protected logic
No changes to question set/order/scoring/eligibility/ranking in this correction bundle.

### Master / Affiliate / Coupon / Price protected layers
Only make the minimum source-specific correction required after reconciliation; no architecture migration bundled with factual corrections.

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
`POST_AUTH_CORRECTION_BUNDLE_PREPARED / AUTH_AND_PRODUCTION_RECONCILIATION_BLOCKING_IMPLEMENTATION`
