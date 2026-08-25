# PLATFORM HUB CONTENT SPEC

更新日：2026-08-26 JST
Status：CONTENT SPEC CONFIRMED
Production code changes：NONE

## 1. Route

Future route：`/platforms/`

Public implementationはFirm Detail foundation後までHOLD。

## 2. Purpose

初心者が「どの取引プラットフォームが良いか」ではなく、

- 何が違うのか
- どこを確認すればよいか
- Firmによって何が変わるのか

を理解する入口にする。

## 3. Canonical platform scope

- MetaTrader 5
- MetaTrader 4
- TradeLocker
- cTrader
- Match-Trader
- DXtrade
- BlackArrow
- Quantower
- Volumetrica

## 4. Recommended page order

1. Breadcrumb / H1
2. 取引プラットフォームとは
3. 最初に見る4点
4. 9 Platform card list
5. Platformによって違うこと
6. Firmによってさらに違うこと
7. 初心者Glossary
8. Platform比較への将来導線
9. Firm Detailへの導線
10. Verification / checked date
11. Disclaimer

## 5. First 4 checks

初心者向け比較軸：

1. 利用形態：Web / Desktop / Mobile
2. 注文・チャート操作
3. Market Data / DOM等の高度機能
4. Firm側の制限・有効化範囲

価格やAffiliateをHubの主役にしない。

## 6. Card contract

各Platform cardは最低限：

- name
- short neutral description
- availability surfaces where verified
- beginner check point
- status / checked date
- detail link（detail page公開後のみ）

禁止：
- ranking number
- star rating
- fastest / best / safest labels
- unsupported user counts
- Firm usage count before verified mapping

## 7. Cross-link rule

Hub → Detail：Detail pageがpublicかつQA済みの場合のみ。

Hub → Firm：Firm × Platform relationがacceptedの場合のみ。

Dead-link placeholder禁止。

## 8. Compliance

Required text concept：

`同じ取引プラットフォームでも、プロップファームごとに利用できる機能・銘柄・市場データ・注文条件・口座仕様は異なる場合があります。Platform名だけでFirmの利用条件を判断せず、各Firmの最新情報をご確認ください。`

## 9. SEO

Suggested Title：
`プロップファームの取引プラットフォーム比較｜MT5・TradeLocker・cTraderなどを初心者向けに整理`

Suggested H1：
`プロップファームの取引プラットフォームは何が違う？初心者向けに整理`

No index until release gate PASS.

## 10. Acceptance

- 9 canonical platform coverage
- ranking bias 0
- Affiliate influence 0
- dead links 0
- Firm-specific claims without relation evidence 0
- unique purpose vs Firm pages

Final Status：
`PLATFORM_HUB_CONTENT_SPEC_CONFIRMED`
