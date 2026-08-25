# FundedElite Flash Activation option-matrix recheck

更新日：2026-08-26 JST
目的：M14 HOLD中の FundedElite Flash Activation について、現行公式情報の base/default 条件と customizable/add-on 表現を再照合する。Production変更は行わない。

## 結論

Status：`HOLD_CONTINUES_OPTION_MATRIX_INCOMPLETE`

現行公式情報から base/default 条件は再確認できる一方、ランディングページは「Profit Target as Low as 2%」「Up to 95% Profit Split」「Customizable Rules」「profit target / max loss limit / payout pace を選択」と明示している。FAQの base/default 6% / 3% / 6% / 80% / 14日 と両立し得るが、購入時に選べる正確な option matrix が公開テキストだけでは確定できないため、HOLD解除はしない。

## 公式再確認

### Dedicated FAQ — base/default

Source:
- https://faq.fundedelite.com/en/articles/12683940-flash-activation-challenge
- https://faq.fundedelite.com/ja/articles/13645496-フラッシュアクティベーションチャレンジ

確認できた内容：
- 1-step evaluation
- entry fee starts at $5; account size / add-ons により変動し得る
- Evaluation Profit Target 6%
- Daily Drawdown 3%
- Maximum Drawdown 6%
- Evaluation DD type Static
- Evaluation minimum trading days なし
- pass後 KYC / trader agreement / activation fee
- standard activation fees: 25K $159 / 50K $329 / 100K $499 / 200K $989
- activation fee は add-ons 選択時に変動し得る
- Live Daily Loss 3%
- Live Total Drawdown 6% trailing
- Live profitable days 3日、各日 0.5%以上
- consistency: best day <= 30% of total profit
- Profit Split 80%
- payout request every 14 days
- no minimum payout requirement

### Current product landing page — customization layer

Source:
- https://www.fundedelite.com/challenges/flash-activation

確認できた表現：
- Start any account for $5
- Up to 95% Profit Split
- Customizable Rules
- target as low as 2%
- “start from 6% or go as low as 2%”
- Customize Your Flash Activation Challenge
- choose profit target, max loss limit, payout pace

## Interpretation boundary

現時点の安全な解釈：
- FAQの 6% / 3% / 6% / 80% / 14日 は base/default 条件として扱える。
- Landing pageの 2% / 95% / customizable は option/add-on layer の存在を示す。
- ただし「どの選択肢が、どの口座サイズで、価格・DD・profit split・payout cadence とどう組み合わさるか」は公開テキストだけでは確定していない。
- したがって base/default を唯一の現行仕様として表示しない。
- 逆に marketing headline の 2% / 95% を標準条件として表示しない。

## HOLD解除に必要なもの

1. Current checkout/configurator の選択肢一覧
2. Profit Target options
3. Max Loss options
4. Profit Split options
5. Payout cadence options
6. optionごとの追加料金/activation feeへの影響
7. account-size別差分
8. current Terms/FAQとの整合
9. original M14 SourceHealth conflictとの照合
10. Central Command / human approval

## Publication rule

HOLD中は Firm Detail / FAQ / Comparison で以下を守る：
- `公式情報を確認中` または同等の caution status
- base/default と option layer を混同しない
- 2% / 95% を標準条件として断定しない
- 6% / 80% を全購入構成に共通する条件として断定しない
- checkout/configurator の実表示が取得できるまで option matrix を推測しない

## Compliance note

Landing page上の “funding”, “funded account”, “instant payouts”, “life-changing capital” 等は事業者のmarketing wordingであり、当サイトの独立した法的・サービス性質の断定として転用しない。Firm Detailでは current Terms / FAQ / service-nature evidence を優先する。
