# PUBLIC LP POST-AUTH CORRECTION BUNDLE — ADDENDUM WAVE19–21

更新日：2026-08-26 JST
Status：CURRENT ADDENDUM / APPLY WITH MAIN BUNDLE AFTER AUTH + PRODUCTION RECONCILIATION
Parent：`docs/PUBLIC_LP_POST_AUTH_CORRECTION_BUNDLE_2026-08-26.md`

## Purpose

Wave19–21で追加確認された修正・Evidence backfill項目のみを親Bundleへ追補する。
親Bundleの既存項目を削除・上書きするものではない。

## P0 factual correction

### SuperFunded minimum payout
Current public payout route is overly conservative if it says an official minimum could not be confirmed.

Current governing official Rules V2.0 states:
- Minimum Payout = $100
- profit share applied before threshold check
- standard payout waiting period = 14 days

Safe correction after fresh implementation-time Check3:
`最低申請額：利益配分適用後$100（現行Rules V2.0）。プラン固有の条件・Add-onは申請前に確認。`

## P0 conflict-safe correction already confirmed

### Funded7 PAYG Daily/Max
Keep exact Daily/Max in HOLD.
Public route must not present `4% / 8%` as unqualified current truth while current official-source conflict remains.

Verified and safe to retain:
- staged payment architecture
- profit targets8% /6% where current source remains aligned
- PAYG distinct current model
- PAYG monthly payout cap $20,000

## P1 wording update

### FundedElite route wording
Prefer current English product architecture over `日本語購入画面に独立プラン` as the primary current fact.

Safe wording:
`Flash Activationは5ドルから開始し、合格後にActivation費用を支払う1-Step型。口座サイズ・アドオン・最終Activation費用は購入画面で確認。`

Core flow is verified; exact customization matrix remains HOLD.

## No correction / verified scope

### Trading Cult Pro Pay After Pass
Current detailed public block is materially supported for:
- $9.99 entry
- 1-Step /2-Step
- remainder payment within14 calendar days after pass
- funded80% split
- PAP-funded Max Loss3% / trailing3%
- min5 trading days before payout
- valid day >=1% profit
- stability25% /30%
- min trade hold30 seconds

Keep PAP rules clearly separated from non-PAP/standard account rules.

## Evidence backfill — commercial

### Funded7 `KYOUTENP`
Public claim: `利益配分 +10%` for PAYG.
Status:
`PARTNER_EVIDENCE_REQUIRED / DO_NOT_INVALIDATE`

Before strengthening/republication, retain:
- checkout acceptance/current effect OR partner-portal record
- independent current direct official confirmation
- fresh pre-publish check

### Blanket code-validity wording
Avoid unqualified:
`掲載コードは有効です`

Preferred until each exact code/effect has retained evidence:
`掲載コードは運営者が有効性を確認したものです。割引率・対象・併用可否・最終適用は購入画面で再確認してください。`

Full queue:
`docs/AFFILIATE_CODE_EVIDENCE_BACKFILL_QUEUE_2026-08-26.md`

## CTA compliance reminder

For Home and payout/commercial routes:
- official information link -> clean official URL
- conversion CTA -> affiliate/referral URL
- nearby `PR` disclosure

Do not remove monetization; separate purpose and destination.

## Summer200K boundary

No change:
- no deletion instruction exists
- do not remove or convert to100K-only
- dynamic official purchase/support recheck is required only before future detailed rewrite

## Release gate

Nothing in this addendum is implemented until:
1. internal Git auth restored
2. actual Production source reconciled
3. fresh Check3 per changed fact
4. tests/protected hashes/390px/compliance pass
5. central/human publish approval

Final Status：
`ADDENDUM_WAVE19_21_READY_NO_PRODUCTION_CHANGE`
