# Hantec Trader Instant Lite Patch Spec 2026-08-24

確認日：2026-08-24 JST
対象：PF006 / P028 / Hantec Trader / Instant Lite
目的：SH003の再判定と、Master / Diagnosisへ渡す最小差分仕様を確定する。

重要：この文書だけでMaster / Diagnosis / 公開データを自動更新しない。DiagnosisLogicV2は変更禁止。

## 0. 結論

SH003は、2026-08-20更新の現行公式専用Helpを優先すると、旧「本文5% / Add-on欄6→7」の競合は解消している。

現行専用Helpの確定値：

- Profit Target：なし
- Daily Loss：3%
- Max Total Loss：5%
- DD：closed balance trailing → +5%利益到達後starting balanceでlock
- Consistency：20%
- Minimum Profitable Days：各Payout cycle 5日、各日0.5%以上
- First Payout：初回tradeから14日後
- Profit Split：80%標準
- News：high-impact / red-folder event 前後3分はopen / close不可
- Weekend：原則不可。金曜23:45 GMT+3までにclose
- Maximum Open Risk：starting balanceの1%
- EA / Robots：不可
- Mandatory Buffer：最初の3%利益はwithdraw不可

現行Add-on：

- Reward Share：80% → 95%
- Weekly Payout：14日 → 7日
- Consistency：20% → 25%
- Maximum Loss +1%：5% → 6%
- Weekend & News Trading：許可Add-onあり

## 1. 旧SH003の扱い

Master v2.2ではP028のMax Lossを「本文5% / Add-on記載は標準6%を示唆」とし、SH003 / Conflict / Diagnosis Blockにしている。

旧取得版のHelpには、Max Loss本文5%に対してAdd-on欄が「7%（standard 6%）」と表示される版が存在した。

一方、2026-08-20更新の現行専用HelpではAdd-on欄が「6%（standard 5%）」へ修正され、本文5%と整合した。

判断：

- SH003 status = RESOLVED
- resolution = 「2026-08-20更新のdedicated Instant Lite HelpでStandard 5% / Add-on 6%に収束」
- historical conflictは削除せず履歴として保持
- 古いキャッシュ / 旧版の6→7表記を現行値として再採用しない

## 2. P028 PlanCatalogV2 exact patch

変更する値：

- 全体の最大損失：`本文5% / Add-on記載は標準6%を示唆` → `5%（Max Loss +1% Add-on時6%）`
- DD方式：`Trailing→Lock` → `Closed Balance Trailing → +5%利益到達後Starting BalanceでLock`
- 最低取引日：`5 profitable days` → `Payout cycleごと5 profitable days（各日0.5%以上）`
- 出金・利益分配：`14日 / 80%` → `初回14日 / 80%（Weekly Payout Add-on 7日、95% Split Add-onあり）`
- ニュース取引：`±3分制限` → `高影響ニュース前後3分はOpen / Close不可（Add-onで許可可）`
- 週末持ち越し：`不可` → `不可（Add-onで許可可）`
- EA・コピー：`EA不可` → `EA / Robots不可`（Copy Tradingは今回この専用Helpだけでは新規推測しない）
- データ状態：`公式情報競合` → `確認済（旧版Conflict解消）`
- SourceHealth：SH003は参照を残してよいがstatusをRESOLVED化
- 注意点：`最大損失の同一ページ内不整合が解消するまで診断除外` → `Standard Max Loss 5%、+1% Add-on時6%。旧版6→7表記は履歴のみ`

追加保持候補：

- consistency_rule = 20%（Add-on 25%）
- open_risk = 1% of starting balance
- buffer = first 3% profit is mandatory non-withdrawable buffer
- minimum_request = $20
- inactivity = 30 days

変更しない値：

- Plan ID P028
- Firm ID PF006
- 種別 = インスタント
- 販売状態 = 販売中
- Profit Target = なし
- Daily Loss = 3%
- Free Trial = なし
- Japan = 利用可（既存値を維持。今回SH003解除の根拠には使わない）

## 3. DiagnosisPlanCurrent exact patch

対象：CV2-027 / P028相当

現行：

- Daily 3%
- Max Loss = conflict text / numeric null
- DD Trailing
- Min Days 5
- Payout 14日 / 80%
- News Restricted
- Weekend No
- Confidence 55
- Status Conflict
- Block Top3 Yes

更新候補：

- daily_loss = 3%
- daily_loss_numeric = 3.0
- max_loss = 5%
- max_loss_numeric = 5.0
- dd_type = Trailing
- min_trading_days = Payout cycle 5 profitable days
- payout = 14日 / 80%
- news = Restricted
- weekend = No
- confidence = 94を上限候補とする。ただし既存Confidence算定契約に従い、Workで勝手に再計算しない。明示的な既定値が必要なら既存Verified同等のルールを適用
- status = Verified / Resolved
- Block Top3 = No
- source = dedicated Instant Lite Help
- caution = `Max Loss +1% Add-on時6%。旧版SH003は解消履歴として保持`

DiagnosisLogicV2自体は一切変更しない。

## 4. Minimum Trading Daysの表現

Hantec商品ページには「No minimum trading days」と表示される一方、専用Helpには「Minimum Profitable Days - 5 days / Each payout cycle」とある。

これは評価期間が存在しないInstantの「開始条件なし」と、Payout eligibilityの「各cycle 5 profitable days」が別スコープ。

公開表現は：

`開始までの最低取引日数なし / 出金cycleでは5 profitable days`

と分離する。どちらか片方を削除して矛盾扱いにしない。

## 5. 現行ソースの優先順位

最優先：Dedicated Instant Lite Help（2026-08-20更新）

商品ページもDaily 3% / Max 5%を先頭のInstant Lite欄で確認できる。ただし日本語商品ページ下部には別Instant Programの6% / 6%セクションが連結表示されるため、Instant Liteの値として混同しない。

旧HelpキャッシュではAdd-on 7% / standard 6%が残る取得版があるが、最新更新版は6% / standard5%へ修正済み。

## 6. Block影響

現行Block 6のうちHantec Instant Liteを解除候補とする。

他5件は維持：

- Fintokei 速攻プロ
- Funded7 1フェーズ
- Funded7 Instant
- FTM Instant Pro
- FundedElite Flash Activation

したがってHantec解除承認後のBlock見込み = 5。

Blue Guardian 3 StepのLegacy化はBlock解除/追加ではなくDiagnosis母集団からの除外として別処理する。

## 7. 公式一次情報

- Instant Lite dedicated Help: https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite
- Instant Lite product: https://htrader.hmarkets.com/programs/instant-lite/
- Instant Lite JP product: https://htrader.hmarkets.com/jp/programs/instant-lite/

## 8. Workへ渡す時の禁止

- 旧SH003の6% / 7%を現行標準値として採用しない
- Add-on 6%を標準Max Lossとして入れない
- 5 profitable daysを「開始までの最低日数」と誤表示しない
- Block件数を合わせるために他の未確認プランを解除しない
- DiagnosisLogicV2を変更しない

## Status

- Hantec Instant Lite source research: COMPLETE
- SH003: RESOLVED_FOR_PATCH
- P028 Master mapping: READY
- Diagnosis unblock: READY_FOR_REVIEW
- Master write: NOT_STARTED
- Work implementation: NOT_STARTED
