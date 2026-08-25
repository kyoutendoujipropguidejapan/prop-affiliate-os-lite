# FIRM DETAIL WAVE 2 / WAVE 3 PREPARATION

Date: 2026-08-26 JST
Status: PRE-IMPLEMENTATION PREP COMPLETE
Production code changes: NONE

Purpose: Prepare the remaining Firm detail rollout after the Fundora/Fintokei pilot and Wave 1. This document does not authorize implementation by itself; current Production data must be re-read at implementation time.

Remaining Firms covered:

- PF005 The5ers
- PF006 Hantec Trader
- PF010 Blue Guardian
- PF011 Blueberry Funded
- PF002 Funded7
- PF012 FundedElite
- PF013 The5ers Futures
- PF014 FundingPips

The rollout is split by content risk, not by commercial priority.

---

# Wave 2 | Moderate complexity

## PF005 | The5ers

Proposed route:
`/firms/the5ers/`

Editorial angle:
- Do not force all programs into a simplistic 1-step / 2-step / 3-step taxonomy if current official Program selector uses a different current organization.
- Let users narrow by market/product/evaluation type first, then rules.

M14 FAQ status:
- Q1 UPDATE_REQUIRED
- Q2 UPDATE_REQUIRED
- Q3 PASS_WITH_CAUTION
- Q4 PASS_WITH_CAUTION
- Q5 PASS

Required copy replacements:
- Use M14 U03 for Q1.
- Use M14 U04 for Q2.

Compliance focus:
- Avoid implying every program has identical language/support/rule coverage.
- News-trading statements must preserve stage-specific conditions where applicable.
- Do not call The5ers generally “easy” or “beginner safe” based only on brand familiarity.

Future entity links:
- Keep CFD and Futures product families distinct when linking later.

---

## PF006 | Hantec Trader

Proposed route:
`/firms/hantec-trader/`

Editorial angle:
- Separate evaluation plans from Instant-type plans.
- Do not equate fewer evaluation stages with fewer restrictions.

M14 FAQ status:
- Q1 PASS
- Q2 HOLD
- Q3 PASS_WITH_CAUTION
- Q4 PASS
- Q5 PASS_WITH_CAUTION

Critical caution:
- M14 extraction contains a historical HOLD for Instant Lite FAQ content. Current Production state later recorded Hantec Instant Lite SH003 as resolved and blockTop3=false. Therefore implementation must use CURRENT PRODUCTION + newest evidence, not blindly reuse M14 HOLD.
- This is an explicit example of why Handoff historical documents cannot overwrite newer Production truth.

Implementation rule:
- At implementation time, compare current Production rule values to the latest verified official source.
- If current Production remains resolved and evidence is consistent, use current accepted state.
- If conflict reappears, return the affected content to conditional/HOLD; do not copy an older value mechanically.

Compliance focus:
- Japanese availability must not be expanded into complete Japanese rule coverage.
- Add-on/default loss limits must remain distinct if both exist.

---

## PF010 | Blue Guardian

Proposed route:
`/firms/blue-guardian/`

Editorial angle:
- Present current active, caution, listed-only, and legacy plans as separate states.
- Do not make the page look like every historically known plan is currently purchasable.

M14 FAQ status:
- Q1 PASS_WITH_CAUTION
- Q2 PASS
- Q3 PASS_WITH_CAUTION
- Q4 PASS_WITH_CAUTION
- Q5 PASS_WITH_CAUTION

Known Production state from current handoff history:
- 3 Step is legacy / diagnosis excluded.
- 1 Step Nano and 2 Step Nano are active but not automatically connected to Diagnosis.
- BNPL is active WITH_CAUTION and not automatically connected to Diagnosis.
- 1 Step Crypto is listed-only / HOLD.
- 1 Step Pro is legacy.

Implementation rule:
- Re-read current Production; do not hard-code this historical snapshot if newer data exists.
- Never connect plans to Diagnosis merely because they appear on the Firm page.

Compliance focus:
- “listed-only” must not look equivalent to “current verified active.”
- Crypto plan references require separate service/rule verification and must not be generalized from CFD plan facts.

---

## PF011 | Blueberry Funded

Proposed route:
`/firms/blueberry-funded/`

Editorial angle:
- Separate plan families and purchase-era variants.
- Treat “Instant” as a family label only; do not assume identical rules across Instant products.

M14 FAQ status:
- Q1 PASS_WITH_CAUTION
- Q2 UPDATE_REQUIRED
- Q3 PASS_WITH_CAUTION
- Q4 PASS_WITH_CAUTION
- Q5 PASS

Required copy replacement:
- Use M14 U09 for Q2.

Compliance focus:
- Old plan, current plan, Instant variant, and campaign must remain distinct.
- Payout statements must stay summary-only until accepted payout source records exist.

---

# Wave 3 | Higher caution / explicit blockers

Wave 3 Firms are delayed because at least one critical content area has a stronger HOLD/conditional burden, or because product-family separation requires extra validation.

## PF002 | Funded7

Proposed route:
`/firms/funded7/`

M14 FAQ status:
- Q1 PASS_WITH_CAUTION
- Q2 HOLD
- Q3 HOLD
- Q4 PASS
- Q5 UPDATE_REQUIRED

Critical blockers:
- 1-phase rule inconsistency remains a known block in current handoff state.
- Instant maximum-loss inconsistency remains a known block in current handoff state.

Required copy replacement:
- Use M14 U02 for Q5.

Implementation policy:
- Firm page may still exist while affected plans remain clearly “確認中”, but blocked values must not appear as settled comparisons or Diagnosis evidence.
- FAQ schema excludes Q2/Q3 while HOLD.

Compliance focus:
- PAYG/payment timing is not equivalent to lower total cost or easier qualification.
- Coupon eligibility varies; no automatic discount calculation.

---

## PF012 | FundedElite

Proposed route:
`/firms/fundedelite/`

M14 FAQ status:
- Q1 PASS_WITH_CAUTION
- Q2 PASS_WITH_CAUTION
- Q3 HOLD
- Q4 PASS
- Q5 PASS

Critical caution:
- Flash Activation is a known HOLD area in the current handoff state.

Implementation policy:
- Do not use HOLD Flash Activation data as a confirmed value.
- Page may launch without unresolved product detail if the remaining Firm-level content is sufficient and clearly scoped.

Compliance focus:
- Avoid implying activation/funded terminology has the same meaning across firms.

---

## PF013 | The5ers Futures

Proposed route:
`/firms/the5ers-futures/`

Editorial angle:
- Keep The5ers Futures separate from The5ers CFD Firm page while allowing brand-level related links later.

M14 FAQ status:
- Q1 PASS
- Q2 PASS_WITH_CAUTION
- Q3 UPDATE_REQUIRED
- Q4 PASS_WITH_CAUTION
- Q5 PASS

Required copy replacement:
- Use M14 U10 for Q3.

Known later handoff item:
- Day Trade 25K base price and no activation fee were subsequently confirmed as a price-display update candidate. At implementation time, verify that this remains current before displaying.

Compliance focus:
- Do not describe futures evaluation accounts as brokerage accounts or customer investment accounts without official basis.
- Drawdown explanation must preserve midnight/equity calculation nuance.

---

## PF014 | FundingPips

Proposed route:
`/firms/fundingpips/`

M14 FAQ status:
- Q1 PASS
- Q2 PASS
- Q3 PASS_WITH_CAUTION
- Q4 PASS
- Q5 PASS_WITH_CAUTION

Why Wave 3 despite no HOLD FAQ:
- Existing handoff notes identify a need to re-check Affiliate Help summary vs detailed tier/coupon purchase-screen differences (SH011 context).
- Commercial information must not bleed into factual Firm/rule status.

Implementation policy:
- Keep affiliate/coupon content late in the page and clearly separated.
- Re-check current Japan eligibility, product rules, and platform mapping immediately before implementation.

Compliance focus:
- Do not describe affiliate benefit as a universal customer discount unless the current purchase flow confirms applicability.

---

# Shared Wave 2/3 rule

The page template is allowed to omit unsupported sections. Visual uniformity is not a reason to invent values.

If one Firm has a blocker:
- hold that Firm or affected section only
- continue unrelated Firm work if shared infrastructure remains safe

No Wave 2 or Wave 3 release may change:
- DiagnosisLogicV2
- 7 questions/order
- score
- eligibility
- ranking
- Master structure
- affiliate influence on diagnosis/ranking

Final implementation status per Firm:
- `READY_FOR_FIRM_DETAIL_IMPLEMENTATION`
- `READY_WITH_CAUTION`
- `HOLD_FIRM_DETAIL_CONTENT`
