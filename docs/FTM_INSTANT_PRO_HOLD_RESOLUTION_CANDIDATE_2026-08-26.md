# FTM INSTANT PRO — HOLD RECHECK

確認日：2026-08-26 JST
Status：CURRENT OFFICIAL CONFLICT CONFIRMED / KEEP HOLD
Production code changes：NONE

## 1. Background

M14では`Funded Trader Markets | Instant Pro`がHOLD。主因はDaily Drawdown等の公式情報不一致。

2026-08-26の再確認で、Instant Pro専用FAQ / variation matrixはDaily Drawdown 3%へ収束している一方、同じ公式domainのInstant Funding marketing pageに`no Daily Drawdown Limit`表記が現在も残っていることを確認した。

したがって、HOLD解除候補ではなく**current official conflict継続**として扱う。

## 2. Current official signals

### A. Dedicated Instant Pro FAQ — Daily Drawdown 3%

Official FTM Help Center：
- Maximum Daily Drawdown = 3% of Initial Balance
- 5 PM EST時点でBalance / Equityの高い方を参照する例
- Initial Balanceの3%幅を差し引いてstop-out limitを算出
- breachするとaccount violated / closed / disabledと説明

Source：
https://intercom.help/fundedtradermarkets/en/articles/10152114-how-does-the-daily-drawdown-limit-for-the-instant-pro-account-work

### B. Official variation / current comparison — Daily Drawdown 3%

Official FTM variation pageのInstant Pro表示：
- Max Overall Drawdown 3%
- Max Daily Drawdown 3%
- Profit Split Up to 80%

Source example：
https://fundedtradermarkets.com/variations?category=instant&program=instant-pro

Localized variation pagesも同じ3% / 3%構造を表示する。

### C. Official Instant Funding marketing page — contradictory `no Daily Drawdown Limit`

同じFTM公式domainのInstant Funding紹介ページでは、Instant Proの紹介コピーに現在も：

`no Daily Drawdown Limit`

相当の表現が残る。

同じページ下部のcomparison matrixではInstant Pro Daily DD 3%と表示されるため、**同一公式ページ内でもmarketing copyとrule matrixが不一致**。

Source example：
https://fundedtradermarkets.com/de/ftm-instant-funding

この不一致は失格条件に直結するため、単なるコピー差として無視しない。

## 3. Other current Instant Pro signals

### Overall Drawdown

- Overall Drawdown 3%
- trailing / maximum-balance-watermark系の説明が専用FAQに存在

### Consistency

- Best day <= 15% of total profit for payout eligibility
- 超過時は比率が下がるまで追加利益が必要

### Minimum Trading Days / payout eligibility

- minimum 5 qualifying trading days
- each qualifying day >= 0.5% profit

### Profit Split

- 1st reward 50/50
- 2nd 60/40
- 3rd 70/30
- 4th onward 80/20

### Maximum Allocation

- Instant Pro max allocation per trader = $100,000

これらはDaily DD conflictを解除する根拠にはしない。

## 4. Decision

Current status：

`KEEP_HOLD`

理由：

1. scoring / breach criticalなDaily DDについて公式内矛盾が現存
2. dedicated FAQ / matrixは3%だがmarketing pageはno limit表記
3. official source precedenceを勝手に決めて一本化できない
4. Diagnosis / FAQ Schemaへ確定値として流すと誤案内リスクがある

## 5. Resolution Gate

解除条件：

1. FTMがmarketing copyを修正し公式表示が収束する、または
2. FTMから書面でInstant Proの優先ルールを明示する
3. current Production SourceHealthを再照合
4. cohort / purchase date差がないことを確認
5. central / human approval

上記までHOLDを維持する。

## 6. Publication / Diagnosis Policy

HOLD中：

- Diagnosis Top3根拠に使わない
- FAQ schemaへ確定ルールとして入れない
- `Daily DDなし` / `Daily DD 3%`のどちらか一方を独断で正本化しない
- public detailで扱う場合は`公式情報に不一致あり / 確認中`とする

## 7. Compliance

`Instant Funding`という名称を実資金提供の保証として説明しない。

FTMの`Simulated Funded` / `Instant Simulated Funding`等のservice-nature wordingを保持する。

Final Status：
`FTM_INSTANT_PRO_KEEP_HOLD_CURRENT_OFFICIAL_CONFLICT_CONFIRMED`
