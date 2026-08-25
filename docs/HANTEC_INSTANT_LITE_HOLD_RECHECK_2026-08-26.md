# HANTEC INSTANT LITE HOLD RECHECK

更新日：2026-08-26 JST
Status：CENTRAL APPROVED / VERIFIED_WITH_CAUTION / PRODUCTION RECONCILIATION REQUIRED

## Purpose

旧M14 HOLDに含まれていた Hantec Trader `Instant Lite` について、2026-08-26時点の現行公式情報を最低3回再確認し、中央承認後の扱いを固定する。

Production sourceは内部Git認証HOLD中のため、本書の承認はProduction変更・publishを意味しない。

## Current official sources

### Check 1 — Hantec Trader Help Center — Instant Lite

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

### Check 2 — Hantec Trader current EN product page — Instant Lite

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

### Check 3 — Hantec Trader current JP product page — Instant Lite

Official URL:
`https://htrader.hmarkets.com/jp/programs/instant-lite/`

The Japanese page also displays Instant Lite base values of Daily Loss 3%, Maximum Total Loss 5% trailing, no profit target, Consistency 20%, standard 80% reward split with up-to-95% add-on.

Important parser/crawl caution: the long Japanese rendered page also contains neighboring Instant program content. Values such as 6% / 6% belong to other Instant product blocks and must not be mechanically attributed to Instant Lite by whole-page text extraction.

## Original M14 context

`M14_VERIFIED_EXTRACTION_FROM_PDF.md` listed Hantec Trader Instant Lite among five HOLD items but did not preserve the full original conflict evidence in the extracted summary.

The current three-way official recheck explains the previously observed 5% / 6% discrepancy as:

- standard Maximum Total Loss = 5% trailing
- optional `Maximum Loss +1%` add-on = 6%

Therefore the two values must not be treated as competing standard rules.

## Central decision — 2026-08-26

User/central command approved proceeding with the proposed resolution.

Status transition approved:

`HOLD -> VERIFIED_WITH_CAUTION`

Approved current display:

`標準5% Trailing（決済後残高追随→5%利益到達後に開始残高でLock）／+1% Max Loss Add-onで6%`

Trading-day wording must be scope-separated:

`評価・開始の最低取引日数：なし／出金周期の条件：5利益日（各0.5%以上）`

## Remaining caution

This approval does not erase cohort/add-on distinctions and does not authorize an immediate Production edit.

Before Production implementation:

1. inspect actual current Production source for Hantec Instant Lite,
2. confirm no surviving hidden/variant source conflicts with the approved base/add-on interpretation,
3. preserve standard vs add-on separation,
4. run a fresh third-check immediately before edit,
5. regression / protected hashes / 390px / compliance,
6. human approval for Production publish.

## Compliance / service-nature boundary

Use the firm's current wording carefully:

- virtually funded account / simulated balance
- simulated profits / reward share

Do not rewrite this into guaranteed real capital, deposit-taking, or investment-service language.

Final status:
`VERIFIED_WITH_CAUTION_CENTRAL_APPROVED / PRODUCTION_RECONCILIATION_REQUIRED`
