# SHORT-TERM FIRM OFFICIAL RECHECK

確認日：2026-08-26 JST
Status：OFFICIAL WEB RECHECK / NO PRODUCTION PATCH
Production code changes：NONE

Google Drive `prop-firm-official-info-ledger` で2026-08-26を次回確認日としていた主要Firmを中心に、公式一次情報を再確認した。

## 1. Funded Trader Markets

### Japanese surface

公式日本語FAQ surfaceを確認。

Current official FAQ examples：
- Nitro evaluation：evaluation minimum trading daysなし
- 2-Step Plus：各evaluation phase最低3日
- Simulated Funded：payout eligibilityは最低5 trading days
- qualifying dayは少なくとも0.5% profit
- Instant Standard / Pro / Plus：payout eligibilityは最低5 trading days

Official source：
- https://fundedtradermarkets.com/ja/faq/is-there-a-requirement-for-a-minimum-number-of-trading-days

### Instant Pro Daily Drawdown

Official English FAQでCurrent answerを確認：
- Maximum Daily Drawdown = 3% of Initial Balance
- daily stop-out calculation exampleでは前日EOD Balance / Equityの高い方にinitial balanceの3%幅を適用する説明あり

Source：
- https://fundedtradermarkets.com/faq/how-does-the-maximum-daily-drawdown-limit-for-the-instant-pro-account-work

### Important reconciliation note

M14 historical HOLDは古いConflict時点の安全判断。Current official FAQに具体的Daily DD answerが存在することは新しいSignal。

ただしHOLD解除は自動で行わない。Current Production SourceHealth / related official Instant Pro pagesと照合してから解除判断する。

Status：
`FTM_RECHECK_NEW_OFFICIAL_SIGNAL_REQUIRES_SOURCEHEALTH_RECONCILIATION`

## 2. The5ers / The5ers Futures

Official Futures pageを再確認：
- Day Trade 25K Price = $59
- Activation fee = None
- Profit Target 6% evaluation / 4% funded stage
- Max Loss (EOD) 4%
- 2 Mini / 20 Micro
- one-time fee structure / no monthly feesの説明

Source：
- https://www.the5ers.com/futures/

Price gap recheckとも一致。

Status：
`THE5ERS_FUTURES_CURRENT_25K_DAY_TRADE_CONFIRMED`

## 3. SuperFunded

Official FAQ recheck：

Profit Cap：
- first 3 successful payoutsにtemporary cap
- 1 Step：all account sizes 5%
- 2 Step：FAQではhistorical cohort差を記載し、2025-09-10以降開始の2-Stepはall account sizes 5%
- capを超えるwithdrawal requestのextra amountはcarry overしない旨の説明

Source：
- https://superfunded.com/faqs/

Official Rules and Conditions V2.0も確認：
- 1 Step / 2 Step max drawdown structure
- minimum trading days
- inactivity 30 days等

Source：
- https://superfunded.com/wp-content/uploads/2026/01/SuperFunded-Rules-and-Conditions.pdf

### Service-nature / compliance signal

SuperFunded日本語Product pageのrisk disclosureでは：
- educational purpose
- not broker
- deposits not accepted
- third-party technical/data-feed solutions
等の説明がある。

Firm Detailではmarketing記事の`大きな資金を運用`等を本サイト独立表現として採用せず、Rules / risk disclosureのservice natureを優先する。

Status：
`SUPERFUNDED_RECHECK_PASS_WITH_COHORT_CAUTION`

## 4. Governance

このrecheckで：
- Masterを自動更新しない
- SourceHealthを自動resolveしない
- Diagnosis blockを自動解除しない
- Commercial link/commissionをverificationに使わない

Work再入場後、Current Productionとの差分を確認して必要な項目だけ最小patchする。

Final Status：
`SHORT_TERM_OFFICIAL_RECHECK_COMPLETE_PRODUCTION_RECONCILIATION_PENDING`
