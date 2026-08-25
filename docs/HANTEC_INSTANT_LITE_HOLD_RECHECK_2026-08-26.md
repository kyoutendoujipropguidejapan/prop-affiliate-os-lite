# HANTEC INSTANT LITE HOLD RECHECK

更新日：2026-08-26 JST
Status：CURRENT OFFICIAL RECHECK COMPLETE / HOLD RELEASE NOT AUTOMATIC

## Purpose

旧M14 HOLDに含まれていた Hantec Trader `Instant Lite` について、2026-08-26時点の現行公式情報を再確認する。

この文書はHOLD自動解除を意味しない。Production source / original conflict / cohort差分を再照合し、中央承認後にのみStatus変更する。

## Current official sources

### Hantec Trader Help Center — Instant Lite

Official URL:
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite`

Current official baseline:

- Profit Target: None
- Maximum Daily Loss: 3%
- Daily loss basis: 00:00 server time, previous/end-of-day balance or equity whichever is higher
- Maximum Total Loss: 5%
- Total loss type: trails closed balance; after 5% profit it locks at starting balance
- Consistency: 20%
- Minimum profitable days for payout cycle: 5 days, each at least 0.5% profit
- Maximum trading period: None
- Standard reward split: 80%
- First standard reward request: 14 days after first trade
- Minimum reward request: $20
- Mandatory safety buffer: first 3% of profit remains in account
- EA / Robots: not allowed for Instant Lite
- Inactivity: at least one trade every 30 days

Add-ons listed by official Help Center:

- 95% Reward Share
- Weekly Payout: 7 days instead of standard 14
- Consistency Rule +5%: 20% → 25%
- Maximum Loss +1%: 5% → 6%
- Hold Over Weekend & News Trading

### Hantec Trader current product page — Instant Lite

Official URL:
`https://htrader.hmarkets.com/programs/instant-lite/`

The current product page independently supports the same base structure:

- no profit target
- Daily Loss 3%
- Maximum Total Loss 5% trailing balance
- Consistency 20%
- standard reward split 80%, up to 95% with add-on
- leverage 1:50
- no minimum trading days for the program itself
- virtually funded / simulated balance wording

Japanese product page:
`https://htrader.hmarkets.com/jp/programs/instant-lite/`

The Japanese page also displays Instant Lite base values of Daily Loss 3%, Maximum Total Loss 5% trailing, no profit target, Consistency 20%, standard 80% reward split with up-to-95% add-on.

Important parser/crawl caution: the long Japanese rendered page also contains neighboring Instant program content. Values such as 6% / 6% belong to other Instant product blocks and must not be mechanically attributed to Instant Lite by whole-page text extraction.

## Interpretation

As of this recheck, the current dedicated Help Center article and the current dedicated Instant Lite product page are materially aligned on the core Instant Lite base rules.

This reduces the likelihood that the old M14 HOLD still reflects a current official-source conflict. However, the old HOLD must not be removed solely from this recheck because:

1. the original M14 conflict evidence must be identified,
2. Production current source must be compared,
3. historical/cohort or add-on variants must remain separated,
4. any SourceHealth state must be reconciled,
5. central/human approval is required before HOLD release.

## Compliance / service-nature boundary

Use the firm's current wording carefully:

- virtually funded account / simulated balance
- simulated profits / reward share

Do not rewrite this into guaranteed real capital, deposit-taking, or investment-service language.

## Candidate transition

If Production reconciliation confirms no surviving conflicting source and the old M14 conflict is fully explained, candidate status:

`HOLD -> VERIFIED_WITH_CAUTION`

Not automatic.

Until then:

- Top3 block/HOLD protection remains where still active in Production
- do not promote to FAQ schema automatically
- do not use as definitive diagnosis evidence solely from this document

## Next gate

After internal Git authentication recovery:

1. inspect actual current Production source for Hantec Instant Lite,
2. identify original M14 HOLD conflict source,
3. compare current official Help Center/product page against Production data,
4. confirm add-on vs base separation,
5. central command decision on HOLD release.

Final status:
`OFFICIAL_RECHECK_SUPPORTS_RESOLUTION_CANDIDATE / PRODUCTION_RECONCILIATION_REQUIRED`
