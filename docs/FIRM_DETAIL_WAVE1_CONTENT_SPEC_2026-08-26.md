# FIRM DETAIL WAVE 1 CONTENT SPEC

Date: 2026-08-26 JST
Status: CONFIRMED FOR PRE-IMPLEMENTATION
Scope: Firm detail pages after the Fundora/Fintokei pilot is accepted.
Production code changes: NONE in this document.

## Purpose

Define the next four Firm detail pages so Work can implement them later without inventing content, changing diagnosis, or mixing commercial relationships into factual status.

Wave 1 firms:

1. PF004 Funded Trader Markets
2. PF008 Blueberry Futures
3. PF009 Trading Cult Pro
4. PF007 SuperFunded

This document inherits:

- FIRM_DETAIL_CONTENT_CONTRACT_2026-08-26.md
- COMPLIANCE_BASELINE_V1_2026-08-26.md
- M11_FIRM_FAQ_CONTENT_PACK.md
- M14_VERIFIED_EXTRACTION_FROM_PDF.md

No statement in this file overrides verified Production data, SourceHealth, or newer official evidence.

---

# Shared page structure

Use the shared Firm Detail template:

1. Breadcrumb / H1
2. Firm Snapshot
3. First three checks
4. Firm characteristics
5. Current plans
6. Major rules
7. Trading platform
8. Japan-specific checks
9. Payout
10. FAQ
11. Related guides
12. Price / Campaign / Coupon
13. Official / Affiliate CTA
14. Verification status / checked date
15. Disclosure / Disclaimer

Do not add star ratings, ranking, “best”, “safest”, or unsupported popularity claims.

---

# PF004 | Funded Trader Markets

## Proposed route

`/firms/funded-trader-markets/`

## SEO title

`Funded Trader Marketsとは？プラン・ルール・日本語対応を初心者向けに整理`

## H1

`Funded Trader Marketsを使う前に確認したいプラン・ルール・取引環境`

## Intro direction

Explain that the first distinction is evaluation-based plans versus Instant-type plans. Avoid implying Instant is easier, safer, or faster to profit.

## Primary content angle

- Separate evaluation and Instant families.
- Explain that similarly named plans must not inherit each other’s rules.
- Keep rule verification state visible.
- Japanese-language availability may be described only to the extent currently verified in Production or official evidence.

## Critical caution

`Instant Pro` remains blocked for unresolved rule inconsistency. Do not present disputed Daily Drawdown information as a settled value. Do not use it as a diagnosis Top3 basis. Do not include a HOLD FAQ in FAQ schema.

## FAQ application

M14 status:

- Q1 PASS
- Q2 HOLD
- Q3 PASS_WITH_CAUTION
- Q4 PASS
- Q5 PASS

Rules:

- Q2 may be shown only as an explicit “確認中” explanatory block if the current implementation policy permits visible HOLD content; otherwise omit it from public FAQ.
- Q2 must not be structured as FAQ schema.
- Q3 must preserve caution around current Japanese coverage and plan-specific rule verification.

## Compliance notes

- Do not describe the service as guaranteed real-capital funding unless the Firm’s current legal/service documentation explicitly supports that wording.
- If reviewer or promotional accounts were provided, disclose that relationship only on content that relies on that testing relationship; do not attach the disclosure mechanically to unrelated factual sections.
- Affiliate code/coupon must remain CTA-layer only.

## Future links

- Trading platform detail page: connect only when the corresponding platform route exists and mapping is verified.
- Payout: keep summary-only until accepted payout sources exist.

---

# PF008 | Blueberry Futures

## Proposed route

`/firms/blueberry-futures/`

## SEO title

`Blueberry Futuresとは？プラン・DD方式・取引環境を初心者向けに整理`

## H1

`Blueberry Futuresを使う前に確認したいプラン・DD方式・取引環境`

## Primary content angle

For this Firm, the clearest educational angle is the difference in drawdown method by product. Do not reduce the comparison to price.

## Verified editorial direction from M14

Use the updated language for Q2:

- Ascent is presented as EOD in the verified official product information.
- Accelerated is presented as Trailing in the verified official product information.
- The detailed calculation timing must still be checked in the relevant current rules before purchase.

Use the updated language for Q4:

- Official Help Center has a Japanese language option.
- Do not imply every plan-specific rule is available in Japanese to the same extent.

## FAQ application

M14 status:

- Q1 PASS
- Q2 UPDATE_REQUIRED
- Q3 PASS
- Q4 UPDATE_REQUIRED
- Q5 PASS

Use M14 U06 and U07 rather than older M11 wording for Q2 and Q4.

## Price boundary

Base evaluation price and temporary campaign discount are separate layers. Never overwrite base price with discounted campaign values.

At implementation time, use only the current Production-approved pricing layer. If a campaign is active, show it separately with status and end conditions.

## Compliance notes

- “Futures” product language must not be expanded into claims about brokerage, investment management, custody, or regulatory status without evidence.
- Do not imply the DD method alone determines ease of passing.
- Do not present Japanese-language Help Center availability as proof of complete Japanese support.

## Future links

- Future platform links should use verified Platform Registry mappings only.
- Future payout provider links remain disabled until accepted source data exists.

---

# PF009 | Trading Cult Pro

## Proposed route

`/firms/trading-cult-pro/`

## SEO title

`Trading Cult Proとは？プラン・ルール・取引環境を初心者向けに整理`

## H1

`Trading Cult Proを使う前に確認したいプラン・ルール・取引環境`

## Primary content angle

Explain the available model families only from current Production data. Do not infer that Tournament/Arena products are the same account/service as Prop challenge products unless officially mapped.

## FAQ application

M14 status:

- Q1 PASS
- Q2 PASS_WITH_CAUTION
- Q3 PASS
- Q4 PASS
- Q5 UPDATE_REQUIRED

Use M14 U08 for Q5:

- Coupon/referral applicability can vary by model and period.
- Show only operator-verified codes.
- Separate code, effect, target, and expiry.
- Final applicability is confirmed on the official purchase screen.

## Service separation

Where Trading Cult has multiple products, account systems, competitions, or Arena/Tournament experiences, do not merge them simply because they share branding.

If separate registration/account requirements exist, treat that as a separate product fact and verify before publication.

## Compliance notes

- Competition prize, starting capital, simulated balance, credit, reward, and cash payout must never be treated as interchangeable terms.
- If a displayed balance is simulation capital, do not call it prize money or distributable cash.
- Avoid “win money just by joining” type language unless exact official conditions support it.
- PR/Affiliate relationship must be visible near conversion CTA.

## Future links

- Platform pages only after verified Firm × Platform mapping.
- Tournament/Arena content should remain a separate product/content branch rather than being forced into the Firm’s challenge-plan data model.

---

# PF007 | SuperFunded

## Proposed route

`/firms/superfunded/`

## SEO title

`SuperFundedとは？プラン・ルール・取引環境を初心者向けに整理`

## H1

`SuperFundedを使う前に確認したいプラン・ルール・取引環境`

## Primary content angle

Keep the page rule-first. Any existing discount code or giveaway relationship is secondary and must not shape factual status or recommendation ranking.

## FAQ application

M14 status:

- Q1 PASS
- Q2 PASS
- Q3 UPDATE_REQUIRED
- Q4 PASS
- Q5 PASS

Use M14 U05 for Q3:

- Current official FAQ states no time limit in assessment and funded stage.
- Inactivity for 30 days may automatically close the account.
- Plan-specific conditions must still be checked in the corresponding rules.

## Testing/reviewer boundary

If internal review/testing encountered a specific account event, rule event, or balance treatment, do not generalize one account experience into a universal rule unless official evidence confirms it.

User experience evidence may be presented as a case observation, clearly labeled as such.

## Compliance notes

- Giveaway performance metrics are marketing-performance evidence, not proof of Firm quality.
- Affiliate discount must not influence diagnosis/ranking.
- “No time limit” must not be simplified into “no expiration under any circumstances”; inactivity and plan-specific conditions remain relevant.

## Future links

- Platform link only after verified mapping.
- Payout detail only after source acceptance.

---

# Wave 1 shared compliance gate

Before any of these four pages is published, confirm:

- Official URL and Affiliate URL are visually/functionally distinct.
- Affiliate disclosure is visible near conversion CTA.
- Sponsor/test-account disclosure is shown when relevant to the content being relied upon.
- No guaranteed profit, guaranteed payout, guaranteed pass, or safety claims.
- No unsupported “No.1”, “best”, “fastest”, “most popular”, “safest” claims.
- Japan eligibility is not described as Japanese regulatory approval.
- HOLD values are not silently converted to confirmed values.
- Unknown is not converted to unsupported/false/0.
- Current / campaign / legacy data are separate.
- All variable information has a checked date/status.
- FAQ schema excludes HOLD, coupon/referral, volatile eligibility, and other unsafe entries per M14 policy.
- Payout details are not fabricated from summaries or memory.
- No PII/KYC/bank/wallet data enters analytics.

---

# Acceptance condition for rollout

Wave 1 implementation may begin only after:

1. Fundora/Fintokei pilot accepted.
2. Current Production reconciled.
3. Protected Master/Diagnosis/GA4 boundaries confirmed.
4. No unresolved branch/authentication state affecting the Production implementation repository.
5. Each Firm’s current Production data and SourceHealth are re-read immediately before implementation.

If any required content conflicts with current official evidence, stop that Firm only; do not block unrelated Firm pages unless the conflict is shared infrastructure.

Status on conflict: `HOLD_FIRM_DETAIL_CONTENT`.
