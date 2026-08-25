# FTM INSTANT PRO — HOLD RESOLUTION CANDIDATE

確認日：2026-08-26 JST
Status：CANDIDATE ONLY / HOLD NOT AUTO-RELEASED
Production code changes：NONE

## 1. Background

M14では`Funded Trader Markets | Instant Pro`がHOLD。主にDaily Drawdown等の公式情報不一致を安全側で扱ったもの。

2026-08-26の公式Web再確認で、Instant Pro専用FAQにcurrent-looking具体値が確認できたため、HOLD解除候補Evidenceとして整理する。

## 2. Current official signals

### Daily Drawdown

Official FTM FAQ：
- Maximum Daily Drawdown = 3% of Initial Balance
- 5 PM EST時点で前日Balance / Equityの高い方を参照する例を掲載
- Initial Balanceの3%幅を差し引いてstop-out limitを算出する説明

Source：
https://fundedtradermarkets.com/faq/how-does-the-maximum-daily-drawdown-limit-for-the-instant-pro-account-work

### Overall Drawdown

Official FTM Instant Pro FAQ search result / localized FAQ：
- Overall Drawdown Limit = 3%
- Maximum Balance Watermarkを基準とするtrailing overall drawdownとして説明

Source context：
https://fundedtradermarkets.com/faq/category/instant-funding-pro

### Consistency

Official FTM FAQ：
- Best day must not exceed 15% of total profit for payout eligibility
- exceeding does not by itself state immediate account breach; trader continues until ratio falls below threshold

Source：
https://fundedtradermarkets.com/faq/is-there-any-consistency-requirement-on-instant-funding-pro-account

### Minimum Trading Days / payout eligibility

Official FTM Japanese FAQ：
- Instant Standard / Pro / Plus：minimum 5 trading days for payout eligibility
- only days with at least 0.5% profit count

Source：
https://fundedtradermarkets.com/ja/faq/is-there-a-requirement-for-a-minimum-number-of-trading-days

### Profit Split

Official FTM FAQ：
- 1st reward 50/50
- 2nd 60/40
- 3rd 70/30
- 4th onward 80/20

Source：
https://fundedtradermarkets.com/faq/what-is-the-profit-split-offered-in-instant-funding-pro-account

### Maximum Allocation

Official FTM FAQ：
- Instant Pro max allocation per trader = $100,000

Source：
https://fundedtradermarkets.com/faq/what-is-the-maximum-allocation-for-instant-funding-pro-accounts

## 3. Candidate interpretation

2026-08-26時点のOfficial FAQ setでは、Daily DD 3%の具体的説明が存在し、Instant Pro専用FAQ内のoverall/consistency等と組み合わせてcurrent rule setを説明できる可能性が高い。

However：

- old conflicting sourceが現在も別公式pageに残っている可能性
- purchase page / Terms / dashboard ruleと差がある可能性
- Production SourceHealthの元Conflict sourceをまだ照合していない

ため、HOLDをこの文書だけで解除しない。

## 4. Resolution Gate

Work auth recovery / Production reconciliation後に：

1. M14 HOLDの元Conflict sourceを特定
2. current official Instant Pro FAQ setと比較
3. Terms / purchase displayのcurrent value確認
4. account cohort差の有無確認
5. SourceHealth conflictが実質解消したか判定
6. Central Command / human approval

全てPASSなら：

Candidate transition：
`HOLD -> VERIFIED_WITH_CAUTION` または適切なcurrent status

自動で`VERIFIED`へ上げない。

## 5. Compliance

`Instant Funding`という名称を実資金提供の保証として説明しない。

FTM page wordingが`Simulated Funded` / `Instant Simulated Funding`を使用している場合は、Firm Detailでもservice natureを保つ。

Final Status：
`FTM_INSTANT_PRO_HOLD_RESOLUTION_CANDIDATE_AWAITING_PRODUCTION_SOURCE_RECONCILIATION_AND_HUMAN_APPROVAL`
