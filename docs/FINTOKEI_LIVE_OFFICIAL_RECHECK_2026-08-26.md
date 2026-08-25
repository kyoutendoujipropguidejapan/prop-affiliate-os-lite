# FINTOKEI LIVE OFFICIAL RECHECK

確認日：2026-08-26 JST
Status：OFFICIAL WEB RECHECK / PRODUCTION PATCH NOT APPLIED
Production code changes：NONE

## 1. Purpose

Public surfaceでFintokei速攻プロに旧Conflict-style表示が残っているSignalがあったため、2026-08-26時点のFintokei公式日本語Site / FAQを再確認する。

この文書はProduction Masterを自動更新しない。Work再入場後のCurrent Truth reconciliation材料とする。

## 2. SwiftTrader / 速攻プロ — 2026-07-15以降購入口座

公式FAQで明確にcohort分離を確認。

2026-07-15以降購入口座：

- Evaluation：1 step
- Profit Target：6%
- Daily Loss：2%（有効証拠金基準）
- Max Loss：3%（初期資金基準）
- Minimum Trading Days：3日
- Maximum Trading Days：60日（evaluationのみ）
- inactivity：30日間に少なくとも1つの新規取引またはclose取引が必要
- evaluation daily max profit restriction：初期資金の3%
- ProTrader reward target：初期資金の3%

公式Product pageでも、6% / 最低3日 / Daily -2% / Overall -3% / 1 stepを一致確認。

Sources：
- https://support.fintokei.com/ja/articles/12040973-
- https://support.fintokei.com/ja/articles/8409176-
- https://www.fintokei.com/jp/swifttrader/

## 3. SwiftTrader — 2026-07-15より前の口座

旧口座は別条件として公式FAQに残る。

確認できる旧条件：

- Max Loss：6%
- Daily Loss：3%
- Minimum Trading Days：5日
- evaluation targetは公式FAQ記事間でhistorical wording差がある可能性があるため、旧口座本文を新規購入向け表示へ混ぜない
- maximum trading days：旧口座は60日制限対象外と公式FAQに記載

結論：

`OLD_ACCOUNT_CONDITIONS != CURRENT_NEW_PURCHASE_VARIANT`

## 4. Public surface discrepancy

2026-08-26 public crawlでは速攻プロが以下のConflict-styleで表示されていた：

- 10% / 6%
- 3% / 2%
- 6% / 3%
- 5日 / 最短3日

公式一次情報再確認により、**新規購入向けcurrent cohortは6% / 2% / 3% / 3日として公式整合を確認**。

ただしProduction patchはこのChat taskでは行わない。

Work再入場時：
- actual current source
- M14 applied state
- public render source
を照合し、なぜConflict表示が残っているかを特定する。

## 5. Platform official recheck

Fintokei公式FAQで現行Platformを確認：

- MT4
- MT5
- cTrader
- TradingView connection via cTrader context

さらに、チャレンジ / 入門 / 速攻はMT4・MT5・cTraderで利用可能と公式FAQに記載。
チャレンジ・スリムはMT5専用と記載。

Source：
- https://support.fintokei.com/ja/articles/6538834-

この情報はFirm × Platform mapping候補だが、canonical relation登録はPlatform Phaseまで行わない。

## 6. Fintokei Academy official recheck

Fintokei公式FAQ Collectionで`Fintokeiアカデミー` 12記事を確認。

公式説明：
- trading learning app
- lesson
- quiz
- simulation trading
- trading analysis
- roadmap / XP / levels / milestones / benefits
- Academy内tradeはsimulation / virtual environment

Academy XPはアプリ内progress indicatorとして公式説明されている。

Sources：
- https://support.fintokei.com/ja/collections/19647391-fintokei%E3%82%A2%E3%82%AB%E3%83%87%E3%83%9F%E3%83%BC
- https://support.fintokei.com/ja/articles/15516282-
- https://support.fintokei.com/ja/articles/15516660-

### Important boundary

公式Academy記事だけから、特定の`50% OFF`特典をcurrent universal benefitとして確定できなかった。

したがって：
- Academy存在 / 学習機能 / XP / benefit unlock concept = VERIFIED_OFFICIAL
- `50% OFF`の具体的current condition = SEPARATE EVIDENCE REQUIRED / PREPUBLICATION RECHECK

Academy XPとMyFintokei本体Point Stage XPを同一制度として扱わない。

## 7. Service nature / compliance

Fintokei公式FAQは明確に：

- education / evaluation company
- customer deposits for real tradingを集めない
- financial servicesを提供しない
- provided trading accounts are virtual demo environments
- not a broker

と説明している。

Firm Detailではこの公式service natureに合わせ、`実資金を提供される`等の表現を避ける。

Source：
- https://support.fintokei.com/ja/

## 8. Recommended reconciliation outcome

Work再入場後、current source treeが公式recheckと矛盾しない場合：

- current new-purchase SwiftTrader variant：6% / 2% / 3% / min 3 days / max 60 days
- historical cohort：separate
- public Conflict-style表示：remove only after source/data wiring reason confirmed
- Academy：existence and learning entry can be public
- Academy 50% offer：accepted evidence conditionを再確認してから表示

Final Status：
`FINTOKEI_OFFICIAL_RECHECK_CURRENT_VARIANT_VERIFIED_PRODUCTION_RECONCILIATION_PENDING`
